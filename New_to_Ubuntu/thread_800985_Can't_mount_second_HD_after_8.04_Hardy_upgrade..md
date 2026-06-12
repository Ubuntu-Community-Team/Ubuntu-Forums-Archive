---
title: "Can't mount second HD after 8.04 Hardy upgrade."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Darthnix on 2008-05-20
After upgrading to hardy, I cant seem to mount my second hard drive. I can see the drive when I use gparted but it has a warning saying "Couldn't find a valid file system superblock." Also if I boot up using my old 7.04 live disk, I can mount the drive with no problem. Any Ideas?

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91449144

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000006b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19317   155163771   83  Linux
/dev/sdb2           19318       19457     1124550    5  Extended
/dev/sdb5           19318       19457     1124518+  82  Linux swap / Solaris

Disk /dev/sdb is the drive in question.

---

### Post by TeoBigusGeekus on 2008-05-20
Do you see the drive with
```
sudo fdisk -l
```
?

---

### Post by Darthnix on 2008-05-20
Yes sudo fdisk -l brings up the following. Disk /dev/sdb is the drive im having trouble with.

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91449144

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000006b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19317   155163771   83  Linux
/dev/sdb2           19318       19457     1124550    5  Extended
/dev/sdb5           19318       19457     1124518+  82  Linux swap / Solaris

---

### Post by TeoBigusGeekus on 2008-05-20
Can't you see the drive when you go to the menu Places?

---

### Post by Darthnix on 2008-05-20
No its not in there. If I pull up gparted, I can see the drive but it has a warning flag on it that says the following: 

e2label: No such file or directory while trying to open /dev/sdb1
Coundn't find valid filesystem superblock.

dumpe2fs 1.40.8(13-Mar2008)
dumpe2fs: No such file or
directory while trying to open /dev/sdb1

Unable to read the contents or this filesystem!
Because of this some operations may be unavailable.

---

