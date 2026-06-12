---
title: "Os"
date: 2009-02-26
forum: Programming Talk
---

### Post by Lekshmi on 2009-02-26
In the booting process,after the POST step,BIOS will identify the boot device and load the 512 bytes(sector 0) ie master boot record. How it is identifying the boot device? there is some sequence like hard drives, floppy... buton what basis it is understanding that it is the boot device?
My another doubt is if we are having more than one hard disk, how it will understand which one ?

---

### Post by CptPicard on 2009-02-26
There is a BIOS setting for that, that you can change if you go into the BIOS management utility that you can access at boot.

---

### Post by jespdj on 2009-02-26
Which device to boot from is normally a setting in the BIOS.

---

### Post by Lekshmi on 2009-02-26
If there are more than one os,then how will it be possible.
ie like windows in one hard disk and linux in another hard disk. At that time how it will recognise??

---

### Post by tturrisi on 2009-02-26
In multi boot systems there are pointers in the bootloader to the other operating systems, e.g. grub can show a menu of all the bootable operating systems on all the drives.  The bios boots the drives marked as the first boot device & if finds a bootloader the os boots.  In multi-boot Windows, the boot.ini loads and displays the boot menu w/ choices.  The bios only boots one drive and the rest is handled by boootloaders on the drive.

---

