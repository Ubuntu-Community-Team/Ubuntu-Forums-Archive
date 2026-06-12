---
title: "I can't get this older pc to connect to internet !"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by Floridafox on 2008-10-24
Hi all,


I need a little guidance, I've been surfing and trying to get this older PC online.  Its an older e-tower 566ir running 8.04.  Comcast cable internet with Motorola SB5101 (surfboard).  When I installed the live disc it said that DHCP was not present on the PC, so I am trying to configure to get connected to the internet via static IP.  This 566ir is a second PC.  When the pc first booted it had no info in terms of ip address, mask, gateway etc, nothing.  I've tried rebooting the cable modem, nothing

I'm physically switching from this computer to the 566ir in terms of the Ethernet connection, I'm running Ubuntu 8.04 on my newer E-machine, but it must have the DHCP protocol because it was just plug and play.

This 566ir had windows me on it before I installed 8.04.  Would it be easier for me to get a 5 port router (wired) ?  Would this help make the connection to the internet any easier ?

Is there any way I can install DHCP on this older PC ?

It wont ping, the modem is showing PC activity, the network card on the PC is lighting up, I've rebooted the Cable modem loads of times.

When I switch back to my E-machines, everything works fine..

I've tried to copy the connection info from my E-machine to see if will take in the 566ir.. Nada.

Help would be great.. I'm going for a beer !

---

### Post by Floridafox on 2008-10-24
Just to clarify, I've got the IP address, and I have the gateway address, i'm using the same genmask / mask info from my E-machines.  Same with the DNS etc etc.  I tried it with or without.. Nothing.

---

### Post by Iowan on 2008-10-24
I'm a bit confused - dhclient should be on the CD. Being unfamiliar with the Comcast cable internet with Motorola SB5101 (surfboard), I suppose it's possible that the interface needs a driver added/updated.  Try **ifconfig -a** for information on the interfaces, Also check **lspci**.

---

### Post by cariboo on 2008-10-24
The light on your network card just means it is connected, the only time it won't come iis if the card it self is totally dead, the first thing to check is your network card to see if it has been detected and the module installed to do this type in a terminal:

```
sudo lshw -C network
```

you should get an output something like this:

```
description: Ethernet interface
       product: MCP51 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 14
       bus info: pci@0000:00:14.0
       logical name: eth0
       version: a3
       serial: 00:16:17:9c:84:b5
       size: 100000000
       capacity: 1000000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
```

If it is detected and a module installed, make sure /etc/network/interface looks something like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```


now you should be reaady to connect, in a terminal type:

```
sudo dhclient eth0
```

Jim

---

### Post by oldsoundguy on 2008-10-24
off hand, would say that the drivers for the ethernet have not been installed or installed properly.

I use Comcast and have had no issues with connectivity either wired or wireless.  BUT I use D-Link 520G wireless cards and either 3com or D-Link ethernet (NIC) cards.  Currently I have 4 Linux desktops, two XP desktops and two Windows Mobile PDA/GPS units that can and do access the network .. only two .. an XP box and an Ubuntu Gutsy box are hard wired into the D-Link router. That in turn runs to the RCA Modem. 
(BTW .. Comcast is replacing all of the surfboard units with RCA so that they can increase the speed on line .. call them and get the new one!)

---

### Post by Floridafox on 2008-10-25
I think you might be right, I've burned Xununtu and I'm going to try and see if that works, I hioe it has the DHCP.  Thanks for your help.  I'm new to Ubuntu but I love it, I'm a lifer for now on !

---

### Post by Francewhoa on 2008-12-27
Rebooting the cable modem worked for me. [Details and more solutions can be found here.]("http://ubuntuforums.org/showpost.php?p=6443197&postcount=3")

---

### Post by MrWES on 2008-12-27
Exactly... My son is using Comcast Cable without a router, just the cable modem and when he switches the cat5 cable from his computer to his PS3 he must reset the cable modem...hard reset with the small recessed reset button in the back of the cable modem. Appartently, the cable modem stores the MAC address of the NIC and you have to reset that to get it to work with another NIC. PITA, but it works.

Bill

---

### Post by gTinker on 2008-12-27
> **MrWES said:**
> Exactly... My son is using Comcast Cable without a router, just the cable modem and when he switches the cat5 cable from his computer to his PS3 he must reset the cable modem...hard reset with the small recessed reset button in the back of the cable modem. Appartently, the cable modem stores the MAC address of the NIC and you have to reset that to get it to work with another NIC. PITA, but it works.

Just to correct this misinterpretation about the modem. It's the server at the ISP that "remembers" the MAC it is willing to talk to because it has authenticated that interface as belonging to a valid user. I imagine that he has to re-enter his username and password as well as resetting the modem when he switches. 

For the OP Floridafox, many people set these up with a router and a persistent connection to the router's MAC (or clone, on the router, the MAC from the working computer). In a configuration like this, the router stays connected to the modem and does the DHCP (the server part) for your LAN and the NAT for the various computers connected to the router. 

Don't become confused, there are two parts to DHCP, the server which hands out the addresses and the client that requests the address from the server.

---

