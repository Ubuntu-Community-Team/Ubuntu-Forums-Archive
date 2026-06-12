---
title: "Adding another hard drive"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by harry001 on 2008-09-29
Hi all,

l've added another hard drive but can't get it to show. here is the output from fdisk -I

admin@ns364881:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073d16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         650     5221093+  fd  Linux RAID autodetect
/dev/sda2             651       91136   726828795   fd  Linux RAID autodetect
/dev/sda3           91137       91201      522112+  82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2fde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         650     5221093+  fd  Linux RAID autodetect
/dev/sdb2             651       91136   726828795   fd  Linux RAID autodetect
/dev/sdb3           91137       91201      522112+  82  Linux swap / Solaris

Disk /dev/md2: 744.2 GB, 744272560128 bytes
2 heads, 4 sectors/track, 181707168 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 5346 MB, 5346295808 bytes
2 heads, 4 sectors/track, 1305248 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
admin@ns364881:~$ 

what have l done wrong?

---

### Post by Het Irv on 2008-09-29
Have you formatted the new drive?  I don't think unformatted drives show there, but I am not sure.

---

### Post by bumanie on 2008-09-29
You have to format a raw disk with a filesystem before it show up.

---

