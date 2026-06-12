---
title: "Configuring Ralink RT73 for Ubuntu 13.04"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by SaintBen on 2013-05-13
I've just installed Ubuntu 13.04 on a pretty obscure netbook (Kogan Agora). Ubuntu recognises the wifi card, but won't authenticate properly with my router.

I've searched extensively, but can't find a solution for kernal 3.8.

The latest driver I can find (2011_0210_RT73_Linux_STA_Drv1.1.0.5.bz2) is for kernal version 2.4 and 2.6. Attempting to install it leads to this error:

linux/smp_lock.h: No such file or directory

Any help would be much appreciated.

---

### Post by SaintBen on 2013-05-13
Just so no one wastes time responding to me right now, I'm going to give Debian a try since this page seems to deal with my issue: [http://wiki.debian.org/WiFi/rt73](http://wiki.debian.org/WiFi/rt73)

If I fail with Debian and decide to try Ubuntu again and still need help, I'll update this post.

---

### Post by kurt18947 on 2013-05-14
Yes it seems that 3.8 causes some wireless driver issues.  If Mediatec won't address them, any chance of replacing the device? Or using a micro/nano USB adapter known to work?

---

### Post by SaintBen on 2013-05-14
> **kurt18947 said:**
> Yes it seems that 3.8 causes some wireless driver issues.  If Mediatec won't address them, any chance of replacing the device? Or using a micro/nano USB adapter known to work?

I have a USB adapter that works, but I want to use the internal card and it isn't worth upgrading that.

Debian was a dead end, so I'm thinking of installing an older version of Ubuntu or kernal. I don't know enough about Linux to know which of those is the best option or even if they both are options, but I'll look into them next.

---

### Post by kurt18947 on 2013-05-15
> **SaintBen said:**
> I have a USB adapter that works, but I want to use the internal card and it isn't worth upgrading that.

Debian was a dead end, so I'm thinking of installing an older version of Ubuntu or kernal. I don't know enough about Linux to know which of those is the best option or even if they both are options, but I'll look into them next.

Maybe go with 12.04 (assuming that works) and use PPAs if you want newer versions of some apps?  I think 12.04.2 uses the same kernel as 12.10 and I'm sure you could find 12.04 original if you need it.

---

### Post by SaintBen on 2013-05-15
> **kurt18947 said:**
> Maybe go with 12.04 (assuming that works) and use PPAs if you want newer versions of some apps?  I think 12.04.2 uses the same kernel as 12.10 and I'm sure you could find 12.04 original if you need it.
Appreciate the advice, kurt. I tried 10.04 (I think -- whichever was the last version to use kernel 2.6) and still couldn't get wifi working. At that point I thought I might as well go all in and have been configuring Arch Linux since. It's been satisfying to build it up the way I want it and not have the bloat. Wifi even works sometimes, too. Usually it connects after a couple of tries and stays connected. Haven't figured out what's going on there yet, but I'm getting closer.

---

