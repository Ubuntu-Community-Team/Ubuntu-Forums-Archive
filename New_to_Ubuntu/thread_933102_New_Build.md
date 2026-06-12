---
title: "New Build"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by daniell59 on 2008-09-29
Just finished my new build. I have two hard drives. As of yet I have not installed an operating system. I want Vista on one HD and Ubuntu on the other. Would appreciate suggestions on the best way to proceed.

Thanks

---

### Post by Tom--d on 2008-09-29
Install Vista first.
Then Ubuntu, Then set up GRUB to take the boot to the windows boot manager on the other hdd. Simple to do, all you need to do is locate the HDD names for Grub. Its not /dev/sda etc. Its like (hd,0)

So where Windows is have this in your grub.lst at the bottom:
```

# (2) Windows XP
title Windows XP
rootnoverify **(hd0,1)**
makeactive
chainloader +1

```
(hd0,1) should be it. But im not 100%

---

### Post by mike1821 on 2008-09-29
I would suggest to proceed with the installation of windows first. This will allow windows to create their MBR with no problems.

Then by installing Ubuntu (GRUB), it will detect your windows installation and you will not need to do anything further. Something which will not happen by windows.

---

### Post by Sef on 2008-09-29
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by daniell59 on 2008-09-29
Please forgive my ignorance, but what is GRUB?

---

### Post by Tom--d on 2008-09-29
> **daniell59 said:**
> Please forgive my ignorance, but what is GRUB?

Linux's boot loader.

---

### Post by bumanie on 2008-09-29
GRUB - GRand Universal Bootloader It is a linux bootlaoder that has the ability to allow booting of more than one operating system. It will of course boot linux, but in a dual boot scenario it will also recognise that there is windows OS on the computer and if you choose to boot that, grub will hand the booting process over to vista's bootloader to complete the booting of vista. As said above it is best to install windows first, followed by ubuntu. They can be on separate hard drives.

Here's my hard drive lay out - first hard drive (/dev/sda) has xp;
second hard drive (/dev/sdb) has ubuntu with three partitions - one is / one is /home and one is /swap

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006d680

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   268414019   134206978+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000db2bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    41688674    20844306   83  Linux
/dev/sdb2        41688675   334650014   146480670   83  Linux
/dev/sdb3       334650015   342457604     3903795   82  Linux swap / Solaris

---

