---
title: "Ubuntu server VPN gateway/node questions, what resources available?"
date: 2016-01-25
forum: New to Ubuntu
---

### Post by Cybrid013 on 2016-01-25
Hi, I've searched through Google several months now and haven't found a solution or How to.
In all honesty, I don't even know if I have the terminology correct to be able to get effective results.

The question is; How do I set up a home VPN server which I can access externally from the internet and have it access resources on the 'net through my paid commercial VPN. I have hardware (2 spare PC's, a spare NIC, a Tomato router, 2 switches, ...). I don't have the computer/ networking background to do it on my own. Anything that could lead me to a solution would be appreciated. The ideal topology? would be:

VPN Client----internet---ISP Modem---VPN gateway/LAN server---Commercial VPN---Internet

[LIST]

I want to avoid bottlenecks such as:

VPN Client---Commercial VPN---Tomato/OpenVPN client router---VPN server 


If I put my server behind the TomatoRAF router, I will essentially end up running a VPN through a VPN. High overhead.
[/LIST]
[LIST]
If the server is simply behind the ISP modem/router, I risk traffic being traced back to me by the ISP. 

VPN Client---ISP Modem/router---VPN server---ISP Modem(**Snoopy**)---Internet 

If I logged into the server, started a Bit torrent download...I would be easily trace-able. I actually don't download often.
[/LIST]

The closest matches to a solution that I have found are split tunneling or dual NIC with traffic binding/ firewalling.

The topology would be either;
[LIST]

VPN Client--ISP Modem--eth0--firewall (blocking everything but VPN)--VPN Server--eth1--internet
[/LIST]
or 
[LIST]
VPN client--ISP---etho---VPN server---eth0 (separate VPN)---isp---internet
[/LIST]

Essentially it needs to act like a private VPN Node. 

Any suggestions on where to get started and get the best results?

Thanks

---

### Post by sandyd on 2016-01-25
What you want is policy routing.

As an example, I will use the following IPs & info:

OpenVPN Subnet (Home): 10.1.0.0/16
Local LAN Subnet (eth0): 192.168.2.0/24
VPN Provider IP (vtun0): 10.2.0.1/16

```

echo "100 vpn" >> /etc/iproute2/rt_tables # Map "vpn" table to table 100, **run only ONCE**
ip rule add from 10.1.0.0/16 lookup vpn # Force traffic from 10.1.0.0/16 to use this routing table
ip route add 192.168.2.0/24 table vpn dev eth0 # LAN Traffic
ip route add default via 10.2.0.1 table vpn dev vtun0 # Non LAN Traffic -> VPN

```

You may have to adjust the values above depending on your configuration. I suggest not copy/pasting as it will likely create odd results.

May require additional routing rules outside of the "vpn" table to ensure that LAN/VPN networks are aware of it's existence. 

You will still also have to configure NAT for the traffic attempting to reach the External VPN ip as the other side of the external VPN does not know that you have another VPN here; they only see the address at the other side of the tunnel.

---

### Post by Cybrid013 on 2016-01-26
Thanks Sandyd. You reply is way over my head and will need significant reading and digesting. I'll get started... ;)

I think I understand the general gist. The policy routing tells the server to direct traffic in specific routes based on rules I give it. 

I simply don't understand the syntax and context of your example to adapt it to my needs.  This is where I anticipate some long hours of work ahead.

---

