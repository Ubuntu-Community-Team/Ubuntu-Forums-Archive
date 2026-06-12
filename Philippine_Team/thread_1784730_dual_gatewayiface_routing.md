---
title: "dual gateway/iface routing"
date: 2011-06-17
forum: Philippine Team
---

### Post by lianne_john07 on 2011-06-17
Help! Please!

eth0
address 192.168.2.1
netmask 255.255.255.240
gateway 192.168.2.30

eth1
address 192.168.1.1
netmask 255.255.255.0
gateway 192.168.1.30

How can i use them both at the same time.

---

### Post by daxumaming on 2011-06-19
I've been using 2 connections in the office, 1 wlan (internet access) and 1 eth (local network access). I can't use both without setting one interface to *use this connection only for resources on this network*. Unfortunately, that option's only available through Network-Manager. I still haven't figured out how to do it without NM.

---

