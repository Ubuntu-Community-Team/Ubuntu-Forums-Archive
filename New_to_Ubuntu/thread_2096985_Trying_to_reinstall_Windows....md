---
title: "Trying to reinstall Windows..."
date: 2012-12-21
forum: New to Ubuntu
---

### Post by amaleerowan on 2012-12-21
...and it's not going so well. I had a dual boot with ubuntu 12.04 and windows xp, but I wanted to wipe the hard drive and install windows on its own, so I wiped the windows 7 partition from my mounted ubuntu 12.04 partition and tried to delete it using gparted. I didn't realize that the partition formerly known as windows was the only primary partition and thus couldn't be deleted until after the fact. This computer doesn't boot from a usb (i've tried) and now the boot menu claims my install CD isn't bootable, either.

I love ubuntu and i'm only trying to reinstall windows on this computer so that i can resell it (nobody wants to buy a computer running ubuntu, unfortunately, because it's so difficult to run windows programs in it for the average person.) But I would really appreciate some help.

I've got the iso file for windows, is there a way to do a fresh install on the primary partition from within ubuntu? I've tried copying the iso file to the empty partition and adding said partition back to grub, but it didn't work.

---

### Post by superDave972 on 2012-12-21
This has happened to me before and it has always been 1 of 2 causes. Either I didn't burn the iso correctly (as an image) or my boot options in my BIOS were not set correctly. I would double check those settings and try booting a different machine with your windows iso disc - just to make sure it is burned properly.

---

