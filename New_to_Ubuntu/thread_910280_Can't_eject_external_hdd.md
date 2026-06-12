---
title: "Can't eject external hdd"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by 71CH on 2008-09-04
Hi all
I did many searches both on these forums and on google but can't find a satisfactory solution.  Whenever I try to unmount any of my external hdds it always tells me that it can't eject it due to some unknown error.  A little help please. :)

---

### Post by halitech on 2008-09-04
can you post the output of```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by paul_mcl on 2008-09-04
# fdisk -l
-bash: fdisk: command not found

---

### Post by halitech on 2008-09-04
strange...
okay, try ```
which fdisk
``` and see if it is even there. Might have to do```
sudo fdisk -l
```

---

### Post by 71CH on 2008-09-04
> **halitech said:**
> can you post the output of```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d423d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40b683d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=08960f06-bfcb-4962-b1ef-fd6d03b416a4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=083dc9ab-8535-45f0-9e45-4fc704d25f84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 
```

---

### Post by halitech on 2008-09-04
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux
```

the drive is showing as bootable, did you install or try to install something on it? I think the system thinking its bootable might be whats messing things up

---

### Post by 71CH on 2008-09-04
It shouldn't be bootable cuz I just formatted it to ext3.  Do you know how I can change it so that it's not bootable?

---

### Post by 71CH on 2008-09-04
bizump

---

### Post by halitech on 2008-09-04
try booting from the live cd (partition editor won't let you edit a mounted drive) and see if you can modify the settings

---

### Post by 71CH on 2008-09-04
thanks for your reply but is there no other way?

---

### Post by konungursvia on 2008-09-04
I would try downloading "Gparted" (the ISO or disk image) and burn that, boot from it, and try to unflag the bootable option.

---

### Post by 71CH on 2008-09-06
Thanks but any other ways besides using gparted?

---

### Post by halitech on 2008-09-06
LiveCD or gparted cd are the only 2 ways I know of and even if you use the LiveCD, you are still using gparted as the program to try and unmark it as bootable.

---

