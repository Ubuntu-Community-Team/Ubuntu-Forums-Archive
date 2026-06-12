---
title: "Wireless Not Connecting"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by misterhan on 2008-09-17
I read a lot of the older posts for the same problem. So far I hadn't really had any help.

So the wireless is supposed to be shown under the Network Manager correct?

Nothing is showing up on mine.
I would post information about my notebook, but from the older posts many different commands were given so just tell me what to type and I'll post up from this computer.

---

### Post by porchrat on 2008-09-17
To let us know what wireless card you are running please type post the ouput from this command:

```
lshw -C network
```

(capital C please)

---

### Post by misterhan on 2008-09-17
Here's what came up

  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:49:7b:fa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:ec:67:70
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Hmm I just read that big DISABLED.

---

### Post by porchrat on 2008-09-17
Here is a guide you can follow:

[http://ubuntuforums.org/showthread.php?t=190177]("http://ubuntuforums.org/showthread.php?t=190177")

It is a little outdated, but should still be relevant...lucky for you support for that card is well documented.

In case you wanted to do some research on it this is the name of your wireless card:

> BCM4318 [AirForce One 54g]

Let us know how it turns out.

---

### Post by sands on 2008-09-17
Try this command, if you can see any networks

iwlist *[FONT=monospace]wlan0[/FONT]* scan


Sometimes, even I cannot see the list in network manager. I just enter the essid and connect manually.

---

### Post by misterhan on 2008-09-17
Thanks a lot for the help and quickness. Much appreciated.

-Han

---

### Post by misterhan on 2008-09-17
Double post

Ok I tried that link and I'm stuck on the ndiswrapper-utils it's saying:

E: Couldn't find package ndiswrapper-utils

and I think I have universe repositories enabled.

---

### Post by porchrat on 2008-09-18
Found a newer page for you to use as a guide.  Has worked for quite a few people.

[http://ubuntuforums.org/showthread.php?t=827799]("http://ubuntuforums.org/showthread.php?t=827799")

How are you connecting to the internet at the moment?  You will need an internet connection to access the repositories, are you running it of an ethernet cable plugged into a router?

An alternative way to getting ndiswrapper utilities is by using "synaptic package managaer" you will find it under the "system" menu in the top left corner...just open synaptic and press the binoculars icon labelled "search" then type in "ndiswrapper" (without the quotes - sorry if this is too simplified, but I don't like taking chances)

You'll want to intall the utils ndiswrapper option, just click the checkbox on the side and select "mark for installation"...then you should be sorted

---

