---
title: "How to make a linux distro"
date: 2012-02-24
forum: Programming Talk
---

### Post by 19jon on 2012-02-24
I think this is the right place to post this. Me and two of my friends want to create our own distro. They are experienced in programming and I only know python and a am learning BASIC. If we actually do this, will we have to code most of it ourselves or should we be able to borrow most of the code from another distro?
Also, what exactly are the component of an OS?

---

### Post by Bachstelze on 2012-02-24
Define "distro".

EDIT: More precisely, what exactly do you want to do? What is it with existing "distros", whatever that means, that you dislike so much that you want to make your own?

---

### Post by dwhitney67 on 2012-02-25
> **19jon said:**
> I think this is the right place to post this. Me and two of my friends want to create our own distro. They are experienced in programming and I only know python and a am learning BASIC. If we actually do this, will we have to code most of it ourselves or should we be able to borrow most of the code from another distro?
Also, what exactly are the component of an OS?

Read here:  [http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

Good luck.

---

### Post by alegomaster on 2012-02-25
> **19jon said:**
> I think this is the right place to post this. Me and two of my friends want to create our own distro. They are experienced in programming and I only know python and a am learning BASIC. If we actually do this, will we have to code most of it ourselves or should we be able to borrow most of the code from another distro?
Also, what exactly are the component of an OS?

You can make a custom SUSE, Ubuntu, or Fedora (I am not sure about fedora) distro using some tools.

---

### Post by 3Miro on 2012-02-25
Most people just take an existing distro and modify it. If you want to make one from scratch, then you need to read "Linux From Scratch". However, while you can make a distro, keeping it working and up-to-date is more work then 3 people can handle.

BTW, Linux is mostly C/C++, although there is plenty of Python and Java around. However, there is no BASIC or whatsoever. If you want to go into Linux, BASIC is a bad choice.

---

### Post by lisati on 2012-02-25
> **3Miro said:**
> BTW, Linux is mostly C/C++, although there is plenty of Python and Java around. However, there is no BASIC or whatsoever. If you want to go into Linux, BASIC is a bad choice.

+1 for learning something from what might be loosely described as the "C" family of languages.

Although I've seen BASIC mentioned on the forum from time to time - and there are versions available that work with Ubuntu - it doesn't seem to be used that much by those who frequent this forum.

---

### Post by 3Miro on 2012-02-25
> **lisati said:**
> +1 for learning something from what might be loosely described as the "C" family of languages.

Although I've seen BASIC mentioned on the forum from time to time - and there are versions available that work with Ubuntu - it doesn't seem to be used that much by those who frequent this forum.

I think at this point BASIC has only educational purpose to help people get into programming. I don't think BASIC has anything to offer to a person who already knows Python. I may be wrong, but I would like to know of a real program that is written in BASIC.

---

### Post by kalaharix on 2012-02-26
<quote>
 I may be wrong, but I would like to know of a real program that is written in BASIC.
</quote>

Whilst I accept that it is not sensible to write  an operating system using BASIC, I cannot let 3Miro's comment go unchallenged. The problem with BASIC is a lack of standards. You may look at one version of BASIC and decide that it cannot be used to write real software but that is not the end of it. Suspect as the TIOBE index is, it must give you a feeling for the huge legacy of BASIC applications in all industry especially the financial industry. As an aside, I see that TIOBE now separates Visual Basic .Net from other generic BASICs. It will be informative to see how it progresses up the list. Incidentally 'Visual BASIC' still occupies a position well above Python in the TIOBE list.

Anyway to answer the question with 3 interesting examples:

1) Guygle: a web-centric GIS ([http://www.guygle.net](http://www.guygle.net)) written using Gambas. A brief synopsis in English:

Guygle is a web application made by the ASAP company that can manage any sort of network or geographical data. It has tons of features:
Uses Google Maps to display the data and geolocalize it.
Data can be filled from any PDA, with eventually a camera, a GPS, a barcode reader...
Objects can be tagged with RFID chips.
Can track people or vehicles, provided they carry a specific tracking device.
The database is fully customizable.
Data can be exported in OpenOffice, Microsoft Excel or Google Earth.
Human-like syntax queries.
Can generate PDF documents.
...and so on.
Guygle was used for developing the following applications:
- call centre.
- clean-up network management system.
- waste collect management system.
- road sign management system for Paris & Annecy (two French cities).
- car and truck tracking system.
- sales offer management system.

2) Domotiga: Home automation software written in Gambas ([http://www.domotiga.nl](http://www.domotiga.nl))

3) Craft Integrated Electronics Suite (CIES) from Azimuth Inc written in RealBASIC ([http://www.realsoftware.com/community/navy-azimuth.php](http://www.realsoftware.com/community/navy-azimuth.php))

---

### Post by DangerOnTheRanger on 2012-02-26
> **dwhitney67 said:**
> Read here:  [http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

Good luck.

Word of warning on LFS: I spent literally about 24 hours building the vanilla LFS itself (no modifications) - and LFS is about the easiest way out :)

Don't give up though; there have been people who have completed the LFS book, and made their own distro with it.

---

### Post by Bachstelze on 2012-02-26
> **DangerOnTheRanger said:**
> there have been people who have completed the LFS book, and made their own distro with it.

Like? It takes a lot more than "the LFS book" to make a distro that's not just another distro with different packages installed by default.

---

### Post by 3Miro on 2012-02-26
> **kalaharix said:**
> <quote>
 I may be wrong, but I would like to know of a real program that is written in BASIC.
</quote>

Whilst I accept that it is not sensible to write  an operating system using BASIC, I cannot let 3Miro's comment go unchallenged. The problem with BASIC is a lack of standards. You may look at one version of BASIC and decide that it cannot be used to write real software but that is not the end of it. Suspect as the TIOBE index is, it must give you a feeling for the huge legacy of BASIC applications in all industry especially the financial industry. As an aside, I see that TIOBE now separates Visual Basic .Net from other generic BASICs. It will be informative to see how it progresses up the list. Incidentally 'Visual BASIC' still occupies a position well above Python in the TIOBE list.

Anyway to answer the question with 3 interesting examples:

1) Guygle: a web-centric GIS ([http://www.guygle.net](http://www.guygle.net)) written using Gambas. A brief synopsis in English:

Guygle is a web application made by the ASAP company that can manage any sort of network or geographical data. It has tons of features:
Uses Google Maps to display the data and geolocalize it.
Data can be filled from any PDA, with eventually a camera, a GPS, a barcode reader...
Objects can be tagged with RFID chips.
Can track people or vehicles, provided they carry a specific tracking device.
The database is fully customizable.
Data can be exported in OpenOffice, Microsoft Excel or Google Earth.
Human-like syntax queries.
Can generate PDF documents.
...and so on.
Guygle was used for developing the following applications:
- call centre.
- clean-up network management system.
- waste collect management system.
- road sign management system for Paris & Annecy (two French cities).
- car and truck tracking system.
- sales offer management system.

2) Domotiga: Home automation software written in Gambas ([http://www.domotiga.nl](http://www.domotiga.nl))

3) Craft Integrated Electronics Suite (CIES) from Azimuth Inc written in RealBASIC ([http://www.realsoftware.com/community/navy-azimuth.php](http://www.realsoftware.com/community/navy-azimuth.php))

Good info, apparently some people are using it. I am not in the financial world, so I didn't know about its use.

I wonder if there are any programs in the Ubuntu Software Center that are written in BASIC.

---

### Post by kalaharix on 2012-02-27
I have looked at LFS in the past. All I can say is Respect for those who compile and maintain distributions.

That however is not the end of the story. Not only does the developer have to have technical skills but he must have people skills as well (always a tricky one for we nerds). Not only does your distribution need a USP in a very cluttered market but it needs to attract a corona of interested and motivated bodies around it for all the other bits and pieces like look-n-feel, documentation and support.

The big guys can buy these services (you know who I mean) while the smaller guys have to rely on inspiring a small army to the cause. Its amazing that it ever works at all. Big tinny to Barry Kauler for example.

3Miro wrote: I wonder if there are any programs in the Ubuntu Software Centre that are written in BASIC.

Seriously? You mean people actually use Ubuntu? A forum post on the RealBASIC forum (RealBASIC is cross-platform) was commenting that he had managed to sell software that he had written some 7000 times. Of those 4 were for the Linux version. That's Linux not Ubuntu.

I love Linux and FOSS dearly. They just suit me down to the ground. I accept however that the real world is outside the tent.

---

### Post by Bachstelze on 2012-02-27
Yeah because of course, software so crappy it only sold 7000 copies = the real world.

---

### Post by DangerOnTheRanger on 2012-02-27
> **Bachstelze said:**
> Like? It takes a lot more than "the LFS book" to make a distro that's not just another distro with different packages installed by default.

Take a look around DistroWatch; there are several such distributions.

---

### Post by Simian Man on 2012-02-28
It takes virtually no programming to make a "distro".  All you do is repackage other people's work.  It does take programming to write some tools developed by distros such as installers and package managers, but that is different topic.

Things like Linux from Scratch are neat to play with, but aren't really difficult or worthwhile in my opinion.

---

### Post by Lyfang on 2012-10-29
See also: [remastersys (Ubuntu Information)]("http://www.remastersys.com/ubuntu.html")  and [APTonCD]("http://aptoncd.sourceforge.net/").

---

