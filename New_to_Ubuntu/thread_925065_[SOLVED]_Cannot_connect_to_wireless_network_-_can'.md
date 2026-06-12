---
title: "[SOLVED] Cannot connect to wireless network - can't find answer on forum."
date: 2008-09-20
forum: New to Ubuntu
---

### Post by AndyJG on 2008-09-20
Hello everyone.

I have another problem unsolved which I can't solve until the wireless Internet is connected.

I have an Orange Wireless router and a Edimax EW-7318UG which was bought as the Ubuntu site said it was supported by Hardy Heron. Wireless shows up in the Network Manager and I've put in the WEP key and network name etc (I have attached a screengrab showing what I've done). However, Firefox won't connect to the Internet. I've also tried the roaming mode with no luck.

I may have missed something here - on my Windows XP system you select from the wireless networks available and connect to the Internet that way but I can't find anything like this in Ubuntu, unless the Network Manager does this when it finds a network.

I'm getting a popup saying updates are available for my system - does this mean the Internet is connected? How would the system know updates were available otherwise?

I notice in other posts the output from a command in Terminal is asked for so I've done that - hopefully I've run the right code:

andy@bob-the-laptop:~$ sudo lshw -C network
[sudo] password for andy: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: eth0
       version: 10
       serial: 08:00:46:91:8f:60
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:1f:1f:03:2d:81
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
andy@bob-the-laptop:~$

I'd be grateful if anyone can advise on this.

Thanks in advance.

Andy.

---

### Post by Kevbert on 2008-09-20
Rather than setting up wireless as shown in your screenshots try setting wireless to roaming mode.  If you look at the top right-hand corner of the desktop you should have an icon consisting of two screens (if wireless is not enabled). Right click on it at make sure that wireless is ticked.  If you left click on the icon you should get a list of available networks.

---

### Post by AndyJG on 2008-09-24
Thanks, Kevbert.

This is certainly a step forward - I now have my wireless network showing. However, there's an entry next to the network name showing '0%'. What does this mean? I still can't actually connect to the Internet.

Thanks again.

Andy.

---

### Post by superprash2003 on 2008-09-24
in your terminal type ifconfig and post output.. try pinging your router and post output

---

### Post by AndyJG on 2008-10-28
Hello everyone.

Sorry for the delay in completing this thread.

I've fixed the problem - I overlooked the 'pairing' button on the Orange Livebox. Doh! It's all up and running now.

Thanks to everyone for their help.

Andy.

---

### Post by random turnip on 2008-10-28
I have a similar problem with a HP built in wireless card but the Wireless Connection option isn't even in Network settings box!

---

