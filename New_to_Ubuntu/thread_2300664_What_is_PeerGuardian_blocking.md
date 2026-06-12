---
title: "What is PeerGuardian blocking?"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by feartheterrapin on 2015-10-27
I just installed PeerGuardian and am amazed all the traffic that is apparently being blocked.  I have no applications running and not connected to a VPN, however, much is being blocked both in and out. I did not expect to see any outgoing traffic.   Attached is a screenshot.    Are there embedded/hidden apps calling home.  Should I be looking to delete some sort of malware?

---

### Post by jimmy-frydkaer on 2015-10-27
Have a look at this wiki:

[https://en.wikipedia.org/wiki/PeerGuardian](https://en.wikipedia.org/wiki/PeerGuardian)

---

### Post by feartheterrapin on 2015-10-27
I am not sure that answers my question.  The blocked traffic is outgoing.  I am not concerned that the traffic is being blocked as much as what application or process is trying to communicate out from my PC out to these sites.  Is there malware or something else I need to be concerned with?

---

### Post by sandyd on 2015-10-27
Took a quick look

First few entries are all openNIC - are you using that?
The remaining are all connections to private internet access.

---

### Post by feartheterrapin on 2015-10-28
> **sandyd said:**
> Took a quick look

First few entries are all openNIC - are you using that?
The remaining are all connections to private internet access.

Thanks.  I am using openNIC for my DNS and I do occasionally use PIA via OpenVPN.   I am still confused on the names of the connection provided by PeerGuardian and how you were able to relate the IP numbers.  My IP searches on kloth provided no info.

---

### Post by sandyd on 2015-10-28
> **feartheterrapin said:**
> Thanks.  I am using openNIC for my DNS and I do occasionally use PIA via OpenVPN.   I am still confused on the names of the connection provided by PeerGuardian and how you were able to relate the IP numbers.  My IP searches on kloth provided no info.

The first few are all port 53 - probably some kind of DNS, went and searched the IPs on opennic, and found them there.

The PIA addresses - PIA always changes the addresses around, but lists of addresses used by PIA can be found on Google as well.

---

