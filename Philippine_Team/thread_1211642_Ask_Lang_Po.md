---
title: "Ask Lang Po"
date: 2009-07-12
forum: Philippine Team
---

### Post by sieg06 on 2009-07-12
May free software ba para ma block ang instant messenger and website in network using ubuntu

---

### Post by dodimar on 2009-07-12
> **sieg06 said:**
> May free software ba para ma block ang instant messenger and website in network using ubuntu

In a network ba? kung madaming computers.. setup a dedicated firewall/proxy server... (smoothwall is a good one)

---

### Post by dannybuntu on 2009-07-12
Sa pagkaalam ko po, pwede kaya lang hindi directa. 

Sa IM, pwede mo iblock ang port na ginagamit ng protocol. 
Sa website pwede kang maginstall ng filtering addon sa firefox.

---

### Post by badrra on 2009-07-13
OpenDNS it blocks YM, IRC, porn, violent materials, etc regardless of OS. Visit their site and read more about it at.

---

### Post by dannybuntu on 2009-07-13
> **badrra said:**
> OpenDNS it blocks YM, IRC, porn, violent materials, etc regardless of OS. Visit their site and read more about it at.

[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

Correct po. 

Oo nga this one's good too and easier to implement. You can change dns servers by modifying /etc/resolv.conf

replace entries with:
208.67.222.222 
208.67.220.220

:guitar:

Hehe si pareng Jun Auza pala nagsulat ng instructions dun sa page nila.

For more specific settings - ie. kung anong level ang gusto mong maaccess ng mga client - I think you have to register. I think. 

:D

---

### Post by pinoyskull on 2009-07-16
iptables :D

---

### Post by zeroseven0183 on 2009-07-16
I'd go for OpenDNS also and you can also consider blocking the ports used by the instant messengers.

---

### Post by Script Warlock on 2009-07-17
kung delete ko dns ip ng mydsl sa resolve.conf anung mangyayari sa koneksyon?...di ko na try to sa 8.04.

---

### Post by dannybuntu on 2009-07-17
> **Script Warlock said:**
> kung delete ko dns ip ng mydsl sa resolve.conf anung mangyayari sa koneksyon?...di ko na try to sa 8.04.

404.

Tapos pag nag ping ka sa url- Destination Host Unreachable
Pero pag ping mo yung ip-address ok naman. Assuming memorized mo yung ip address :D

---

