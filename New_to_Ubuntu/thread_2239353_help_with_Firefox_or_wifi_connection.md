---
title: "help with Firefox or wifi connection"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by marakisir on 2014-08-13
Hi im new to Lubuntu because i have an old one pc.. pentium 4 cpu  , 2gb Ram , Intel gpu ans a wifi usb stick NETGEAR WG111v3 54Mbps. So my pc is dual boot via grub bootloader with Windows xo sp3. 
My problem is that i can't connect to any web page via Firefox but my netgear is connected to the network.. So what i'm doing wrong? and when i'm trying to install wine or something else from cmd monitor gave me back an error that can't install.. 
Some help please..... Thank you

---

### Post by Harsh_Parikh on 2014-08-13
Try nm-applet in terminal.....to connect with any network

---

### Post by marakisir on 2014-08-13
But it seems to be  connected to a network ... it shows me that is connected via wifi with 3 bars but no load on web pages
i've made this thing here 
Menu->Preferences->Default Applications for LXSession->Autostart.
nm-applet
and i have the network monitor to my down side bar...

---

### Post by marakisir on 2014-08-13
also i've dowload from my windows xp the ndiswrapper and wine and the drivers of my netgear but i cant install the first two things to continue with my netgear drivers and make an instalation when i boot on lubuntu.. any help is usefull

---

### Post by Rob Sayer on 2014-08-13
Ndiswrapper is something you use as a last resort.  It's actually not very reliable, and frankly I'd just go and buy another usb dongle that works in linux rather than use it..  The trouble is that not all those usb wifi dongles don't consistently have the same innards.  Best to try to see what you have.

Open a terminal and copy and paste into it:

```
sudo lshw -C network
```

then enter your user password and wait for the output.  Post that here, wrapped in code tags.

Then hopefully one of the *real* wireless experts here (which I am definitely not) will answer.

---

### Post by marakisir on 2014-08-14
*-network               
       description: Ethernet interface
       product: NetXtreme BCM5782 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 03
       serial: 00:0f:20:72:41:46
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=5782-v3.13 latency=64 link=no mingnt=64 multicast=yes port=twisted pair
       resources: irq:20 memory:ebb00000-ebb0ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:1.2
       logical name: wlan0
       serial: 00:1e:2a:d6:b2:db
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.13.0-24-generic firmware=N/A ip=192.168.1.69 link=yes multicast=yes wireless=IEEE 802.11bg

This is what i take from thw above command....

---

