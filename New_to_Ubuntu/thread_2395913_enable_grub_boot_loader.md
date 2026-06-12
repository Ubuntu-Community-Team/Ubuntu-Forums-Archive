---
title: "enable grub boot loader"
date: 2018-07-08
forum: New to Ubuntu
---

### Post by dyesdyes on 2018-07-08
Hey, 

I'm new to ubuntu.

I had a windows 10 already installed. I installed ubuntu 18.04 later on. Both work but...

Grub doesn't appear. I would like to select between windows and ubuntu at the startup, it's a bit annoying to have to press F12 at each startup to choose the right partition.

I have no clue what's going on, so here is the report that might help:

Here is the boot-repair paste bin: [http://paste.ubuntu.com/p/xB45DGC8P8/](http://paste.ubuntu.com/p/xB45DGC8P8/)

Thanks a lot !

---

### Post by oldfred on 2018-07-08
What brand/model system?

You have UEFI system, and it looks like you have Windows installed in UEFI mode.
You may have Ubuntu in UEFI mode, but cannot tell for sure.

You need to boot the Ubuntu live installer in UEFI mode, and re-run report.
You booted in BIOS/CSM/Legacy mode. Your UEFI should have two boot entries for Ubuntu live installer.

---

