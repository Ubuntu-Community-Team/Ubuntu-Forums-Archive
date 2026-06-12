---
title: "Dual booting Ubuntu and Vista; seperate drives, using RAID"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Nacimota on 2008-08-13
Hi there,

I have a problem with installing and booting Ubuntu. I am a Windows user at heart, and while I have dabbled briefly with a wide variety of Linux distributions over the years, I'm not really familiar with Linux itself.

Here's my problem. I have Windows Vista Ultimate installed on a 500gb RAID0 volume spread across two 250gb SATA hard disks. I have an empty 500gb SATA hard disk that I want to put Ubuntu on.

I have *no intention* of making any changes to the the RAID or the disks that it resides on (except to install/configure boot loaders). I want to install Ubuntu on the third disk only. This means no resizing the Vista partition to make room for Ubuntu, etc.

I think I can get Ubuntu installed, but I just can't get it to boot; I've tried letting GRUB take over the Vista bootloader and I've tried adding Ubuntu to the Vista bootloader via EasyBCD - I'm certain that I am doing something wrong

I would definately prefer to use the Vista boot loader if possible; however, I will settle for GRUB.

Can someone please walk me through some possible solutions to this problem?

Thanks in advance,
Nacimota

---

### Post by confused57 on 2008-08-13
If you already have Ubuntu installed on the separate drive and you're able to set bios to boot first to this drive, use the Ubuntu live cd to install grub to this drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
see the instructions, but instead of installing grub to (hd0), install it to your Ubuntu drive's mbr, e.g.:
```
root (hd2,0)
setup (hd2)
```
substitute the results of "find /boot/grub/stage1" for (hd2,0).

You should get a grub boot menu when you boot first to the Ubuntu drive, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, then change root from (hd2,0) to (hd0,0), press "enter", then "b" to boot.  This change is temporary if it works, but you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

It shouldn't be a problem to add an entry to boot Windows from grub.

---

### Post by Nacimota on 2008-08-13
> **confused57 said:**
> If you already have Ubuntu installed on the separate drive and you're able to set bios to boot first to this drive, use the Ubuntu live cd to install grub to this drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
see the instructions, but instead of installing grub to (hd0), install it to your Ubuntu drive's mbr, e.g.:
```
root (hd2,0)
setup (hd2)
```
substitute the results of "find /boot/grub/stage1" for (hd2,0).

You should get a grub boot menu when you boot first to the Ubuntu drive, highlight the first Ubuntu entry, press "e", highlight the line with root, press "e" again, then change root from (hd2,0) to (hd0,0), press "enter", then "b" to boot.  This change is temporary if it works, but you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```

It shouldn't be a problem to add an entry to boot Windows from grub.

Thanks! I figured out that GRUB and Ubuntu see the drives differently, I changed the boot sequence as you suggested and everything works great now.

thanks again!

---

