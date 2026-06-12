---
title: "problems mounting usb devices"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by tjlane on 2008-11-19
Hi everyone, thanks in advance for reading.

I'm running 8.10 on a Toshiba Satellite A305, and having trouble getting USB devices to mount. I've tried my Sansa e200 in Rhapsody and PlaysForSure modes- (MTP and MSC), and it will not mount.

My USB drives will detect the devices if they are plugged in at bootup, but I cannot access them.

lsusb, with nothing plugged in at startup, returns: 
josh@josh-laptop:~$ lsusb
Bus 006 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

If I plug something in and then run lsusb, it returns nothing at all.

What am I missing?

---

