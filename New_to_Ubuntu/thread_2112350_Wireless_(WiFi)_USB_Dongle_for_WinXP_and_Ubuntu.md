---
title: "Wireless (WiFi) USB Dongle for WinXP and Ubuntu"
date: 2013-02-04
forum: New to Ubuntu
---

### Post by KieranMonday on 2013-02-04
I've managed to find a post from 2009 about compatible wireless internet dongles however the answers on that post are outdated and no longer available in shops. So any help with any USB dongles that work with Windows XP _and_ Ubuntu would be greatly appreciated.
Ive found one that was 'advised' on amazonUK: [http://www.amazon.co.uk/Belkin-F7D1102ED-Micro-Wireless-Adaptor/dp/B0042ORTW2/ref=sr_1_1?s=electronics&ie=UTF8&qid=1359998372&sr=1-1](http://www.amazon.co.uk/Belkin-F7D1102ED-Micro-Wireless-Adaptor/dp/B0042ORTW2/ref=sr_1_1?s=electronics&ie=UTF8&qid=1359998372&sr=1-1)
but would like a conformation or a similarly priced alternative.

---

### Post by sandyd on 2013-02-04
> **KieranMonday said:**
> I've managed to find a post from 2009 about compatible wireless internet dongles however the answers on that post are outdated and no longer available in shops. So any help with any USB dongles that work with Windows XP _and_ Ubuntu would be greatly appreciated.
Ive found one that was 'advised' on amazonUK: [http://www.amazon.co.uk/Belkin-F7D1102ED-Micro-Wireless-Adaptor/dp/B0042ORTW2/ref=sr_1_1?s=electronics&ie=UTF8&qid=1359998372&sr=1-1](http://www.amazon.co.uk/Belkin-F7D1102ED-Micro-Wireless-Adaptor/dp/B0042ORTW2/ref=sr_1_1?s=electronics&ie=UTF8&qid=1359998372&sr=1-1)
but would like a conformation or a similarly priced alternative.

See if any of these check out for you :)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Javelin Dan on 2013-02-04
I routinely download and try as many different distros of Linux as I can get my hands on. I always test compatibility with my SMC wireless USB dongle. I can remember only one instance where (I think!) a derivative of Debian (or was it Slackware…?) didn’t recognize it. I know for a fact that it works with ALL versions of Ubuntu past 10.04 and all versions of Puppy past 5.0. I’ll plead ignorance here and tell you I don’t know for sure about Windows as I only use it at work and of course that is networked off an Ethernet cable.  But all the dongles I’ve seen come with an installation driver CD for Windows, so that would seem to be the less problematic of the two.

---

### Post by zealibib slaughter on 2013-02-04
I had one from netgear i got at biglots for $10 which worked great too bad it got lost.  I think it was a g54 g111 or something like that.

---

### Post by kurt18947 on 2013-02-04
> **KieranMonday said:**
> I've managed to find a post from 2009 about compatible wireless internet dongles however the answers on that post are outdated and no longer available in shops. So any help with any USB dongles that work with Windows XP _and_ Ubuntu would be greatly appreciated.
Ive found one that was 'advised' on amazonUK: [http://www.amazon.co.uk/Belkin-F7D1102ED-Micro-Wireless-Adaptor/dp/B0042ORTW2/ref=sr_1_1?s=electronics&ie=UTF8&qid=1359998372&sr=1-1](http://www.amazon.co.uk/Belkin-F7D1102ED-Micro-Wireless-Adaptor/dp/B0042ORTW2/ref=sr_1_1?s=electronics&ie=UTF8&qid=1359998372&sr=1-1)
but would like a conformation or a similarly priced alternative.

That Belkin unit will probably work but not without replacing the native driver with one from RealTek's site.  I have an Edimax that uses the same chipset.  It works beautifully with RealTek's driver and is great for notebooks.  They only protrude about 8-10 mm.  

  For plug -n- play I've had very good success with either a Dlink DWA-131 or Trendnet TEW-649UB.  They're pretty much twins, using RealTek's 8192SU chipset.  There is *one* Netgear that is plug-n- ply,  the WNA-1100 that uses an Atheros ATH9K chipset.  You have to be careful with Netgear because they have some that are pretty much impossible to get working with Linux.  If you want 'retro' and cheap take a look at Trendnet TEW-424UB v.3  It uses a RealTek 8187B chipset that has been plug-n-play since Ubuntu 9.10 I think.

---

### Post by darrell derrick on 2013-02-04
What is possible using the hardware already inside the Laptop, that was installed by Dell, I have C610,D610,D810, all worked on windows xp, b4 install of Ubuntu, but not after. My C610 worked after but with a Belkin 802.g Pcmia plug in card, but it went with my Gdaughter in the laptop.
all of the above machines run on rj45 fine. I need wireless, for travel.
Any one have a solution. Thanks, Darrell In Magnolia ,Texas, kb5zxm

---

### Post by squakie on 2013-02-04
I have a Tenda w311m that I got at Micro Center for less than $10, and it works fine right out of the box.

---

### Post by DuckHook on 2013-02-04
> **darrell derrick said:**
> What is possible using the hardware already inside the Laptop, that was installed by Dell, I have C610,D610,D810, all worked on windows xp, b4 install of Ubuntu, but not after. My C610 worked after but with a Belkin 802.g Pcmia plug in card, but it went with my Gdaughter in the laptop.
all of the above machines run on rj45 fine. I need wireless, for travel.
Any one have a solution. Thanks, Darrell In Magnolia ,Texas, kb5zxm

The Dell laptops you mention all use different iterations of the Broadcom chipset, which can be made to work with Ubuntu but require some configuration and downloads.

The following help page deals with installing drivers for the BCM43xx chipset.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by sandyd on 2013-02-07
> **darrell derrick said:**
> What is possible using the hardware already inside the Laptop, that was installed by Dell, I have C610,D610,D810, all worked on windows xp, b4 install of Ubuntu, but not after. My C610 worked after but with a Belkin 802.g Pcmia plug in card, but it went with my Gdaughter in the laptop.
all of the above machines run on rj45 fine. I need wireless, for travel.
Any one have a solution. Thanks, Darrell In Magnolia ,Texas, kb5zxm

Just get a Intel Centrino Advanced N Half Mini PCI-E (if your laptop supports it). Works out of the box

---

### Post by DuckHook on 2013-02-07
> **sandyd said:**
> Just get a Intel Centrino Advanced Half Mini PCI-E (if your laptop supports it). Works out of the box
+1 Totally agree. Or a USB stick with known support, that also works out of box. Sometimes the effort needed to wrestle with these balky chipsets is just not worth it, especially for new users, and especially given the fact that sandyd's alternative can be purchased for the price of a Big Mac meal.

---

### Post by kurt18947 on 2013-02-07
> **DuckHook said:**
> +1 Totally agree. Or a USB stick with known support, that also works out of box. Sometimes the effort needed to wrestle with these balky chipsets is just not worth it, especially for new users, and especially given the fact that sandyd's alternative can be purchased for the price of a Big Mac meal.

The PCIe mini cards are optimal IF they're accessible.  Some portables require removing the keyboard and more to access the wireless card.  Non technically inclined users may not care for partially disassembling their baby.

---

