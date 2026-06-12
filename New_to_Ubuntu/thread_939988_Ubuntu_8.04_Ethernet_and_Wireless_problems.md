---
title: "Ubuntu 8.04 Ethernet and Wireless problems"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by pincheLinux on 2008-10-06
Hi, I just updated from Ubuntu 6.06 to 8.04 through the Update Manager and everything seems to be working fine except that I can't connect to the internet either throught the Ethernet or Wireless modem (roaming mode is enabled). I have an Averatec 3200 Series laptop. Any help? I'm brand new to Linux and Ubuntu.

*ifconfig* exports:


> eth0      Link encap:Ethernet  HWaddr 00:40:45:25:e4:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2e00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1580 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79000 (77.1 KB)  TX bytes:79000 (77.1 KB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:0e:24:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-09-0E-24-33-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


*lspci -v* exports

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
	Subsystem: VIA Technologies, Inc. Unknown device 0000
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: dde00000-dfefffff
	Prefetchable memory behind bridge: d5d00000-ddcfffff
	Capabilities: <access denied>

00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Unknown 802.11g mini-PCI Adapter
	Flags: bus master, slow devsel, latency 32, IRQ 11
	Memory at dfffe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 20)
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device c602
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 10
	Memory at 28000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00001000-000010ff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device c905
	Flags: bus master, medium devsel, latency 32, IRQ 7
	I/O ports at e400 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device c905
	Flags: bus master, medium devsel, latency 32, IRQ 7
	I/O ports at e800 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80) (prog-if 00 [UHCI])
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device c905
	Flags: bus master, medium devsel, latency 32, IRQ 7
	I/O ports at ec00 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20 [EHCI])
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device c905
	Flags: bus master, medium devsel, latency 32, IRQ 7
	Memory at dfffdf00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
	Subsystem: VIA Technologies, Inc. Unknown device 0000
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device 1205
	Flags: bus master, medium devsel, latency 32, IRQ 255
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device 0408
	Flags: medium devsel, IRQ 10
	I/O ports at dc00 [size=256]
	Capabilities: <access denied>

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device 1005
	Flags: medium devsel, IRQ 10
	I/O ports at e000 [size=256]
	Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device 0207
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at d800 [size=256]
	Memory at dfffde00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA controller])
	Subsystem: TWINHEAD INTERNATIONAL Corp Unknown device 030d
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 9
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Expansion ROM at dfef0000 [disabled] [size=64K]
	Capabilities: <access denied>


---

### Post by pytheas22 on 2008-10-06
Just a few questions to help clarify the situation:

Do you have a wireless device recognized by the system?  If so, when you left-click on the Network Manager icon (top-right corner of the screen), do you see a list of wireless networks?  If so, what happens when you try to connect to one?  You have an rt2500 chipset, which should be supported with no problems in 8.04.

As for the ethernet: does the system recognize a device at all?  What happens if you type:
```

sudo ifconfig eth0 up
sudo dhclient eth0
```

That should get you an IP address (otherwise it will time out).  Does it work?

Also, please post the output of:
```

lspci -nn
lshw -C Network
dmesg | grep -e rt2 -e wlan -e eth0 -e eth1 -e VIA -e via
```

---

### Post by pincheLinux on 2008-10-06
Hi pytheas, thanks again for your help. I have a wireless router in my house and a wireless device in the laptop, but Ubuntu does not see the network. When I left-click on the Network Manager it does not list the wireless network. When I connect an ethernet cable directly to the laptop Ubuntu doesn't recognize it either. Sometimes it does connect and if I click on the monitors icon on the upper right the Wired Network option is selected, but there is no internet - going to Google from Firefox returns Address Not Found. Keep in mind that when I had Ubuntu 6.06 right before I updated to 8.06 it did see the wireless network and the ethernet worked (so it's not the hardware, I'm assuming).

Wheh I type *sudo ifconfig eth0 up* I get *sudo: unable to resolve host LinuxBuster* (LinuxBuster is the laptop name).

*sudo dhclient eth0*

> Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:40:45:25:e4:cc
Sending on   LPF/eth0/00:40:45:25:e4:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


*lspci -nn*

