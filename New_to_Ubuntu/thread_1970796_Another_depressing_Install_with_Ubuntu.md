---
title: "Another depressing Install with Ubuntu"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by dvdivx on 2012-05-01
Driver for Broadcom 4312 not loading no internet access until installed. Even the right deb files don't install. XP partition also not listed in grub.Need help getting the wireless to work but also wondering why drivers are not loaded. Even Windows can do that. Even old versions of Red Hat didn't have this problem

---

### Post by souravc83 on 2012-05-01
Which version, 12.04?
I haven't tried that. You might be better off installing 11.10 until the dust settles down a bit on the new release, and things get smoothed out.
I have never faced problems with wireless drivers in 11.10, with three different wireless cards I have tried.

---

### Post by Paqman on 2012-05-01
To get your wifi drivers you'll need to plug directly into your router and run Additional Drivers.

To try and get Windows back into grub open a terminal (Ctrl-T) and run this command:
```
sudo update-grub
```
If that doesn't work you'll need to check that your Windows partition is still present.

---

### Post by Rex Bouwense on 2012-05-01
> **dvdivx said:**
> Driver for Broadcom 4312 not loading no internet access until installed. Even the right deb files don't install. XP partition also not listed in grub.Need help getting the wireless to work but also wondering why drivers are not loaded. Even Windows can do that. Even old versions of Red Hat didn't have this problem

Linux is not Windows.  See here for a solution to your Wireless problems.
[http://ubuntuforums.org/showthread.php?t=1869293](http://ubuntuforums.org/showthread.php?t=1869293)
It solved mine.

---

