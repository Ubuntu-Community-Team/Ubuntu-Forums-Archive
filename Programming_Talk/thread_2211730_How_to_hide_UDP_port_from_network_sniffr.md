---
title: "How to hide UDP port from network sniffr"
date: 2014-03-17
forum: Programming Talk
---

### Post by dani_b1 on 2014-03-17
Hi
I would like to develop a program which listen to specific UDP port without netstat or nmap detect it
Any suggestion?

---

### Post by ofnuts on 2014-03-17
Use "[port knocking]("http://en.wikipedia.org/wiki/Port_knocking")"?

---

### Post by TheFu on 2014-03-17
If the port is open and listening, then it will appear open to those tools. You can limit the access as dani_b1 says by using some form of port knocking and only open the port to the specific IP via firewall rules that provided the correct "knock" packets. It will not be "stealth", but .... 

There is only so much you can do.

Another option is to only make it accessible over a strong VPN like openvpn.  That is fairly common, so running a VPN woudn't be odd to discover and your UDP port wouldn't need to be seen on the internet at all that way.

---

