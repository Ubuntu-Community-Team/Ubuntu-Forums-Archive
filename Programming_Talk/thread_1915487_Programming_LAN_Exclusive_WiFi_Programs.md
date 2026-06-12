---
title: "Programming LAN Exclusive WiFi Programs"
date: 2012-01-26
forum: Programming Talk
---

### Post by Scott Vierge on 2012-01-26
Hola,

What is a way wherein a signal can be sent via the local area network wifi exclusively?

---

### Post by Tony Flury on 2012-01-27
Not sure why you would need to do this - but in general if a device has multiple connections the device can do one of two things : 
1) it will use the "best" connection for all of it's traffic - best is normally defined in terms of speed, but depending on other things it can have other criteria
2) It will try to share the traffic across multiple connections.

This is all normally determined by the network and and IP routing layers.

By the time you get to the higher level protocols (TCP or IP datagrams) then you normally (as a programmer) don't have control over the interface that you use - since the lower layers have done all of this for you.

You don't say what programming language you are using, or which protocols or libraries you will want to use. It may be that on networking library you are going to use, you can specify which interface to use, or at least a priority for each interface.

Maybe the simplest way is simply to disable the interfaces you don't want to use, other than that you may well need to write your own lower layers to ensure that you program uses WiFi only.

Note : You might find that if you only want to use WiFi for some applications, and those applications only go to some hosts, you might be able to use a firewall (or similar) to block traffic to those hosts from anything other than your Wifi connection - I don't know if a firewall exists that does that though.

Another way would be to organise your network (via routers etc) so that each PC interface gets a different IP address, and then choose which source IP address your program uses when it connects. you might well find that your PC gets unique IP addresses per interface anyway - that depends on your router.

---

