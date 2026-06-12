---
title: "Netgear WNA3100"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by Bofuzzy on 2012-03-25
Hi,
 Have wanted to try Linux out for a long time and decided to give it a go. I have installed Ubuntu 11.10 (dual boot with XP). I have spent countless hours looking through forums and help guides but cannot connect to my USB Netgear WNA3100 wireless internet connection. I do not have an ethernet cable. i am an absolute beginner with Ubuntu and would like to give it a go. Can someone please assist with my netgear problem, i've noticed it seems to be a common issue

---

### Post by winh8r on 2012-03-26
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1549190]("http://ubuntuforums.org/showthread.php?t=1549190")

That should help you.

---

### Post by Bofuzzy on 2012-03-27
Thanks for the reply, but didn't help at all. I followed what was said but I probably did it wrong anyway as i'm new and it looked like double dutch to me. Its a shame, but if its this much trouble hooking up to the internet, and i have spent hours ++ trying, i will give it away.

---

### Post by Mark Phelps on 2012-03-27
> **Bofuzzy said:**
> ... if its this much trouble hooking up to the internet, and i have spent hours ++ trying, i will give it away.

It's not accessing the Internet that's the problem.  

The problem is that very few hardware suppliers provide Linux drivers for their devices.  So, if the Ubuntu installer doesn't automatically load the wireless drivers you need, there could be a fair amount of work involved to do that yourself.

You should also try searching in the Networking forum using wna3100 to see if there are any other threads to see if anyone else has solved this already.

---

### Post by winh8r on 2012-03-28
This link [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100")
from the original thread posted above seems to resolve the issue with regard to driver configuration on the Netgear WNA3100.

There is also information on where to find the required drivers.

 If you have any problems following the step by step guide, just post your questions here.

Hope this helps you.

---

### Post by kurt18947 on 2012-03-28
If you're in the U.S. and are not on TOO tight a budget, you might consider a wifi adapter that's more Linux friendly.  I have no relationship with this Ebay vendor beyond buying this adapter which uses a RTL-8192SU chipset and is plug -n- play with 11.04 and later in my experience.

[http://www.ebay.com/itm/D-Link-DWA-131-Wireless-N-WIFI-Nano-USB-Micro-Mini-Compact-Adapter-/370598494558?pt=LH_DefaultDomain_0&hash=item564964415e](http://www.ebay.com/itm/D-Link-DWA-131-Wireless-N-WIFI-Nano-USB-Micro-Mini-Compact-Adapter-/370598494558?pt=LH_DefaultDomain_0&hash=item564964415e).

The adapter is available from other sources of course but $12.99 and free shipping is pretty sweet.  The Netgear WNA-3100 uses a Broadcom chipset that currently has no Linux support

[http://wikidevi.com/wiki/Netgear_WNA3100](http://wikidevi.com/wiki/Netgear_WNA3100)

and I've not had much luck with NDISwrapper personally.

---

