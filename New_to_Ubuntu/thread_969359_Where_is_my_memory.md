---
title: "Where is my memory?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by franco81 on 2008-11-03
Few issues with Ubuntu performance lately, I had a previous thread with booting issues - some of which persist. But also having problems with memory management. I'm a beginner Linux user, but here are some of the areas I think I'm having problems in:

on booting up a lot of time seems to be used on:
dhcpdiscover
ntpd
and/or sendmail

I'm connecting to different wireless networks, one in the office and one at home. I tried removing ntpd, but still takes ages with dhcpdiscover. The network is configured to the correct address sometimes, so don't know why it is taking so long.

Sendmail was giving me greif on bootup as well, even once I removed it it was still trying to load some config files, though I think this is sorted now.

Eclipse is getting what seem like the same aptana updates frequently. Has been crashing often today with out of memory errors - which brings me to memeory. Not sure where it is getting used but about 1 gig of memory is taken - when I view the running processes it doesn't seem to add up.

Any help, general tips/advice appreciated.

---

### Post by adieb on 2008-11-03
about dhcp sendmail and stuff like that:

try changing /etc/init.d/rc:

CONCURRANCY=none to CONCURRANCY=shell

This allows the services to load parallel.


2. what does "free -m" say. (in a console)
If you have lets say 4GB you must use the 64Bit version of Ubuntu to get more than 3.1GB...

---

### Post by franco81 on 2008-11-03
Thanks - I have tried the concurrancy trick. Looking forward to faster loads on that front. 

Here is free -m on my system. Running Ubuntu 8.04 - unsure but I think using 32bit?

             total       used       free     shared    buffers     cached
Mem:          2025       1887        138          0        191        525
-/+ buffers/cache:       1170        855
Swap:          254          0        254

cheers for the help.

---

### Post by waffen on 2008-12-10
Did you setup you swap memory to double of your total RAM?

---

