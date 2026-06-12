---
title: "[SOLVED] Can't partition/format external drive"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by bertwagner on 2008-05-19
I'm trying to use gparted to partition/format an external hard drive (sdb).  Whenever I try to create a disk label or create a new partition (the whole drive is currently unallocated space) I receive the following error:

```

Unable to open /dev/sdb - unrecognised disk label.
Input/output error during write on /dev/sdb

```


My fdisk -l output is:

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x546d30ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29649   238155561   83  Linux
/dev/sda2           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 2174.2 GB, 2174225669632 bytes
255 heads, 63 sectors/track, 264334 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3cad3ca

Disk /dev/sdb doesn't contain a valid partition table

```

This problem has been driving me nuts all day and I've been searching for alternate ways of formatting the drive but have not had any success.  Any help would be greatly appreciated.

---

### Post by domace on 2008-05-19
Try this-

 In the terminal type this and then the disks location not the one in it which is mine

cfdisk /dev/sdb1

---

### Post by bertwagner on 2008-05-19
> **domace said:**
> Try this-

 In the terminal type this and then the disks location not the one in it which is mine

cfdisk /dev/sdb1

I tried typing in "cfdisk /dev/sdb" and "cfdisk /dev/sdb1" and on both instances received the message: 

```
FATAL ERROR: Cannot open disk drive
Press any key to exit cfdisk
```

---

### Post by domace on 2008-05-19
These may help as well-meaning if your disk is a 'raid' it cant be formated

[http://www.linuxquestions.org/questions/linux-hardware-18/not-valid-partition-table-393042/](http://www.linuxquestions.org/questions/linux-hardware-18/not-valid-partition-table-393042/)

[http://www.tldp.org/HOWTO/Software-RAID-HOWTO-11.html](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-11.html)

---

### Post by domace on 2008-05-19
It might as well be a os problem or hardware problem, does the device mount?

---

### Post by bertwagner on 2008-05-19
The first link you gave, post #2, worked. Thanks!  The drive was able to mount and all my data was on it.  I was then able to properly format it using gparted.

If anyone else has the same issue, this what I did:

sudo fdisk /dev/sdb
d (to delete partitions)
n (create new partition with default settings)
w

Then I used gparted to create new partitions and format the drive as ext3.  Thanks again!

---

### Post by domace on 2008-05-19
no problem always glad to help:)

---

