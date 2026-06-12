---
title: "USB Boot Damn Small Linux problem"
date: 2008-10-03
forum: Other OS Talk
---

### Post by kevindubrow on 2008-10-03
Hi, I am trying to boot Damn Small Linux from a USB stick. While DSL was loading up, it got to looking for CDROM in /dev/sda1 and eventually timed out saying that the KNOPPIX file system could not be found. Does anyone know what I should do to fix this? the Knoppix file is in the USB stick. Thanks!

---

### Post by kerry_s on 2008-10-03
> **kevindubrow said:**
> Hi, I am trying to boot Damn Small Linux from a USB stick. While DSL was loading up, it got to looking for CDROM in /dev/sda1 and eventually timed out saying that the KNOPPIX file system could not be found. Does anyone know what I should do to fix this? the Knoppix file is in the USB stick. Thanks!

sda1 is the usb. how did you install? just try to reinstall to the usb drive. i find it's easier to burn the cd, then do a frugal install to the usb.

---

### Post by kevindubrow on 2008-10-03
alright, I'll check that out. Thanks for the tip.

I installed it by extracting the dsl-4.4-embeded zip file onto the USB stick and using syslinux to make it bootable.

---

### Post by www.rzr.online.fr on 2008-10-22
> **kevindubrow said:**
> Hi, I am trying to boot Damn Small Linux from a USB stick. While DSL was loading up, it got to looking for CDROM in /dev/sda1 and eventually timed out saying that the KNOPPIX file system could not be found. Does anyone know what I should do to fix this? the Knoppix file is in the USB stick. Thanks!

I've been affected by this issue too, but I remember it used to work
I suppose it depends on your BIOS ?

may this help :

[http://rzr.online.fr/q/knoppix](http://rzr.online.fr/q/knoppix)

[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=Print;f=36;t=18732](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=Print;f=36;t=18732)

---

