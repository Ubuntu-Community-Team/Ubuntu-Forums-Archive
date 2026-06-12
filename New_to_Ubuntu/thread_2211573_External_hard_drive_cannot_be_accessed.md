---
title: "External hard drive cannot be accessed"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by Jeff_Haberman on 2014-03-16
I had a copy of QuickBooks 5.0 loaded on a Windows 98SE machine which died on me. I reloaded QB 5.0 on a Win XP Pro machine and put the old hard drive in a Hard Drive Enclosure for access to the stored data. I could then load QB and direct it to the HDD for data recovery and storage. This worked for nine months. Now external hard drive cannot be accessed. Message from Win XP says it is not formatted. Tried a number of ways to recover data including loading latest version of Ubuntu. Ubuntu does not read the existence of the external drive at all. Only sees the internal HDD and it's start up partition and the CD ROM. Are there any tricks with Ubuntu that my still allow me to recover the missing data? P.S. I committed the cardinal sin of not backing up regularly so I have a lot of drudge work if I have to re-enter all the lost data. Thanks.

---

### Post by tfrue on 2014-03-17
It may have a Read/Write error, which isn't good for obvious reason. With the drive plugged in, post the output of:
What is the brand name and what size is the drive (GB wise)?
```

sudo fdisk -l; sudo blkid;lsblk

```

---

### Post by Jeff_Haberman on 2014-03-17
Drive is a WD 310200 Enhance IDE Caviar with about 10GB of memory. Using Ubuntu version 13.10.

I am not sure what output you want me to post. If I click on the drive icon it says I have to format the Disk before it can be accessed. As I understand it Formatting will erase all the stored data which is exactly what I don't want to do.

---

