---
title: "Wireless Shows that I can connect to home router. but no internet connection"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by disappearedng on 2008-07-15
Hi everyone
I have just recently reinstalled ubuntu hardy on T61. The funny thing is, my wireless card no longer works. I began investigating this problem with the following:

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Lenovo Unknown device 20b3
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Unknown device 20b5
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Lenovo Unknown device 20b5
	Flags: bus master, fast devsel, latency 0
	Memory at f8200000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 216
	Memory at fe000000 (32-bit, non-prefetchable) [size=128K]
	Memory at fe225000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T60
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1880 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fe226c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fe220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d8000000-dbdfffff
	Prefetchable memory behind bridge: 00000000dfe00000-00000000dfefffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: dc000000-df3fffff
	Prefetchable memory behind bridge: 00000000dfb00000-00000000dfbfffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: fc000000-fdffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f80fffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=0c, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d4000000-d5ffffff
	Prefetchable memory behind bridge: 00000000df800000-00000000df8fffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0d, subordinate=14, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d0000000-d1ffffff
	Prefetchable memory behind bridge: 00000000df500000-00000000df5fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 18a0 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 18c0 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 18e0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe227000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=15, subordinate=18, sec-latency=32
	I/O behind bridge: 00007000-0000afff
	Memory behind bridge: f8300000-fbffffff
	Prefetchable memory behind bridge: 00000000f4000000-00000000f7ffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
	Subsystem: Lenovo Unknown device 20b6
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1c00 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 218
	I/O ports at 1c50 [size=8]
	I/O ports at 1c44 [size=4]
	I/O ports at 1c48 [size=8]
	I/O ports at 1c40 [size=4]
	I/O ports at 1c20 [size=32]
	Memory at fe226000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Lenovo ThinkPad T61
	Flags: medium devsel, IRQ 11
	Memory at fe227400 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c60 [size=32]

02:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
	Subsystem: Intel Corporation Turbo Memory Controller
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at dbdffc00 (32-bit, non-prefetchable) [size=1K]
	I/O ports at 2000 [size=128]
	[virtual] Expansion ROM at dfe00000 [disabled] [size=64K]
	Capabilities: <access denied>

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Lenovo ThinkPad T51
	Flags: bus master, fast devsel, latency 0, IRQ 217
	Memory at df3fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
	Subsystem: Lenovo Unknown device 20c6
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at f8300000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=15, secondary=16, subordinate=17, sec-latency=176
	Memory window 0: f4000000-f7fff000 (prefetchable)
	Memory window 1: 40000000-43fff000
	I/O window 0: 00007000-000070ff
	I/O window 1: 00007400-000074ff
	16-bit legacy interface ports at 0001

15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04) (prog-if 10 [OHCI])
	Subsystem: Lenovo Unknown device 20c7
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at f8301000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
	Subsystem: Lenovo Unknown device 20c8
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at f8301800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
	Subsystem: Lenovo Unknown device 20c9
	Flags: bus master, medium devsel, latency 0, IRQ 11
	Memory at f8301c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
	Subsystem: Lenovo Unknown device 20ca
	Flags: medium devsel, IRQ 11
	Memory at f8302000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
	Subsystem: Lenovo Unknown device 20cb
	Flags: medium devsel, IRQ 11
	Memory at f8302400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

This is what my ifconig shows:
```

eth0      Link encap:Ethernet  HWaddr 00:1c:25:70:55:ce  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:12937179 (12.3 MB)  TX bytes:905731 (884.5 KB)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70500 (68.8 KB)  TX bytes:70500 (68.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:34:51:9f  
          inet addr:76.10.128.244  Bcast:76.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21d:e0ff:fe34:519f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:775482 (757.3 KB)  TX bytes:28291 (27.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-34-51-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```
The funny thing is:
Under my router's network, I can't seem to find my laptop's connectiveness. wlan0 shows that i have an 76.10.128.244 which is an external ip. 

Any clues why this is so? 
I thought all ath0 network card are supported by default? 

Thx

---

### Post by bobnutfield on 2008-07-15
This probably the IP of your ISP. Are you using DHCP on your router or static IP?

---

### Post by Dedoimedo on 2008-07-15
Hi,

When you say no internet connection:

- Can you ping any site by name / IP?
- Do you use DHCP / static IP?
- Did you define a DNS server for your network cards?

Dedoimedo

---

