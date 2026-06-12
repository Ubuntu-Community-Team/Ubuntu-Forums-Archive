---
title: "second hard drive issues"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by imT on 2008-05-12
on a hardy system i installed xfce 4 speed 	:-\"
i have 2 hard drives but in xfce it only sees one.
here's some outputs:
```
user@ubpc:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3d9e2e07-88c3-4da8-b1c0-2f6106fd66ae /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=1c2477b0-7ad3-4ffa-8695-28ed0ef9e316 /home           ext3    relatime        0       2
# /dev/sda1
UUID=a0e89187-b70d-4579-9fa8-f54a28ca3c6d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
and
```
user@ubpc:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95439543

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         124      995998+  82  Linux swap / Solaris
/dev/sda2   *         125        1369    10000462+  83  Linux
/dev/sda3            1370        9729    67151700   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21832182

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241   83  Linux

```

apparently it dose not see the sdb1... how do i mount that and also how to set it in order to self mount at login ?:confused:

---

### Post by tamoneya on 2008-05-12
you mount it like this:```
sudo mkdir /seconddrive
sudo mount /dev/sdb1 /seconddrive
```
If you want it to mount automatically add this to the bottom of fstab:```
/dav/sdb1 /seconddrive ext3 defaults 0 0
```

---

### Post by imT on 2008-05-12
thanks, much appreciated :KS

---

### Post by tamoneya on 2008-05-12
/seconddrive can of course be changed to whatever you want.

---

