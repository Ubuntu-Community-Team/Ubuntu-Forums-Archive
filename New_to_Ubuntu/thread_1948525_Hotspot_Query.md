---
title: "Hotspot Query"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by Greycloud on 2012-03-28
Hi,

I heard that WiFi Hotspot feature can be enabled in Ubuntu 11.10 x64 only if internet is passed through wired broadband connection, is it true? Is this also possible via 3G USB Dongle, if yes then please explain the process.

Thanks!

---

### Post by androssofer on 2012-03-28
> **Greycloud said:**
> Hi,

I heard that WiFi Hotspot feature can be enabled in Ubuntu 11.10 x64 only if internet is passed through wired broadband connection, is it true? Is this also possible via 3G USB Dongle, if yes then please explain the process.

Thanks!

you mean turn your computer into a router?

this might help.. but is quite complex:

[http://hariniachala.blogspot.co.uk/2010/04/turn-your-laptop-into-wireless-router.html](http://hariniachala.blogspot.co.uk/2010/04/turn-your-laptop-into-wireless-router.html)

---

### Post by grahammechanical on 2012-03-28
Think about what you are wanting to do.

You want to use the wireless card in the computer to access the router/modem using a wireless connection and then you want the same wireless card to use wireless communication to other wireless cards in other computers.

Do the makers of wireless cards say that this is possible?

My motherboard came with a wireless adapter built in. The user guide for this wireless adapter shows a diagram for Access Point mode, which is what you are talking about. That diagram shows the computer being used as the wireless access point for other computers but it itself is connected to the ADSL or cable modem by ethernet cable.

This would still be the case if I was using the Windows operating system and the Windows drivers that came with the motherboard. The Motherboard user guide makes no mention of Linux at all.

It is possible in Linux to set a wireless adapter to Access Point mode. But it is not easy. Things are better in 12.04 because there is a slider for putting the wireless adapter into Access Point mode or Use as a Hotspot, as it is called.

But I think that there will still be this limitation of needing a wired connection to the router to get internet access.

Regards.

---

### Post by ben aveling on 2012-03-30
I don't believe the original poster is trying to create two networks on one network card, rather they want to use a USB dongle.

I'm possibly in a similar situation. 

I'm connected to the web via a USB dongle. 

I've gone through the steps to create a hotspot, seemingly successfully. I can see both networks using 'connection information', and both look OK.  

I've tried varies settings for the hotspot network, but I whatever I do, I can't see my hotspot network from my other device (an android).  

It can see other wireless networks and I've used it to connect to a different wireless network in the past, so I don't think the problem is in the android.

Any suggestions for what to try next would be appreciated.  

Update: tried using a borrowed netbook. Unlike the Android, it can see the hotspot network, but can't connect to it. Progress?  :-7

---

### Post by Greycloud on 2012-04-05
> **ben aveling said:**
> I don't believe the original poster is trying to create two networks on one network card, rather they want to use a USB dongle.

I'm possibly in a similar situation. 

I'm connected to the web via a USB dongle. 

I've gone through the steps to create a hotspot, seemingly successfully. I can see both networks using 'connection information', and both look OK.  

I've tried varies settings for the hotspot network, but I whatever I do, I can't see my hotspot network from my other device (an android).  

It can see other wireless networks and I've used it to connect to a different wireless network in the past, so I don't think the problem is in the android.

Any suggestions for what to try next would be appreciated.  

Update: tried using a borrowed netbook. Unlike the Android, it can see the hotspot network, but can't connect to it. Progress?  :-7

Yeah I want to create a Wi-Fi Hotspot using a 3g USB Dongle inorder to use internet for upgrading firmware (available only OTA) of my android phone...Plz Help!!!

---

### Post by 3rdalbum on 2012-04-05
> **Greycloud said:**
> Yeah I want to create a Wi-Fi Hotspot using a 3g USB Dongle inorder to use internet for upgrading firmware (available only OTA) of my android phone...Plz Help!!!

Easy done. Use the "Create Wireless Network" function in Network Manager. When you have followed the prompts, connect to the 3G and then "connect" to the new wireless network you created. The internet connection will automatically be shared as an "ad-hoc" network.

Not sure if Android can connect Ad Hoc networks though.

---

### Post by ben aveling on 2012-05-27
> **3rdalbum said:**
> Not sure if Android can connect Ad Hoc networks .

Sounds like some can, some can't, at least out of the box.

There is perhaps a solution here: [http://www.androidsim.net/2011/08/how-to-35-connecting-to-adhoc-networks.html](http://www.androidsim.net/2011/08/how-to-35-connecting-to-adhoc-networks.html)

I have not tried it, so this is not a recommendation, just an FYI.  If anyone does try it, I would be curious to hear what happens.

Cheers, Ben

---

