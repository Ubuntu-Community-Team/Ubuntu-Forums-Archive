---
title: "External disk, just vanished! Maxtor OneTouch4"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Piddell on 2008-06-16
Hi there,
I just got a 250Gb Maxtor OneTouch4 external HD.  Following the threads on here I reformatted to ext3 and mounted it under /media/OneTouch4.
I also set the permissions from the dark side (command line) so all users could read and write to it - as for some odd reason the disk manager only allows ROOT access, which is not much use.

All was well and I copied 20,000 pictures over to it. and all was well.

Came in today and "you do not have permission" to write to this folder.

I had a look with file browser and all the files seem to have vanished - replaced with an empty "lost+found" directory (with a X on its icon)
I tried accessing from the command line as sudo but it was the same story.

What am I doing wrong?

Phill

---

### Post by superprash2003 on 2008-06-16
please post an output of cat /etc/fstab ..

---

### Post by Piddell on 2008-06-16
phill@phill-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

The disk is showing on disks manager as /dev/sdb1
The access path keeps changing to /media/usbdisk from /media/OneTouch4 (I disabled it and re selected the path the enabled it last time the machine was on)

Thanks

Phill

---

### Post by Raccoon1400 on 2008-06-16
To change permissions, open terminal
```
sudo su
nautilus
```
navigate to the device, click properties, and edit the permissions tab.

---

