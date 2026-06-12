---
title: "Cannot connect to known networks and archive manager issue."
date: 2012-12-02
forum: New to Ubuntu
---

### Post by Ray Huang on 2012-12-02
Good afternoon,  I am new to Ubuntu and downloaded 12.10 in a Mac as a double boot using Refit.

I cannot see my access point using a Lynksis e1200 router which is seen by all other macs and PC's in the house.

 I have read many posts and I cannot figure it out. I deleted and reinstalled Ubunto OS today as well.  One post suggested using a Windows Installation, but anything I try to install from CD or download I get this error:

"An error occurred while loading the archive"  making it impossible to try anything further.


Ethernet work fine though. I'd appreciate any help form a patient user.

TIA,
Ray

---

### Post by gandaran on 2012-12-02
for the wireless problem post the wireless card info, you may need to install drivers first.
```
sudo lshw -C network
```
running this code in terminal will get the hardware info

---

### Post by Ray Huang on 2012-12-02
If it helps I ran that in Terminal and it came up with only asking for my password, no information following. My admin password does not work.


> **gandaran said:**
> for the wireless problem post the wireless card info, you may need to install drivers first.
```
sudo lshw -C network
```
running this code in terminal will get the hardware info

---

### Post by Ray Huang on 2012-12-02
Sorry, I somehow got it right this time:

       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:26:4a:07:09:de
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:44 memory:d3486000-d3486fff ioport:21e0(size=8) memory:d3489000-d34890ff memory:d3489300-d348930f
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:23 memory:d3200000-d3203fff

---

### Post by Ray Huang on 2012-12-02
Results for iwconfig:


lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by Ray Huang on 2012-12-02
More info:

lspci -nn | grep 0280:

03:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

Does this mean that ubuntu sees my wireless card? Now how do I turn it on?

TIA,
Ray

---

### Post by Ray Huang on 2012-12-02
SOLVED: I went to the software center and downloaded additional drivers. I activated the Broadcom STA driver and immediately I had wireless.:KS

---

