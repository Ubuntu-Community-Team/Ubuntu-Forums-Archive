---
title: "Windows partitions lost after installing ubuntu??"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by p4nikos on 2012-03-14
Hi,
I have two physical hard disks, one around 200GB and one 1TB. I had the large one splitted into 3 partitions around 300GB each. I used Windows XP.
Yesterday I formatted the small disk and installed Ubuntu 10.4 (trying not to mess with anything in the large disk).
Now from within Ubuntu I can see only the third partition of the large disk (referring as size 1TB). 
I tried to use GParted but it still mentions only one large partition (that contains only the files of the third previous partition).
Any way to recover lost partitions?

Thank you very much,
Nick

---

### Post by The Cog on 2012-03-14
That's a bit worrying. Can you start a terminal and run the two commands ```
sudo fdisk -l
sudo blkid
```
and post the output here?

---

### Post by p4nikos on 2012-03-14
> **The Cog said:**
> That's a bit worrying. Can you start a terminal and run the two commands ```
sudo fdisk -l
sudo blkid
```and post the output here?

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d1369

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19084   153285632   83  Linux
/dev/sdb2           19084       19458     3002369    5  Extended
/dev/sdb5           19084       19458     3002368   82  Linux swap / Solaris

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c5e4805

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   42  SFS

Disk /dev/sdc: 4137 MB, 4137680896 bytes
255 heads, 32 sectors/track, 990 cylinders
Units = cylinders of 8160 * 512 = 4177920 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09ab09aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         990     4039184    b  W95 FAT32

sudo blkid
/dev/sdb1: UUID="89507a20-4644-4d9c-9e53-ca2f28a84363" TYPE="ext4" 
/dev/sdb5: UUID="a6a39719-6cc9-4de3-83d8-566eef6fc761" TYPE="swap" 
/dev/sda1: LABEL="HugeFiles" UUID="7C6052056051C714" TYPE="ntfs" 
/dev/sdc1: LABEL="RED 4GB" UUID="B215-FA4C" TYPE="vfat"

---

### Post by Mark Phelps on 2012-03-14
The 1TB drive shows SFS -- which means any Basic Disks (MS's term for partitions) that were there before have been converted into Dynamic Disks.  This is done automatically in MS Windows when you try to have more than 4 primary partitions on a single drive that is not GPT or UEFI.

Linux can't handle Dynamic Disks, so it can't accurately report what is there, and it can't install to them.

There are s couple of Windows products, which can be downloaded and burned to CD, that will convert Dynamic Disks back to basic -- but I think you have to purchase the PRO options of either: Partition Wizard or EASEUS Partition Master.

---

### Post by p4nikos on 2012-03-14
> **Mark Phelps said:**
> The 1TB drive shows SFS -- which means any Basic Disks (MS's term for partitions) that were there before have been converted into Dynamic Disks.  This is done automatically in MS Windows when you try to have more than 4 primary partitions on a single drive that is not GPT or UEFI.

Linux can't handle Dynamic Disks, so it can't accurately report what is there, and it can't install to them.

There are s couple of Windows products, which can be downloaded and burned to CD, that will convert Dynamic Disks back to basic -- but I think you have to purchase the PRO options of either: Partition Wizard or EASEUS Partition Master.

Thank you very much,
in about a week I am expecting my new disk, so then I will try to recover the partitions through windows. I was concerned that they may have been gone forever...
:p
anyway, now I am appreciating ubuntu speed - I am going to keep it for all my non windows work.

---

### Post by oldfred on 2012-03-14
SFS is dynamic partitions in Windows. But I thought dynamic only worked with Vista or 7? You normally get dynamic partition from the Windows 7 partitioning tool when you try to create more than 4 partitions. How did you get the SFS partition?

> Device Boot Start End Blocks Id System
/dev/sda1 * 1 121601 976760001 42 SFS


Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.

As such Linux does not work with dynamic volumes.

---

