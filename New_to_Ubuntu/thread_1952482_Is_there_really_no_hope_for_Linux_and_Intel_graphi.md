---
title: "Is there really no hope for Linux and Intel graphics?"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by Avaritia on 2012-04-04
After finding out the MMO I play sometimes (Vendetta Online) has a Linux client and alternatives for the Windows software I use I took the plunge and installed Ubuntu as the only OS on this laptop.

Then I found out how bad the Intel driver is, I have Mobile 4 series chipset, after doing research I installed the latest mesa and drivers from the xorg-edgers PPA, but all of the games I run on Ubuntu tell me my card doesn't support anti-aliasing and s3tc shaders, 

This means games I could run on max settings in Windows have weird glitches (objects in Vendetta Online are filled in with bright colors since it thinks my card doesn't support shaders.)

Is there an Intel graphics driver for Linux that supports features made in the last 12 years? I really don't want to give up on Ubuntu but this laptop is my only computer and I like to play games now and then, games I know my card can run.

---

### Post by Cheesemill on 2012-04-04
I don't use Ubuntu for gaming so this may not answer your question, but I have found that the default Intel drivers that are included in the kernel have much better support & compatibility than either the nVidia or ATI drivers that are available, as the Intel drivers have all been open sourced.

PS - I use the built in drivers for the Core i3 chips, I'm not sure how good the drivers are for the Mobile 4 chipset. Do the Windows drivers support the features that you are after?

---

### Post by Avaritia on 2012-04-04
Yes the Windows drivers lets me run the games at max settings.

---

### Post by bcschmerker on 2012-04-04
> **Cheesemill said:**
> I don't use Ubuntu for gaming so this may not answer your question, but I have found that the default Intel drivers that are included in the kernel have much better support & compatibility than either the nVidia or ATI drivers that are available, as the Intel drivers have all been open sourced.

PS - I use the built in drivers for the Core i3 chips, I'm not sure how good the drivers are for the Mobile 4 chipset....Thanks for a confirmation on how well the Intel® iGPU functions in Kernel 3-up.  I am currently preplanning a rebuild of my hybrid Everex® with all-AMD® chips except for a Creative Laboratories® SB0350 PCI audio (as of April 2012) around an Asus® P8Z68-M PRO and Intel® Core i7-2600 series (LPGA 1155) in order to get a fast and reliable system for Kernel 3.2.*n*-realtime, and with it the best performance out of Precise (12.04-rc as of 4 April 2012).  Depending on the software demands, the i7's internal IGP may very well run circles around my current Gigabyte® GA-MA78GM-S2HP's planar AMD® Radeon HD 3200, assuming all systems go under 12.04.1-LTS.

---

### Post by andrew.46 on 2012-04-05
I battled on with intel graphics for years with mixed results but when I built a new computer recently I moved to an NVidia card and the proprietary driver. This is a move I would highly recommend and it has made my computer usage so much easier :). Goodbye intel graphics......

---

### Post by bodhi.zazen on 2012-04-05
> **Cheesemill said:**
> I don't use Ubuntu for gaming so this may not answer your question, but I have found that the default Intel drivers that are included in the kernel have much better support & compatibility than either the nVidia or ATI drivers that are available, as the Intel drivers have all been open sourced.

Depends on the card. The intel gma500 is NOT open source and, until recently, has not worked out of the box.

Same with nvidia and ATI. Some cards are more compatible then others.

---

### Post by mastablasta on 2012-04-06
> **Avaritia said:**
> Yes the Windows drivers lets me run the games at max settings.
 
some cards have very good support, some don't have as it was said. 
 
an option is to dualboot or if you have a desktop PC you can also upgrade with a cheap Nvidia or ATI card.

---

### Post by bcschmerker on 2012-04-07
> **bodhi.zazen said:**
> Depends on the card. The intel gma500 is NOT open source and, until recently, has not worked out of the box.

Same with nvidia and ATI. Some cards are more compatible then others.In fact, so far I have had little trouble from my system's present configuration, as the AMD® Radeon HD 3000 Series performs well with the X.org open-source driver (package: xserver-xorg-video-radeon), except in cases where I have a strange display unit that has the edges of the desktop literally off the screen (as can happen with HD television displays; that would force the AMD® Catalyst Control Center, packages: fglrx, fglrx-amdcccle).  The AMD® Radeon HD Series up to the 6850 will remain a backup to the integral IGP in the Core i7, in case the X.org GMA driver proves disappointing.

---

