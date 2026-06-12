---
title: "HOWTO: Wireless and a Hoary Upgrade"
date: 2005-02-09
forum: Outdated Tutorials &amp; Tips
---

### Post by mike998 on 2005-02-09
Okay, after a lot of messing around, I finally got my wireless up and running.  I searched the forums trying to figure a way out but didn't find anything.

If anyone is interested, I managed to get my "Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)" up and running by 

Installing the bcmwl5.inf driver (the .SYS driver is also required) after downloading the correct driver .exe from the dell website and using the ndiswrapper -i command.
Origianlly this didn't work too well, and the ndiswrapper -l didn't really help much.  I did an upgrade to Hoary (I was curious) and got a large amount of garbage on the system's boot up at the "Starting Network" stage.  This was due to an incorrect driver being installed (the bcmwl5a driver).  Once I had uninstalled the driver using the diswrapper-e bcmwl5a command, and installed the correct driver all was good.

A little googling suggests that there is something to do with the Kernel version used in Hoary, but I don't really know.  So, if you are having problems with your wireless drivers not seeming to work you may want to try an upgrade to Hoary.

Sorry if this doesn't make much sense, it's late and I am tired.

---

### Post by Rancoras on 2005-02-09
Don't forget the "howto" tag.

Caveat for this post:  If you're not comfortable with possible system breakage, don't upgrade to Hoary just yet.  It doesn't have too much longer until release.

---

### Post by mike998 on 2005-02-10
Actually, this is the THIRD upgrade to Hoary that I tried.  The first two had problems which I probably could have fixed, but didn't feel up to.

I'm looking forward to the actual release of Hoary!

---

