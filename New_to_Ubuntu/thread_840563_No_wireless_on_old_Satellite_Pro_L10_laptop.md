---
title: "No wireless on old Satellite Pro L10 laptop"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by MangasColoradas on 2008-06-25
@ubuntu1:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:b6:0b:60
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.107 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32



I can see nothing helpful under the network manager. Do I need a driver?

---

### Post by MangasColoradas on 2008-06-26
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) 

sorted

---

### Post by bemental on 2009-03-12
Hey Mangas,

I assume you figured out what you needed to do to take care of this, yes?

Any pointers before I kick it off and give it a go?

---

