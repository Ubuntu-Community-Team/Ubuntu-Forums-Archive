---
title: "[SOLVED] Yet another Wireless problem"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-10-18
I left my laptop on and unplugged and left. When I returned, the battery had died and the laptop had switched off. I turned it on only to find that it was no longer detecting wireless networks at all. I tried disabling the drivers and re-enabling them, I tried reinstalling them, but I managed nothing. Why did this happen and what can I do to fix it?

---

### Post by Kobalt on 2008-10-18
You can find out information about your network interfaces using this command line:
```
sudo lshw -C network
```
It will tell you if the driver is effectively recognized, and which driver is used, etc.

---

### Post by Haruki-kun on 2008-10-18
> **Kobalt said:**
> You can find out information about your network interfaces using this command line:
```
sudo lshw -C network
```
It will tell you if the driver is effectively recognized, and which driver is used, etc.

I got this:
>   *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:74:73:e9
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:c4:22:c4:6e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


I hate to say it, but... I don't really know how to read it. What does it mean?

---

### Post by nothingspecial on 2008-10-18
Madwifi works for these cards

In system > administration > Hardware Drivers disable any wireless drivers (anything that says atheros)


Download the latest madwifi snapshot.


```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz
```

Unzip it

```

tar -xvf madwifi-hal-0.10.5.6-current.tar.gz
```


navigate to the extracted file

```

cd madwifi-hal-0.10.5.6-r3861-20080903
```

If you`ve not got the tools necessary for compiling get them


```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then compile it

```
sudo make
```

```

sudo make install
```

Load it

```

sudo modprobe ath_pci
```

Then to get it to load at boot do this

```
gksudo gedit /etc/modules
```

then copy and paste this to the bottom of that file

```

ath_pci
```

Save
Close
Reboot

---

### Post by Haruki-kun on 2008-10-18
Fixed! Thanks a lot! :)

---

### Post by nothingspecial on 2008-10-18
Cool
:guitar:

---

### Post by A1len on 2008-10-20
> **nothingspecial said:**
> 

If you`ve not got the tools necessary for compiling get them


```

sudo apt-get install build-essential linux-headers-$(uname -r)
```


I'm having this same problem. The trouble with me, I'm dual-booting Vista and Ubuntu, but ubuntu can't go onto the internet and for various reasons I don't have an ethernet connection. Is there a manual way to do it? Or some other way to do it? Thanks in advance.

---

### Post by A1len on 2008-10-20
actually, scratch my last post. 

lshw -c network =

Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

I = :confused:

EDIT: I'm gonna start a new thread for this one.

---

