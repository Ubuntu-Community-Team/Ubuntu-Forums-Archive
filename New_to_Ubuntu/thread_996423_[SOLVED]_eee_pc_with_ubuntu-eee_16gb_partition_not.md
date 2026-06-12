---
title: "[SOLVED] eee pc with ubuntu-eee 16gb partition not usable"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by borisbauer on 2008-11-28
My fstab seems to be blank.

~$ sudo fdisk -l 

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000de4ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ec18ec1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1962    15759733+  83  Linux

I did format both drives as est3 with gparted, but the 16gb stays that way no matter what I do. 
Could someone tell me step by step what I have to do to make this partition usable...

Thanks,
B.

---

### Post by sisco311 on 2008-11-28
hi and welcome to the forums.

please post the output of:
```
cat /etc/fstab
```
and
```
sudo blkid
```

---

### Post by borisbauer on 2008-11-28
asus900@asus900-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=99035650-f400-4e6e-9ddf-8b3593d3b9a7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=be03acf0-b77c-4f56-9b4e-e89d1d6302ad none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

*********************************

asus900@asus900-laptop:~$ sudo blkid
[sudo] password for asus900: 
/dev/sda1: UUID="99035650-f400-4e6e-9ddf-8b3593d3b9a7" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="be03acf0-b77c-4f56-9b4e-e89d1d6302ad" 
/dev/sdb1: UUID="58b7dacd-75eb-42e5-97cd-06d61e11e276" TYPE="ext3" 


Thanks for the fast reply... ;>)

B.

---

### Post by sisco311 on 2008-11-28
edit the fstab:
```
sudo nano /etc/fstab
```and add a new enrty:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=99035650-f400-4e6e-9ddf-8b3593d3b9a7 / ext3 relatime,errors=remount-ro 0 1
[b]# /dev/sdb1
UUID=58b7dacd-75eb-42e5-97cd-06d61e11e276 */media/sdb1* ext3 relatime 0 2[/b]
# /dev/sda5
UUID=be03acf0-b77c-4f56-9b4e-e89d1d6302ad none swap sw 0 0
/dev/sdc1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
save the file and exit(Ctrl+o, Enter, Ctrl+x)

create the mount point(/media/sdb1)
```
sudo mkdir */media/sdb1*
```
mount the partition:
```
sudo mount -a
```
set the owner:
```
sudo chown -R $USER: */media/sdb1*
```

---

### Post by borisbauer on 2008-11-28
FLAWLESS.

Thank you so much.

B.

---

