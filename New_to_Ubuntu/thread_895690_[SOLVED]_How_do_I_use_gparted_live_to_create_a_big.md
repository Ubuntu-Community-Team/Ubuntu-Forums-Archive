---
title: "[SOLVED] How do I use gparted live to create a bigger partition?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by bmann11 on 2008-08-20
I burned the gparted live iso onto a cd, but I don't know what to do from here.  I'm starting to have issues running ubuntu because I don't have enough disc space.

---

### Post by linuxguymarshall on 2008-08-20
You should just be able to select your hard drive, and drag the bar around

---

### Post by tuxxy on 2008-08-20
Boot the Live CD mode, and run the gparted program to edit partitions

---

### Post by mlentink on 2008-08-20
GParted is on your Ubuntu Live CD as well.

-Boot with you Ubuntu Live CD
-Make sure you unmount all partitions on the harddrive in question
-Go to System > Maintenance > Partition Editor and fire up GParted

and then you can change partition sizes. Just note that if you want to make one thing bigger, you usually need to make another thing smaller....
So back up your valuable data first!

---

### Post by sandysandy on 2008-08-20
> **bmann11 said:**
> I burned the gparted live iso onto a cd, but I don't know what to do from here.  I'm starting to have issues running ubuntu because I don't have enough disc space.

pop ur gparted Cd in Cd drive and reboot.

once in gparted all ur partitions would be visible.

u can then shrink adjoining partition to ubuntu and expand ubuntu partition in the free space thus created.

see this excellent gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

