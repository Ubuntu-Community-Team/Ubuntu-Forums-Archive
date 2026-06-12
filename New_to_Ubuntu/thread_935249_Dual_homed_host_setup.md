---
title: "Dual homed host setup"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by marufaberlin on 2008-10-01
Hi,

Can someone please help me setting up a dual homed host?

What I intend to do is this:

Network 192.168.1.1/24 will have direct internet access via the router at 192.168.1.1.
Network 192.168.0.1/24 is not connected directly to the web and is managed by the router at 192.168.0.3

The two routers mentioned above are each connected to a dual homed host running debian.

How can I set up this dual homed host to route traffic from the network 192.168.0.1/24 to the web?

---

### Post by The Cog on 2008-10-01
This configuration in/etc/network/interfaces will do a lot of the work:
> auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
up echo 1 > /proc/sys/net/ipv4/ip_forward
up iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE



That should take care of it. You may need to dig through this:
[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

---

### Post by marufaberlin on 2008-10-03
Thank you, that really helped me.

Now I am faced with the next problem:

how do I set up this host as a DHCP server for both networks?

---

