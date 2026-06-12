---
title: "Using a pendrive instead of burning a CD?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by matthewblair on 2008-11-04
Is there anyway to boot the Kubuntu installer off a pendrive? The CD burner in my laptop never seems to work correctly and the computer can boot from usb flash drives, but when i tried extracting the files from the Kubuntu ISO on the drive it didn't boot.

I'm using Ubuntu 8.1 atm but I wanted to try out KDE if that helps?

---

### Post by LowSky on 2008-11-04
google: pendrive linux

---

### Post by willmacleod on 2008-11-04
just download and run syslinux on your pen drive, copy the iso files over to it, move the files in isolinux from that folder to the root and rename isolinux.cfg to syslinux.cfg. Done!

---

### Post by matthewblair on 2008-11-04
Hmm I'm not actually trying to run linux off the pendrive, I want to install it from a pendrive rather than a CD. Is that possible?

---

### Post by philinux on 2008-11-04
Does this help.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by mihaiv on 2008-11-04
Yes you can. In ubuntu 8.10 go to System->Administration->Create a USB startup disk. You can even do this from the live CD.

---

