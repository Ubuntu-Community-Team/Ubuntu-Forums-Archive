---
title: "Rescue USB drive for Ubuntu Linux ..."
date: 2016-08-15
forum: New to Ubuntu
---

### Post by cwmoser on 2016-08-15
What is a good rescue USB or CDROM to have around just in case something
happens to an Ubuntu OS failure?????

I'm mostly interested in ability to restore the boot menu, do fsck, etc.

---

### Post by grahammechanical on 2016-08-15
There is Boot Repair

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Grub menu>Advanced options>recovery kernel will bring us to a recovery menu where we can do a file system check (fsck). We can also do it from a Live session by pressing Enter at the first purple screen.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Regards

[URL="https://help.ubuntu.com/community/BootOptions"]

[/URL]

---

### Post by yancek on 2016-08-15
In addition to boot repair, keeping the Ubuntu installation DVD/flash drive is always a good idea.  SystemRescueCD has just about every tool available under Linux and is small enough to fit on a bootable CD.

---

### Post by oldfred on 2016-08-16
I consider the Ubuntu live installer as first choice and you can add just about any other tool from repository that is not already included.

But years ago when I still used CD, I had Knoppix, gparted, parted rescue, Boot-Repair, and Supergrub. But they changed frequently, so I was burning new CDs and then had many old CD.
So I learned to directly boot ISO from flash drive and put many of the same on one flash drive.

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by C.S.Cameron on 2016-08-16
Using MultiBootUSB to make the disk, you can install hundreds of different iso's to the drive including Ubuntu, gparted, boot-repair, clonezilla, etc.
The script builds a pendrive similar to drs305 and automatically provides menuentries for many Linux tools.
It uses grub2 to boot iso files.

---

### Post by Bucky Ball on 2016-08-16
> **yancek said:**
> SystemRescueCD has just about every tool available under Linux and is small enough to fit on a bootable CD.

++1. Never leave home without it. I never do. ;)

[http://www.system-rescue-cd.org/SystemRescueCd_Homepage](http://www.system-rescue-cd.org/SystemRescueCd_Homepage)

---

### Post by mastablasta on 2016-08-17
ultimate boot CD is also a good choice.

---

