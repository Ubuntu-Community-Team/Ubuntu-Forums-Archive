---
title: "Internet Connection Protection While Traveling"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by meep7 on 2012-10-08
I don't have a wireless card, so when I use my ubuntu, I use the hard wired connection to my dsl.  I'm going to be staying in a hotel on an upcoming trip and I was wondering if there was an ubuntu application like this: [https://www.publicvpn.com/index.php](https://www.publicvpn.com/index.php), that I can use to protect myself while browsing online while I'm staying there.  

I will not have a wireless connection.  Most things I've seen online are protection for wireless only.   I will definitely have a wired connection, so wireless instructions won't help me.  I can't afford to buy a wireless card right now with my other travel expenses.

---

### Post by audiomick on 2012-10-08
Did you see this, right at the bottom of the site that you linked to?

> Unofficially supported Operating Systems

Microsoft Windows 95, Microsoft Windows 98, Microsoft Windows ME, Microsoft Windows NT 4.0, Microsoft Windows 2000
Apple Mac OS 9 and below.
Any computer that can connect to a PPTP or L2TP/IPsec&#8211;based VPN, [COLOR="Red"]such as ones running Linux[/COLOR], FreeBSD, PalmOS, etc. 

I am sorry I can't help you set it up, but I am sure it can be made to work.

---

### Post by DuckHook on 2012-10-08
There's no such thing as absolutely secure, so it's a matter of how much risk is tolerable. I use the wired connection in hotels without further safeguards, but then, I am aware of the increased risk and don't do things like banking over the connection. If it's just a matter of looking up the nearest restaurant, then I figure the guy in the next room with a packet sniffer and too much time on his hands can see all he wants. Such voyeurism is much harder to do on a wired connection anyway, so you are an order of magnitude safer than if you were accessing through WIFI.

The Linux world actually has very robust tools for the truly paranoid. Ubuntu already has openVPN preinstalled. All you need is a router at home that is VPN capable and you can establish a secure tunnel to your home network for safe connection no matter where you are in the world. This does away with the cost of paying someone like *publicvpn* It will likely be a slower connection than you are used to, but it is balm for the truly paranoid. The details for setting up openVPN is beyond the scope of a beginners' forum.

Conclusion: hotel wired connections are reasonably safe. If you aren't exchanging sensitive personal info, I would not worry too much about it.

---

### Post by meep7 on 2012-10-08
No i didn't see that, thank you.  I looked all over the site (or what I thought was all over the site) and didn't see it.  I have no idea how to make it work either.  It sucks.  I paid for it without realizing that i have to be careful with stuff i buy since i'm now not on windows.  hopefully i can figure it out.  thanks again.

---

### Post by meep7 on 2012-10-08
> **DuckHook said:**
> There's no such thing as absolutely secure, so it's a matter of how much risk is tolerable. I use the wired connection in hotels without further safeguards, but then, I am aware of the increased risk and don't do things like banking over the connection. If it's just a matter of looking up the nearest restaurant, then I figure the guy in the next room with a packet sniffer and too much time on his hands can see all he wants. Such voyeurism is much harder to do on a wired connection anyway, so you are an order of magnitude safer than if you were accessing through WIFI.

The Linux world actually has very robust tools for the truly paranoid. Ubuntu already has openVPN preinstalled. All you need is a router at home that is VPN capable and you can establish a secure tunnel to your home network for safe connection no matter where you are in the world. This does away with the cost of paying someone like *publicvpn* It will likely be a slower connection than you are used to, but it is balm for the truly paranoid. The details for setting up openVPN is beyond the scope of a beginners' forum.

Conclusion: hotel wired connections are reasonably safe. If you aren't exchanging sensitive personal info, I would not worry too much about it.


this helps me out a lot.  thank you.  i will be careful with this browsing.

---

### Post by cprofitt on 2012-10-08
> **meep7 said:**
> I don't have a wireless card, so when I use my ubuntu, I use the hard wired connection to my dsl.  I'm going to be staying in a hotel on an upcoming trip and I was wondering if there was an ubuntu application like this: [https://www.publicvpn.com/index.php](https://www.publicvpn.com/index.php), that I can use to protect myself while browsing online while I'm staying there.  

I will not have a wireless connection.  Most things I've seen online are protection for wireless only.   I will definitely have a wired connection, so wireless instructions won't help me.  I can't afford to buy a wireless card right now with my other travel expenses.

A couple of things:

[LIST]
[*]You can bring a travel router with you. Such as the ASUS N travel router - WL-330N. This can be used as a router (firewall, etc) even for a wired hotel connection. You can also use it in many different ways.
[/LIST]
This avoids having to use the hotels wireless (or some other wireless that you do not trust as much). At least with a wired connection you know the hotel put it there; with a wireless it could be some guy next door naming it to look like the hotel.

As one poster said - no connection can be 100% secure, but you can reduce your risk. I would still NEVER conduct banking over a network other than my own. Even a VPN connection could be compromised if you are hooked in to the wrong network to establish the VPN connection. A VPN makes it more difficulty, but not impossible.

---

