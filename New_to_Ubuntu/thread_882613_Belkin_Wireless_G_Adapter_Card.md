---
title: "Belkin Wireless G Adapter Card"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by CosmicFlux on 2008-08-07
Hey,

I've just added a Belkin Wireless G network card to my system. Ubuntu doesn't seem to have noticed it automatically, do I have to download drivers for this product manually?

Cosmic

---

### Post by ibutho on 2008-08-07
You first need to determine what chipset the wireless card uses. You can do this by running Application -> Accessories -> Terminal and enter the commands below
```
sudo lspci | grep -i net
```
and
```
sudo lshw -C network
```
Post back the output.

---

### Post by CosmicFlux on 2008-08-09
OK,

The output of the first command chain is:
[COLOR="DeepSkyBlue"]
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:0e.0 Ethernet controller: Belkin Unknown device 700f (rev 20)[/COLOR]

And the second output was:

[COLOR="DeepSkyBlue"]*-network:0 UNCLAIMED   
       description: Ethernet controller
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: e
       bus info: pci@0000:00:0e.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32[/COLOR]

---

### Post by starcannon on 2008-08-09
It appears some versions of that chipset may be problematic:
[http://ubuntuforums.org/showthread.php?t=550334](http://ubuntuforums.org/showthread.php?t=550334)

though some have gotten them to work fine, try that thread, and see if anything helps, if not come back to this thread and we'll carry on from here.

---

### Post by augie48 on 2008-08-09
how do I subscribe to networking and wireless forum , it says I am in read only,

---

### Post by augie48 on 2008-08-09
I also have a Belkin wireless G USB Network adapter, ver 5000 I think I can learn what to do on network and wireless forum if I learn how to get posting priveleges

---

### Post by augie48 on 2008-08-10
02:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10
this is my first

this is my second

  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@0000:02:0b.0
       logical name: eth0
       version: 10
       serial: 00:13:46:31:12:7f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=208.51.232.200 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
rachel@rachel-desktop:~$ 02:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)

I think they refer to the Dlink not the belkin cannot find the chipset, the disk that came off the shelf with the wireless USB only works with windows

---

