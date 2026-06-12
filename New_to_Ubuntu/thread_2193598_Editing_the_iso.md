---
title: "Editing the iso"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by bradleyswain1 on 2013-12-13
I made a previous post about some trouble installing any version of Linux and found something that looks like it should work [HERE]("http://askubuntu.com/questions/228927/ubuntu-12-04-install-failed-command-identify-packet-device").

My question is, because I am unable to install Linux at all, how do I go about editing the "lib/udev/rules.d/60-persistent-storage.rules" file in the iso? Is that even possible?

Thanks!

---

### Post by DuckHook on 2013-12-13
Are you the original poster to the linked thread? If so, then I would recommend first trying what the last comment on that thread suggests: moving your CD/DVD to another SATA port.

Whenever you see an "ATA"-type error, it points to a drive not communicating properly with the MOBO. Often, especially with old drives, this means the drive has failed and there's nothing you can do in software&#8212;the only option is to replace the drive (or sometimes, the MOBO). If other OSes see the drive properly, then the drive is not the issue. Rather, it is some arcane conflict between Ubuntu, the MOBO and the drive that is causing indigestion. Sometimes just moving the drive cable to another SATA port is all that is needed to fix it.

Re: your question:

It is not possible to edit any settings in the .iso. ISO images are by nature read-only formats. The stated solution was meant for an already installed system to allow it to read the DVD drive after the fact. If you wish to try this solution, then you need to find an alternate way of installing your system first, that does not use the problematic DVD drive. If you have access to another computer, then the easiest way to do this is to use *unetbootin*, burn the .iso image to a USB stick, and install through USB. You can then try the given instructions after your system boots.

---

