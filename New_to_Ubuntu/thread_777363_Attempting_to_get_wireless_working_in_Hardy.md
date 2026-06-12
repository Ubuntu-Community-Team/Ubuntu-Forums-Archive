---
title: "Attempting to get wireless working in Hardy"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Berean on 2008-05-01
Hi, I've got a Netgear WG511 pcimcia wireless card and am trying to get it to connect to my Netgear DG834 hub.  However, I'm failing!  I think I have a network and my card works out of the box, but I may be wrong.  I am a newb and have just done a fresh install of Hardy.  Can anyone help, please?

---

### Post by Ek0nomik on 2008-05-01
> **Berean said:**
> Hi, I've got a Netgear WG511 pcimcia wireless card and am trying to get it to connect to my Netgear DG834 hub.  However, I'm failing!  I think I have a network and my card works out of the box, but I may be wrong.  I am a newb and have just done a fresh install of Hardy.  Can anyone help, please?

Well, we should know if it works if it can pick up a network.

```
sudo iwlist scan
```

Do you get any results?

---

### Post by Berean on 2008-05-01
Hi and thank you.

ian@ian-laptop:~$ sudo iwlist scan
[sudo] password for ian: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ian@ian-laptop:~$ 

However, I'm sure I have a network.
ian@ian-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:03:0d:0f:4f:f5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 ip=192.168.0.3 latency=64 maxlatency=11 mingnt=52 module=sis900 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
ian@ian-laptop:~$ 

Thanks again.

---

