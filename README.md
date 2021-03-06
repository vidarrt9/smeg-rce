# Reverse engineering the SMEG+I

> Hey there, perhaps you'd also like to [take a peek into our Wiki](https://github.com/vidarrt9/smeg-rce/wiki)?

The SMEG+I is an enhanced version of the original SMEG, both apparently manufactured by Magneti Marelli for PSA.

This repository is mainly about the SMEG+I, not about the original SMEG or the successor which is called SMEG+Iv2. You can generally tell them apart by looking at the firmware version number:

* SMEG: 3.x, i.e. some version in the version 3 range
* SMEG+I: 5.x
* SMEG+Iv2: 6.x

From here on and also in the Wiki whenever you read **SMEG+** you will have to make a mental note that **this refers to the SMEG+I specifically**, although a lot of the details will also be applicable to its predecessor (SMEG) and successor (SMEG+Iv2). There also seem to be several parallels to other even older onboard entertainment systems.

Much of the information you can find here is deduced from observing the behavior of the SMEG+, looking at the firmware and map update packages and of course by looking at and interacting with the hardware.

Only [one official document](https://fccid.io/ANATEL/00719-14-05386/MANUAL/DADF0ABD-43AA-405C-8165-C6B5BEC8D0EC/PDF) (named `SMEG+I_HW Technical Datasheet_V1.pdf`) is known pertaining to the hardware specifications of the SMEG+I. If you know others, _please_ open a ticket or drop me a mail at the address you can find from the Git commits. Your best bet in general when looking for information is to use terms from the glossary in the project Wiki and operators. And while we loathe Google for daily use you can't beat its reach for this sort of thing. A search for `SMEG+I site:fccid.io` or `SMEG+Iv2 site:fccid.io` respectively is your best bet. What it does is to limit the scope of the search to `fccid.io` and subdomains and then looks for the other given term or terms. If you want to know more it's worthwhile reading up on Google's search operators.

**NB:** We are intentionally only linking. Reverse engineering efforts in the EU are perfectly legal within certain limits, but reproducing a document to which we don't hold the copyright could lead to some serious trouble. In order for all of us - who may now or in future be interested in this hardware and the software that runs on it - to be able to access the documents, we encourage the use of the [Internet Archive Wayback Machine](https://web.archive.org/save). Whenever you encounter a useful page and visit it, make sure to also copy the URL, visit the Internet Archive Wayback Machine and queue it to be archived there. This will ensure that in the future we all have access to these documents as much as possible without any copyright infringement. Not all content can be archived this way, so you may want to reach out to any contributors of this project (with its repository and Wiki).

## Links to resources that we found useful

For some of these you will want to use machine translation or -- if you can afford it -- learn the language in question to grasp the meaning.

* [ANATEL 00719-14-05386](https://fccid.io/ANATEL/00719-14-05386) is a link leading to an overview page which contains links to documents pertaining to SMEG+I (which this project is all about).
    * The link named [MANUAL](https://fccid.io/ANATEL/00719-14-05386/MANUAL/DADF0ABD-43AA-405C-8165-C6B5BEC8D0EC) leads to the document whose PDF we already linked above. It is originally named `SMEG+I_HW Technical Datasheet_V1.pdf` and was created in February 2014 by an author with Italian name (Magneti Marelli is an Italian company), likely using Windows (as Ghostscript was used in the process).  
      It seems we're lucky that the Brazilian authorities require these details, as they help a little.
* [ANATEL 02183-15-05386](https://fccid.io/ANATEL/02183-15-05386) is a link leading to an overview page which contains links to documents pertaining to SMEG+Iv2. Please note that these documents are by far not as helpful to this effort as those from the SMEG+I!
* :fr: [Forum post explaining how to replace a SMEG+ by a NAC](https://www.forum-peugeot.com/Forum/threads/tuto-remplacement-smeg-par-un-nac-wave2-sur-308-t9-bta-2-0.9539/)
* :de: [Forum post about updating all SMEG generations](https://www.peugeottalk.de/index.php?thread/2367-smeg-software-update-faq-s/) (from user/owner perspective)
* [Home of the famous Mira scripts](http://mira308sw.altervista.org/en/)  
  The homepage of a person going by the moniker mira308sw has apparently written some scripts which can be executed by software running on the SMEG+ as well as software to inspect data from the SMEG+ and manipulate it. As far as I can tell most of the stuff comes without source, unfortunately.
* :ru: [Website detailing some "adventures" with SMEG+](https://www.drive2.com/l/453828648118518250/) ... the title is roughly "programming the SMEG+Iv2 without DiagBox"
    * :ru: [Similar info](http://www.c4-sedan.ru/forum/viewtopic.php?f=61&t=3349)
* [RT4 Wiki](http://rt4.wikidot.com) is a Wiki collecting information about the RT3, a predecessor of the SMEG and SMEG+, sharing a number of details  
  The whole Wiki is chock-full with spam, but we have an archived and cleaned up version that we will probably attempt to make available at some point
* :fr: [Forum post under the title "Rooting the SMEG+?"](https://www.forum-peugeot.com/Forum/threads/rooter-le-smeg.9541/)
* :nl: [SMEG cheat codes](https://www.jvd-projects.nl/peugeot-smeg-cheat-codes/)
* :ru: [Russian blog post about radar/danger POIs](http://twistedminds.ru/2015/06/smeg-radar-dangerz/)
* [qresExtract](https://github.com/tatokis/qresExtract) is a software allowing to extract `.rcc` files, those are Qt compiled resource files
* In conjunction with [psakey](https://github.com/Mwyann/psakey.git) and derived work [this](https://blog.soutade.fr/post/2016/07/create-your-own-usb-gadget-with-gadgetfs.html) could prove useful
* While on the hardware side not directly applicable, [information from here](https://hackaday.io/project/4177-lvds-laptop-display-interfacing) could prove useful when trying to get the display signal (LVDS) to work without the actual hardware from PSA

Also look below for some prior art.

## Additional reading

* We found the book "The Car Hacker's Handbook" by Craig Smith (ISBN: 978-1-59327-703-1) quite useful to get an overview of what to expect, where to look and what tools to use to dig deeper.
    * It appears the whole book is available as [a single big HTML file from opengarages.org](http://opengarages.org/handbook/ebook/).

## Upstream repositories/projects and related work

* [`https://github.com/bousqi/SMEG_PLUS.git`](https://github.com/bousqi/SMEG_PLUS)
* [`https://github.com/bousqi/smeg-plus_key.git`](https://github.com/bousqi/smeg-plus_key)
* [`https://github.com/Mwyann/psakey.git`](https://github.com/Mwyann/psakey)
    * ... and the fork (currently not diverged) [`https://github.com/bousqi/psakey.git`](https://github.com/bousqi/psakey)
* [`https://github.com/autowp/autowp.github.io.git`](https://github.com/autowp/autowp.github.io) (abandoned upstream?)
    * [`https://github.com/prototux/PSA-CANbus-reverse-engineering.git`](https://github.com/prototux/PSA-CANbus-reverse-engineering) (this is where it all moved)
        * ... and supposedly moved again [`https://git.prototux.net/reverse-engineering/psa/canbus.git`](https://git.prototux.net/reverse-engineering/psa/canbus) (not yet much content)
* [`https://git.prototux.net/cosmos/car/libpsa.git`](https://git.prototux.net/cosmos/car/libpsa)
