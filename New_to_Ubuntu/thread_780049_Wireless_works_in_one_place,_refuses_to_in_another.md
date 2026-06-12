---
title: "Wireless works in one place, refuses to in another?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Forcestar on 2008-05-03
Hey all-

I've been using Dapper on my oooold Dell Latitude C610 for a while, and it's been quite good. Recently, though, I ran into a problem.

I just moved from an apartment with a wireless connection. My wireless there worked fine, but when I moved to another place and tried to connect there, I was out of luck. After some tinkering with the Gnome Wireless applet, I got it to acknowledge the network, put in the WEP key, all that. IT shows that it's connected (the little computer icon on the tray flashes occasionally, the strength bars are all lit up) but I can't access the internet. I know there -is- net, because there are others who are using it just fine, but I can't seem to get any. Help please? I can paste terminal excerpts, just unsure what to post really :P

---

### Post by spiderbatdad on 2008-05-03
run ifconfig, then sudo ifup eth1
maybe that will prod it to start...sometimes works on my friends old HP wireless with pcmcia card.

---

### Post by Forcestar on 2008-05-03
Fraid that didn't work. All I got was:

> ifup: interface eth1 already configured

I booted up firefox after and tried to access Google, no dice.

If it helps, when I right-click the icon and click "Properties", it shows that it has received no packets, but it has sent 331 (!!!)

---

### Post by Forcestar on 2008-05-03
Any chance I could get an answer? I can paste anything that are necessary, I just need to know what you want.

---

### Post by spiderbatdad on 2008-05-03
well, why dont you paste: ```
sudo lshw -C net
```

seems like mainly config setting problem, as it works elsewhere...are you set to roaming?

---

### Post by NIT006.5 on 2008-05-03
FYI, to get the ifup command to work, you could append the --force option to the end, which should bring the interface up again even if its already configured. 

I have had quite a few issues with wireless and haven't found any decent solutions yet either, but nothing quite like this problem.

---

### Post by spiderbatdad on 2008-05-03
> **NIT006.5 said:**
> FYI, to get the ifup command to work, you could append the --force option to the end, which should bring the interface up again even if its already configured. 

I have had quite a few issues with wireless and haven't found any decent solutions yet either, but nothing quite like this problem.

Indeed. I left that out...also runing like this:```
sudo ifdown eth1
sudo ifup eth1
```

---

### Post by Forcestar on 2008-05-03
Had to type this in by hand as my flashdrive with the paste file isn't working... but here yah go!
> sudo lshw -C net
	*-network DISABLED
description: ethernet interface
product: 3c905C-TX/TX-M [Tornado]
endor: 3Com Corporation
physical id: 0
bus info: pci@02:00.0
logical name: eth0
version: 78
serial: 00:06:5b:d5:be:Ib
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=half link=no multicast=yes port= MII speed=10MB/s
resources: ioport:ec80-eff iomemory:f8fffc00-f8fffc7f irq:11
*-network
description: TrueMobile 1150 Series PC Card
product: Version 01.01
vendor: Dell
physical id: 0
slot: Socket 2
resources: irq: 5
*-network
description: Wireless interface
physical id: 2
logical name: eth1
serial: 00:02:2d:44:e2:ab
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Lucent/Agere6.16 link=yes multicast=yes wireless =IEEE 802.11b
nathan@nathan-laptop:~sudo ifdown eth1
Internet Systems Consortium DHCP Client V3.-3
Copyright 2004-2005 Internet Systems Consortium.
All rights reservted.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:02:2d:44:e2:ab
Sending on LPF/eth1/00:02:2d:44:e2:ab
Sending on Socket/fallback

DHCPRELEASE on eth1 to 192.168.50.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

nathan@nathan-laptop:~$ sudo ifup eth1

Internet Systems Consortium DHCP Client V3.-3
Copyright 2004-2005 Internet Systems Consortium.
All rights reservted.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:02:2d:44:e2:ab
Sending on LPF/eth1/00:02:2d:44:e2:ab
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18

No DHCPOFFERS received.
No working leases in persistent database - sleeping.


---

