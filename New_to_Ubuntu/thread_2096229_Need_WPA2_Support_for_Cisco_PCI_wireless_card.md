---
title: "Need WPA2 Support for Cisco PCI wireless card"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by OSIsOpenSource on 2012-12-19
Hi, I want to install Ubuntu, I have installed it before, and there is no WPA2 support. It can detect my wifi network, but it won't let me click it. If I try to add it manually, it will freeze up at the enter encryption key dialog, and I won't be able to type it in, because there is nowhere to type it in! (Ubuntu didn't freeze, it was just the dialog.) I have a IBM ThinkPad T30 with a Cisco Systems PCI Wireless LAN Adapter for Wifi, and a Intel(R) PRO/100 VE Network Connection for Ethernet. Wired connections work perfectly, I just don't have a long enough ethernet cable. So Can you please help a noob here? Your Gratitude is appreciated. :KS

-Os Is Open Source

---

### Post by Pjotr123 on 2012-12-19
Try this:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by steeldriver on 2012-12-19
Is that the Aironet 350 card? I had one in my old X30 - iirc it supports WPA but I never found any way to get it to support WPA2

---

### Post by haqking on 2012-12-19
> **OSIsOpenSource said:**
> Hi, I want to install Ubuntu, I have installed it before, and there is no WPA2 support. It can detect my wifi network, but it won't let me click it. If I try to add it manually, it will freeze up at the enter encryption key dialog, and I won't be able to type it in, because there is nowhere to type it in! (Ubuntu didn't freeze, it was just the dialog.) I have a IBM ThinkPad T30 with a Cisco Systems PCI Wireless LAN Adapter for Wifi, and a Intel(R) PRO/100 VE Network Connection for Ethernet. Wired connections work perfectly, I just don't have a long enough ethernet cable. So Can you please help a noob here? Your Gratitude is appreciated. :KS

-Os Is Open Source

> **steeldriver said:**
> Is that the Aironet 350 card? I had one in my old X30 - iirc it supports WPA but I never found any way to get it to support WPA2

The CISCO Aironet 350 series do not support WPA2

> Cisco Aironet 350 series products do not support WPA 2 because their 		radios lack AES support. 

From [http://www.cisco.com/en/US/tech/tk722/tk809/technologies_configuration_example09186a008054339e.shtml](http://www.cisco.com/en/US/tech/tk722/tk809/technologies_configuration_example09186a008054339e.shtml)

---

### Post by holycow131415 on 2012-12-19
Why not just reconfigure your router's encryption to WPA, or even WEP? Not all cards support all encryptions.

---

### Post by OSIsOpenSource on 2012-12-27
> **steeldriver said:**
> Is that the Aironet 350 card? I had one in my old X30 - iirc it supports WPA but I never found any way to get it to support WPA2
must be. I'm running windows and it works fine with WPA, but not WPA2.

---

### Post by haqking on 2012-12-27
> **OSIsOpenSource said:**
> It's not. I'm running windows and it works fine with WPA2.

Do you want to go out on a limb and tell us what card it is then ;-)

The forum crystal ball is experiencing heavy traffic over the holiday season.

Peace

---