> 00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge [1106:3205]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI Bridge [1106:b198]
00:09.0 Network controller [0280]: RaLink RT2500 802.11g Cardbus/mini-PCI [1814:0201] (rev 01)
00:0a.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972] (rev 20)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video [1106:7205] (rev 01)


*lshw -C Network*

> WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wmaster0
       version: 01
       serial: 00:11:09:0e:24:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=32 module=rt2500pci multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:25:e4:cc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes


*dmesg | grep -e rt2 -e wlan -e eth0 -e eth1 -e VIA -e ia*

> [    0.000000] ACPI: RSDT 1DFF0000, 0028 (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 1DFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 1DFF00C0, 46E7 (r1    VIA   VIA_K7     1000 INTL  2002024)
[   15.561129] PCI: VIA PCI bridge detected. Disabling DAC.
[   18.630915] PCI: VIA VLink IRQ fixup for 0000:00:10.0, from 0 to 7
[   18.733979] PCI: VIA VLink IRQ fixup for 0000:00:10.1, from 0 to 7
[   18.748020] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   18.837914] PCI: VIA VLink IRQ fixup for 0000:00:10.2, from 0 to 7
[   18.941953] PCI: VIA VLink IRQ fixup for 0000:00:10.3, from 0 to 7
[   19.062541] eth0: VIA Rhine II at 0xdfffde00, 00:40:45:25:e4:cc, IRQ 11.
[   19.063254] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   19.069965] pata_via 0000:00:11.1: version 0.3.3
[   19.072046] scsi0 : pata_via
[   19.072865] scsi1 : pata_via
[   36.633953] agpgart: Detected VIA KM400/KM400A chipset
[   41.301988] udev: renamed network interface wlan0 to ra0
[   47.632209] [drm] Initialized via 2.11.1 20070202 on minor 0
[  210.585749]  [<de8c1e38>] rhine_interrupt+0x3b8/0x730 [via_rhine]
[  210.586126]  [<de8c1a80>] rhine_interrupt+0x0/0x730 [via_rhine]
[  210.586194]  [<de8c3297>] rhine_open+0x47/0x1e0 [via_rhine]
[  210.587105]  [<de8c35c0>] netdev_get_link+0x0/0x10 [via_rhine]
[  210.587822] [<de8c1a80>] (rhine_interrupt+0x0/0x730 [via_rhine])
[  210.588417] eth0: link down
[   82.698828] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  249.330902] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  249.331039] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1052.373587] eth0: no IPv6 routers present
[ 1073.516801] NETDEV WATCHDOG: eth0: transmit timed out
[ 1073.516972] eth0: Transmit timed out, status 5003, PHY status 786d, resetting...
[ 1073.517789] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  260.706249] NETDEV WATCHDOG: eth0: transmit timed out
[  260.706404] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  260.707087] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1091.202576] NETDEV WATCHDOG: eth0: transmit timed out
[ 1091.202747] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[ 1091.203552] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1


---

### Post by pytheas22 on 2008-10-07
Please try running these commands and see if they get the ethernet connected (please post all output):

```
cp /etc/network/interfaces ~/Desktop
sudo rm -rf /etc/network/interfaces
sudo /etc/init.d/networking restart
sudo ifconfig eth0 up
sudo dhclient eth0
```

Also, the wireless interface looks like it should be working, so I'm not sure why you don't see networks.  Let's try scanning from the command-line.  Please post the output of:
```

sudo iwlist scan
```

I think that the problems are the result of having upgraded from 6.06--the networking configuration was quite different back then, and the upgrade process seems not to have translated your previous settings into what 8.04 expects very well.  But we'll figure it out.

---

### Post by rcadby on 2008-10-07
I'm having the same problem(s). Can I join it, here? I have a DELL PC still using Ubuntu 7.10 with a Belkin wireless that connects to the Kyocera KR2 wireless router just fine.

I upgraded my DELL AMD64 laptop from 7.10 to 8.04. I connect fine to the router via ethernet cable, but no joy via my Broadcom BCM94311MCG wireless card. I jumped through all the hoops I could find on this forum for latest driver and wrapper, but have something goofed up.

Here's the output from 

sudo iwlist scan

