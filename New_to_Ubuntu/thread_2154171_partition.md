---
title: "partition?"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by jfbooth on 2013-06-13
I am on an old Win ME destop with 512MB and a 10GB hard disk.  It has an upgraded (but old) GE Force Video card ... but I don't know how that card contributes to or detracts from memory.

I want to know if my HD is partitioned correctly.  _I am not a partitioning expert by a long shot_.  The machine is used primarily for FOLDING AT HOME and occasional web browsing.  If it needs 'attention', please provide the procedure.

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders, total 19541088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005a27f

 Device   Boot      Start         End            Blocks   Id  System
/dev/sda1   *        2048       18495487     9246720  83  Linux
/dev/sda2        18497534    19539967      521217    5   Extended
/dev/sda5        18497536    19539967      521216   82  Linux swap / Solaris

Thank you in advance. :D

---

### Post by ajgreeny on 2013-06-13
You're fine as you are, so live with it all as it is.

There is no point having any more swap on a machine with such a small hard drive, and certainly you do not have space for a separate /home partition or anything like that.

---

### Post by jfbooth on 2013-06-13
Thank you, Sir.

---

