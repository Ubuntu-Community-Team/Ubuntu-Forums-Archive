---
title: "Probably a dumb wireless problem"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Desidarius on 2008-07-14
I just installed kubuntu on my notebook (Dell Inspiron E1705) and when I went to use my wireless it won't turn on. The light stays off and when I go into the network settings it shows the card and all, but when I hit the button to activate it it immediately turns it back off (I'm using a thumb drive with Puppy Linux to connect right now). I feel like there should be some setting somewhere and it would let me turn it back on but I'm just not finding it. Also when I click on the active drivers thingy it only shows my display driver, but when I run the kubuntu live cd it shows the wireless driver.

edit: I was also searching the forums for help turning on wireless and found the "sudo lshw -C network" command and that turned up

  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:a7:bc:c1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:31:9f:72:48
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

so I don't know why that is disabled or how I can get it turned on, and I did try Fn-F2 just in case and nothing happened.

---

### Post by spiderbatdad on 2008-07-14
try installing bcm43xx-fwcutter from synaptic. There are mixed reviews as to whether that works better than ndiswrapper...either way you need one or the other as a driver for this card.

There are some good how-tos regarding ndiswrapper for the broadcom wireless card on this forum.

It may be a bit of a challenge to get wireless workking on this card, but do-able. Good luck.
[http://ohioloco.ubuntuforums.org/showthread.php?t=197102](http://ohioloco.ubuntuforums.org/showthread.php?t=197102)  #For ndiswrapper...also you'll need to add "ndiswrapper" to /etc/modules I didn't see that mentioned in the how-to. There may be better guides.

Guess I would try the bcm43xx-fwcutter first, as it is easiest to install.

---

### Post by OffAxis on 2008-07-14
here's a broadcom how to:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/)

and you can use
```

sudo ifup wlan0
```

```
sudo ifdown wlan0
```

to manually start or start your card.

---

