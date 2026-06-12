---
title: "Spyware or what?"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by nycap on 2013-04-23
I have heard that ubuntu has no open ports and that spyware doesnt work on it.  using wireshark i can see stuff coming and going though.  so what is it then?

---

### Post by MoebusNet on 2013-04-23
Ubuntu will check automatically for security and bug repair updates. Versions after 12.04 integrate Amazon searches as well, so there will be some activity that is not directly user-initiated. I haven't checked, but I think the server versions don't have the Amazon search integrated. Perhaps someone else can confirm my guess about the server version.

---

### Post by deadflowr on 2013-04-23
> [COLOR=#000000]Perhaps someone else can confirm my guess about the server version.[/COLOR]

Being that the amazon and/or shopping lenses is unity-desktop specific, I would think that a non gui server wouldn't have that.
Nor would any desktop other than unity.
So if you wanted to run a server with a gui, and decided to install, let's say openbox, you wouldn't have the unity-shopping-lens.

---

### Post by craig10x on 2013-04-23
And you can turn off the internet search (including amazon shopping) by going to privacy settings and hit two off buttons...

---

### Post by Old_Grey_Wolf on 2013-04-23
It could be normal traffic on a LAN or internal loopback traffic.

What ports are you seeing in Wireshark? What IP address is it communicating with?

---

### Post by nycap on 2013-04-24
there is activity other than the router and the loopback.

---

### Post by haqking on 2013-04-24
> **nycap said:**
> I have heard that ubuntu has no open ports and that spyware doesnt work on it.  using wireshark i can see stuff coming and going though.  so what is it then?

Spyware works on anything and Ubuntu does have "open" ports.

> Default  installations of Ubuntu must have no listening network services after  initial install.** Exceptions to this rule include network infrastructure  services such as the DHCP client and mDNS** (Avahi/ZeroConf, see [ZeroConfPolicySpec]("https://wiki.ubuntu.com/ZeroConfPolicySpec")  for implementation details and justification). When installing Ubuntu  Server, the administrator can, of course, select specific services to  install beyond the defaults (e.g. Apache). 

 Testing for this can be done with netstat -an --inet | grep LISTEN | grep -v 127.0.0.1: on a fresh install.




Source: [https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

If you NMAP a default 12.10 install for example you will see Ports 68/UDP, 5353/UDP and 631/TCP are listening.


Also if you know how to use wireshark then you would know what the traffic is, if you dont then how do you know what you are seeing at all ? ;)

Peace

---

