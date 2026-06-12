---
title: "Disk (name) doesn't contain a valid partition table"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by wlraider70 on 2012-03-22
I'm getting this error.

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

I have second hard drive that I partitioned via a live disk and made the whole thing ext3. Its only for storage, but obviously I did something wrong. 

here is the full context.
```



sudo fdisk -l
[sudo] password for server:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009ce3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   156301311    77899777    5  Extended
/dev/sda5          501760   156301311    77899776   8e  Linux LVM

Disk /dev/mapper/ubuntu-root: 79.2 GB, 79230402560 bytes
255 heads, 63 sectors/track, 9632 cylinders, total 154746880 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 536 MB, 536870912 bytes
255 heads, 63 sectors/track, 65 cylinders, total 1048576 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

```

a bit more code


server@ubuntu:~$ sudo umount /dev/mapper/ubuntu-swap_1
umount: /dev/mapper/ubuntu-swap_1: not mounted
server@ubuntu:~$ sudo mount /dev/mapper/ubuntu-swap_1 /mnt/halftb -t ext3
mount: /dev/mapper/ubuntu-swap_1 already mounted or /mnt/halftb busy

---

### Post by MG&amp;TL on 2012-03-23
Okay, if it's empty and only going to be used for data, just try again from disk utility or whatever-perhaps something went wrong the last time. You should just be able to format the disk as you wish.You do need to create a partition over the entireity of the disk to use it though.

---

