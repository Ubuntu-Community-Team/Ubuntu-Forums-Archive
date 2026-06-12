---
title: "No Internet Connection"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Beetlebum_007 on 2008-12-01
I have installed Ubuntu on my Acer Aspire 5315 laptop. Everything seems to work fine apart from when I try to connect to the internet. The operating system doesn't seem to recognise my internet connections - to be honest I'm struggling with the setup and finding my way around the system - and there are a couple of things I am unable to find eg; the start>control panel instruction baffles me because I can't find the start button on the screen.
I would be grateful if someone could help me to become acquainted with this and to get me connected to the internet.
Thanx in advance!
Beetlebum

---

### Post by zephyrcat on 2008-12-01
I don't know about the internet problem (try some googling with the laptop model and ubuntu), but Ubuntu does not exactly have a start button. It looks like you are trying to follow instructions for Windows, not Ubuntu. Various settings are found in Ubuntu under the System menu (at the top of the screen).

---

### Post by shadowlands on 2008-12-01
I think we are in the same boat, thus I hope a solution is found. My previous OS bit the dust over the holidays so I amn trying out Ubuntu.  I can not connect to the net and I think my five year old is going to revolt if I can not find a solution so that I can get off of his computer.  Oh, my laptop is an Aspire 5570z.


> **Beetlebum_007 said:**
> I have installed Ubuntu on my Acer Aspire 5315 laptop. Everything seems to work fine apart from when I try to connect to the internet. The operating system doesn't seem to recognise my internet connections - to be honest I'm struggling with the setup and finding my way around the system - and there are a couple of things I am unable to find eg; the start>control panel instruction baffles me because I can't find the start button on the screen.
I would be grateful if someone could help me to become acquainted with this and to get me connected to the internet.
Thanx in advance!
Beetlebum

---

### Post by halitech on 2008-12-01
open a terminal and post back the results of
```
lshw -C network
```

---

### Post by xjcannonx on 2008-12-01
A terminal is a command prompt in windows, if you want to navigate there then go to "Applications --> Terminal" find Applications on the taskbar...called a panel in linux

---

### Post by gasto on 2008-12-01
description: ethernet interface
product: SiS900 PCI Fast Ehternet
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 91
serial: xx:xx:xx:xx:xx:xx
width: 32 bits
clock: 33Mhz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=32 maxlatency=11 mingnt=52 module=sis900 multicast=yes

---

### Post by halitech on 2008-12-01
looks like it is seeing your wired connection, least the hardware portion of it. Still in the terminal, type this and post the results
```
ifconfig
``` and see what it gives us for a result.

---

### Post by gasto on 2008-12-02
ifcongif eth0

eth0 Link encap: Ethernet adapter HWaddr 00:16:ec:6e:c3:83

---

### Post by Beetlebum_007 on 2008-12-09
In reply to you earlier post - open terminal and enter lshw -C network this was my result;-

 description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:db:97:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.0.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
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

Sorry for taking so long to get back to you as my connection was useless for a while!
Thanx for your help.
Beetlebum

---

### Post by rev0lv3r on 2008-12-09
Are you guys unable to cnnect to the internet using wired?
Or only wireless does not work.

If wired does work, I suggest you enable additional software repositories (system -> administratoin -> software sources), and then do software update
Then check to System -> administration -> hardware drivers if there are available drivers

I know that in the most recent kernals support for many Artheros chipsets has been included.

---

### Post by newbee70 on 2008-12-10
> **Beetlebum_007 said:**
> In reply to you earlier post - open terminal and enter lshw -C network this was my result;-

 description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:db:97:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.0.2 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
**  *-network UNCLAIMED**
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

Sorry for taking so long to get back to you as my connection was useless for a while!
Thanx for your help.
Beetlebum
** like this **

  *-network:0 UNCLAIMED                   <<<<<<<<<<<<<<<<<<<<<<<<<<<<
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10

[B]
no driver, including ndiswrapper, is trying to claim the card. This is bad, because you want ndiswrapper to claim it.
[/B]

hope this helps. 

but then I'm just a noob so take my thoughts with a grain of salt.

---

### Post by Beetlebum_007 on 2008-12-13
running the same command 'lshw -C network' now gets this result;-

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:db:97:b8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 ip=192.168.0.2 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:9c:05:e3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:f7:a7:5c:66:6a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I hasten to add I have upgraded to 8.10 intrepid in an attempt to solve my wireless problems without any success.
Thanx
Beetlebum_007

---

