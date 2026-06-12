---
title: "[SOLVED] Changing ip address"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-06-27
If I unplug a wireless device from my router and plug a laptop in to the same hole, will the laptop`s ip address become the ip address of the wireless device, remain the same or be completely different?
Thanks

---

### Post by patrickaupperle on 2008-06-27
Completely different, I think.

---

### Post by hyper_ch on 2008-06-27
depends on how you setup your networks and clients.

---

### Post by wormser on 2008-06-27
It depends on the router.  Usually the router assigns the DHCP address to a MAC address for the duration of the lease.  So, different MAC address equals different IP numbers.  What are you trying to do?

---

### Post by nothingspecial on 2008-06-27
I`m trying to install Gutsy using [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

I`ve got to the point in the install where it asks me to choose a mirror but none of them work.
 It`s occured to me that as the wireless on the laptop doesn`t work out of the box in Gutsy this might be the problem.
But I`ve already entered my ip address in the install process and wondered weather I would have to start the install again.

---

### Post by lisati on 2008-06-27
> **wormser said:**
> It depends on the router.  Usually the router assigns the DHCP address to a MAC address for the duration of the lease.  So, different MAC address equals different IP numbers.  What are you trying to do?

I don't know if this will be of help to the OP, but here goes:

The router I use (a Netgear WGR614v7) can be set to assign a fixed IP address to a particular MAC address. Different machines have different MAC addresses, even if they have the exact same model hardware. One thing to keep in mind, however, is that the wired connection usually has a different MAC address to the wireless card.

---

### Post by nothingspecial on 2008-06-27
It`s changed my ip address. No problem, I`ll start again.
Thanks all.

---

