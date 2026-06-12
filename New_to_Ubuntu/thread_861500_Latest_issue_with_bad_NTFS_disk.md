---
title: "Latest issue with bad NTFS disk"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Fred the blarney owl on 2008-07-16
Finally I got around to putting the Ubuntu 64 live CD on my Compaq. I tried to look at the data from my wife's dead Dell (connected via USB) and found the drive would not mount.

I would very much like to access the data, do a diskcopy of all the files and folders in each of the 3 partitions on the hard drive to either DVDs or to another HDD.

I believe it is possible as I have seen the files/folders using some software on Windows by an Indian software house. Unfortunately I don;t have the cash at the moment to buy that software or I'd have done it by now.

Has anybody any suggestions accessing the data from a USB drive caddy?

---

### Post by annda on 2008-07-16
you can try this:
[http://www.sysresccd.org](http://www.sysresccd.org)

i've had a great experience with one of the included tools, TestDisk (also available in the ubuntu repositories)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Fred the blarney owl on 2008-07-16
> **annda said:**
> you can try this:
[http://www.sysresccd.org](http://www.sysresccd.org)

i've had a great experience with one of the included tools, TestDisk (also available in the ubuntu repositories)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I used Test Disk. Things are progressing...

I can now see the 3 partitions from OSX but cannot access them though. I can see nothing via XP.

TestDisk can see the 3 partitions and their contents.

Stupid of me - I should have backed up the entire drive rather than just the data, when I backed it up a few months ago. Ah well... live and learn!

The data is there - as the Indian software proved.

How should I proceed from here?

Edit...

I can see the three partitions from Ubuntu now. I have a FAT 16 partition, an NTFS partition and a FAT 32 partition then some unpartitioned space (about 7mb). The two FAT partitions appear to be fine. The NTFS partiton seems to have a corrupt filing system. How do I uncorrupt the filing system?

---

