---
title: "How can I make a usb startup with updates"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Michaelg14 on 2008-11-02
I have 8.10 with a few mb of updates and would like to make a startup usb drive that included the updates.  It asks for an iso file which is of course lacking several updates.  Is it possible?

---

### Post by C.S.Cameron on 2008-11-02
You can make a Full install of Ubuntu to USB using the install on the Live CD.
Most modern computers see flash drive as just another hard drive.
Probably best to disable your internal drive first.

You might also be able to clone your install to the USB drive using dd if it is not too large.

Persistent install with usb-creator will also save updates.
These are kept in files called casper-rw and home-rw.
I'm not sure how to save to these files externally.

Persistent install with usb-creator will also default persistence to partitions named casper-rw and home-rw, you can save to these externally.

If you want to remaster a flash drive so that you can make custom installs from it, I have found this, but not tried it.
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

