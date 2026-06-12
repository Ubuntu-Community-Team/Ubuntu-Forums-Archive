---
title: "floppy problem"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by hubiedo on 2008-07-23
i am unable to mount my floppy drive either with gfloppy, places>computer>floppy drive etc. i have tried manually to mount it with sudo mount etc.

when i use sudo gfloppy the message i get is:

The filesystem creation utility (/sbin/mkdosfs) reported the following errors:

mkdosfs: unable to get diskette geometry for '/dev/fd0'
 (56)

this is the contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc3
UUID=66e6abb9-66cf-4060-b506-5d5b4ede7985 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=bf59b4a0-94c8-4ff5-8fb2-d65992f71603 /appl           ext3    relatime        0       2
# /dev/sdc1
UUID=937e2f3b-82a4-4890-aeca-1686c106c50f /boot           ext3    relatime        0       2
# /dev/sdc8
UUID=dc8243b7-e1e9-4953-bd4e-7e0b9fce7ebf /bulin          ext3    relatime        0       2
# /dev/sdc5
UUID=0957cf0a-e821-447d-9d30-12cb907bea86 /home           ext3    relatime        0       2
# /dev/sdc7
UUID=4a21a0ba-18a1-44fb-b65b-1ea7230217df /u              ext3    relatime        0       2
# /dev/sdc2
UUID=a8302613-3392-4ec2-9d43-5724a7e73b78 none            swap    sw              0       0
# orig config below
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#HJK CONFIG
#/dev/fd0        /media/fd0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/fd0  /mnt/floppy     auto   user,defaults,noauto   0  0
#/dev/cdrom  /mnt/cdrom     auto   user,rw,defaults,noauto   0  0
# UBUNTU CONFIG TO ALLOW ALL USERS TO MOUNT FD0
/dev/fd0        /media/floppy0  auto rw,users,noauto,fmask=111,dmask=000  0   0

you can see several different ways i have tried to change the fstab file. nothing works.i have used several different diskettes and it was working in win2k so i am pretty sure that it is not a hardware problem.

if anyone has any ideas or suggestions, it would be greatly appreciated.

hubie

---

### Post by halitech on 2008-07-23
I have 8.04 on my laptop (only machine with a working floppy anymore) and I just went to Places - Floppy and it mounted it and opened nautilus to show the files.

---

### Post by plucky on 2008-07-24
> #/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

Un-comment that line in fstab

> /dev/fd0 /media/floppy0 auto rw,users,noauto,fmask=111,dmask=000 0 0


Comment that line

Then try ```
sudo mount /dev/fd0 /media/floppy0
``` and a floppy icon should appear on your desktop.

Don't forget to dismount the drive before removing the disk.


Good Luck

---

### Post by maybeway36 on 2008-07-24
You shouldn't need to use sudo if you're in the "floppy" group.

---

