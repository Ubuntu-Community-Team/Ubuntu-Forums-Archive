---
title: "share internet from vbox vm back to its ubuntu host"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by tsh3po on 2012-03-09
Hi Guys

This is probably silly but is it possible?

Basically I'm running Ubuntu 11.10 x64 as host to a win7 vbox vm. now what I normally do is connect the host to the internet using a normal 3G card then through NAT use the win7 to connect to my work VPN (Juniper VPN, which I struggled to get working and finally gave up).

This method works but now what if I wanna share that VPN connection back to my Ubuntu host and have my Ubuntu system as part of VPN network.

---

### Post by Jon Monreal on 2012-03-09
It would be my guess that you could use internet connection sharing in the guest OS to share the connection with the host just as you would with two physical machines, using an unused network interface. I would hope that from there the traffic would go through the VPN.

---

### Post by tsh3po on 2012-03-11
thanks but fought with the VPN and through a combination of guides finally got it working

here are the links used though it now changes to "how to get juniper working in ubuntu"


```
http://holyarmy.org/2009/06/vpn-on-ubuntu-linux-with-juniper-network-connect/
http://mad-scientist.us/juniper.html
http://www.joshhardman.net/juniper-network-connect-vpn-linux-64-bit
```

---

