---
title: "Problems with wireless configuration"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by QuizasQuizas on 2008-07-02
Hello, all!
First off, I will readily admit that I am now in over my head. I just installed a new hard drive on my laptop and I am running Hardy, but my wireless card is no longer being recognized (on the first hard drive, Hardy recognized my wireless card with no disputes; worked right out of the box). I have also downloaded [Wifi-Radar]("http://wifi-radar.systemimager.org/"), but it won't do me any good as long as "iwconfig" is telling me there's no "wlan0" present. Going to System > Administration > Hardware Testing, it says I've got an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01). I'm not sure how compatible this card should be and what I should do to make these things work.

I have no idea what I'm doing and I've scoured Google for several guides and possible solutions, but I am now completely lost. Any input will be greatly appreciated, and thank you.

---

### Post by caljohnsmith on 2008-07-02
> **QuizasQuizas said:**
> Hello, all!
First off, I will readily admit that I am now in over my head. I just installed a new hard drive on my laptop and I am running Hardy, but my wireless card is no longer being recognized (on the first hard drive, Hardy recognized my wireless card with no disputes; worked right out of the box). I have also downloaded [Wifi-Radar]("http://wifi-radar.systemimager.org/"), but it won't do me any good as long as "iwconfig" is telling me there's no "wlan0" present. Going to System > Administration > Hardware Testing, it says I've got an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01). I'm not sure how compatible this card should be and what I should do to make these things work.

I have no idea what I'm doing and I've scoured Google for several guides and possible solutions, but I am now completely lost. Any input will be greatly appreciated, and thank you.
If your wireless card worked before with Hardy "out-of-the-box", then maybe for some reason the madwifi drivers didn't get loaded for your card this time around. Try doing the two following commands:
```
sudo modprobe ath_pci
sudo modprobe wlan_scan_ap
```
If that doesn't get your wireless card to show up with iwconfig, then post the output of "sudo lshw -C network" and we could go from there.

---

### Post by QuizasQuizas on 2008-07-02
This is what I get from "sudo lshw -C network":

```
 *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:d7:55:7c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.96 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
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

```

---

