---
title: "[SOLVED] USB Hardrive problem."
date: 2008-10-10
forum: New to Ubuntu
---

### Post by lover_of_sc on 2008-10-10
Hi there,

I have a external usb harddrive, i recently changed it from FAT to EXT3 file system - but now I haven't got write/read permission to it anymore? i can't remember how to rectify it? 

-------

anders@anders-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf5966b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1de2c90e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3fcdf9c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

---

### Post by fr.theo on 2008-10-10
Just had similar problems and some one just helped me out go to this Thread, here is the link

[http://ubuntuforums.org/showthread.php?t=943313](http://ubuntuforums.org/showthread.php?t=943313)


good luck.

---

### Post by lover_of_sc on 2008-10-10
Hmmmm thank you for your reply, still a little confused though.

Here is my fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a8ece2c8-1bfb-4f2d-8261-e418284af78d /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1   /media/disc   ext3   defaults   0   1
# /dev/sda5
UUID=f3692d2a-63a0-4f91-befe-1a8406428a35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

Not sure what to add?

Thanks.

---

### Post by niteshifter on 2008-10-10
Hi,

Assuming that /dev/sdd is the external and it automounts to /media/disk2:

```
sudo chown anders:anders /media/disk2
```
will give user "anders" (you) ownership. You should then be able to read and write with it.

Permissions usually don't need setting on external USB drive. But if you wish or need to:
```
sudo chmod 755 /media/disk2
```
Gives you (the owner) full permissions (7 == rwx), your group read and execute (5 == r-x), and everyone else read and execute.

---

### Post by lover_of_sc on 2008-10-11
Ah fantastic!!!! Thank you. :-)

---

