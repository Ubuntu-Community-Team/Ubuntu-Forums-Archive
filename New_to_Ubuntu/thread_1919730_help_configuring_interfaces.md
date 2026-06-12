---
title: "help configuring interfaces"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by bsmichel on 2012-02-03
HI all.

I'm trying to configure a dual homed host. The eth0 interface is connected to a cable-modem which assigns it an ip by DHCP (usually something like 93.x.y.z). 

I did the initial setup of my host using only this interface. When the setup was finished I configured the second interface (eth1) to connect to my lan. As I was planning to use this host as a router I configured this interface with a static IP in the ip range of my LAN (192.168.10.0/24). There is another host in my lan that acts as dhcp-server serving the range 192.168.10.10-192.168.10.25
After reboot eth0 that was supposed to obtain a dynamic ip in the range 93.x.y.z got the ip address in the range 192.18.10.10-192.168.10.25

The /etc/network/interfaces is as follows:

auto eth0 
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.10.1
netmask 255.255.255.0

So I got: 
 eth0: ip->192.168.10.23
 eth1: ip->192.168.10.1

How can I avoid eth0 from getting its ip address from the lan's dhcp-server?

---

### Post by The Cog on 2012-02-03
Your config looks sensible.

I don't think eth0 should be getting dhcp config from a server on eth1. Are you sure there isn't another dhcp server on eth0? Try rebooting with eth1 unplugged. 

You could also try the command ```
sudo dhclient -v eth0
``` and watch what it says as it tries to use dhcp again.

---

### Post by bsmichel on 2012-02-03
If I unplug eth1 then eth0 gets the ip by dhcp from the cable modem, that's the way it should always work but as soon as I plug eth1 again eth0 gets the ip from the dhcp server in the lan-side (the lan attached to eth1). It's very strange.... like if eth0 was asking for an ip through eth1...

I'm pasting below the output of dhclient -v eth0:

```
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/f8:d1:11:02:c6:1a
Sending on   LPF/eth0/f8:d1:11:02:c6:1a
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.10.10
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.10.10
bound to 192.168.10.21 -- renewal in 2882 seconds.
```

as you can see the internal lan dhcp-server is at 192.168.10.10

---

### Post by The Cog on 2012-02-05
That's very odd. It makes me wonder if there's some kind of bridging connection between the two LANs somewhere. 

My next step would be to use tcpdump to capture packets on eth0 to see if the dhcp offer is being received there, or repeat while dumping on eth1 and see what happens there. Actually, I'd probably use 3 windows. In the first use **sudo tcpdump -i eth0**, in the second use **sudo tcpdump -i eth1**, and once those two are listening use **sudo dhclient -v eth0** in a third window. That way, you can see what is happening on each interface as dhclient acquires the address.

---

