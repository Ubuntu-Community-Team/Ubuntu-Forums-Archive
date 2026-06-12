---
title: "[SOLVED] help with automounting hard drive"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by tantrik on 2008-05-19
I have a fat32 partition on my hard drive... earlier wen i was using gutsy the partition used to auto mount at startup.. now it doesnt happen nymor... can someone tell me wat needs to b done... is it wid the fstab or jus some regular command needs to b added to d startup...

thnx in advance

---

### Post by tamoneya on 2008-05-19
this has to be added to fstab.  Post /etc/fstab as well as the result of ```
sudo fdisk -l
```Then we should be able to easily tell you what lines you need to add to fstab.

---

### Post by tantrik on 2008-05-19
fstab goes like dis...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dd1ff6d4-00ec-45aa-bcb1-6be62316a576 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=7f3df34f-8888-4a2a-b051-f0fea514aff1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


n fdisk results are as follows

tantrik@tantrik-laptop:~$ sudo fdisk -l
[sudo] password for tantrik: 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74b7f7ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1033     8297541   83  Linux
/dev/sda2            1307        7296    48114675    b  W95 FAT32
Partition 2 does not end on cylinder boundary.
/dev/sda3            1034        1306     2192872+  82  Linux swap / Solaris

Partition table entries are not in disk order
tantrik@tantrik-laptop:~$

---

### Post by tantrik on 2008-05-20
can anybody help in dis regard??

---

### Post by Helgiks on 2008-05-20
If I understand you correctly you wan't "sda2" to load on startup. Than add something like:

/dev/sda2 <LOCATION> vfat rw 0 0

To you're fstab.

---

### Post by pluckypigeon on 2008-11-14
And if you are still stuck: 

(I'd recommend trying to edit fstab first, just for practice)

install pysdm

```
sudo apt-get install pysdm
``` in a terminal

you can run it by System > Administration > Storage Device Manager

or 

```
gksudo pysdm
``` in a terminal

Then.. go to the partition in question (e.g sdc1 or whatever yours is)

Click on "Assistant"

Make sure "The file system is mounted at boot time" is checked

Click "OK" then "Apply" then "Close"

I might p*ss of some people by putting this here but if you are stuck with editing fstab then this may be useful to you!

Check out the fstab file after to check how this has edited it, you may learn something that way!

This is just a ui for editing fstab

---

### Post by larryfroot on 2008-12-23
Thank you loads!

I was trawling around for fstab advice, but your recommendation for such a fab little utility saved me so much time. Keep on being ace! LF

---

