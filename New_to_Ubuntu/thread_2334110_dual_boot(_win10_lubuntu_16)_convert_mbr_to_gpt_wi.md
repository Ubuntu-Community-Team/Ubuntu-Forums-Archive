---
title: "dual boot( win10 lubuntu 16) convert mbr to gpt without data loss????"
date: 2016-08-16
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2016-08-16
ive got a dual boot setup with win 10 and ubuntu 16, it time to covert from mbr to gpt
is there any simple apps that will take care of all the heavy lifting and spit out a working system?
windows applictions or linux apps ?

better to start from scratch?

---

### Post by oldfred on 2016-08-16
There are Linux apps to convert, never used them.

But the issue really is that Windows only boots in BIOS boot mode from MBR partitioned drives.
And Windows only boots in UEFI mode from gpt partitioned drives. (and you need newer UEFI hardware).

Ubuntu can boot from gpt with either BIOS or UEFI but with BIOS you must have a 1 or 2MB unformatted partition with the bios_grub flag for BIOS boot or a FAT32 formatted partition as the ESP - efi system partition.

Probably best to fully backup and reinstall if you have newer UEFI hardware.

I started converting to gpt years ago when I still had XP. But XP was on MBR drive with Ubuntu on gpt drive.

       Converting to or from GPT
[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]http://www.rodsbooks.com/gdisk/mbr2gpt.html
[/URL]
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]
[/URL]

---

