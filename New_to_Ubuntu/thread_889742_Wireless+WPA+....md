---
title: "Wireless+WPA+..."
date: 2008-08-14
forum: New to Ubuntu
---

### Post by japelj on 2008-08-14
Hello!

I recently get myself new version of Ubuntu (8.04). Now, as many before me, I have a problem establishing wireless connection. First I taught, I should get ndiswrapper, drivers ... well, you know the story. But now I think I have a problem concerning WPA. I folowed instructions ([https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)) and came to the point, where I should find connection to the router. The instructions sent me here

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=(wpa](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=(wpa))

and now I ask you: are these instructions good for the new version.

Also, before I move forward, I'll send you results from when I enter 

sudo lshw -C network

in terminal. Is there everything OK, or not?


 *-network               
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:29:86:42:ae
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-2 latency=0 link=no module=e1000 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:00:00:21:00:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by darrelljon on 2008-08-27
I think your wireless network is disabled.

---

### Post by Tom--d on 2008-08-27
> **darrelljon said:**
> I think your wireless network is disabled.

post the outcome of,
```
iwlist wlan0 scan
```

---

