---
title: "[SOLVED] stuck partitioning and formating a usb drive"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by z01nx on 2008-06-25
I am trying to create a usb bootable distro. I am running fsck on /dev/sbd1 to check the file system and it keeps returning with: 
```
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Seek to 2004860416:Invalid argument

```
when according to the guide I am following I should receive something like this: 
```
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 0 files, 1/264543 clusters
```
Is it ok to continue along or do I need to correct something? Here is a list of my partitions on the usb drive:
```
Disk /dev/sdb: 2004 MB, 2004877312 bytes
129 heads, 32 sectors/track, 948 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         512     1056752    b  W95 FAT32
/dev/sdb2             513         948      899904   83  Linux

```
Thanks for any help.

---