lo        Interface doesn't support scanning.

eth1      No scan results

eth0      Interface doesn't support scanning.



I tried this:

sudo ifconfig eth1 up
sudo dhclient eth1

getting:

There is already a pid file /var/run/dhclient.pid with pid 15593
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:1d:60:a9:7a:c3
Sending on   LPF/eth1/00:1d:60:a9:7a:c3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I also followed your previous instructions. Below are the results:

lspci -nn

00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)


lshw -C Network

  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1d:60:a9:7a:c3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:b4:50:12
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.198 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s



dmesg | grep -e rt2 -e wlan -e eth0 -e eth1 -e VIA -e via

which got me no output.



I'm also a newb (in case you couldn't tell).

TIA .........Ron

---

### Post by pytheas22 on 2008-10-07
rcadby,

What is the output of:
```

dmesg | grep -e ndis -e wlan
ndiswrapper -l
uname -m
cat /etc/modprobe.d/blacklist
sudo iwlist scan
```

---

### Post by rcadby on 2008-10-07
> **pytheas22 said:**
> rcadby,

What is the output of:
```

dmesg | grep -e ndis -e wlan
ndiswrapper -l
uname -m
cat /etc/modprobe.d/blacklist
sudo iwlist scan
```



root@rcadby-laptop:~# dmesg | grep -e ndis -e wlan
root@rcadby-laptop:~# ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
root@rcadby-laptop:~# uname -m
x86_64
root@rcadby-laptop:~# cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

#Block Airprime driver to force kernel to use usbserial
blacklist airprime

#Block bcm43xx
blacklist bcm43xx

#Block b43
root@rcadby-laptop:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      No scan results

eth0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2008-10-07
rcadby,

Something a bit strange seems to be going on.  ndiswrapper says that it's installed correctly and that it can see your card with no problem, and your wireless interface (eth1) appears to be up.  However, 'dmesg' doesn't record the ndiswrapper module being inserted at all, which should not be happening if ndiswrapper is really working.  Also, you can't seem to see networks when you scan, and your wireless interface is named 'eth1', which is weird (normally under ndiswrapper it would be called 'wlan0').

