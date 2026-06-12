---
title: "Ubuntu rejects Wireless Security"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-11-17
I seem to be unable to connect to any Wireless network with enabled security other than my own, which I configured by Wired Network first.

I've been living with it since I switched and have been unable to fix it. The problem as it goes is:

I select a network with enabled security, the Passphrase Window appears, and then I input the passphrase. It attempts to connect, then a few minutes later, the window appears again and asks for the passphrase again. If I give it again, the same thing happens.

Why is this happening, and how can I fix it?

---

### Post by shifty_powers on 2008-11-17
first thing first.

what version of ubuntu are you using?

---

### Post by aysiu on 2008-11-17
What wireless card are you using? What router are you using? What kind of wireless encryption are you using? And which version of Ubuntu are you using?

---

### Post by Haruki-kun on 2008-11-17
> **aysiu said:**
> What wireless card are you using? What router are you using? What kind of wireless encryption are you using? And which version of Ubuntu are you using?

Ubuntu Version 8.04

[Router: 2Wire 2700HG]("http://images.channeladvisor.com/Sell/SSProfiles/23000009/Images/2/2wire_4.jpg")

Wireless Card: I'm not sure, but I believe it says "Atheros 802.11 Wireless LAN Cards" under Hardware Drivers.

Wireless Encryption: I have no idea. How can I find out?

---

### Post by aysiu on 2008-11-17
I have an Atheros wireless card, and I've never been able to get it to work using the drivers in Hardware Drivers. Some people recommend disabling that and rebooting. That has also never worked for me, but you can try it. If that doesn't work for you either, I would install *ndisgtk* and then find the Windows drivers for it and use *gksudo ndisgtk* to install them.

That may fix the issue. The other thing could be that you're attempting the wrong encryption, especially if you don't know what it is. It should be WEP, WPA, or WPA2.

---

### Post by Haruki-kun on 2008-11-17
> **aysiu said:**
> I have an Atheros wireless card, and I've never been able to get it to work using the drivers in Hardware Drivers. Some people recommend disabling that and rebooting. That has also never worked for me, but you can try it. If that doesn't work for you either, I would install *ndisgtk* and then find the Windows drivers for it and use *gksudo ndisgtk* to install them.

That may fix the issue. The other thing could be that you're attempting the wrong encryption, especially if you don't know what it is. It should be WEP, WPA, or WPA2.

Alright, I tried that. Question, though: How do I find the Windows drivers?

---

### Post by aysiu on 2008-11-17
You can probably get them off the Atheros website:
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

Mine came on the DVD that came with my Eee PC.

---

### Post by mapes12 on 2008-11-17
If the previous suggestions don't work you may want to try wcid. Others have reported success with changing from Network Manager to wcid. Here's some starting points:

[http://ubuntuforums.org/showthread.php?t=893347](http://ubuntuforums.org/showthread.php?t=893347)

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

BTW - you find Windoze drivers by looking up the manufactures web site of your device or a Google search. Also, look up ndiswrapper to use windoze wifi drivers under Linux. But, in my experience this can be a hit and miss fix.

Adaptors with native Linux support are my favourites:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by Haruki-kun on 2008-11-17
> **mapes12 said:**
> If the previous suggestions don't work you may want to try wcid.

I decided to give this a try. It works with Wired, apparently, but when I attempt to connect to the Wireless (with security), I get an error Message. It reads:

> This network requires encryption to be enabled.

What does it mean?

---

### Post by bodhi.zazen on 2008-11-17
> **Haruki-kun said:**
> What does it mean?

It means the network is using encryption (WEP or WPA). In wicd select the protocol (WPA 1 and 2 are combined) and enter your password.

---

### Post by Haruki-kun on 2008-11-17
> **bodhi.zazen said:**
> It means the network is using encryption (WEP or WPA). In wicd select the protocol (WPA 1 and 2 are combined) and enter your password.

I just tried all of them, and I still can't connect to the network. Now it starts trying to connect, but doesn't connect at all.

---

### Post by bodhi.zazen on 2008-11-17
> **Haruki-kun said:**
> I just tried all of them, and I still can't connect to the network. Now it starts trying to connect, but doesn't connect at all.

Why did you do that ? Is this your router you are trying to connect to ? If so, what are your wireless settings ? Is your router using an (MAC) access list ?

When trying to trouble shoot wireless, I advise you shut off security / encryption, make sure your wireless card is working, then re-enable security one at at time.

If you can not connect at all, then we have a problem with your wireless driver and the next step is to try ndiswrapper and the correct driver for your card.

If you can connect with security disabled, then it is an issue with your security protocol.

So, IMO, next step, try connecting to an unsecured, public WAP.

---

### Post by Haruki-kun on 2008-11-18
> **bodhi.zazen said:**
> Why did you do that ? Is this your router you are trying to connect to ? If so, what are your wireless settings ? Is your router using an (MAC) access list ?

When trying to trouble shoot wireless, I advise you shut off security / encryption, make sure your wireless card is working, then re-enable security one at at time.

If you can not connect at all, then we have a problem with your wireless driver and the next step is to try ndiswrapper and the correct driver for your card.

If you can connect with security disabled, then it is an issue with your security protocol.

So, IMO, next step, try connecting to an unsecured, public WAP.

Already did. There is no problem connecting to unsecure wireless.

The one I have in my apartment (since I live away from home in college) causes no problems when connecting either. But when I go visit home, I'm unable to connect to my parents' wireless. It also causes problems here and there, at friends' homes and stuff, but I was mostly focusing on my parents' Wi-Fi.

I'm back at my apartment now, but I'd like to figure out how to fix this for the future...

---

### Post by bodhi.zazen on 2008-11-18
> **Haruki-kun said:**
> Already did. There is no problem connecting to unsecure wireless.

So the problem is not with your wireless drivers / hardware, but rather with the encryption / authentication protocols.

> The one I have in my apartment (since I live away from home in college) causes no problems when connecting either. But when I go visit home, I'm unable to connect to my parents' wireless. It also causes problems here and there, at friends' homes and stuff, but I was mostly focusing on my parents' Wi-Fi.

I'm back at my apartment now, but I'd like to figure out how to fix this for the future...

Well, to answer the question we need to know how your parents WAP (or any other) is set up. What encryption protocol (WEP, WPA, other), is access restricted by MAC, etc.

I had a LOT of issues with 8.04 and network manager, it almost never worked. I switched to wicd and (not that it helps you) that solved my issues.

Network manager on 8.10 is working @ home , I have yet to test it traveling.

My only other observation has been that sometimes my wireless connection seems to hang for some reason. When this happens a re-boot seems to fix it. I have not been able to resolve this issue, and it occurs infrequently ...

---

