---
title: "Problems with xfce4-terminal and USB flash drives on Xubuntu 8.04"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by silent contender on 2008-05-15
I am new to Linux and do not have clue what to do to fix my problems in Xubuntu.  Terminal has some graphic problem that I can't explain.  USB flash drives mounts only after running *lsusb* twice.

This is my graphic problem with terminal:

[ATTACH]70243[/ATTACH]

The borders are solid black.

The output from terminal (for flash drive problem) after running *lsusb*:

[I]lsusb
Bus 001 Device 001: ID 0000:0000
lsusb
Bus 001 Device 002: ID 0781:5151  SanDisk Corp. Cruzer Micro 256/512MB Flash Drive[/I]

The flash drive is 1GB and mounts after running *lsusb* twice.  Is there some way to auto-mount?  Thanks in advance.

---

### Post by phidia on 2008-05-15
Are you using the correct driver for your gpu/video card? 
Check the stickies/guides at the top of [this page]("http://ubuntuforums.org/forumdisplay.php?f=334") to get the how to for your card.
The usb mounting problem could be related to a bug briefly addressed [here]("http://ubuntuforums.org/showthread.php?t=745672&highlight=automount+usb+thumb")?

---

### Post by aimpau on 2008-05-16
Go to Applications>>Settings>>Settings Manager>>>Window Manager

Try to change the window theme. If that doesn't help. Log out and log in again using an Xfce session (not Xclient session).

---

### Post by balagosa on 2008-05-16
> **silent contender said:**
> I am new to Linux and do not have clue what to do to fix my problems in Xubuntu.  Terminal has some graphic problem that I can't explain.  USB flash drives mounts only after running *lsusb* twice.

This is my graphic problem with terminal:

[ATTACH]70243[/ATTACH]

The borders are solid black.

The output from terminal (for flash drive problem) after running *lsusb*:

[I]lsusb
Bus 001 Device 001: ID 0000:0000
lsusb
Bus 001 Device 002: ID 0781:5151  SanDisk Corp. Cruzer Micro 256/512MB Flash Drive[/I]

The flash drive is 1GB and mounts after running *lsusb* twice.  Is there some way to auto-mount?  Thanks in advance.

why running lsusb? lsusb only shows what devives are present in your usb drives. hmmm...i dont experience this. my Xubuntu 8.04 auto-mounts

---

### Post by james_vanb on 2008-05-16
If you have the NeoMagic Video Controler, there is a problem with the default terminal in Xubuntu.  See this Bug Report:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/194769](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/194769)

---

### Post by morgengenuss on 2008-05-16
regarding automount in xfce go to thunar -> edit -> preferences -> advanced -> volume management configure

and change it to your liking.

---

