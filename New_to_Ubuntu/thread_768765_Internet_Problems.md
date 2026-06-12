---
title: "Internet Problems"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by asakurax on 2008-04-26
A friend of mine tried to install Gutsy when it came out, and the internet didn't work almost completely. the ICQ protocol via Pidgin worked, and some webpages, but mostly, nothing worked. Now he waited for Hardy to come out, and he's experiencing the same problems.

Hmph
He just told me that on Fiesty everything worked fine, but he doesn't wanna use it because of the low NTFS support

---

### Post by firecat53 on 2008-04-26
Need more information about what's specifically not working (which web pages do and don't work), what kind of hardware, etc, before anyone can help you!

Scott

---

### Post by Michael.Godawski on 2008-04-26
Please post the output of these terminal commands. It is hard to make a suggestion without knowing some facts:

```
lspci

sudo lshw -C network

iwconfig
```

---

### Post by asakurax on 2008-04-27
lspci

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:03.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
```

sudo lshw -C network
```
 *-network               
       description: Ethernet interface
       product: VT6105 [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 86
       serial: 00:50:fc:b0:f0:96
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.3 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
```

iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by asakurax on 2008-05-02
Bump :)

---

### Post by lswest on 2008-05-02
So, from the outputs, i assume it's a wired connection.  What happens if you plug in an ethernet cable and run ```
sudo dhclient eth0
``` any errors?

---

### Post by asakurax on 2008-05-02
```
sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6127
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:50:fc:b0:f0:96
Sending on   LPF/eth0/00:50:fc:b0:f0:96
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.3 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.3 from 192.168.1.1
bound to 192.168.1.3 -- renewal in 15323869 seconds.
```

:)

---

### Post by asakurax on 2008-05-03
Bump :)

---

### Post by asakurax on 2008-05-04
Bump :) :)

---

### Post by asakurax on 2008-05-09
Bump :) :) :)

---

### Post by subzero316 on 2008-05-09
> **asakurax said:**
> A friend of mine tried to install Gutsy when it came out, and the internet didn't work almost completely. the ICQ protocol via Pidgin worked, and some webpages, but mostly, nothing worked. Now he waited for Hardy to come out, and he's experiencing the same problems.

Hmph
He just told me that on Fiesty everything worked fine, but he doesn't wanna use it because of the low NTFS support



Can you be more specific... WHat are the webpages you cant view..And what is the error you get when you type in those adresses. Since you can login via pidgin There`s no problem with the connection.

---

