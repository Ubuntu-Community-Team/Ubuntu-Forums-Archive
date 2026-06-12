---
title: "Ndiswrapper Not playing nice with Wireless card (not working)"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by epuppet on 2008-09-23
Computer Dell Precision 530 Wireless Card Belkin N1 fd8001

here is my lspci -nn
```
frank@ubuntu:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82860 860 (Wombat) Chipset Host Bridge (MCH) [8086:2531] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge [8086:2532] (rev 04)
00:02.0 PCI bridge [0604]: Intel Corporation 82860 860 (Wombat) Chipset AGP Bridge [8086:2533] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 04)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 04)
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 04)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 04)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7800 GS] [10de:00f5] (rev a2)
02:1f.0 PCI bridge [0604]: Intel Corporation 82806AA PCI64 Hub PCI Bridge [8086:1360] (rev 03)
03:00.0 PIC [0800]: Intel Corporation 82806AA PCI64 Hub Advanced Programmable Interrupt Controller [8086:1161] (rev 01)
03:0e.0 SCSI storage controller [0100]: Adaptec AIC-7892P U160/m [9005:008f] (rev 02)
04:0b.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
04:0c.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) [104c:8020]
04:0e.0 Network controller [0280]: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter [168c:0023] (rev 01)

```

And here is my lshw -C network
```
frank@ubuntu:~$ sudo lshw -C network
[sudo] password for frank: 
  *-network:0             
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: b
       bus info: pci@0000:04:0b.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:08:b5:d0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.16.7 latency=64 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Network controller
       product: AR5416 802.11abgn Wireless PCI Adapter
       vendor: Atheros Communications Inc.

```

I have followed a couple posts and tried manually making this card use the correct driver ( or so Im told correct driver ) to no avail.

Also if memory serves me correctly, There are 2 diff chipsets for the versions, ie.. below v3.000 one chipset above v3.001 ( those are not the correct version numbers just used to give an example)  At least I remember the drivers were different for these on windows. 

Any help would be apreciated.  Thanks Guys.

THe driver being used is the NetMW14x.inf as shown on the compatability list:[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#PCI)

I will send one slightly eaten, partially melted, non-existant Almond Joy to the guy/gal who gets it working..:lolflag:

---

