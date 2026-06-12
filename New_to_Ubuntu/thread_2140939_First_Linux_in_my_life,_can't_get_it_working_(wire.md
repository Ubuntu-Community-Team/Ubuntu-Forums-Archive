---
title: "First Linux in my life, can't get it working (wireless driver + build essentials)"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by ElectricBlake on 2013-05-01
Hi, everyone! I bought a laptop with Ubuntu (DELL 5520). I never worked with Linux before, so assume zero knowledge. My friend insisted that we have identical Ubuntu versions - 12.04LTS and told me to upgrade from 11.10 that I had. 
Important: when I had 11.10 everything worked almost correctly, even after the updates.
I must say here that I don't have any access to wired or adsl network, only wireless (or 3G, but that doesn't work either). 
So, after I managed to upgrade 11.10 to 12.04 it forgot how to use wireless. I tried to activate Broadcom wireless proprietary driver, but it requires internet which I can't have if I can't use wireless module!!!
Surely I googled and found out that I'm not alone with this problem. Here's what I've found: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
I downloaded the driver, but to install it I need a whole bunch of other files.... I can't do this part of the instruction:

On Ubuntu, you will need headers and tools.  Try these commands:# apt-get install build-essential linux-headers-generic# apt-get build-dep linux
Because to get it... I need Internet... which I can't have because I can't use wireless. Kinda recursive Linux logic :(((((. And I don't have a place where I can go and connect to wired network. :(((( 
Is there a solution to this problem??? Please help!

---

### Post by TheFu on 2013-05-01
You are in a pickle.  I would be surprised if the full DVD/ISO install of 12.04 doesn't include all the needed files - just perform the install without the network connection at all.  If you do need non-repository files, have those ready on other media.  The manifest inside a .DEB package lists 1st order dependencies, but not other lower dependencies.

Another option is to get a **wifi-bridge** device so you can connect the PC with a wired connection - not needing any wifi drivers. Your PC connects to it with a wired connection, then the device connects over wireless to the internet. I assume you pay for a wifi-only internet provider?  Then you can install the wifi drivers when connected to the internet.

Otherwise, you can get a $15 wifi/wired router and plug into the router with an ethernet cable directly.  Actually, that would be preferred.  WiFi will always - always - always be less easy than wired ethernet.

Anyway, a few options.  Being wifi only is dangerous still and can be difficult unless you get the best supported, F/LOSS-ready wifi chips. Using proprietary wifi chips from companies who are less-than-nice towards Linux and troubles will likely follow. Sorry.

---

### Post by wildmanne39 on 2013-05-01
Please post the output of:
```
lspci -nnk | grep -iA2 net
```
Thanks

---

### Post by Mopar1973Man on 2013-05-01
Another answer is to go to a public library, friends house or such where wired Internet is available and then get the required packages installed. Check and make sure you WiFi is working before you leave.

---

### Post by kurt18947 on 2013-05-01
> **TheFu said:**
> You are in a pickle.  I would be surprised if the full DVD/ISO install of 12.04 doesn't include all the needed files - just perform the install without the network connection at all.  If you do need non-repository files, have those ready on other media.  The manifest inside a .DEB package lists 1st order dependencies, but not other lower dependencies.

Another option is to get a **wifi-bridge** device so you can connect the PC with a wired connection - not needing any wifi drivers. Your PC connects to it with a wired connection, then the device connects over wireless to the internet. I assume you pay for a wifi-only internet provider?  Then you can install the wifi drivers when connected to the internet.

Otherwise, you can get a $15 wifi/wired router and plug into the router with an ethernet cable directly.  Actually, that would be preferred.  WiFi will always - always - always be less easy than wired ethernet.

Anyway, a few options.  Being wifi only is dangerous still and can be difficult unless you get the best supported, F/LOSS-ready wifi chips. Using proprietary wifi chips from companies who are less-than-nice towards Linux and troubles will likely follow. Sorry.

If you have an unused router, you could check if one of the 3rd party firmwares (DD-WRT, Tomato etc.) can install.  At least DD-WRT can temporarily convert a wireless router into a wifi-bridge referenced above.  Another option would be to get an inexpensive WiFi adapter that 'works out of the box'.  Use that to help get the integral wifi working.

---

