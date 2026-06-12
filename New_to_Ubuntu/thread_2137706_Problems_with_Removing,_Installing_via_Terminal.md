---
title: "Problems with Removing, Installing via Terminal"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by carterlangley on 2013-04-21
Hi all,

Please help!
I am getting the following error when I try to install or remove from the terminal.

dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

How do I overcome this?

Running Ubuntu 12.10

---

### Post by Slim Odds on 2013-04-21
run 'sudo dpkg --configure -a', just like it says.

---

### Post by carterlangley on 2013-04-21
Thanks Slim Odds.

I now get the following

Setting up ntp (1:4.2.6.p3+dfsg-1ubuntu5) ...
 * Starting NTP server ntpd                                                                                                                                               
*** glibc detected *** lockfile-create: malloc(): memory corruption (fast): 0x00000000025c50e0 ***

And it seems to just hang there and do nothing.

---

### Post by Slim Odds on 2013-04-21
> **carterlangley said:**
> Thanks Slim Odds.

I now get the following

Setting up ntp (1:4.2.6.p3+dfsg-1ubuntu5) ...
 * Starting NTP server ntpd                                                                                                                                               
*** glibc detected *** lockfile-create: malloc(): memory corruption (fast): 0x00000000025c50e0 ***

And it seems to just hang there and do nothing.
Well... "memory corruption" does not look good. Have you rebooted lately? I'd try that first.

---

### Post by carterlangley on 2013-04-22
Yep, both hard and soft restarts tried. 
I have everything backed-up to a 1 terrabyte external hard drive anyway, so will just do a re-install tonight. Thanks for being there anyway! Always good to know that there are people around when you are trying to find your feet.

---

