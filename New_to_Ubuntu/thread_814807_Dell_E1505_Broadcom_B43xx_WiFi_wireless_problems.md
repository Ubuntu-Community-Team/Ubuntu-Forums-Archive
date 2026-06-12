---
title: "Dell E1505 Broadcom B43xx WiFi wireless problems"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by thinking2loud on 2008-06-01
Had the worst problem getting WiFi to work on this laptop.

* After you load Ubuntu from a CD, don't just follow the speech bubbles and check boxes that they give you.  They don't work.

First, there's two ways to get wifi to work:  native drivers, or ndiswrapper and a Windows driver.  I screwed around until (probably by luck) I got ndiswrapper and the Windows driver to work.  In my house I have an unsecured network and a WPA network.  I want to connect to the WPA network; the unsecured network is for games and junk.  The ndiswrapper setup would connect to the unsecured network 100% of the time.  I would connect to the secured network about 20% of the time.  It would eventually connect, but I would have to select it over and over again until it finally worked.

I just got a native driver to work.  For other chips, I assume that it is part of the distribution.  With the Broadcom B43xx chips, there is some software that is Broadcom proprietary so the usual Linux distributors can't legally give it away.  So they invented this contraption called b43-fwcutter which takes a Windows driver and snips out the appropriate part and puts it into a Linux driver.

First, you need to be able to use gcc for real.  To do this you need build-essential (select it with Synaptic Package Manager).  Then, you need to follow these directions:

[http://www.linuxwireless.org/en/users/Drivers/b43#fw-b43-old](http://www.linuxwireless.org/en/users/Drivers/b43#fw-b43-old)

I just connected to the WPA network no-touch-first-time in 9 of 10 trials.

---

### Post by Pioneer5000 on 2008-06-01
Try the following link, look for my last post at bottom of page and try those instructions.

[http://ubuntuforums.org/showthread.php?t=807979](http://ubuntuforums.org/showthread.php?t=807979)

---

