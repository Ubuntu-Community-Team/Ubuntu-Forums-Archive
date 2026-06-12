---
title: "Using GParted to resize Swap space."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by josephpford on 2008-10-25
Howdy!

I'd like to use GParted to resize my partitions such that the Swap space is increased significantly.  I have 512MB of ram, and I am using the GIMP to do some photo editing and I watched my free swap space disappear and then the GIMP gave messages that it was unable to allocate more ram so it couldn't do simple operations.  (I'm working with extremely large files).

Here's my setup:
/dev/sda1 ext3 / 26.75 Total 7.76 Used 18.99 Free
/dev/sda2 extended 1.20 
  /dev/sda5 linux-swap 1.19

I'd like to change the swap space to 3GB using the free space on my / partition.  When I open GParted, all Resize/Move operations are disabled (grayed out).  I looked online and see that I have to unmount non-swap partitions I want to resize, and "Swapoff" the swap partition.  However, how can I unmount my file system if I'm currently using in it?  This seems bad to me.  Do I/should I use a Live CD, or can I do this while booted normally into Ubuntu?

Thanks for all your help.

Regards,
Joseph Ford

---

### Post by drs305 on 2008-10-25
Yes, you will have to reboot with the livecd, a systemrescue cd, or a gparted cd. Operations can't be performed on a running system.

Here is the link to the systemrescuecd page if you are interested:
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by Duck2006 on 2008-10-25
Some info on using gparted.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)

---

