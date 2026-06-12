---
title: "Who can see someone's MAC address?"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by hanzj on 2012-05-21
Hello,

Who can see your MAC address?

Can an app/program see your MAC address?
Can websites?

---

### Post by rai4shu2 on 2012-05-21
I think you should assume that your MAC address is out there. If you rely on it for security, then you need to rethink your security.

---

### Post by roelforg on 2012-05-21
> **rai4shu2 said:**
> I think you should assume that your MAC address is out there. If you rely on it for security, then you need to rethink your security.

Local ones can be found by ping sweeping and checking the arp cache.

---

### Post by choppyfireballs on 2012-05-21
Technically no one can see your mac address. however it is possible for someone to sniff the packets that your computer sends to the router. 

your pc sends a packet to the router with your internal ip address and mac address. 

from there your router strips off the mac and the ip replaces them respectively with its external ip/ and it's wan port mac address.

stores what is being sent and received using sockets. This is called Network Address Translation or NAT so technically no one on the outside can see your mac/ip. However if someone is sniffing your network they can get your mac before your router strips it. Also your mac is not unique it is possible to get two network cards with the same MAC address. Though it's EXTREMELY rare.

---

### Post by Lars Noodén on 2012-05-21
In effect, anyone on your LAN or any program on your machine can find your MAC address.  It's not useful in any kind of security measures, if that's what you're asking.  It's trivial to change it, too.

---

### Post by choppyfireballs on 2012-05-21
> **Lars Noodén said:**
> In effect, anyone on your LAN or any program on your machine can find your MAC address.  It's not useful in any kind of security measures, if that's what you're asking.  It's trivial to change it, too.

I wouldn't say it's COMPLETELY pointless if someone is just sniffing wifi in your area it can be a deterrent because there WILL be an easier network to get into, that being said it should not be your primary measure of security.

---

