---
title: "start up issues ubuntu 12.04"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by gregyork88 on 2014-01-17
PLEASE HELP!!
OK I posted this in an effort to get some help with a common issue. I have checked my HDD with the Ubuntu utility and it shows a healthy drive. Live CD enviroment recognizes HDD and so I am guessing HDD is OK, it's just taking to dadgum long to be recognized during boot.  I have also learned that changing one of the boot modules(apparently missing) is a fix but I havent seen a place to get the module from unless you are using diferent ubuntus together, which I am not.


i have recently installed Ubuntu 12.04 lts via USB on a HP Pavillion that had XP on it.With Xp it ran fine, but I ditched Xp because updates and drivers are a pita. During the boot process I am seeing this error-    ata3 is slow to respond plesae wait (error16)-.    eventually the 'kernel'? times out and boot up continues without it.  I can only use Ubuntu from the Live USB enviroment.  I used this same USB stick to install Ubuntu to a Dell D810 laptop but that machine finally died. 
From my research I have learned to run to a couple commands and the output are 
```

ubuntu@ubuntu:~$ sudo parted -l
Model:  USB Flash Memory (scsi)
Disk /dev/sda: 2008MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  2008MB  2004MB  primary  fat32        boot


Model: ATA Hitachi HDT72502 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  247GB  247GB   primary   ext4            boot
 2      247GB   250GB  2950MB  extended
 5      247GB   250GB  2950MB  logical   linux-swap(v1)
AND
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 2008 MB, 2008023040 bytes
16 heads, 32 sectors/track, 7660 cylinders, total 3921920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        8064     3921919     1956928    b  W95 FAT32

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097697

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   482633727   241315840   83  Linux
/dev/sdb2       482635774   488396799     2880513    5  Extended
/dev/sdb5       482635776   488396799     2880512   82  Linux swap / Solaris
```
SOMEBODY please help !!

---

### Post by mörgæs on 2014-01-18
If you look around in BIOS, do you see an option to change AHCI settings?

---

