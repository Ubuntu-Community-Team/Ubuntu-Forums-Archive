---
title: "rebooted into BusyBox"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by Gakumerasara on 2012-02-22
What's this BusyBox PoS and how do I 'fix' my computer?  Nothing I find from searching online is useful to me, guides are incomplete and unresolved, and I'm getting spammed with:

udevd[119]: timeout: killing '/sbin/modprobe -bv pci:[lots of numbers]' [202]

followed by

ata_id[278]: HDIO_GET_IDENTITY failed for '/dev/sda': No message of desired type

This machine was working fine an hour ago, when I rebooted following a routine Ubuntu update, and now I've got this mess.  ](*,)

---

### Post by mastablasta on 2012-02-22
[http://en.wikipedia.org/wiki/BusyBox](http://en.wikipedia.org/wiki/BusyBox)
 
try booting form LiveCD and then run boto info script. 
 
though it seems something is wrong with disk or at least it looks like it can't find it.

---

### Post by Gakumerasara on 2012-02-22
> **mastablasta said:**
> [http://en.wikipedia.org/wiki/BusyBox](http://en.wikipedia.org/wiki/BusyBox)
 
try booting form LiveCD and then run boto info script. 
 
though it seems something is wrong with disk or at least it looks like it can't find it.

I just unplugged all hard drives except the main one, and that seems to have 'solved' the problem.  I'll just have to live with it like this for now; I've got deadlines to meet and can't risk it going down again right now.  Thanks for the advice though.  I'll try it once things settle down a bit.

---

