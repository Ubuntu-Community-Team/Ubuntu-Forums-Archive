---
title: "[SOLVED] how to auto mount a HDD"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by swotie on 2008-04-29
I have cut my HDD in two parts with Gparted ... but when I boot up, I must Mount the second drive manuelly ... How can I auto mount it, so it works proberly. when I boot up

---

### Post by hermes0710 on 2008-04-29
You must add an entry in file /etc/fstab in order to have the second partition mounted on boot. See the existing entry for the first drive in this file and add another one changing the values (ex device location,where to mount it etc) accordingly.

To edit fstab:

```
sudo gedit /etc/fstab
```

---

### Post by swotie on 2008-04-29
The drive I want to auto mount is /dev/sda4 ... but I can't see it here

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5b9bbbfc-ff4a-4ca6-ade6-d75aaacc7c10 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=cefb275f-19c5-4834-aad2-b00deb0576a3 /home           ext3    defaults        0       2
# /dev/sda1
UUID=ad80b6d0-0350-4c7d-83fd-9dbeec6c5248 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


If I use the code: sudo fdisk -l ... I can see it

Disk /dev/sda: 500.1 Gb, 500107862016 byte
255 heads, 63 sectors/track, 60801 cylinders
Units = cylindre of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00026492

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1               1         122      979933+  82  Linux swap / Solaris
/dev/sda2   *         123        2554    19535040   83  Linux
/dev/sda3            2555       22474   160007400   83  Linux
/dev/sda4           22475       60801   307861627+  83  Linux

---

### Post by hermes0710 on 2008-04-29
What is the type of the driver? ntfs/fat/ext3?

---

### Post by swotie on 2008-04-29
ext3

---

### Post by hermes0710 on 2008-04-29
Add this line to your fstab file

```
/dev/sda4 /whatever           ext3    defaults        0       2
```

replacing whatever with the folder in which you want the drive to be mounted.

The folder must exist so if you want to create it use:

```
sudo mkdir /whatever
```

---

### Post by swotie on 2008-04-29
It didn't help

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5b9bbbfc-ff4a-4ca6-ade6-d75aaacc7c10 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=cefb275f-19c5-4834-aad2-b00deb0576a3 /home           ext3    defaults        0       2
# /dev/sda1
UUID=ad80b6d0-0350-4c7d-83fd-9dbeec6c5248 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/sda4 /media/diverse           ext3    defaults        0       2

---

### Post by phr0ze on 2008-04-29
Umm. You don't want a # sign in front. That means ignore this line.

Edit, change to this:
# /dev/sda4 
/dev/sda4 /media/diverse ext3 defaults 0 2

---

### Post by Het Irv on 2008-04-29
after you edit fstab, you can use this to mount your drives without restarting
```
sudo mount -a
```

---

### Post by hermes0710 on 2008-04-29
> **phr0ze said:**
> Umm. You don't want a # sign in front. That means ignore this line.

exactly

---

### Post by swotie on 2008-04-29
it will not work

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=5b9bbbfc-ff4a-4ca6-ade6-d75aaacc7c10 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=cefb275f-19c5-4834-aad2-b00deb0576a3 /home           ext3    defaults        0       2
# /dev/sda1
UUID=ad80b6d0-0350-4c7d-83fd-9dbeec6c5248 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda4/media/diverse           ext3    defaults        0       2

---

### Post by hermes0710 on 2008-04-29
You need a space between /dev/sda4 and /media/diverse in your last line

---

### Post by swotie on 2008-04-29
It works ... :-) ... THANKS

---

