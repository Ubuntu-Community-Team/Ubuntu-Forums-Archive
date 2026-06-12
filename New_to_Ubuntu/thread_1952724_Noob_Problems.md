---
title: "Noob Problems"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by alagator on 2012-04-04
Not exactly a complete noob, but close enough. Installed Ubuntu NBR onto an ASUS EEE pc 900A Linux (now with 64 Gb. SSD and 2 Gb. RAM) back about ver. 9.04. Upgraded since then and successfuly running the full Gnome desktop at ver. 11.10. Two small problems recently. At least since the last upgrade, GRUB reports finding at least half-a-dozen versions, all of which are bootable from the GRUB Menu, with a few small provisos. None will boot w/o my 8 Gb. SD chip inserted, even though gparted reports sda as bootable. Also one of the vers. boots normally from GRUB only to end at a menuless (Dare I say it) Blue Screen. This isn't the infamous BSOD though Because Ctrl.Alt.T will bring up a working Terminal window. I know I buggered this up myself trying to reconfigure things on the desktop, just can't fix it. Anyone wanna try to solve my screwup?:popcorn:

---

### Post by Gadgetech on 2012-04-04
The multiple listings in your GRUB menu are most likely just different versions of the Linux Kernel. I've written a few posts on my blog on how to remove the old kernels from your system. You'll want to log into the one you want to keep, then follow the one of the sets of instructions linked below. 

[Manually remove old kernels in Ubuntu]("http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/")
or 
[Remove the old kernels in Ubuntu with one command]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/")

Not sure why your system won't boot without your SD card installed. Could it be that GRUB is actually installed to the SD card?

---

### Post by alagator on 2012-04-04
Anything is posssible, but I thought I checked that. Thx

---

### Post by buzzkiller88 on 2012-04-05
hi i need help i am trying to write a boot disk for ubuntu and i cant find the location where it dl'ed to i have been sitting at my pc for like 3 hrs trying this and that but i jst cant seem to find it i am using win xp and i am trying to write the disk using infrarecorder my ? is this can i just download it to my desktop and write it from there thanks for any and all help

---

### Post by alagator on 2012-04-05
Desktop folder will work just fine under XP, you'll need to browse to, and select the name of the Desktop folder in the "Save As" dialog. On my XP machine that's "C:/Documents and Settings/"YourUsername"/Desktop". The "YourUsername" will vary depending on your installation.

---

### Post by alagator on 2012-04-06
> **Gadgetech said:**
> The multiple listings in your GRUB menu are most likely just different versions of the Linux Kernel. I've written a few posts on my blog on how to remove the old kernels from your system. You'll want to log into the one you want to keep, then follow the one of the sets of instructions linked below. 

[Manually remove old kernels in Ubuntu]("http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/")
or 
[Remove the old kernels in Ubuntu with one command]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/")

Not sure why your system won't boot without your SD card installed. Could it be that GRUB is actually installed to the SD card?
Grub seems to be loaded onto both the 64Gb. SSD(preferred boot drive) , and the 8Gb. SD chip. How do I get it to Ignore the SD and use the SSD?

---

### Post by dasjew on 2012-04-06
If you go into the bios before the grub screen sets up, go to bootloader options. It sounds like your computer has the sd chip set before the SSD. not sure if that'll solve your problem, but it's worth a try

---

### Post by alagator on 2012-04-07
Already eliminated everything but the SSD from the boot sequence, still apparently ru8nning GRUB from the SD.

---

