---
title: "Give Ubuntu a new try.. how"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by ajmannen on 2008-05-22
Hi, I uninstalled Ubuntu about a year ago as I couldn't stand terminal <.< (I'll try to cope with it now) 

The thing is, I wan't to re-install Ubuntu but for a starter, I have limited HDD space (12 gigs free in writing moment), I can clear out some more if needed. I also have Ubuntu 7.04 laying on my HDD but it is not working :S i, somehowe broke it. 

So to the main problem, I have one Ext2 HDD, and allot of files on it, and a broken Ubuntu 7.04 and no back-up nor do I have a portable HDD. 

I wan't to remove Ubuntu 7.04 and install the newest Ubuntu there but still keep my files, is that possible?

---

### Post by spiderbatdad on 2008-05-22
Seems like you could install 8.04 then mount your existing file system and copy the files to the new installation. Then use a partitioning tool to free up the unwanted partition. If you have a problem due to too many disk partitions, you can mount the existing partition with the live cd and create a /home partition for the file system, then install 8.04 on the unused space.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Peter09 on 2008-05-22
If you install Hardy with the live CD (it runs from the CD not your hard drive) then you can use the partition manager to clear you unwanted Ubuntu partion and install Hardy.

PC

---

### Post by ajmannen on 2008-05-22
The Ubuntu partition is 70 GB large and I have ALLOT of files there that I wan't to keep, so I can't really "clear it out", that's the main problem

---

### Post by philinux on 2008-05-22
My ubuntu root partition is using only 4.1 gig out of 12 that I gave it on install.

---

### Post by ajmannen on 2008-05-22
Well, I have ALLOT of files in my Ubuntu partition, get it? Ubuntu is mixed up with the rest

[[img]http://bildr.no/thumb/202119.jpeg[/img]](http://bildr.no/view/202119)

---

### Post by ubername on 2008-05-22
> **spiderbatdad said:**
> Seems like you could install 8.04 then mount your existing file system and copy the files to the new installation. Then use a partitioning tool to free up the unwanted partition. If you have a problem due to too many disk partitions, you can mount the existing partition with the live cd and create a /home partition for the file system, then install 8.04 on the unused space.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Here's a possible, but arduous, way, and obviously all the normal caveats about backing up should be taken as read, but I guess with about 60Gb of stuff, you might choose to take the risk. Besides which, if you had a back-up you probably wouldn't be asking this question!:

First, can you install ubuntu on the space in either your C: (Acer) drive or your D: (local disk) drive (10.6Gb and 11.0Gb free respectively)? (i.e. have you got fewer than four primary partitions on either of these drives?)

If so, as mentioned up-thread, you can create a new partition for 8.04, using as much free space as possible (using the live CD). The new install should automatically detect your old partition. Then copy as much as possible (say 8 Gb) from your D: drive (the old ubuntu one) into the free space remaining on the new partition (and as much as possible on to the space on the C: drive, if you can create the new partition on the D: Drive).

Delete what you have copied elsewhere from the old ubuntu partition, restart with the Live CD, resize the old ubuntu partition, now that you have deleted stuff from it, resize the new ubuntu partition to take up the freed space from the old partition and repeat the whole process. It should take eight or so iterations (assuming 8Gb at a time) even if you only use the D: drive. It would take fewer if you can use the free space on both drives.

You could refine this approach by making two new partitions, one for /boot and one for /home at the start and then resizing the /home partition, but the principle remains the same.

Hope this helps.

---

