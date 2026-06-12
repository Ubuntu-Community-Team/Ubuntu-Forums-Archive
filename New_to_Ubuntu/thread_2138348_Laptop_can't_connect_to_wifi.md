---
title: "Laptop can't connect to wifi"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by pingu2 on 2013-04-23
Hi I'm new to linux and running Ubuntu 12.04 from a usb 
my laptop doesent seem to be able to see any wifi networks any idea how to fix?
I will try to respond to any terminal result requests asap.
any help much apreciated.

---

### Post by Hodevah on 2013-04-23
If your able to go to the Menu and access System Settings>Hardware>Network. From there you can configure your wireless. 
As an alternative, you can also go through the Menu and go to Network or Network Connections. You should be able to access and configure your wireless from either of the above moves.

As an informational matter, you might want to post the output of the following:

```
lsusb
```

```
sudo lshw -C network
```

```
route -n
```

```
lsusb
```

Place everything into their seperate code tags for ease of reading.

---

### Post by pingu2 on 2013-04-24
hi, thanks for replying. i tried the two first options but I'm not sure what to do, the wireless seems to be configured but no wifi networks show up.
again thanks for helping, heres the code:
lsusb:
```
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 002: ID 1210:25f4 DigiTech 
Bus 002 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 
```


sudo lshw -C network
```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f4000000-f400ffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 00
       serial: 00:24:54:b7:bd:39
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.71 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f6000000-f6003fff ioport:3000(size=256)
ubuntu@ubuntu:~$ 
```


route -n
```
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
ubuntu@ubuntu:~$ 
```

lsusb:
```
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 002: ID 1210:25f4 DigiTech 
Bus 002 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$ 
```

---

### Post by grahammechanical on 2013-04-24
Network UNCLAIMED would indicate that either the Wireless adapter is turned off. This is sometimes controlled on a laptop by the keyboard or the wireless adapter has been switched off in Windows and so Ubuntu cannot switch it back on. Or, you need a driver.

When I run sudo lshw -C network on my machine I see this
>  configuration: broadcast=yes driver=rtl8187 driverversion=3.8.0-19-generic firmware=N/A ip=192.168.1.65 link=yes multicast=yes wireless=IEEE 802.11bg

There is nothing like that in your printout. Broadcast = yes indicates the the wireless adapter is broadcasting a signal to any available wireless access points. I have a Realtek wireless adapter. So, my driver is rtl8187.

You may need to install a driver. We usually do that from the Additional Drivers utility and we need an ethernet connection to the Internet. Even if you are able to install a wireless driver to a USB live session it will not be permanent. It will depend on the type of USB install that you have. Is it with persistence?

Regards.

---

### Post by Kopkins on 2013-04-24
Hi, can you post the output of the following commands? Please put the output in between code tags like this [noparse]```

```[/noparse]

It looks like you need the ath9k module which should be included with the kernel.

```

rfkill list

```
```

uname -a 

```

Then try ```
sudo modprobe ath9k
```

Then try connecting to wireless.

Good Luck,

Kopkins

---

