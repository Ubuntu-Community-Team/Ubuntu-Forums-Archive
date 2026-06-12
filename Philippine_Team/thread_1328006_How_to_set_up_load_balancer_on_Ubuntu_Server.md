---
title: "How to set up load balancer on Ubuntu Server?"
date: 2009-11-16
forum: Philippine Team
---

### Post by Pedro0727 on 2009-11-16
i got 2 ISP, PLDT and the BAYANTEL, kindly help mo plz to set up load balancer and proxyserver.

thank you in advance..

---

### Post by pinoyskull on 2009-11-16
try this one
[http://ubuntuforums.org/showthread.php?t=665377](http://ubuntuforums.org/showthread.php?t=665377)

---

### Post by Pedro0727 on 2009-11-16
> **pinoyskull said:**
> try this one
[http://ubuntuforums.org/showthread.php?t=665377](http://ubuntuforums.org/showthread.php?t=665377)

Thanks for the response :-)

---

### Post by badrra on 2009-11-19
Nose bleed hehehhehe

---

### Post by Pedro0727 on 2009-11-19
> **badrra said:**
> Nose bleed hehehhehe

uunga lol.. 

Mga master help nmn plz..

---

### Post by kiminaiseah on 2009-11-21
@Pedro0727


give me access to your box.. setup ko xa.... 

heheh

load balancing... keepalive..connection... autofailover switch
QOS, IP bandwidth limiting, squid proxy... yun nga lang walang gui. purely console lang

---

### Post by loell on 2009-11-21
do you really want to have load balancing?


or.. are you looking for NIC Bonding?


[http://www.howtoforge.com/network_bonding_ubuntu_6.10]("http://www.howtoforge.com/network_bonding_ubuntu_6.10")

---

### Post by Pedro0727 on 2009-11-21
> **loell said:**
> do you really want to have load balancing?


or.. are you looking for NIC Bonding?


[http://www.howtoforge.com/network_bonding_ubuntu_6.10]("http://www.howtoforge.com/network_bonding_ubuntu_6.10")

NIC bonding i think will works for me, thank u po :)

---

### Post by Pedro0727 on 2009-11-21
@ kiminaiseah ung QOS and squid pwede b gamitin ung webmin dun?
@loell
meron kc akong dalawang ISP but wala akong router, switch lng, pag ssabayin ko b un dalawang ISP s switch p puntang server n mag babalance?  or masmaganda ung NIC bonding, mag lalagay ako ng 3 NIC, ex eth0, eth1 and eth2. Tapos e babalance ung dalawang ISP palabas s etho2 papuntang switch n mag ddistribute, nka config n dun dapat ung DHCP, squid, etc. possible b un?


Anu po b kailangan ko para maimprove ko ung network setup ko?


Thank you po s lahat nag response :)

---

### Post by loell on 2009-11-21
> **Pedro0727 said:**
> 
@loell
meron kc akong dalawang ISP but wala akong router, switch lng, pag ssabayin ko b un dalawang ISP s switch p puntang server n mag babalance?  or masmaganda ung NIC bonding, mag lalagay ako ng 3 NIC, ex eth0, eth1 and eth2. Tapos e babalance ung dalawang ISP palabas s etho2 papuntang switch n mag ddistribute, nka config n dun dapat ung DHCP, squid, etc. possible b un?


yep, possible yun, basically yun siguro ang primary use case ng nic bonding, bandwidth consolidation of two service providers.

---

### Post by Pedro0727 on 2009-11-22
> **loell said:**
> yep, possible yun, basically yun siguro ang primary use case ng nic bonding, bandwidth consolidation of two service providers.

Maraming s salamat po sir loell, at s ibang nagresponse.

---

