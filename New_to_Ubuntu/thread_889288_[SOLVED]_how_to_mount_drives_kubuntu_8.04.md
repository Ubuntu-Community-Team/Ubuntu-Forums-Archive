---
title: "[SOLVED] how to mount drives kubuntu 8.04"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by stonerrob420 on 2008-08-13
I've got drive it's a western digital 80 GB drive. Connected to computer by a promise ultra 66 PCI host card. How can I mount that drive where I can access the data on the drive? It shows up in storage media tab but doesnt mount. Any help is much appreciated.

---

### Post by iaculallad on 2008-08-13
> **stonerrob420 said:**
> I've got drive it's a western digital 80 GB drive. Connected to computer by a promise ultra 66 PCI host card. How can I mount that drive where I can access the data on the drive? It shows up in storage media tab but doesnt mount. Any help is much appreciated.

Post the output of the following commands below:

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

---

### Post by stonerrob420 on 2008-08-13
sudo fdisk -l

Disk /dev/hdf: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   ?      216399     1904881   850995205    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdf2   ?      723265     1262922   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hdf3   ?      167316      167316           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hdf4         2671568     2671619       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007d0ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

sudo blkid

rob@OEMCOMPUTER:~$ sudo blkid
/dev/sda1: UUID="37a2979e-0ac5-4500-899c-a948e7d541e1" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="348b610b-89db-4c9b-852e-846965441bc1"
/dev/hdf: UUID="1E40B2C240B2A047" TYPE="ntfs"
rob@OEMCOMPUTER:~$

rob@OEMCOMPUTER:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=37a2979e-0ac5-4500-899c-a948e7d541e1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=348b610b-89db-4c9b-852e-846965441bc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
rob@OEMCOMPUTER:~$

---

### Post by iaculallad on 2008-08-14
The problem might be on the physical drive as fdisk doesn't know how to categorize it, try re-arranging the pin configuration of your western digital drive (Master/Slave/Auto).

---

### Post by stonerrob420 on 2008-08-14
cool I'll give it a try. Thanks.

---

### Post by stonerrob420 on 2008-08-14
Got it figured out. Went to system menu then clicked on storage media. right clicked on 81GB media. Went to mounting tab selected ticked read only. now the drive mounts. I knew there had to be a easier way to make the drive mount. thanks for your help. it was very informative.

---

