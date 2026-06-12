---
title: "Mounting Ubuntu Partition on Xubuntu"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by cymoril on 2008-04-25
Hello!

I installed Xubuntu 8.04 on the hard drive which had my Ubuntu 7.10 installation.

I can't access the data on my Ubuntu partition while using Xubuntu. I think I'm supposed to mount the partition and edit /etc/fstab but I'm not sure how to do this.

fdisk -l yielded the following:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2595    20844306   83  Linux
/dev/sda2            2596        4870    18273937+   5  Extended
/dev/sda5            4687        4870     1477948+  82  Linux swap / Solaris
/dev/sda6            2596        4593    16048872   83  Linux
/dev/sda7            4594        4686      746991   82  Linux swap / Solaris

Partition table entries are not in disk order

..

These are the contents of /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=debad23b-546d-4da2-957f-d5dd4bd6c770 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=34a67aa7-e5c8-4a5f-9a6c-b60182e3df72 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

What must I do?

Thank you.

---

### Post by gsmanners on 2008-04-26
Go to a console and type:

sudo mkdir /media/sda1
gksudo mousepad /etc/fstab

Then, in mousepad add the following:

/dev/sda1 /media/sda1 ext3 defaults 0 0

---

