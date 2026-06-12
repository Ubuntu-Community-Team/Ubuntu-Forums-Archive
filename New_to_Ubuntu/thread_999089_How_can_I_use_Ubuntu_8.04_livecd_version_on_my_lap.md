---
title: "How can I use Ubuntu 8.04 livecd version on my laptop"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by abrand888 on 2008-12-01
Hello,

I have a laptop and I would like to use the 8.04 livecd version of the Ubuntu program on my laptop. When I use my laptop in windows xp , the Atheros wireless adapter automatically recognizes my wireless signal in my house and I am able to go on line. On my regular computer upstairs, a Intel Q6600 CPU processor, the live cd version of 8.04 will find my ssid, I click connect and it connects immediately. I would like to replicate my success with my laptop on my first floor.

I am trying to use the enabled restricted driver to make the Ubuntu Live cd working so I can go online  to the internet. According to hardware drivers listing support for atheros 802.11wireless lan card enabled and in use and the device driver atheros hardware access layer (HAL) is also enabled and in use.

I went to network settings, disabled roaming, entered my ip address  subnet and gateway address , left roaming disabled and then I saw that wired connection listed my ip address and I was able to ping my gateway  but I can't go anywhere in Firefox. 

Is there a step I am missing ? All I would like to do now is used the Ubuntu 8.04 as a live cd.

Loook forward to your suggestions.

Thanks.

I ran in terminal mode sudo to get the information below.  ubuntu@ubuntu:~$ sudo  lshw  -C network 
  *-network               
       description: Ethernet interface 
       product: NetLink BCM5906M Fast Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1b:38:5e:c4:da 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.0.112 latency=0 link=no module=tg3 multicast=yes port=twisted pair 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix cap_list 
       configuration: latency=0 
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo  lshw  -C network 
  *-network               
       description: Ethernet interface 
       product: NetLink BCM5906M Fast Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1b:38:5e:c4:da 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 ip=192.168.0.112 latency=0 link=no module=tg3 multicast=yes port=twisted pair 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:06:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix cap_list 
       configuration: latency=0 
ubuntu@ubuntu:~$

---

### Post by Het Irv on 2008-12-01
If I remember correctly.... you cannot use the restricted drivers on the Live CD.  It has to do with the fact that the OS's files are burnt onto the CD, and you cannot write to the CD.

---

### Post by abrand888 on 2008-12-02
Is there a way that I can use a livecd without using restricted drivers on my laptop ?and be able to go on the internet ? 

Thanks

---

### Post by Cypher on 2008-12-02
Try the 8.10 (Intepid Ibex) LiveCD which has better Wifi support to see if it fares better on your laptop..

---

### Post by stalkingwolf on 2008-12-02
you might also try enabling roaming and dhcp

---

