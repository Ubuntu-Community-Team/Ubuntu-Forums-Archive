---
title: "Increase root.disk size?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Champers on 2008-04-23
I just downloaded Ubuntu 8.04 last weekend, and I've been having fun learning about how to do things in it. I installed it in Windows, and not on its own real partition. I originally thought that I would only need about 5GB, because I thought that most programs could be run off my NTFS XP setup. Wine requires many programs to be installed on the root.disk in order to work. **I want to know if I can increase the size of the root.disk from 5GB to 20GB without reinstalling Ubuntu.** It took me days to get all of my drivers working (Wireless was a killer!) and I would rather not go through all of that again. If my only option is re-installation, is there any way to save what I have done (drivers/software) on this installation and put it into a new installation?


Answer bolded question if you can help.

---

### Post by Monicker on 2008-04-23
> **Champers said:**
> I just downloaded Ubuntu 8.04 last weekend, and I've been having fun learning about how to do things in it. I installed it in Windows, and not on its own real partition. I originally thought that I would only need about 5GB, because I thought that most programs could be run off my NTFS XP setup. Wine requires many programs to be installed on the root.disk in order to work. **I want to know if I can increase the size of the root.disk from 5GB to 20GB without reinstalling Ubuntu.** It took me days to get all of my drivers working (Wireless was a killer!) and I would rather not go through all of that again. If my only option is re-installation, is there any way to save what I have done (drivers/software) on this installation and put it into a new installation?


Answer bolded question if you can help.

If you have the ubuntu live cd, you can boot from that and resize the partition using gparted.  Or you can use a cd like PartedMagic.

---

### Post by Tatty on 2008-04-23
Do you mean you used wubi to install?  If so then try this:

[https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b)

---

### Post by Champers on 2008-04-23
> **Tatty said:**
> Do you mean you used wubi to install?  If so then try this:

[https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b)

Well, something went wrong with that and I can't boot Ubuntu now. I hear something about a release coming up soon? Maybe I'll just reinstall when that comes out.

---

### Post by reacocard on 2008-04-23
> **Champers said:**
> Well, something went wrong with that and I can't boot Ubuntu now. I hear something about a release coming up soon? Maybe I'll just reinstall when that comes out.

Yep, next version (8.04) should be out sometime in the next day or so. I'd recommend getting that and doing a full installation to disk.

---

