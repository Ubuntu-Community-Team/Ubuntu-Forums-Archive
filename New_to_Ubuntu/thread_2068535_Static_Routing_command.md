---
title: "Static Routing command"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by 14309 on 2012-10-09
Hi.
I am running Virtual box with two VMs (Debian 6) on Ubuntu 12.04 host. 
One of the VM is DHCP server and has 3 NICs. One connected to Internet  (NAT through Virtualbox) and two NICs are connected to internal  networks.

My clients PCs can get IP from DHCP server i.e. VM Debian 6. But how do I get Internet working on them?


here is my configuration.

eth0 - 10.0.2.15 - connected to Internet with NAT (Virtualbox GUI) 
eth1 (DHCP) - 192.168.1.x - connected with switch. Client PCs connect to switch.
eth2 - 192.168.2.x - other internal network.

if I add this command, DHCP stops working.
```
route add -net 192.168.1.0 netmask 255.255.255.0 gw 10.0.2.15 eth0
```I am not sure if this is right command. Please Help!

---

### Post by Elfy on 2012-10-09
Thread closed. Please do not post duplicates, it dilutes community effort.

---

