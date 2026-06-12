---
title: "netcat Help"
date: 2009-06-09
forum: Programming Talk
---

### Post by wiibur on 2009-06-09
Hi, I am just wondering if there are any netcat/networking guru's here who would assist me with a specific task I'm trying to complete. I don't think it's too complicated but I'm just not familiar enough with all of it's nuances.

To put it simply, I want this to happen on one single machine. I want to make http requests from this machine, to this machine, and have the requests look like they're coming from an external IP address. This is because I am also running snort, and I want snort to detect certain things in these requests, but they need to come from an "external" source.

Diagram:
[http://i40.tinypic.com/qqobvd.png](http://i40.tinypic.com/qqobvd.png)

Thanks.

---

### Post by randallecook on 2009-06-11
All network-connected machines seem to have at least two network interfaces: the loopback interface (127.0.0.1) and the regular interface (usually assigned by DHCP when on a LAN). Perhaps you could use one to send the request, but have it aimed at the other. In C you have total control of interfaces, and I am sure netcat/nc provides similar functionality, but I'm not sure how to use it for this purpose. An alternative is to install another NIC in your machine, or just use another computer, if one is available.

---

