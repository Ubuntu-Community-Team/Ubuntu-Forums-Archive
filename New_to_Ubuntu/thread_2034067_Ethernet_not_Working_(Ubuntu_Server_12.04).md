---
title: "Ethernet not Working (Ubuntu Server 12.04)"
date: 2012-07-27
forum: New to Ubuntu
---

### Post by Banana937 on 2012-07-27
Hey. I'm pretty new to Linux. I've messed around with Ubuntu Desktop with a dual-boot on my laptop, but never gotten into the command line and everything. I recently built a server that I'm using to host Minecraft, teamspeak, and LAMP, and everything was going well until last night. I was almost done setting up Minecraft when I had to leave for dinner, and when I got home, the power had obviously surged, because the server was off. I turned it back on, logged in, and then attempted to connect via SSH from my laptop. I realized it didn't work, so I headed over to the router and noticed that the light was green for the ethernet port I was using (green means plugged in but not connected, blue means connected). I unplugged the router and plugged it back it, only to find that this didn't help.

**tl;dr:** My server isn't connecting to the internet (via ethernet) after a power surge.

eth0 doesn't show up in "ifconfig", either. I just need this fixed. Does anyone know how to fix it?

---

### Post by papibe on 2012-07-27
Hi Banana937. Welcome to the forums ):P

Try running this:
```
sudo service networking restart
```
If that doesn't work, please post the result of these commands:
```
lspci -nnk | grep -iA2 eth

sudo lshw -C network
```
Regards.

---

### Post by Banana937 on 2012-07-27
> **papibe said:**
> Hi Banana937. Welcome to the forums ):P

Try running this:
```
sudo service networking restart
```
If that doesn't work, please post the result of these commands:
```
lspci -nnk | grep -iA2 eth

sudo lshw -C network
```
Regards.

I tried restarting the networking, and I got the error:
```
stop: Unknown instance:
networking stop/waiting
```

When I did the "lspci" command, I got:
```
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
Subsystem: Giga-byte Technology Device [1458:e000]
Kernel driver in use: atl1c
```

And for the "lshw -C":
```
*-network DISABLED
description: Ethernet interface
product: AR8151 v2.0 Gigabit Ethernet
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@000:02:00.0
logical name: eth0
version: c0
serial: 50:e5:49:d0:9e:9e
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
resources: irq:18 memory:fddc000-fddfffff ioport:df00(size=128)
```

---

### Post by papibe on 2012-07-27
Try enabling you eth0:
```
sudo ifconfig eth0 up
```
and then again:
```
sudo service networking restart
```
If that doesn't work, please post the result of this command:
```
cat /etc/network/interfaces
```
Regards.

---

### Post by Banana937 on 2012-07-27
> **papibe said:**
> Try enabling you eth0:
```
sudo ifconfig eth0 up
```
and then again:
```
sudo service networking restart
```
If that doesn't work, please post the result of this command:
```
cat /etc/network/interfaces
```
Regards.

No luck, got the same unknown instance error. As for the interfaces file:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

iface eth0 inet static
    address 192.168.1.130
    gateway 192.168.1.1
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
```

---

### Post by papibe on 2012-07-27
Edit your /etc/network/interfaces so that the commented line:
```
#auto eth0
```
Is un-commented, and it looks like this:
```
auto eth0
``` 
Restart.

Let us know hot it goes.
Regards.

---

### Post by Banana937 on 2012-07-27
> **papibe said:**
> Edit your /etc/network/interfaces so that the commented line:
```
#auto eth0
```
Is un-commented, and it looks like this:
```
auto eth0
``` 
Restart.

Let us know hot it goes.
Regards.

Thank you very much, it seems to be working now. I just realized I have to re-forward all of my ports, though. Uggh.

Thank you for your time :P

---

### Post by papibe on 2012-07-27
:D Great!

Please mark the thread as solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

