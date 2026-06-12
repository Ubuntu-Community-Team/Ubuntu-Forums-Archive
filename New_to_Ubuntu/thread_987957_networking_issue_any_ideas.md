---
title: "networking issue any ideas"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Gadomuda on 2008-11-20
I have an old dell pc that at one point ran xp. I recently put ubuntu on it and it seems now that I cannot connect to the internet  I ran through the help tips and even pulled up the specs in the terminal. The terminal informed me that my network hardware was [DISABLED] the help notes do not cover what to do in this situation   . This doesn't make any sense to me because i was getting the internet just fine when i booted from the cd but now i have no network connections since i have installed. is there a terminal code to enable network hardware? This is not the first ubuntu pc i have had just the most stubborn. Any advice would be great.

---

### Post by saru411 on 2008-11-20
How are you connected to the net, WiFi or Ethernet? Are you using a router or just straight to modem? If using a router do you know how to set it up and is resetting it an option? What is the output of ifconfig in temrinal?

---

### Post by nhasian on 2008-11-20
it may be helpful if you could post the output of:

```
lshw -C network
```

---

### Post by Gadomuda on 2008-12-15
Sorry it took so long to get this up but my friend let me borrow his wireless adapter and that seems to be work all right for now this is the output for that code you asked me to run. thanks for your help so far. 

*-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:07:e9:c3:d1:ba
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:30:bd:fe:18:e8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:08:e7:e5:70:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:2
       description: Wireless interface
       physical id: 3
       logical name: wlan1
       serial: 00:18:39:16:5d:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.105 multicast=yes wireless=IEEE 802.11bg

---

### Post by abn91c on 2008-12-15
if your friends adapter works, then you need a new Ethernet card or get a wireless adapter like the one you are using now, they are not that expensive now. if you live in the USA you can get one at Walmart or Best buy for less that $45.00. Im on a 400mhz old pc now, the PCI NIC dont work, but I am using a Belkin USB adapter with ubuntu 8.10

---

