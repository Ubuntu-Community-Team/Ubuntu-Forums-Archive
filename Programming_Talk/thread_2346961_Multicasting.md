---
title: "Multicasting"
date: 2016-12-20
forum: Programming Talk
---

### Post by chuchi on 2016-12-20
Hi there!
 

 I have an application that performs a discovery via a Multicast and SLP. I have learnt that routers, by default, do not allow Multicast to travel through different subnetworks. Routers should be configured to support IGMP to allow multicast traffic but I can't change the router configuration.
 

 So I can only discover devices in my own subnetwork. My question is...
 

 Is there a way, from the application side, to discover devices in other subnetworks?
 

 I have tried to increase the TTL flag in the call to setsocketopt with no success either.
 

 

 Thanks a lot!

---

