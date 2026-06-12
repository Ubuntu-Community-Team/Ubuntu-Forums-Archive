---
title: "Wireless for complete novice."
date: 2008-09-21
forum: New to Ubuntu
---

### Post by nathanr on 2008-09-21
Hello

I've been pointed here after trying to rectify a problem with my laptop. The other day I installed Ubuntu onto my laptop ( HP Pavilion dv6000) which already has Vista. Now this is the problem on Vista (such as now) wireless generally works fine and a blue light is lit by the wireless switch to show it is working. However on Ubuntu it is orange and wont work and will not find any networks to connect to. I know there are several including my own one in range. I've done a search on the forum and found some stuff relating to it, but it goes completely over my head. Are there any guides for morons ?

Thanks in advance ( sorry if i have broken any rules )
Nathan

---

### Post by nothingspecial on 2008-09-21
First you need to find out what your wireless card is.

Open a terminal accessories > terminal in your menu and copy and paste 
```
lspci -v
``` into it 
Then post the results back here.

---

### Post by nathanr on 2008-09-21
Copied into Word and came up as 7 pages.
I assume you only want this part
> 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02) 
	Subsystem: Hewlett-Packard Company Unknown device 1375 
	Flags: bus master, fast devsel, latency 0, IRQ 19 
	Memory at f6000000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 
Thanks again

---

### Post by nothingspecial on 2008-09-21
Ethernet controller`s the bit I want.

Try and get a wired connection to your laptop in Ubuntu
It`s a lot easier if you do

---

### Post by nathanr on 2008-09-21
> :0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2) 
	Subsystem: Hewlett-Packard Company Unknown device 30cf 
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 508 
	Memory at f6488000 (32-bit, non-prefetchable) [size=4K] 
	I/O ports at 30f8 [size=8] 
	Memory at f6489c00 (32-bit, non-prefetchable) [size=256] 
	Memory at f6489800 (32-bit, non-prefetchable) [size=16] 
	Capabilities: <access denied>

That it ?

---

### Post by nothingspecial on 2008-09-21
Sorry lets try a different tack

```
lshw -C network
```

Post results please

---

### Post by anewguy on 2008-09-21
Did a Google search of Ubuntu BCM94311MCG and several things were returned.  The following thread explains how to get it working.  Don't be concerned it's not the same laptop - it's the wireless adapter that's important at this point.

[http://zugaldia.wordpress.com/2008/04/30/setting-up-the-broadcom-bcm94311mcg-in-ubuntu-804/]("http://zugaldia.wordpress.com/2008/04/30/setting-up-the-broadcom-bcm94311mcg-in-ubuntu-804/")

Dave :)

---

### Post by nothingspecial on 2008-09-21
What we are trying to do is find out exactly what your wireless card is.

Then we are going to download the windows xp drivers and use them in an app called ndiswrapper that will use windows drivers in linux.

If you can get a wired connection in your menus system > administration > synaptic package manager.

Click search and type ndis

Scroll down until you find  ndisgtk ndiswrapper-common and ndis-utils-1.9(might be a different number). Check the boxes next to them and install them using the apply button.

Download the windows drivers and use ndisgtk (found in your menus somewhere, it`s called windows drivers or something like that) to install them. ie place the .inf and .sys files.

---

### Post by nathanr on 2008-09-21
> **nothingspecial said:**
> Sorry lets try a different tack

```
lshw -C network
```

Post results please

> nathan@nathan-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: MCP67 Ethernet 
       vendor: nVidia Corporation 
       physical id: a 
       bus info: pci@0000:00:0a.0 
       logical name: eth0 
       version: a2 
       serial: 00:1b:24:81:33:2d 
       width: 32 bits 
       clock: 66MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes 
  *-network 
       description: Network controller 
       product: BCM94311MCG wlan mini-PCI 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       version: 02 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=b43-pci-bridge latency=0 module=ssb 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:00:00:1a:73:94 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 

Just for sake of doing.


And thanks Dave I shall give it ago.

---

### Post by nothingspecial on 2008-09-21
> **nathanr said:**
> Just for sake of doing.

Sorry 1st post [SIZE="3"]was[/SIZE] the relevant one but I`m trying to work here also and my kids are driving me nuts.:oops::D

---

