---
title: "Define a Partition ?"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Drakkor on 2008-06-18
Yeah, trying to make a flash drive Ubuntu installation , but can't proceed after Define a Partition :confused:

---

### Post by steve101101 on 2008-06-18
use l to list all partitions then type the name of the flash drive.

---

### Post by Drakkor on 2008-06-18
Getting this: 
Disk /dev/sdb: 2008 MB, 2008023040 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea43a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1959898+   b  W95 FAT32
root@ubuntu:/home/ubuntu# umount /dev/sdb1
root@ubuntu:/home/ubuntu# fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 2008 MB, 2008023040 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea43a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1959898+   b  W95 FAT32

Command (m for help): d
Selected partition 1

Command (m for help): 
Command (m for help): 1
1: unknown command
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

Command (m for help): d
No partition is defined yet!

Command (m for help):

---

### Post by steve101101 on 2008-06-18
look here ... [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)

---

### Post by steve101101 on 2008-06-18
or here [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by Drakkor on 2008-06-19
That's exactly what I'm following  ```
p
```, for show partition, ```
d
```, for delete
```
p
``` to show any other partitions , I get the same partition again, it's not deleted !

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# fdisk /dev/sdb

Command (m for help): p

Disk /dev/sdb: 2008 MB, 2008023040 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea43a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1959898+   b  W95 FAT32

Command (m for help): d
Selected partition 1

Command (m for help): p

Disk /dev/sdb: 2008 MB, 2008023040 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea43a

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): d
No partition is defined yet!

---

### Post by cariboo on 2008-06-19
You have to create a partition before you can delete it.
In your example you deleted he partition when you chose 1. It won't echo anything back.

Choose n to add a new partition
choose t for the partition type
choose p to see the partiton you created
Chose w to write the partition to the device and exit

If you are running Ubuntu why can't you use gparted it would make things a lot easier.

Jim

---

### Post by RequinB4 on 2008-06-19
I HIGHLY Recommend the GParted LiveCD - always a good thing to have anyway, and a dead horse could partition with it.

info:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

download:

[http://download.tuxfamily.org/gpartedlive/](http://download.tuxfamily.org/gpartedlive/)

---

