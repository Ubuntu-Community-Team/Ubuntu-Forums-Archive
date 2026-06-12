---
title: "Fixing a LiveUSB"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by Scooterdork07 on 2013-03-21
OK, I've got a couple of flash drives and SD cards that I've been using to LiveUSB linux things through The universal USB installer. My problem is, I can't figure out how to revert them back to working in windows, preferably using windows. Anyone have a link that WORKS?

---

### Post by slickymaster on 2013-03-21
Check these ones out:

[Restore Your USB Key to it's original state]("http://www.pendrivelinux.com/restoring-your-usb-key-partition/")
[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by Cheesemill on 2013-03-21
Google for '[hp usb format tool]("https://www.google.com/search?q=hp+usb+format+tool")'.

---

### Post by Scooterdork07 on 2013-03-21
OK, technically, the problem drive is an SD card, and BOOTICE isn't working. Will the HP thing work for me?

EDIT the SD card shows up in Drive manager, but not in My Computer

---

### Post by Scooterdork07 on 2013-03-21
OK, it doesn't even show up in the HP thing

---

### Post by cortman on 2013-03-21
Perhaps you should format the drives/cards in Linux, using GParted- I've always had good luck with it. Format them as FAT32 or NTFS.

---

### Post by Scooterdork07 on 2013-03-21
OK, that probably shoul have been my first step. Trying noW!

---

### Post by Scooterdork07 on 2013-03-21
this@this:~$ sudo su
root@this:/home/this# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe54a8aa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   935811071   467802112    7  HPFS/NTFS/exFAT

Disk /dev/mmcblk0: 2028 MB, 2028994560 bytes
255 heads, 63 sectors/track, 246 cylinders, total 3962880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x821bd032

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             128     3958911     1979392    6  FAT16

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    31262489    15631213+   c  W95 FAT32 (LBA)
root@this:/home/this# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xe54a8aa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   935811071   467802112    7  HPFS/NTFS/exFAT

Disk /dev/mmcblk0: 2028 MB, 2028994560 bytes
255 heads, 63 sectors/track, 246 cylinders, total 3962880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x821bd032

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1             128     3958911     1979392    6  FAT16

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    31262489    15631213+   c  W95 FAT32 (LBA)
root@this:/home/this# fdisk /dev/mmcblk0p1

Command (m for help): d
Partition number (1-4): 1

Command (m for help): d
Partition number (1-4): 2

Command (m for help): d
Partition number (1-4): 3

Command (m for help): m                           
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): n
Partition type:
   p   primary (1 primary, 0 extended, 3 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1): 1
No free sectors available

Command (m for help): w
fdisk: unable to write /dev/mmcblk0p1: Operation not permitted
root@this:/home/this# fdisk /dev/mmcblk0
You will not be able to write the partition table.

Command (m for help): d
Selected partition 1

Command (m for help): w
fdisk: unable to write /dev/mmcblk0: Bad file descriptor
root@this:/home/this#

---

### Post by cortman on 2013-03-21
You may want to try running the delete and create new commands separately.
Or use GParted if it is available.
Just as a tip as well: you can use fdisk with sudo, no need to change accounts.
Good luck.

---

