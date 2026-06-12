---
title: "formatting usb drive"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by hugh4 on 2014-03-06
I have a usb drive that I formatted using ubuntu/osx or other, now can't format using any OS.
Tried gparted but not listed in available drives.
fdisk -l and mkfs gives:

Disk /dev/sdc: 16.1 GB, 16106127360 bytes
255 heads, 63 sectors/track, 1958 cylinders, total 31457280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      409639      204819+  ee  GPT
/dev/sdc2          411648    31455231    15521792    7  HPFS/NTFS/exFAT
/dev/sdc3         1048576     1048576           0    0  Empty
/dev/sdc4           16386       16386           0    0  Empty
root@NUC:/home/hugh# mkfs.ntfs /dev/sdc
Could not open /dev/sdc: Read-only file system

How can I format this usb so It's usable?

---

### Post by phidia on 2014-03-06
You can try > sudo umount /dev/sdc1 
sudo fsck.vfat -f -v /dev/sdc1 

If you run into problems take a look at [this]("http://askubuntu.com/questions/22381/how-to-format-a-usb-flash-drive").

---

