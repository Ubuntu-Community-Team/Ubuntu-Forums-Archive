---
title: "Installing Windows 8.1 over Ubuntu 12.04"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by smw22 on 2014-04-02
Hey everybody!

I want to install windows 8.1 completely over Ubuntu. I have a CD for windows 8.1. I have used this CD before on this computer. From what I know I need to restart my computer with the disc in to install windows 8.1 but I am not getting any prompts at start-up.

How can I install windows 8.1?

Thanks,

-smw2

---

### Post by oldfred on 2014-04-02
Windows does not see nor like LInux formatted partitions. 
It either wants unallocated space or primary partition (if MBR) formatted NTFS with boot flag.

Also may make a difference if UEFI or BIOS, if computer is newer and has both modes.
Windows only boots from gpt partitioned drives with UEFI and you must then boot installer in UEFI mode.
Windows only boots from MBR(msdos) partitioned drives with BIOS and you must boot installer in BIOS mode.

---

### Post by Double.J on 2014-04-02
Hey there!

sounds like your bios isn't trying to boot from the CD? Check the options you have in the first loading screen - something like 'boot select' if there isn't one, enter the bios and change the boot order list.

as for installing windows over ubuntu, best use a live cd to delete the drive. Easiest way is boot the ubuntu installer disk and use gparted to delete the drive.

NB do not format the drive as NTFS - it may seem like it'll be ready for windows, but windows is often not happy about ntfs volumes made by gparted. Just leave the disk blank.


Another good test here is if the ubuntu disk boots and the windows one doesn't it's a problem with the windows media

Jj

---

### Post by oldfred on 2014-04-02
If you just have CD, is that an upgrade and not a full install of Windows? Upgrade would have to see a full install of Windows on hard drive.

---

### Post by jeff49 on 2014-04-02
I just did this on mine. I had to go into my boot menu in bios and fiscally press on my dvd drive to boot windows cd after that it starts and you can then go in and delete the Ubuntu partition and then install windows

---

