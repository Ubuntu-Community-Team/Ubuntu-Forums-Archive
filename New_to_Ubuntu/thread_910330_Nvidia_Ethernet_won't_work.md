---
title: "Nvidia Ethernet won't work"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Matuku on 2008-09-04
My laptop appears to have a nvidia ethernet according to this:
```

 *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:65:62:99
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

```

But it doesn't seem to recognise when I plug in an ethernet cable; I read somewhere that the forcedeth driver isn't great but is there an alternative?

---

### Post by halitech on 2008-09-04
are you trying to connect with the wired or wireless connection primarily? can you post the output of```
ifconfig
```

---

### Post by Matuku on 2008-09-04
> **halitech said:**
> are you trying to connect with the wired or wireless connection primarily? can you post the output of```
ifconfig
```

The wireless connection itself is having lots of issues; I'm trying to get the wired connection up so that I can fix the wireless.

Here is ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1d:72:65:62:99  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81000 (79.1 KB)  TX bytes:81000 (79.1 KB)

```

---

### Post by halitech on 2008-09-04
try ```
sudo dhclient eth0
``` and post back any errors or messages

---

### Post by Matuku on 2008-09-04
Here it is:
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1d:72:65:62:99
Sending on   LPF/eth0/00:1d:72:65:62:99
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

The weird thing is if the ethernet is connected before starting up the laptop it appears to connect but then doesn't allow any internet access; if it is connected after the laptop is already on then it doesn't even seem to connect.

---

### Post by halitech on 2008-09-04
> **Matuku said:**
> Here it is:
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1d:72:65:62:99
Sending on   LPF/eth0/00:1d:72:65:62:99
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

The weird thing is if the ethernet is connected before starting up the laptop it appears to connect but then doesn't allow any internet access; if it is connected after the laptop is already on then it doesn't even seem to connect.

try rebooting with the cable in then and do the ifconfig and see what IP address it is giving you

---

### Post by Matuku on 2008-09-04
ifconfig now gives:
```

eth0      Link encap:Ethernet  HWaddr 00:1d:72:65:62:99  
          inet6 addr: fe80::21d:72ff:fe65:6299/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6081 (5.9 KB)
          Interrupt:222 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:72:65:62:99  
          inet addr:169.254.6.182  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:222 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84364 (82.3 KB)  TX bytes:84364 (82.3 KB)

```

"sudo dhclient eth0" now gives:
```

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1d:72:65:62:99
Sending on   LPF/eth0/00:1d:72:65:62:99
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And "lshw -C network" now gives:
```
*-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:65:62:99
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

```

---

### Post by Matuku on 2008-09-04
*bump*

---

### Post by halitech on 2008-09-04
so its not actually giving you an ip address on reboot. Do you know the IP address of the router? maybe we can try setting a manual IP address and see if it works

---

### Post by Matuku on 2008-09-04
> **halitech said:**
> so its not actually giving you an ip address on reboot. Do you know the IP address of the router? maybe we can try setting a manual IP address and see if it works

Unforunately not; how would I go about finding it out? What I attempted just know was to disconnect this PC and use the IP address that had been given to it from the router and enter that information manually into the laptop, but to no avail.

---

### Post by Dougie187 on 2008-09-04
What is the ip address on the computer that you make these posts from?

---

### Post by Matuku on 2008-09-04
> **Dougie187 said:**
> What is the ip address on the computer that you make these posts from?

192.168.1.198 which I tried to assign to the laptop just now, as I said. I need to get one of either the wired or wireless working before I can fix the other, a real Catch22.

---

### Post by halitech on 2008-09-04
is the computer thats working now a Windows based computer or Linux?

also, you say you tried entering the info, what exactly did you enter and where?

---

### Post by Matuku on 2008-09-04
> **halitech said:**
> is the computer thats working now a Windows based computer or Linux?

also, you say you tried entering the info, what exactly did you enter and where?
It's running Ubuntu as well. I entered the IP address, Subnet mask and Gateway address as a static IP address on the manual configuration of the wired connection on the laptop.

---

### Post by halitech on 2008-09-04
try adding the info manually here

```
gksu gedit /etc/network/interfaces
```

---

### Post by Matuku on 2008-09-04
It appears to be there already, it reads:
```

auto lo
iface lo inet loopback




iface eth0 inet static
address 192.168.1.168
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

---

### Post by halitech on 2008-09-04
> **Matuku said:**
> It appears to be there already, it reads:
```

auto lo
iface lo inet loopback




iface eth0 inet static
address 192.168.1.168
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

it also seems to think it should use DHCP. I would remove the static info from there and from the network manager and see if it will pick up an IP address
here is mine with using the Network manager
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
```

---

### Post by Matuku on 2008-09-04
So delete anything to do with eth0 except the "auto eth0" from the file and then set the configuration to DHCP from network mananger?

---

### Post by halitech on 2008-09-04
we can try that or if you want to use Network Manager, delete the auto eth0 as well

---

### Post by Matuku on 2008-09-04
No luck; I tried both DHCP and just plain roaming mode; roaming mode will "connect" to the network if the cable is in on bootup but all the assigned values (IP address, subnet mask, etc) all have 0.0.0.0

---

### Post by halitech on 2008-09-04
did you try in the terminal
```
sudo dhclient eth0
```

---

### Post by Matuku on 2008-09-04
I have tried dhclient on both now, but to no avail; they give the same readout as before.

---

### Post by halitech on 2008-09-04
ok, time to take drastic measures now. Can you disconnect the router and go direct to the modem and do the ```
sudo dhclient eth0
``` again

---

### Post by Matuku on 2008-09-04
I believe the modem and router we have are one and the same; at least, the router is connected directly to the phone line socket in the wall.

---

### Post by halitech on 2008-09-04
ok, power it down, shut the computer down, then power up the modem/router, wait for the lights to finish blinking (about 45 seconds) then start the computer back up.

---

### Post by Matuku on 2008-09-05
I tried it and it didn't work so I attempted something even more drastic; I redownloaded the .iso and just installed it all again and now, it works!

EDIT: Turns out I had an 8.04 disk but 8.04.1 fixed the problem, so upon downloading and installing from the 8.01 ISO, the problem was fixed.

---

