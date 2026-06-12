---
title: "Wifi and wired connections not working under 12.10"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by MOG34 on 2012-10-22
I installed 12.10 the other day on my macBookPro 5,5 and have been having some problems setting up the wifi drivers.

I tried to connect to the internet with an ethernet cable but that wasn't recognized either. I managed to install fakeroot, dkms and bcmwl-kernel-source from the install disk. However, when I was installing bcmwl-kernel-source i got, FATAL: Module wl not found.

I'm kind of stuck here. I did an lspci and I'm using a Broadcom 4322 802.11 STA driver. Any help would be appreciated.

---

### Post by daslinkard on 2012-10-22
What happens when you run the following sudo commands:

```
sudo apt-get remove --purge bcmwl-kernel-source
``` ```
sudo modprobe -r wl
``````
 sudo apt-get install linux-firmware-nonfree
```

Then reboot your system
```
sudo reboot
```

---

### Post by MOG34 on 2012-10-23
Thanks for the reply. 

sudo apt-get remove --purge bcmwl-kernel-source
This removed all of my DKMS Modules.

sudo modprobe -r wl 
This returned FATAL: Module not found

 sudo apt-get install linux-firmware-nonfree
This returned E: Unable to locate package linux-firmware-nonfree
(I  don't have the install disk on me to see if it's in there. I'm not sure  if that would make a difference but I can get it and try again later today)

---

### Post by Bucky Ball on 2012-10-23
> **MOG34 said:**
> (I  don't have the install disk on me to see if it's in there. I'm not sure  if that would make a difference but I can get it and try again later today)

Yes, try that, as:

```
sudo apt-get install linux-firmware-nonfree
```requires you to be online ...

I'm not completely sure but think the b43-fwcutter and firmware-b43-installer are on the install CD now. You might want to check that as sometimes they work when the STA drivers don't and vice versa.

Could you post the output of:

```
sudo lshw -C network
```

---

### Post by MOG34 on 2012-10-23
I found my install disk and tried
 ```
sudo apt-get install linux-firmware-nonfree
```
```
sudo apt-get install firmware-b43-installer
```
Both threw E: Unable to locate package errors

I already have b43-fwcutter installed.

my output from ```
sudo lshw -C network
``` is

*-network
[INDENT]description: Ethernet interface
product: MCP79 Ethernet
vendor: NVIDIA Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: b1
serial: 00:26:b0:d7:60:60
capacity: 1Gbit/s
width: 32 bits
clock: 66MHz
capabilities: pm msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
resources: irq:44 memory:d3486000-d3486fff ioport:21e0(size=8) memory:d3489000-d34890ff memory:df3489300-d348930f[/INDENT]
*-network UNCLAIMED
[INDENT]description: Network Controller
product: MCP79 BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
rescources: memory:d3200000-d3203fff[/INDENT]

---

### Post by MOG34 on 2012-10-23
I went into the Additional Drivers tab under software sources and it says that my Wireless LAN Controller is using Broadcom 802.11 Lixux STA wireless driver source from bcmwl-kernel-source.

If I just removed bcmwl-kernel-source, could it cause a problem?

---

### Post by Bucky Ball on 2012-10-23
Don't do that as your output from the code I gave you doesn't indicate that at all. I suggest disabling that STA driver in Additional Drivers, rebooting and see what happens. If nothing, enable it again and see what happens. Without a wired connection it is hard.

```
*-network UNCLAIMED[INDENT]description: Network Controller
product: MCP79 BCM4322 802.11a/b/g/n Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
rescources: memory:d3200000-d3203fff[/INDENT]
```It's not showing any driver. Your ethernet is, though. 

```
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64
```I'm wondering if  you have everything set up correctly in Network Manager. Are you going  through a router? Is that serving you an IP address or are you using a  static one? 

Open Network Manager and make sure 'Connect Automatically' is ticked for the cable (and wireless for that matter).

PS: Just out of interest ... was all this working in your last install? If so, did you have any reason to install a very new release which is bound to be buggy around the edges? Okay if you want to report bugs and and learn how to fix some but for general day to day computing I would steer clear until it becomes a little more stable.

---

### Post by MOG34 on 2012-10-26
> PS: Just out of interest ... was all this working in your last install? If so, did you have any reason to install a very new release which is bound to be buggy around the edges? Okay if you want to report bugs and and learn how to fix some but for general day to day computing I would steer clear until it becomes a little more stable.

This is actually my first linux install. I guess I don't really have any good reason to be trying 12.10 over 12.04 or another version. I just sort of grabbed the most recent Ubuntu without giving it much thought. Usually I don't mind working through these kinds of problems. I've already learned a ton more about how my hardware is set up and I never learn too many shell commands. That said, I think this has reached the point where it is more trouble than it's worth. I hate giving up, but I'll take a crack at it with 12.04. 

Thanks for all your help.

---

