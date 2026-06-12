---
title: "evdev driver replacement"
date: 2011-09-19
forum: Programming Talk
---

### Post by dclapp on 2011-09-19
I am trying to get a touchscreen working with the right click functionality.  This has been implemented in xf86-input-evdev in a release later then what is available in Ubuntu 11.04 that I am using.  So I want to upgrade my driver, which is in the package called xserver-xorg-input-evdev.

I was able to grab the package "xf86-input-evdev" and compile it to produce a evdev_drv.ko library.  

So here is my question.  How do I go about replacing the old driver with the new one?  I tried to do a "make install" with then new driver, but I don't think it replace things in the correct place by default, or it corrupted something.  It is trying to use "libtool" to do the installation.

How do I replace a *.ko and check and see if it was successful?

What is the relation between xserver-xorg-input-evdev, Ubuntu release and the xf86-input-evdev, and is it important for what I am trying to do?

I am new to driver development and changing the linux kernel

Some background:

I am running Natty on a armel Beagleboard C4.
Using a eGalaxa touchscreen driver, which works good out of the box with the old evdev and xinput (except for right click, three button emulation).
I downloaded and compiled a non-release version of xf86-input-evdev because it had the chances I needed, but did not require a upgrade to xserver.

Any suggestion appreciated.

Dan

---

