---
title: "Wifi problem"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by HIgHer82 on 2008-08-17
I installed kubuntu yesterday, and want to connect wireless i have the atheros 5007 EG and i guess it is working at the moment. If I use KWifimanager i can see a few networks. (see attachement) Including my own. I want to connect to my own (WPA) network but i really cant find out a way to do it.

this is the outcome of lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Crafty Kisses on 2008-08-17
Post the following output:
```
lshw -C network
```

---

### Post by HIgHer82 on 2008-08-17
erik@laptop:~$ sudo lshw -C network
[sudo] password for erik:
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:1f:c6:61:1f:0d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical                                                                                                                           tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion                                                                                                                          =1.20 duplex=full firmware=N/A ip=192.168.1.14 latency=0 link=yes module=sky2 mu                                                                                                                          lticast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:15:af:6a:00:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet                                                                                                                           physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci mult                                                                                                                          icast=yes wireless=IEEE 802.11g

---

### Post by Crafty Kisses on 2008-08-17
Sorry I forgot to ask, post this one too:
```
ifconfig
```

---

### Post by HIgHer82 on 2008-08-17
```

ath0      Link encap:Ethernet  HWaddr 00:15:af:6a:00:33
          inet6 addr: fe80::215:afff:fe6a:33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1f:c6:61:1f:0d
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe61:1f0d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:708 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:785380 (766.9 KB)  TX bytes:103015 (100.6 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-15-AF-6A-00-33-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7706 errors:0 dropped:0 overruns:0 frame:291
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280
          RX bytes:1096486 (1.0 MB)  TX bytes:9338 (9.1 KB)
          Interrupt:17


```

---

### Post by Kevbert on 2008-08-17
One thing I notice is that your signal strength and hence quality (displayed) is very poor.  Is the router/wireless source in the same room ?
It may be that you need to use a signal boosting antenna to improve this in order to get a decent connection.

---

### Post by Crafty Kisses on 2008-08-17
Yeah I noticed that too, try moving the router if that doesn't work please post back, also there maybe something interfering with the connection like lamps, phones, microwaves, just make sure nothing is possibly doing that.

---

### Post by HIgHer82 on 2008-08-17
i am sitting next to it, the quality is 75, seems to me that is good enough

but i can't even find an option to connect.

---

### Post by Crafty Kisses on 2008-08-17
This link may help you > [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by HIgHer82 on 2008-08-17
sorry i didn't proper research it myself, with the manuals i found out that it was about WPA, sorry for bothering you and thanks for helping out!

---

