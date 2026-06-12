---
title: "WiFi Problems on Acer 5000 laptop"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by thorin81 on 2008-08-11
I did a search first to see if I could find a similar problem on my system, but no luck...

I have an Acer 5000 Laptop and just installed 8.04 on the machine to dual boot with XP Pro. The install went fine, but I cannot get the machine to detect a wireless network. After running lspci I know that the wireless adapter is recognized, but I cannot figure out how to turn the adapter on... There is a switch (button) on the front of the machine that I use to turn on the adapter in XP, but I cannot figure out how to turn on the adapter in 8.04.

Any suggestions?

Thanks!!

---

### Post by Ryadt on 2008-08-11
Can you post the output of ```
lshw -C network
```

---

### Post by thorin81 on 2008-08-11
lshw -C network results:

 *-network:0              
       description: Ethernet interface 
       product: SiS900 PCI Fast Ethernet 
       vendor: Silicon Integrated Systems [SiS] 
       physical id: 4 
       bus info: pci@0000:00:04.0 
       logical name: eth0 
       version: 91 
       serial: 00:c0:9f:c4:1c:f8 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes 
  *-network:1 
       description: Network controller 
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller 
       vendor: Broadcom Corporation 
       physical id: b 
       bus info: pci@0000:00:0b.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master 
       configuration: driver=b43-pci-bridge latency=64 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:14:a4:2c:bc:fc 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by thorin81 on 2008-08-11
Bump.

---

### Post by thorin81 on 2008-08-12
Bump 24hr...

---

### Post by dca on 2008-08-12
Have you tried this thread?
 
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

