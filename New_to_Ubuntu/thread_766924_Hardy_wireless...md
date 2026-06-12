---
title: "Hardy wireless.."
date: 2008-04-25
forum: New to Ubuntu
---

### Post by cartisdm on 2008-04-25
Sorry, I hate to post a thread that's probably giving lots of other people problems but I can't find a solution.

I just did a clean install to Hardy (previously had Gutsy).  It picked up my wireless just fine and located my nearest networks.  I tried to connect to my local network (WEP 128 HEX) and I entered my key and everything.  It successfully connects and gives my 95% strength but I can't get online!!

Right now I'm using wired connection but I don't understand why I can't reach my network wirelessly

---

### Post by cartisdm on 2008-04-25
anyone?

---

### Post by nepaliman on 2008-04-25
dude .. sory to bother u ..
actually i couldnt even connect or search .. and while maximising and minimising the windows its black for a sec .. why is that ... 

i m using acer travel mate 2420 ...1 gb ..

---

### Post by Monicker on 2008-04-25
> **cartisdm said:**
> Sorry, I hate to post a thread that's probably giving lots of other people problems but I can't find a solution.

I just did a clean install to Hardy (previously had Gutsy).  It picked up my wireless just fine and located my nearest networks.  I tried to connect to my local network (WEP 128 HEX) and I entered my key and everything.  It successfully connects and gives my 95% strength but I can't get online!!

Right now I'm using wired connection but I don't understand why I can't reach my network wirelessly


While trying to use the wireless, give the output of the following commands from a terminal:

```
lspci -v
iwconfig
/sbin/ifconfig
```

---

### Post by cartisdm on 2008-04-25
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: dfd00000-dfefffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Memory behind bridge: dfc00000-dfcfffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dfa00000-dfbfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d01fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Memory behind bridge: df900000-df9fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at bfa0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Dell Unknown device 01bd
	Flags: medium devsel, IRQ 5
	I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA controller])
	Subsystem: Dell Unknown device 2003
	Flags: bus master, fast devsel, latency 0, IRQ 4
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at ee00 [size=256]
	Memory at dfdf0000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at dfd00000 [disabled] [size=128K]
	Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
	Subsystem: Dell Inspiron 6400
	Flags: bus master, fast devsel, latency 64, IRQ 22
	Memory at df9fe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at df9fd800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
	Subsystem: Dell Unknown device 01bd
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at df9fd400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
	Subsystem: Dell Unknown device 01bd
	Flags: medium devsel, IRQ 9
	Memory at df9fd500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
	Subsystem: Dell Unknown device 01bd
	Flags: medium devsel, IRQ 9
	Memory at df9fd600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1020
	Flags: bus master, fast devsel, latency 0, IRQ 220
	Memory at dfcff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

dan@dan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:88:40:BC:E3   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=93/100  Signal level=-37 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Monicker on 2008-04-25
There seems to be mixed results with the intel 3945 chipset.  You might try some of the suggestions in this thread:  [http://ubuntuforums.org/showthread.php?t=765647&highlight=3945]("http://ubuntuforums.org/showthread.php?t=765647&highlight=3945")

---

