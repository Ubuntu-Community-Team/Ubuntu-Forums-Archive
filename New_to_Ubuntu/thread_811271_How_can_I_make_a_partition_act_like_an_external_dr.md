---
title: "How can I make a partition act like an external drive?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by TriviallyTravis on 2008-05-29
For example, if I take an external hard drive and plug it into my USB port, it'll mount automatically and show up on the desktop. From there, I can right-click it, share it, change the label, etc. etc. I want to be able to do this with partitions on my hard drive. Basically right now the HDD is set up like this: 

20GB - /
2 GB - swap
200 GB - fat32
266 GB - fat32

I tried to set them up when I first installed ubuntu by mounting them at /media/disk1 and /media/disk2 but that apparently did not work. After struggling with it for a couple of hours, and getting no help from Google, I thought I'd turn here. Ultimately I want to be able to share these two drives to my Macbook over a LAN.

I'm using version 8.04. 

Thanks!

---

### Post by logos34 on 2008-05-29
$ **gconf-editor**

apps>nautilus>desktop>volumes visible

sudo mkdir /media/whatever

gksudo gedit /etc/fstab

add a line for each partition like this:

> /dev/sda? /media/whatever vfat defaults,umask=0000 0 0 

Or use the UUID format.  Find with:

blkid

or

ls -l /dev/disk/by-uuid

To add [disk labels]("http://www.linux.com/base/ldp/howto/Partition/labels.html#volumelabels"):

sudo tune2fs -L label /dev/sda?

---

