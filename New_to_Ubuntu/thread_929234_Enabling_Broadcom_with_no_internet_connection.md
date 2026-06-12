---
title: "Enabling Broadcom with no internet connection?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by vidus on 2008-09-24
Hello,
I currently dual boot xp and 8.04. My xp is messed, and I plan to wipe the drive and install 8.04 only. My question is, once installed, how can I enable my broadcom without an internet connection, my apartment offers wifi, but no wired connection.

I forget if it worked right out of the box on 8.04 when I originally installed, I don't remember what I did. I recall something called ndiswrapper, perhaps I used that. Is this something I could throw on a usb drive, install and be on my way without having to plug in?

---

### Post by Crafty Kisses on 2008-09-24
Is there anyway you can post the results of this command:
```
lspci | grep Broadcom\ Corporation
```

---

### Post by RequinB4 on 2008-09-24
> **vidus said:**
> Hello,
I currently dual boot xp and 8.04. My xp is messed, and I plan to wipe the drive and install 8.04 only. My question is, once installed, how can I enable my broadcom without an internet connection, my apartment offers wifi, but no wired connection.

I forget if it worked right out of the box on 8.04 when I originally installed, I don't remember what I did. I recall something called ndiswrapper, perhaps I used that. Is this something I could throw on a usb drive, install and be on my way without having to plug in?

Yes.  For any package it wants you to sudo apt-get install, you can get from packages.ubuntu.com and transfer via flash drive or CD or something:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by vidus on 2008-09-24
> **Codename said:**
> Is there anyway you can post the results of this command:
```
lspci | grep Broadcom\ Corporation
```

Broadcom Corporation BCM4318

---

