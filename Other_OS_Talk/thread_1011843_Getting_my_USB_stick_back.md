---
title: "Getting my USB stick back"
date: 2008-12-15
forum: Other OS Talk
---

### Post by joffeloff on 2008-12-15
Hi guys,

A while ago I installed Arch Linux on a USB stick I have. Now, whenever I insert it into my Windows machine it only recognizes one of the tiny, megabyte-sized partitions, and whenever I insert it into my Ubuntu machine it doesn't recognize it as a device, it only sees the various partitions. I tried this umount /dev blah blah and mkfs ext3 somethingorother but it only works on the first partition of the stick, and beyond that it gets too complicated for me.

How can I 'un-partition' it, format it completely and get it back to its normal size so I can use it to create an Ubuntu 8.10 Live USB?

---

### Post by sertse on 2008-12-15
[http://www.pendrivelinux.com/2007/07/19/restoring-your-usb-key-partition/](http://www.pendrivelinux.com/2007/07/19/restoring-your-usb-key-partition/)

The usual guide I use, seems to work well.

---

### Post by joffeloff on 2008-12-15
I got a tip to download and run GParted, and that worked. Very simple too, just select /dev/sdb and clear it. Awesome stuff.

Thanks anyway though!

---

