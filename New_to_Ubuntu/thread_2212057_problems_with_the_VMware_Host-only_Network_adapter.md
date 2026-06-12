---
title: "problems with the VMware Host-only Network adapter"
date: 2014-03-19
forum: New to Ubuntu
---

### Post by Horst_Noll on 2014-03-19
Hi,

I encounter serious problems with the VMware Host-only Network adapter in Ubuntu 13.10 (server).

I am currently setting up a router which should make possible to get access each other from within two different networks.

Therefore I created a VMware with Ubuntu Server 13.10 on it with one bridged adapter and one VMNet10 host-only adapter...

[B][U]eth0 (bridged)
[/U][/B]IP Address = 192.168.1.254
Network = 192.168.1.0
Prefix = 24
NETMASK = 255.255.255.0
GATEWAY = 192.168.1.1 (Hardware-Router)
DNS = 192.168.1.1 (Hardware-Router)

_**eth1 (host-only)**_
IP Adress = 192.168.10.254
Network = 192.168.10.0
Prefix = 24
NETMASK = 255.255.255.0
GATEWAY = 0.0.0.0

Unfortunately I got an error message in eth1 "Interrupt:19 Base address:0x2000"? How can I get rid of this message and bring eth1 to work?

Thank you.

---

