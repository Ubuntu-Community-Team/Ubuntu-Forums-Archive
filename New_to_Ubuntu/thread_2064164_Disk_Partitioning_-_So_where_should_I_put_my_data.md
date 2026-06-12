---
title: "Disk Partitioning - So where should I put my data"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by clskier on 2012-09-28
I'm setting up an Ubuntu server as a central file server in my house.  The boot drive is a 750 Gb drive.  I let the installation create my partitions automagically, and now I'm confused which partition to mount for data storage.  I do have two other drives in the box that will be all data, but I wanted to make use of the boot drive too since I don't see needing all 750 Gb for the OS.  Below is the fdisk -l for the drive:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2d55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1465147391   732322817    5  Extended
/dev/sda5          501760  1465147391   732322816   8e  Linux LVM

---

### Post by clskier on 2012-09-28
More information:
I just noticed these two entries further down the fdisk -l output:

Disk /dev/mapper/HTPC-root: 741.7 GB, 741729107968 bytes
255 heads, 63 sectors/track, 90176 cylinders, total 1448689664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/HTPC-root doesn't contain a valid partition table

Disk /dev/mapper/HTPC-swap_1: 8166 MB, 8166309888 bytes
255 heads, 63 sectors/track, 992 cylinders, total 15949824 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/HTPC-swap_1 doesn't contain a valid partition table

Are these maybe the 3rd and 4th partition on my sda disk?

---

### Post by oldfred on 2012-09-28
I do not use LVM, but know you cannot use standard fdisk & gparted with LVM. You have to use the LVM tools to edit or view LVM partitions.

Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

With Linux RAID & LVM 
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

