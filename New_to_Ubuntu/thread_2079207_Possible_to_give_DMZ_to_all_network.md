---
title: "Possible to give DMZ to all network?"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by honeybear on 2012-11-01
Hi,

I would like to transform my Router [http://www.usr.com/support/8003/8003-ug/index.html](http://www.usr.com/support/8003/8003-ug/index.html)  into a simple HUB where there is no subnetwork.

DMZ can be done only given to a single IP. 

Thank for you tipps

---

### Post by mcduck on 2012-11-01
If your router(/modem) has an option to disable the routing and use bridged mode instead, that would be exactly what you are trying to do.

(Having an option for DMZ to all network instead of a syubsection of it wouldn't make much sense, as that would be the same as not having a router at all and usng a bridged network instead.)

---

### Post by honeybear on 2012-11-01
> **mcduck said:**
> If your router(/modem) has an option to disable the routing and use bridged mode instead, that would be exactly what you are trying to do.

(Having an option for DMZ to all network instead of a syubsection of it wouldn't make much sense, as that would be the same as not having a router at all and usng a bridged network instead.)

is it what it is called VIRTUAL-SERVER?

i added

192.168.123.100      21-8000
192.168.123.101      21-8000

rebooted

but the other router does not see them. only thew single router robotics

---

### Post by mlentink on 2012-11-01
Perhaps you would care to explain what it is you want to achieve?

As I understand it, you want to turn that router into a switch (or hub, as may be) so switch off all of it's routing functions? That would mean you need another router to connect to the internet.
I'm confused.

---

### Post by honeybear on 2012-11-01
> **mlentink said:**
> Perhaps you would care to explain what it is you want to achieve?

As I understand it, you want to turn that router into a switch (or hub, as may be) so switch off all of it's routing functions? That would mean you need another router to connect to the internet.
I'm confused.

indeed, you know what I meant.

I guess that there is not routing function on this router... (above link , first post indicated the model) :(

---

### Post by mlentink on 2012-11-05
Then there's an awfully simple method: do not use the WAN-port and you've got yourself a hub.

---