I do see that you're running 64-bit Ubuntu.  Did you install a 64-bit Windows driver into ndiswrapper?  If not, that's the problem: ndiswrapper needs a 64-bit Windows driver if your Linux kernel is also 64-bit.  If you followed a tutorial somewhere for configuring ndiswrapper (like [this one]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")), that fact may not have been mentioned because it assumed that everyone was on 32-bit.

If you're sure that you installed a 64-bit Windows driver, then please try running the following commands (in this order) and post the output:
```

sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
sudo modprobe ndiswrapper
dmesg | tail
sudo iwlist scan
```

Your ethernet connection may not be working at this point (making it difficult to post information here), because the commands above removed the ethernet driver.  To get the ethernet working again, type:
```

sudo modprobe b44
sudo modprobe ssb
sudo dhclient eth0
```

or just save the output to a text file, reboot your computer and the ethernet should work again (any modules that you manually remove will be reinserted the next time your computer restarts).  Then you should be able to post your terminal output here easily.

Another possibility is that everything is working correctly, but your wireless network is simply not broadcasting in 11g mode.  Are you sure it's in 11g mode (99% of networks these days are, but if you have an old router, maybe you use 11b mode, or maybe you're on 11n if you have a new router).  If you type 'sudo iwlist scan' on your other Ubuntu computer, what is the output (it should list information for each of the wireless networks in range, including the mode that they're operating in)?

---

### Post by rcadby on 2008-10-08
root@rcadby-laptop:~# sudo modprobe -r b44 b43 b43legacy ssb ndiswrapper bcm43xx
root@rcadby-laptop:~# sudo modprobe ndiswrapper
root@rcadby-laptop:~# dmesg | tail
[ 2124.669972] atkbd.c: Unknown key released (raw set 2, code 0xd5 on isa0060/serio0).
[ 2124.669980] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[ 2125.146486] atkbd.c: Unknown key pressed (raw set 2, code 0xd5 on isa0060/serio0).
[ 2125.146494] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[ 2125.153802] atkbd.c: Unknown key released (raw set 2, code 0xd5 on isa0060/serio0).
[ 2125.153809] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[ 2125.618363] atkbd.c: Unknown key pressed (raw set 2, code 0xd5 on isa0060/serio0).
[ 2125.618371] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[ 2125.625688] atkbd.c: Unknown key released (raw set 2, code 0xd5 on isa0060/serio0).
[ 2125.625696] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
root@rcadby-laptop:~# sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      No scan results



The new router indeed handles '/n' (I don't know/understand what you mean by '11 n'). Here's result of 'sudo iwlist scan' on other PC:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:14:60:F4:8C:39
                    ESSID:"Kyocera KR2-c39"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36
Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=94/100
                    Extra: Last beacon: 388ms ago
          Cell 02 - Address: 00:18:F8:69:F5:1F
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36
Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=100/100
                    Extra: Last beacon: 188ms ago

---

### Post by Cpuboye11 on 2008-10-08
I had this problem along the same lines. My laptop which is a Dell C640, upgraded from 7.10 to 8.04... Lost all internet and network features.. or couldn't get to them. Lost Visual's... Lost sound... or atleast most of it.. And my update manager wouldn't even open..

I would say back up all your stuff that you want... Maybe get a copy of the programs installed on your computer... and go download the new up-to-date copy of 8.04 and reinstall...

I spent about 3 whole sleepless nights working on the visuals alone.. and it came done to.. You have to reinstall. Something went CRAZY during the Update!!!!!! It's the easiest and fastest way out.. Just my two bits. :lolflag:

---

### Post by pytheas22 on 2008-10-08
> The new router indeed handles '/n' (I don't know/understand what you mean by '11 n'). Here's result of 'sudo iwlist scan' on other PC:

Your router is broadcasting on 11b/g so this is not the problem.

It looks like your wireless card may be physically turned off.  If there's a button on your laptop that you have to press to enable it or a key combination (like Function+F2), try toggling it.  I think that this is why the wireless isn't working.  If that doesn't help, please post the total output of:
```

dmesg
```

(it will be pretty long, but it would be good to see it all).

---

### Post by Cpuboye11 on 2008-10-08
> **pytheas22 said:**
> Your router is broadcasting on 11b/g so this is not the problem.

It looks like your wireless card may be physically turned off.  If there's a button on your laptop that you have to press to enable it or a key combination (like Function+F2), try toggling it.  I think that this is why the wireless isn't working.

Not that i'm saying your wrong.. But maybe i didn't read it but... Even if that was turned off.. Why was his Ethernet not working.

---

### Post by pytheas22 on 2008-10-08
> Not that i'm saying your wrong.. But maybe i didn't read it but... Even if that was turned off.. Why was his Ethernet not working.

His ethernet is working, as far as I can tell (the output of 'lshw -C Network' indicates that he had an IP address on his ethernet interface).  I think that just the wireless is the problem...

---

### Post by Papa-san on 2008-10-08
This is actually for the peeps who do the development here:

I'm almost 100% positive that the old 'logical name' for your wireless interface was eth1. The upgrade managed to change it to wmaster0. Now your files in your 'home' directory are looking for eth1, and is only finding this: ```
wmaster0 Link encap:UNSPEC HWaddr 00-11-09-0E-24-33-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
```

---

### Post by rcadby on 2008-10-08
Thanks, but my 'problem laptop' works via ethernet cable (although it doesn't seem to like this forum at the moment...using PC now). Email and browsing works except for my truant wireless card.

I've thought about a re-installation using my Ubuntu 7.10 CD which is what I'm using now on this PC.

I'm hoping to avoid that, though. .....Ron

---

### Post by pytheas22 on 2008-10-08
> This is actually for the peeps who do the development here:

I'm almost 100% positive that the old 'logical name' for your wireless interface was eth1. The upgrade managed to change it to wmaster0. Now your files in your 'home' directory are looking for eth1, and is only finding this:

Yes, this is true, but it's not actually a problem.  The reason that it happens is that in Ubuntu 7.10 and earlier, Broadcom wireless cards (which the original poster in this thread has) used a driver called bcm43xx, which created an interface named eth1.  In Hardy and later, bcm43xx has been replaced by a new driver called b43, which creates two interfaces: one named wmaster0 and another named wlan0 (wlan0 is really just a virtual interface based on wmaster0...this is the new way that Linux has decided to handle wireless networking, which has various advantages over the traditional approach...you can read more about it if you google around).  So that's why there are differences in the interface names, but I don't think that that's what's causing the problem here...I think it's that radio on the wireless card is physically disabled and needs to be switched on.

---

### Post by rcadby on 2008-10-08
I toggled the wireless a few times to be sure the laptop indicator showed, re-booted,.........

OK. At first the wireless wouldn't work. 

Then, I opened the Network Settings and put the Wireless connection in roaming mode.

Then, I clicked on the network icon at the top of the screen and found that it could see my two local WiFi's and selected the new router which is connected to the web via my UM150 usb modem.......

Guess what? I'm editing this and will now save it to the forum.

Wahoo!

I seem to be in business. 

Thanks for all the help. 

I'm sure I'll be back. Now, I have to figure out how to talk to set up my house wireless network to get that router to work with the other PC and printer.

........Ron

---

### Post by Papa-san on 2008-10-08
Thanks.
I do understand the difference and it's advantages. My only concern is that all the files that need to have the switch made to them haven't been changed. 

If they have been, I apologize for bringing it up.
My system was flawless before I upgraded. Getting both wired and wireless to function took me a few days of tinkering, and even then, I have to actually go into System>Administration>Network and re-enter my information about half of the time... (It loses my 11 character passphrase and replaces it with an unknown 64 character password that doesn't work...) All of this happened when the interface changed from eth1 to wmaster0. And, for what it is worth, I do actually consider this to be a problem...

---

### Post by pytheas22 on 2008-10-08
rcadby,

Glad to hear that things are solved :) (or this particular thing, at least)

Papa-san,

You don't need to apologize.  I think I read your post incorrectly the first time; I didn't realize that you were asking for help as well.  Please post the output of the following commands and I'll try to tell you what you need to do to get your wireless working:
```

lshw -C Network
lspci -nn
uname -m
sudo iwlist scan
```

It probably is just a matter of straightening out some issues with the drivers.

Also, you upgraded from 7.10 to 8.04 too, right?

---

### Post by pincheLinux on 2008-10-10
Hey **pytheas**. Yikes, this thread has you busy! Following is my long due reply. Let me know what you think, although I am starting to wonder if maybe the best solution is to re-install Ubuntu 8.04 from scratch (after saving my current xong.conf file which was what required me to do an update from 6.06 to begin with).

*cp /etc/network/interfaces ~/Desktop* exports nothing.

*sudo rm -rf /etc/network/interface*s exports
> sudo: unable to resolve host LinuxBuster

*sudo /etc/init.d/networking restart*
> sudo: unable to resolve host LinuxBuster
 * Reconfiguring network interfaces...                                          ifdown: couldn't read interfaces file "/etc/network/interfaces"
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]
*sudo ifconfig eth0 up*
> sudo: unable to resolve host LinuxBuster


*sudo dhclient eth0*
> sudo: unable to resolve host LinuxBuster
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:40:45:25:e4:cc
Sending on   LPF/eth0/00:40:45:25:e4:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
francisco@LinuxBuster:~$ sudo iwlist scan
sudo: unable to resolve host LinuxBuster
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

ra0       No scan results

---

### Post by pytheas22 on 2008-10-10
pincheLinux,

Sorry that didn't work.  The problem (or at least part of it) seems to be that your computer thinks it needs to resolve its local hostname (LinuxBlaster is the name of your computer, I guess?) for some reason, but it can't do that.  It might help to open up your hosts file by typing:

```
sudo gedit /etc/hosts
```

and remove or comment out (by putting a # at the beginning of the line that you want to ignore) any lines that mention "LinuxBlaster."

It could also help to type:
```

sudo gedit /etc/network/interfaces
```

and make that file look like this:
```

auto lo
iface lo inet loopback
```

That might solve the problem (restart your computer to see if it will connect after that), but if not, and you don't mind installing with 8.04 or (8.10), that might be the only way to go.  I wish I had a more concrete idea of what exactly is wrong, but none of my guesses so far seem to have been the problem...

---

### Post by chi0 on 2008-10-19
Got an AV3250HS and I think I may have found something. Try establishing internet connection with X disabled. I usually delete xorg.conf to bring up the command line. eth0 will work just fine till X is loaded. Basically, soon as I load X net connections drop.

---

### Post by pytheas22 on 2008-10-19
> Got an AV3250HS and I think I may have found something. Try establishing internet connection with X disabled. I usually delete xorg.conf to bring up the command line. eth0 will work just fine till X is loaded. Basically, soon as I load X net connections drop.

That's strange--I can't think of much that X would be doing to break the ethernet.  It could be that Network Manager (which won't start till you launch the graphical server) is doing something, however.  Does the problem still occur if you uninstall NM:

sudo apt-get remove network-manager

In its place, you could install [wicd]("http://wicd.sourceforge.net"), or connect manually of course.

---

### Post by chi0 on 2008-10-19
First time I detected the problem was after I installed slackware 12.1 which is also 2.6.24, Slackware doesn't have a graphical network manager, yet the problem is exactly the same. X loads network goes away. Upgrading to 2.6.27 yielded limited network connectivity. Browser wouldn't open anything except for a few google pages.

---

### Post by pytheas22 on 2008-10-19
> First time I detected the problem was after I installed slackware 12.1 which is also 2.6.24, Slackware doesn't have a graphical network manager, yet the problem is exactly the same. X loads network goes away. Upgrading to 2.6.27 yielded limited network connectivity. Browser wouldn't open anything except for a few google pages.

Did you check dmesg or system logs to see if they mention anything about why the interface is crashing when X starts?  Also, you've had this problem in Ubuntu too, right--not just Slackware?

---

### Post by chi0 on 2008-10-19
Yes, same problem occurs in Ubuntu too. The interface doesn't crash. I can start and stop it without any errors. dmesg or any system logs don't return any viable information as to whats causing this.

---

### Post by pytheas22 on 2008-10-19
What do you get if immediately after logging into the desktop, you run these commands:
```

lshw -C Network
ifconfig
ping -c 5 google.com
host google.com
ping -c 5 64.233.187.99
```

Then after it crashes, what is the output of:

```
sudo dhclient eth0
lshw -C Network
ifconfig
cat /etc/resolv.conf
ping -c 5 google.com
host google.com
ping -c 5 64.233.187.99
```

From your description, I'm wondering if it's an issue with DNS rather than the interface actually going down or the IP being lost...

---

### Post by chi0 on 2008-10-20
Once X loads I can't ping the router to which this computer is connected to. It is not a DNS  issue. Is 8.10 going to include newer version of X?

---

### Post by pytheas22 on 2008-10-20
Yes, 8.10 includes a newer version of X.  I still don't understand what's going on, however--it makes no sense to me that running X would cause you to lose the connection.  Do you still have an IP address even when you can't ping the router?  What happens if you renew it, or if you bring the interface down and up again?  Have you tried using static IP?

---

### Post by chi0 on 2008-10-20
I'm using a static IP address which eth0 still maintains after X loads. I really can't grasp what is causing this since unloading certain modules that X loads doesn't correct the issue. ifconfig eth0 down and ifconfig eth0 up doesn't do anything either.

I installed Ubuntu 7.04 and everything is back to normal now except for wifi which requires that I install newer kernel and rutil.

It could be that the combination of newer X version, kernel 2.6.24+ and via chipset is causing this really strange problem.

---

### Post by pytheas22 on 2008-10-20
And you can't get a connection again by typing:
```

sudo dhclient -r eth0
sudo dhclient eth0
```

after you're logged into X?

---

### Post by chi0 on 2008-10-20
Nope. Thanks for your help though I appreciate it. I'll deal with this some other time for now 7.04 works fine.

---

### Post by Geryon on 2008-11-02
The solution for this is to add the following line to your xorg.conf's display section:

   Option "DisableIRQ"

This works with the 'via' driver and will allow networking and GUI to co-exist.  (posting this from an Averatec 3250 w/ RALINK NIC and Via UniChrome under 8.04 LTS).  

Enjoy!

---

