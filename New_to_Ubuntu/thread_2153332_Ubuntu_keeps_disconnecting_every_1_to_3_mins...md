---
title: "Ubuntu keeps disconnecting every 1 to 3 mins.."
date: 2013-06-10
forum: New to Ubuntu
---

### Post by conorr on 2013-06-10
description: Network controller
product: BCM4313 802.11b/g/n Wireless LAN Controller
vendor: Broadcom Corporation

Version: 12.04 LTS
My defualt system is Windows 7 if this helps at all.
Im new to linux and stuff, so it would be great if anyone could help has anyone had this problem or knows how to fix this?

---

### Post by d4m1r on 2013-06-10
Do you mean your **internet** keeps disconnecting every 1-2 minutes?

If that is the case, are you running the 32 or 64 bit version of 12.04? Also, is your wireless working 100% when you boot into Windows 7?

---

### Post by conorr on 2013-06-11
> **d4m1r said:**
> Do you mean your **internet** keeps disconnecting every 1-2 minutes?

If that is the case, are you running the 32 or 64 bit version of 12.04? Also, is your wireless working 100% when you boot into Windows 7?

Yeah, I mean internet
64 Bit and its working when I go onto Windows 7.

---

### Post by coffeecat on 2013-06-11
> **conorr said:**
> 
product: BCM4313 802.11b/g/n Wireless LAN Controller

At the moment you are using the default open source driver for this wireless device. Experience seems to vary. I experience no problems with the open source driver and the BCM4313 chipset, but other people do see what you are seeing and need to install the proprietary driver.

You need to download and install a package and since your wireless is unreliable at the moment, can you connect to your router with an ethernet cable temporarily? This, at least, will make the download reliable. Open the Software Centre, search for the package bcmwl-kernel-source and install it. Then reboot. Let us know if that works for you.

---

