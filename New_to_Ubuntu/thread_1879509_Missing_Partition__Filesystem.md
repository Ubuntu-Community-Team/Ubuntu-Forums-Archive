---
title: "Missing Partition / Filesystem"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by hallph on 2011-11-11
Hi all, I'm using Ubuntu 11.04 and it's been fine until now.
One of my partitions/filesystems has gone missing in the browser. 

Does anyone know what I can do to get it back there? Before, it was listed as '92gb Filesystem'


The output from the following is attached:
sudo fdisk -l

```
sudo fdisk -l

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders, total 231496650 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   215095296   219000831     1952768   83  Linux
/dev/sda2            2046   215094284   107546119+   f  W95 Ext'd (LBA)
/dev/sda3       219000832   226813951     3906560   82  Linux swap / Solaris
/dev/sda5        34812918   215094284    90140683+   7  HPFS/NTFS/exFAT
/dev/sda6            2048    34811903    17404928   83  Linux

Partition table entries are not in disk order

```

---

### Post by jerrrys on 2011-11-11
testdisk may work for you.  you can load it from the software center.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Mark Phelps on 2011-11-12
Before you presuming it is gone, suggest you open the Disk Utility and see if it's still there.

If you're talking about the Windows partition, it could simply not be mounting anymore, not missing.

---

### Post by Rubi1200 on 2011-11-12
It would also help us if you can post the results of the boot info script please.

There is a link at the bottom of my post with instructions.

Thanks.

---

