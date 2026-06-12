---
title: "PCI Card Not working - help asap"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Gennn89 on 2008-10-20
OMFG I've been on this darn laptop all morning trying to make my bloody wireless work please someone tell me how to do this

im using a dell inspiron 1525 with apparently a broadcom card or something rather and following the guides ive come up with 14e4:4315 as the pci id. someone please tell me how to get this stupid thing working im so tired of looking at blogs, guides and calling numbers ><

---

### Post by panhandle on 2008-10-20
ok, open a terminal, type this command, and post the results here.

> lshw -C network

This will give us the needed specs on your NIC.

---

### Post by Gennn89 on 2008-10-20
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:f2:3e:ee
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=208.98.208.3 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

***What does it mean by super-user?***

---

### Post by beno1990 on 2008-10-20
If you're using a Dell Inspiron 1525 you might need to install the backports drivers.

I'm assuming you're using a wired connection to make that post?

If so, go to System -> Administration -> Software sources -> "updates" tab

Check the backports button.

Open a terminal and type:

```

sudo apt-get update

```

And then

```

sudo apt-get install linux-backports-modules-hardy

```

And then reboot, your wireless and webcam (if your 1525 has one) should work, if you're using the in-built wireless card.

---

### Post by Iowan on 2008-10-20
> **Gennn89 said:**
> ***What does it mean by super-user?***That'd be "root" - or run "sudo lshw -C network"... seems to work, anyway.

---

### Post by Gennn89 on 2008-10-20
No i still havent got a connection available so what do i do now?

---

### Post by Gennn89 on 2008-10-20
*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:f2:3e:ee
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

this is the current outcome when not connected to the internet (using the computer in question) via ethernet cable

I installed the two upgrades recommended but still nothings changed in my network utilities (meaning network, network tools, and network icon in corner)

---

### Post by beno1990 on 2008-10-20
The kernel is only detecting the wired ethernet controller (eth0). It is the internal wireless card you're trying to get working, and not an external one, right? I need that clarifying, because if it's an internal card those modules should work for the Inspiron 1525.

---

### Post by Gennn89 on 2008-10-21
Internal wireless card. Right. I have a usb wireless adapter but its a no-dice with that either and i'd rather have a wireless connection from my computer. the card is probably better anyway... so the codes not working, what do i do?

---

