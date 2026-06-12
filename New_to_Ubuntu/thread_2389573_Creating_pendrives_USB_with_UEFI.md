---
title: "Creating pendrives USB with UEFI"
date: 2018-04-18
forum: New to Ubuntu
---

### Post by lynx6 on 2018-04-18
Hello everyone.
How to properly create a flash drives USB for notebooks with UEFI.
1) Create partition table in GPT?
2) Formatted in FAT32?

Thank you!

---

### Post by oldfred on 2018-04-18
Installer, Installer with persistence, or full install of Ubuntu to flash drive?

Standard Ubuntu live installer is both UEFI & BIOS on a FAT32 formatted partition. Does not really matter if MBR or gpt.
Although some UEFI/BIOS may make a difference, but should not if UEFI standards followed. Only extremely old systems might not recognize gpt.
And some are configured as hybrid DVD/flash drive which then is not a standard partitioned drive.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) 
            UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
    
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

      
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by lynx6 on 2018-04-18
Hi *oldfred*, Thank you very much for the explanations.
What program would you recommend to create a partition table (GPT) note?
1) On Windows?
2) On Linux?

---

### Post by oldfred on 2018-04-18
Do not know Windows, but its partitioning tools should create gpt.
I have this in my notes:
 Windows 10 Creators Update April 2017
Business users will like the MBR2GPT utility, for example, which helps you convert a drive to GPT partitioning without destroying data, enabling migration to UEFI (Unified Extensible Firmware Interface) in place of BIOS, 

For Ubuntu I use gparted.

 Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. 
This will erase drive, all data but other tools like fixparts or gdisk can convert a MBR(msdos) drive to gpt.

You can also use gdisk from command line or if server.
      
 [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)

Parted like gparted supports gpt, but only new copies of fdisk support gpt.

---

### Post by lynx6 on 2018-04-19
Thank you very much for the explanations.
I got to create a new table of partitions in *GPT*.
I used GParted in *Ubuntu* to create a new table of partitions in *GPT*.

Greetings.

---

### Post by C.S.Cameron on 2018-04-19
Mkusb works great for creating a BIOS/UEFI boot disk in Ubuntu.
It will make a USB drive with FAT boot partitions, read only ISO 9660 OS partition, ext2 casper-rw persistence partition and NTFS data partition that both Windows and Linux can use.
YUMI UEFI Beta is a good boot disk maker for Windows, I think it is UEFI only.
It can make a USB with multiple Persistent OS.
MKUSB is a BIOS/UEFI boot disk maker for Windows that also works with multiple OS.

---

### Post by lynx6 on 2018-04-19
Thank you very much for the information.

---

