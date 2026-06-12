---
title: "New Installation 8.x"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by fdates on 2008-10-11
Hello.

I'm BRAND NEW to Ubuntu and Linux. The idea of possibly getting away from Windows intrigues me.

With that said...

I burned a CD and verified that it was good using Ubuntu's cd verify selection.

The machine is a x386 box that has an existing 'buggy' Windows XP on the hard drive.

I want to completely WIPE THIS DRIVE of Windows and install Ubuntu v8.x

When I boot up on the CD, the VIDEO display is okay to allow me to select ENGLISH and to select INSTALL UBUNTU. But then, the VIDEO gets all whacky to where I can partially see the installation but many words are not clear. I do not know how to make this VIDEO look correctly so I can proceed with the installation, and the install CD does not appear to notice that the VIDEO is not displaying correctly or trying to correct it.

What do I do?

System Specifications:

Intel Desktop Board D201GLY2
Celeron 220 w/ 533 Mhz system bus
1 gig 240-pin DDR SDRAM DIMM

SIS662 Northbridge
SIS964 Southbride

ADI AD1888 audio codec

Integrated SiS Mirage 1 graphic engine.

Thanks.
Rick

---

### Post by ChildOfMana on 2008-10-11
Hi, and welcome!

Sounds like your problem could be a driver issue.

After a little digging around on google I found [this](http://pclinuxoshwdb.com/index.php?option=com_content&task=view&id=824&Itemid=1). It's from the PCLinuxOS website so may not be much use to you as an Ubuntu user but the crux of it is that SiS have either not written, or not relased, 3D Linux drivers for this chipset.

**Edit:** Unfortunately I can't be of much more help to you than this as I wouldn't know how to go about fixing/working around this problem but google is your friend. Plenty of knowledgeable and friendly people on this forum too.

---

### Post by Kevbert on 2008-10-11
Agree with the last post, please take a look at this [COLOR="Red"][post]("http://ncc-1701a.homelinux.net/WikiBerd/?page=LinuxSis67x")[/COLOR].
In any case you won't be able to use such things as compiz fusion (the rotating cube) as the display adapter doesn't support 3D graphics acceleration.  Unfortunately your best bet is to buy a cheap Nvidia, ATI or Intel graphics card.

---

### Post by cariboo on 2008-10-11
You shouldn't have to go out and purchase a new video card just install Ubuntu, or try solutions from other distributions. You can change the boot options by pressing F4 at the menu screen, In your case select safe graphics mode, you should get the LiveCD to run. BTW specify *.x as the version doesn't really help as there are versions 8.04, 8.04.1 and a soon to be released 8.10,

Jim

---

### Post by fdates on 2008-10-11
I want to thank you guys for replying to my cries for help. Much appreciated.

Fortunately, I was able to finally get ubuntu installed by going the "safe video" route. Didn't see it earlier. And I did not after updating my BIOS for the Intel motherboard.

It would appear that your suggestion about getting an updated video card is a very good one indeed. It's unfortunate that this 'box' only has one expansion slot. I'd like to get a better box, but the whole idea was to salvage this box in order to determine whether I wanted to go the 'linux' route without a heavy investment in component, and not to install the OS on our XP systems here. (This is my daughters old computer. Her school provided her with a new machine, so I 'borrowed' this one. :-b)

Right now I have a 'wireless card' in stalled in that single expansion slot. What I may do is get a USB wireless adapter to free up the PCI slot, and then look to get a 3D compatible video card to go into that PCI slot so I can take full advantage of what this 'linux' OS is suppose to offer.

Thanks again!
Rick

---

