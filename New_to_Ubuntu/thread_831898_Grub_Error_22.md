---
title: "Grub Error 22"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by ryanparrish on 2008-06-17
Grub is toast I tried several things from the archives and other sources I get error 22 on boot so I am using my Gutsy live CD right now

---

### Post by jpeddicord on 2008-06-17
You didn't happen to install Windows overtop of Ubuntu did you? If so, follow the directions in this guide to repair your GRUB boot sector:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Give a good read through the topics of that page before doing anything, however, as some of those are for different situations.

---

### Post by ryanparrish on 2008-06-17
Yeah thats what I read this error is common to people that install windows, I have not installed windows as a dual boot option. I run windows via virtual box

---

### Post by ryanparrish on 2008-06-17
also when I try to mount /hda1 it throws an error about 
```
mount: special device /dev/hda1 does not exist
```

my Fdisk is 

```
 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34af8c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1        8001    0  Empty
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda3               2           5       32130   83  Linux

Partition table entries are not in disk order

```

---

### Post by bumanie on 2008-06-17
You could try super grub disk it has a good reputation for curing grub issues such as you have.  Get it [here]("http://www.supergrubdisk.org/"), it is a live cd. Unusual to have grub error such as that without another OS being involved. Post back if super grub disk does not work.

PS: Looking at your fdisk -l output, it looks as though you have removed the / file system. You will have to reinstall. Also you have sata drives, you should have used /dev/sda1 - but it doesn't matter at this point as /dev/sda1 is empty.

---

### Post by ryanparrish on 2008-06-17
yeah I was looking at Gparted I have 108 gb un allocated is it possible that my data is on their or is it completely lost to the world?

---

### Post by bumanie on 2008-06-17
Unfortunately unallocated = no file system on the hard drive - it is now basically a 'raw' disc. 
Advice for reinstallation: 
It is a good idea to choose manual at the partitioning stage of a reinstall so that you can set up a separate / partition and a separate /home partition (+ swap of course) that way if you wreck the file system, 99% of the time, data in /home is safe and you only have to reinstall to / - saves heaps of hassles.

PS: You could get hold of testdisk and try to recover you lost partition. It is a data/partition recovery program that can run as a live cd. It would be best to download and burn it onother computer so that you leave your hard drive as undisturbed as possible. It is a good tool, I recently recovered a fragged xp partition table with it. get it[ here]("http://www.cgsecurity.org/wiki/TestDisk_Download")

---

### Post by melrom on 2008-06-17
I get grub error 22 a lot. I didn't install Windows over Ubuntu. I would get the supergrub disk that has already been recommended.

---

### Post by adrian15 on 2008-06-18
> **ryanparrish said:**
> 

my Fdisk is 

```
 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34af8c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1        8001    0  Empty
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda3               2           5       32130   83  Linux

Partition table entries are not in disk order

```

My piece of advice is to use testdisk to see if it can recover your former partition table layout and after that use Super Grub Disk to recover your boot.

adrian15

---

