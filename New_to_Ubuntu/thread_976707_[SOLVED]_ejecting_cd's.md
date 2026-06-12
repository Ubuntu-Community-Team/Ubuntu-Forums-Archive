---
title: "[SOLVED] ejecting cd's"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by gj_clt on 2008-11-09
I think I saw a post about this but can't find it.
I have done a fresh install of 8.10 and everything is O.K except when I click on a CD to eject it the drive opens and then shuts so quickly you can't get the CD out unless you grab the drive and hold it out. Is there a fix for this?

---

### Post by Dr Small on 2008-11-09
What about trying this?
```
eject /dev/cdrom
```

If /dev/cdrom in your device.

---

### Post by kansasnoob on 2008-11-09
> **gj_clt said:**
> I think I saw a post about this but can't find it.
I have done a fresh install of 8.10 and everything is O.K except when I click on a CD to eject it the drive opens and then shuts so quickly you can't get the CD out unless you grab the drive and hold it out. Is there a fix for this?

There is now a fix for that in Intrepid proposed. It's the udev update!

> 
 Martin Pitt wrote on 2008-11-03: (permalink)

It seems that this this actually an udev problem after all:

[http://git.kernel.org/?p=linux/hotplug/udev.git;a=commitdiff;h=f755fd5657b619fd27160ad202fc5d773d096e9c](http://git.kernel.org/?p=linux/hotplug/udev.git;a=commitdiff;h=f755fd5657b619fd27160ad202fc5d773d096e9c)

So it seems that the last ioctl kernel patch referenced above just fixed the return status enough to make the emitted change events actually work, so that udev's rules would kick in.
 Martin Pitt wrote on 2008-11-03: (permalink)

Accepted into intrepid-proposed, please test and give feedback here. Please see [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for documentation how to enable and use -proposed. Thank you in advance!


[https://bugs.launchpad.net/ubuntu/intrepid/+source/udev/+bug/283316](https://bugs.launchpad.net/ubuntu/intrepid/+source/udev/+bug/283316)

---

### Post by gj_clt on 2008-11-09
Thank you for both replies. Eject command works and the fix is also working.

---

### Post by m_l17 on 2008-11-10
Thank You for this thread :D

---

