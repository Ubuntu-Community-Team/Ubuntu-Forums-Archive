---
title: "Ubuntu Lucid 32 bit Busybox error using linux mint live usb to fix it."
date: 2012-05-22
forum: New to Ubuntu
---

### Post by TheManno1 on 2012-05-22
I have ubuntu lucid 32 bit and am currently using linux mint on a usb to type this.

Using this to solve it but can't find root drive partition numbers.
[http://www.tuxtrix.com/2009/12/solving-busybox-black-screen-problem-in.html](http://www.tuxtrix.com/2009/12/solving-busybox-black-screen-problem-in.html)

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001fd00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59935   481426432   83  Linux
/dev/sda2           59936       60802     6957057    5  Extended
/dev/sda5           59936       60802     6957056   82  Linux swap / Solaris

Disk /dev/sdb: 4001 MB, 4001366016 bytes
124 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      419273      451359   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(419272, 58, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(451358, 103, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       56305      157201   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(56304, 96, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(157200, 21, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      243180      492820   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(243179, 38, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(492819, 2, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      259536      260619     4161536    a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(259535, 64, 9)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(260618, 15, 14)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

