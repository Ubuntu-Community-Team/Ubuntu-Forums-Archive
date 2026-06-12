---
title: "Help with Linux Mint"
date: 2008-04-11
forum: Other OS Talk
---

### Post by Google Spider on 2008-04-11
Hi, I want to forward my ports using Ktorrent's Upnp plugin but it is not detecting my devices (perhaps). I pressed the 'Rescan' button but nothing happens. My router is UT300R2U. I am running it on Linux mint 4.0 KDE community edition. 

I am new to Linux and don't know much about iptables and all, but I can provide additional details if needed. I hope someone can help me with port forwarding. Thanks for your time.


[IMG]http://i268.photobucket.com/albums/jj17/Google_Spider/ktorrent.png[/IMG]

---

### Post by renzokuken on 2008-04-11
first of all does your router support upnp? because not all do

and if it does you have to make sure it is enabled in ouyr router settings

---

### Post by Google Spider on 2008-04-11
> **renzokuken said:**
> first of all does your router support upnp? because not all do


I have no idea how to figure that out:confused:

---

### Post by renzokuken on 2008-04-11
try logging into it. open your browser and enter the address 192.168.1.1 (an industry standard) if that doesnt work, run 

```
ifconfig
``` from your terminal, look for the gateway address and that should be the address of your router, then try that address in your browser



EDIT: in fact this guide shows you how to get into its settings [http://www.portforward.com/english/routers/port_forwarding/UTStarcom/UT-300R2U/default.htm](http://www.portforward.com/english/routers/port_forwarding/UTStarcom/UT-300R2U/default.htm) and the upnp settings are under the advanced tab by the looks of things

---

