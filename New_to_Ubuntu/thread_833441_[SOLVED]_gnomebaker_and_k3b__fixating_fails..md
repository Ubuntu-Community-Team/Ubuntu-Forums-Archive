---
title: "[SOLVED] gnomebaker and k3b  fixating fails."
date: 2008-06-18
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-06-18
When I use gmonebaker or k3b for write a CD disk on my BCE 24x IDE drive, everything works OK up untill the fixating starts.  At that tiem the fixating will run for 20 or more minutes even though the disk is nearly filled.  It will then tell me the disk write has failed, yet the write light on the cd drive keeps flashing.  At this point my only way of getting the cd out of the drive is to hit the reset button and eject the disk.  Now for the odd part, when I put the cd in my reader it shows everything was written correctly..  Is there anyway to fix this error.  Never had it in any of the earlier versions of ubuntu.

---

### Post by Hospadar on 2008-06-18
You could try using brasero, also try maybe using infrarecorder through windows if you have the option and see if you get a similar kind of error.  It might just be a little software bug.  If the cd's are burning just fine though, you could always just wait till new versions of the burning libraries (which are probably the same between gnomebaker and k3b) come out.  Try upgrading your packages to make sure you aren't missing anything.

sudo apt-get update
sudo apt-get upgrade

---

### Post by alienexplorers on 2008-06-18
Any other idea's.  I am thinking about adding combined_mode=libata to my grub file version 19 kernel line.  Do you think this will help?

---

