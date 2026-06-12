---
title: "Need help installing wireless adapter."
date: 2008-05-07
forum: New to Ubuntu
---

### Post by diablo75 on 2008-05-07
A friend of mine just bought a used PC which (from the look of the driver CD that came with it) has a D-Link DWL-G510.  The restricted driver manager does not list an available driver for easy install.  But more odd:  when I type "lspci" into a terminal window, I don't see anything mentioning a wireless adapter listed.  So I'm not sure if it's being detected by the OS or not.  It appears to be getting power, as the back of the card has a green light that blinks on occasion near the antenna.

What other command might I try in the terminal window to see if I it can detect the card?  All I really need is the ability to install a driver.  Thanks for the help in advanced.

---

### Post by gkrules on 2008-05-07
lspci -v and lspci -n
thats to checks ur devices
it shud say something about the wireless card



it shud also say what ur chipset in the card is
and from that u shud be able to recognize wat program to use
if its atheros use madwifi

---

### Post by tjwoosta on 2008-05-07
on my laptop i have an internal usb adapter 
(is it possible yours is too?)

try 
```

lsusb

```

---

### Post by diablo75 on 2008-05-07
Here's what I got:

```
brian@brian-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
	Subsystem: Intel Corporation 82875P/E7210 Memory Controller Hub
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: e0000000-efffffff

00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 32
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: f8000000-f80fffff

00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
	Subsystem: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
	Flags: fast devsel
	Memory at f8101000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at cc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at c000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at c400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Intel Corporation Unknown device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f8100000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 00007000-0000afff
	Memory behind bridge: f6000000-f7ffffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Unknown device 24d2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: Intel Corporation Unknown device 24d2
	Flags: medium devsel, IRQ 9
	I/O ports at 0500 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV36 [GeForce FX 5700LE] (rev a1) (prog-if 00 [VGA controller])
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at f5000000 [disabled] [size=128K]
	Capabilities: <access denied>

02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
	Subsystem: Intel Corporation PRO/1000 CT Desktop Connection
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	Memory at f8000000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at b000 [size=32]
	Capabilities: <access denied>

03:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at 7000 [size=256]
	Capabilities: <access denied>

03:06.0 Mass storage controller: ALi Corporation ALi M5281 Serial ATA / RAID Host Controller (rev a1) (prog-if 85)
	Subsystem: ALi Corporation ALi M5281 Serial ATA / RAID Host Controller
	Flags: bus master, 66MHz, medium devsel, latency 128, IRQ 20
	I/O ports at 7400 [size=8]
	I/O ports at 7800 [size=4]
	I/O ports at 7c00 [size=8]
	I/O ports at 8000 [size=4]
	I/O ports at 8400 [size=16]
	[virtual] Expansion ROM at f6000000 [disabled] [size=64K]

03:06.1 Mass storage controller: ALi Corporation M5228 ALi ATA/RAID Controller (rev c6) (prog-if 85)
	Subsystem: ALi Corporation Unknown device 5281
	Flags: bus master, 66MHz, medium devsel, latency 128, IRQ 20
	I/O ports at 8800 [size=8]
	I/O ports at 8c00 [size=4]
	I/O ports at 9000 [size=8]
	I/O ports at 9400 [size=4]
	I/O ports at 9800 [size=16]

03:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: Soyo Computer, Inc Unknown device a419
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at 9c00 [size=256]
	Capabilities: <access denied>

03:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
	Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at f7000000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at a000 [size=128]
	Capabilities: <access denied>

brian@brian-desktop:~$ 

```

And this:

```
brian@brian-desktop:~$ lspci -n
00:00.0 0600: 8086:2578 (rev 02)
00:01.0 0604: 8086:2579 (rev 02)
00:03.0 0604: 8086:257b (rev 02)
00:06.0 0880: 8086:257e (rev 02)
00:1d.0 0c03: 8086:24d2 (rev 02)
00:1d.1 0c03: 8086:24d4 (rev 02)
00:1d.2 0c03: 8086:24d7 (rev 02)
00:1d.3 0c03: 8086:24de (rev 02)
00:1d.7 0c03: 8086:24dd (rev 02)
00:1e.0 0604: 8086:244e (rev c2)
00:1f.0 0601: 8086:24d0 (rev 02)
00:1f.1 0101: 8086:24db (rev 02)
00:1f.3 0c05: 8086:24d3 (rev 02)
01:00.0 0300: 10de:0343 (rev a1)
02:01.0 0200: 8086:1019
03:04.0 0401: 13f6:0111 (rev 10)
03:06.0 0180: 10b9:5281 (rev a1)
03:06.1 0180: 10b9:5228 (rev c6)
03:07.0 0401: 13f6:0111 (rev 10)
03:0a.0 0c00: 1106:3044 (rev 46)

```

lsusb shows nothing but empty ports.  No hardware ID's of any use...

---

### Post by kshtjsnghl on 2008-05-07
I think the application windows wireless drivers in add/remove applications might be able to help you ...

It lets you install your own wireless driver.

---

### Post by kshtjsnghl on 2008-05-07
sorry i posted the same post two times
 thats why deleting this one...

---

### Post by diablo75 on 2008-05-07
Well, crap.  The Windows Driver Installer loaded the driver fine, but it says the hardware is not present....any ideas?

---

