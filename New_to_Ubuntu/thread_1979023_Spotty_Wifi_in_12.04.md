---
title: "Spotty Wifi in 12.04"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by zanknits on 2012-05-12
SOLVED: [http://ubuntuforums.org/showthread.php?t=1783272](http://ubuntuforums.org/showthread.php?t=1783272)
(I used the instructions in the first post)

Hi all,

I've searched around, but haven't found anything to deal with this specific problem - I've upgraded to 12.04, and my wifi is incredibly hit or miss. Usually when I boot up, my wifi doesn't work - sometimes it'll work if I reboot the computer, sometimes it'll work if I go to the drivers section, turn off my broadcom driver, turn it on again, and reboot.

Here are the specs:
Dell inspiron with a broadcom driver, running 12.04
I've removed the bcwml-kernel thingy and tried to replace it with the b43 package that a few others were suggesting. I've also run all available updates.

sudo lshw -class network results:
```
  *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 1c:65:9d:22:2a:0f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.2.2 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: f0:4d:a2:4b:34:89
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.2.9 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)

```


lspci -v results
```


03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information: Len=78 <?>
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [13c] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-9d-ff-ff-22-1c-65
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, bcma, brcmsmac

04:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [180] Device Serial Number ff-4b-34-89-f0-4d-a2-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c

```


firmware-b43-installer is already the newest version.


What else can I do? This is a really annoying problem - I never know what's going to happen when I turn my computer on. 

Thanks guys!

---

### Post by zanknits on 2012-05-13
bump

---

### Post by ts3 on 2012-05-13
> **zanknits said:**
> Dell inspiron with a broadcom driver, running 12.04
I've removed the bcwml-kernel thingy and tried to replace it with the b43 package that a few others were suggesting. I've also run all available updates.

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl, bcma, brcmsmac

firmware-b43-installer is already the newest version.

A couple of comments based on your info.  

First, you say that you've removed the bcmwl kernel source but lspci -v above shows that the kernel driver in use is wl which is bcmwl so doesn't look like it's been removed.  Second, for your card BCM4313 (I have the same card by the way) wl is actually the driver that should work but it's important to remove other conflicting broadcom drivers.  

However, it seems that in 12.04 there've been some changes and for some BCM4313 cards it's the wl driver that works and for others it's the open source brcmsmac driver that works.  Take a look at post #73 in this thread [http://ubuntuforums.org/showthread.php?t=1967515&page=8](http://ubuntuforums.org/showthread.php?t=1967515&page=8) which explains how to try the two drivers and see which works.  

First however check that your card is exactly the same as the one post #73 refers to by running

```
lspci -nn | grep 0280
``` 

Post the results here and I'm sure one of the wireless gurus will step in to help.

Cheers

---

### Post by idoitprone on 2012-05-13
I assuming the above poster is correct

copy paste this command in terminal
```
sudo 'bash -c echo "blacklist bcma\nblacklist brcmsmac" >> /etc/modprobe.d/blacklistwifi.conf'
```This should work and you get a file in /etc/modprobe.d with the name blacklistwifi.conf

It should have the contents
```

blacklist bcma
blacklist brcmsmac
```and reboot

---

### Post by zanknits on 2012-05-13
Thanks so much! Here's lspci:
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

Which is exactly the same as the post you mentioned - so I'm gonna go through there and see if that fixes it, and then come back and tag this as Solved if it does.


Thank you!!!!

---

