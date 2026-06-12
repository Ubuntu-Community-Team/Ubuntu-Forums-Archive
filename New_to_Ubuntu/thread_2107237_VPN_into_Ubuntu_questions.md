---
title: "VPN into Ubuntu questions"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by graphicsmanx1 on 2013-01-21
I am new to Ubuntu but I typically use windows and Ive setup VPN through remote desktop.  However I am switching a few computers to Ubuntu and I am unsure how to VPN into them.  Ive read VPN client but is it setting up the desktop as a server??  What is the best way to VPN a NON server environment?  My goal is to learn how to VPN just like remote desktop into Windows from Ubuntu AND Windows into Ubuntu.

---

### Post by mysteriousdarren on 2013-01-22
I'd use OpenVPN and go through it that way. Are you looking for something like teamviewer? or what exactly?

---

### Post by graphicsmanx1 on 2013-01-22
I wouldnt mind something like TeamViewer but locally done..

---

### Post by doctor82 on 2013-01-22
I could make PPTP work in ubuntu. But unlike windows, openvpn seems to be difficult to be setup. Also many commercial openvpn providers have their own windows version of their software and no linux version. E.g. Hotspotshield.

---

### Post by Bölvaður on 2013-01-22
> **graphicsmanx1 said:**
> Ive read VPN client but is it setting up the desktop as a server??
Yes. If you have a computer streaming content to another computer, that is a server-client situation.

So yes,  you always are setting up a server when ever you install VPN on a computer.

No proper admin would install VPN on their servers, as dedicated servers do not have any graphical environment.



I installed VPN on my Ubuntu computers some years ago, it's easy, but useless. I found it bad to remotely control the computers, as ssh (command-line based remote access) is better. But if you are not able to do what you want using ssh then VPN is definitely for you.... or for spying and freaking people out that is using the computers... it's very fun.

---

