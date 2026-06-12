---
title: "[SOLVED] Wireless Madwifi and  Ndiswrapper"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by jasonruk on 2008-09-09
Sorry I put this in the wrong place to start with.

Hi there, this is my first time!

Thanks to all the threads here about acer_fancontrol I have that working well now.

My problem though is that old chestnut, wireless

I have madwifi installed and it runs but it runs at about a tenth the speed of the windows wifi.

Two things
1. Can I speed this up or do I need to wait for a new version of the driver?
2. How can I now get ndiswrapper to work.

Some background.

I started out with ndiswrapper using net5211.inf and it worked fine, was quick but sometimes didnt connect.  Then it stopped connecting altogether.

I installed madwifi, you know this bit.

I've tried getting rid of madwifi but it still stays unless I remove the hardware driver in Applications (even when selecting do not use in System>Admin and blacklist the ath_pci and hal.

After doing this and adding ndiswrapper I simply cannot connect to the internet, (there never even appears a green dot) but I can see the wireless network plus others in the local area.

OK, so a few thing I think are needed.  I have an acer aspire 5315.

05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)



 *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:df:05:d2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:a1:7e:91
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.2 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

Also on my lsmod output, it looks like this even after deleting the hardware drivers and blacklisting them.

ath_pci               250176  0 
wlan                  254240  1 
ath_hal               333200  1 ,ath_pci
.....
ndiswrapper                   0

Could I have some help either speeding up madwifi or completely getting rid of it to use ndiswrapper and making it work.

 I have most recent ubuntu install with hardy heron

---

