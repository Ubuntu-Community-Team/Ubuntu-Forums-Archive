---
title: "Wacom Create and Lucid?"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by tasey on 2011-11-21
Okay, so, I've tried the tutorial [here]("http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/") and also [here]("http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html") to no avail. I don't know if there is something I am doing incorrectly, or if the tablet model I have just isn't supported yet. I have the "Wacom Bamboo Create" and Ubuntu 10.04.3 with kernel version 2.6.32-35-generic. If there is anything I may have overlooked, or any advice or suggestions anyone can offer, it would be very greatly appreciated. If you need more info, let me know. Thank you

---

### Post by Favux on 2011-11-21
Hi tasey,

Welcome to Ubuntu forums!

With the Create your product ID should be DF.  You'd see that in the output of:
```
lsusb
```
in the Wacom line.

Although your model is brand new (October 2011) Chris Bagwell has already supplied support for it and submitted it the kernel.  Should be available with the 3.3 kernel.

Unfortunately because the mt.h header is needed you won't be able to get it working in Lucid.  In other words you can't compile a wacom.ko that works for the tablet.  The first time mt.h is available that I'm aware of is with the 2.6.38 kernel (Natty).  So you would need to change releases.  If you decide to instructions are available on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Chris has repeated several times that it wouldn't be worth the effort to backport support into input-wacom's wacom.ko for older kernels because it would be a lot of work for not very functional touch.

---

