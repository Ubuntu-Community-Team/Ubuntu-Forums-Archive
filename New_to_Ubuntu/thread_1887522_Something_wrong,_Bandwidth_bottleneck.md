---
title: "Something wrong, Bandwidth bottleneck?"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by DarrenMR415 on 2011-11-27
Been happening for days, I have no idea what it is.  My internet is completely bogged down, but my second computer has no issues, my smartphone has no issues, streaming netflix on my x-box has no problems. Ive done everything I would do on a Windows XP box.  But Im not sure where to go with Ubuntu.  Its 10.04, but with all the up-to-date updates.


Ive looked through the system monitor, and I dont see anything unusual running.  Ran clamAV. 

Any suggestions are appreciated.

---

### Post by DarrenMR415 on 2011-11-27
Also, my connection randomly disconnects, and sometimes it will automatically reconnect, sometimes I have to do it manually.

---

### Post by DarrenMR415 on 2011-11-27
Is there anything at all I can do to diagnose my problem?

---

### Post by linuxman94 on 2011-11-27
Do you have a wired or wireless connection?  Also, please post the output of these commands:

```
ifconfig
lspci
lsusb
sudo lshw -C network
```

---

### Post by DarrenMR415 on 2011-11-27
wireless

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1e:33:af:b1:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:134208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6820706 (6.8 MB)  TX bytes:6820706 (6.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d2:4a:48:7e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d2ff:fe4a:487e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1377652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1140963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1154653836 (1.1 GB)  TX bytes:879302620 (879.3 MB)
```

lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```

lsusb
```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

sudo lshw -C network
```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:af:b1:1f
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:3000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:4a:48:7e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d3100000-d310ffff

```

---

### Post by DarrenMR415 on 2011-11-28
Anyone?

---

### Post by linuxman94 on 2011-11-30
Are you using wireless or wired connection?

---

### Post by sandyd on 2011-12-01
You using ath5k with that?
```

lsmod | grep ath5k

```

Sometimes, theirs the weird hwcrypt bug. I don't know if it still exists, because I don't use ubuntu on a desktop.


If the grep above returns something, run
```

sudo nano /etc/modprobe.conf

```
and add "options ath5k nohwcrypt=1" (without quotes) to a new line on the bottom of the file. and see if its better after restart.

---

