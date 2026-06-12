---
title: "[SOLVED] no internet with ubuntu studio"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Mzwo on 2008-09-16
hi,

just installed ubuntu studio. all fine, except i can't connect to the internet. clicking on the connections icon o the panel won't give me a list of available wirelss networks, it merely lets me know that my wlan is disconnected, but it won't let me connect to it.

also, the connections icon didn't appear automatically, i had to add is manually. 


what to do?

Mzwo

PS: the icon i added was "network monitor" which is different from the connections icon.

---

### Post by phidia on 2008-09-16
First check the easy things; is your wireless card switch in the off position?
Have you had wireless working before with ubuntu? Click on System > Admin > Hardware drivers and see if your card can be enabled there.

If none of that works you'll have to provide your wireless card make and model "lspci -v".

---

### Post by Mzwo on 2008-09-18
hi,

checked all the obivous things. wlan is switched on, ethernet connected. neither works, or rather: ethernet worked after the first boot after install, then stopped working. no connection is establish upon booting. i still cannot figure out how to connect, my wlan-connection is recognised but classed as disconnected (same with ethernet) - without the option to connect. when clicking on "configure" i get the message "interface doesn't exist". all worked fine under plain hardy without any fiddling at all. the handy wee connection icon appeared in the top right corner, gave me a list of all available wireless networks and gave me the option to connect. studio won't show me this. 

i'll check the driver and will post lspci -v output as soon as i'm back home (i.e. tonight gmt +1. ish. :-) ). 

Mzwo

---

### Post by Mzwo on 2008-09-19
sorry, will be a while till i get back to my linux machine. back with details soon.

Mzwo

---

### Post by Mzwo on 2008-09-22
back. 

current status: ethernet works. BUT: only when physically connected at start up. if the cable is removed while the system's up or attahced after booting, no internet. i still haven't figured out how to connect. admin -> network shows both ethernet and wlan, yet no way to connect. talking about wlan: that ain't working. like, at all. 

under plain hardy, never a problem. ubuntu studio just won't have it.

my system's a toshiba satellite A200-29L, wireless card is an intel pro wireless. lspci -v says:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fe000000-fe0fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fe404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: dc000000-dfffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f9ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d8000000-dbffffff
	Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d4000000-d7ffffff
	Prefetchable memory behind bridge: 00000000fc000000-00000000fdffffff
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d0000000-d3ffffff
	Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
	Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=10, sec-latency=32
	Memory behind bridge: fe100000-fe1fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 505
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fe404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: medium devsel, IRQ 10
	Memory at c2000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400 (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at fe000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fe020000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
	Subsystem: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe010000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 504
	I/O ports at 4000 [size=256]
	Memory at d8000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at fa000000 [disabled] [size=128K]
	Capabilities: <access denied>

05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1101
	Flags: bus master, fast devsel, latency 0, IRQ 503
	Memory at d4000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fe100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0c, secondary=0d, subordinate=10, sec-latency=176
	Memory window 0: c4000000-c7fff000 (prefetchable)
	Memory window 1: c8000000-cbfff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00007000-000070ff
	16-bit legacy interface ports at 0001

0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fe102000 (32-bit, non-prefetchable) [size=2K]
	Memory at fe104000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Toshiba America Info Systems Unknown device ff02
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fe101000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Unknown device ff02
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fe102800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
 

thanks for any help.

Mzwo

---

### Post by Mzwo on 2008-09-22
.... and root lspci -v says:


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fe000000-fe0fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
	Capabilities: [88] Subsystem: Toshiba America Info Systems Unknown device ff00
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fe404800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fe400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: dc000000-dfffffff
	Prefetchable memory behind bridge: 00000000f8000000-00000000f9ffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
	Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: d8000000-dbffffff
	Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
	Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: d4000000-d7ffffff
	Prefetchable memory behind bridge: 00000000fc000000-00000000fdffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
	Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: d0000000-d3ffffff
	Prefetchable memory behind bridge: 00000000cc000000-00000000cdffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
	Capabilities: [a0] Power Management version 2

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown device ff00
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fe404c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=10, sec-latency=32
	Memory behind bridge: fe100000-fe1fffff
	Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown device ff00

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 505
	I/O ports at 18d8 [size=8]
	I/O ports at 18cc [size=4]
	I/O ports at 18d0 [size=8]
	I/O ports at 18c8 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fe404000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable+
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: medium devsel, IRQ 10
	Memory at c2000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400 (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at fe000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at fe020000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
	Subsystem: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe010000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint IRQ 0
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 504
	I/O ports at 4000 [size=256]
	Memory at d8000000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at fa000000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Vital Product Data
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] Express Endpoint IRQ 0
	Capabilities: [84] Vendor Specific Information

05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
	Subsystem: Intel Corporation Unknown device 1101
	Flags: bus master, fast devsel, latency 0, IRQ 503
	Memory at d4000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint IRQ 0

0c:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at fe100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=0c, secondary=0d, subordinate=10, sec-latency=176
	Memory window 0: c4000000-c7fff000 (prefetchable)
	Memory window 1: c8000000-cbfff000
	I/O window 0: 00001400-000014ff
	I/O window 1: 00007000-000070ff
	16-bit legacy interface ports at 0001

0c:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at fe102000 (32-bit, non-prefetchable) [size=2K]
	Memory at fe104000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

0c:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
	Subsystem: Toshiba America Info Systems Unknown device ff02
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fe101000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

0c:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller (prog-if 01)
	Subsystem: Toshiba America Info Systems Unknown device ff02
	Flags: bus master, medium devsel, latency 57, IRQ 18
	Memory at fe102800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2


cheers,
Mzwo

---

### Post by angelsguitar on 2008-09-22
Hi. No need to panic! The "problem" is that UbuntuStudio by default doesn't include the network manager applet, which is the connection icon you see in a standard Ubuntu installation.  Remember that UbuntuStudio is optimized for multimedia, and one of the things the do to optimize it is remove the packages that aren't absolutely needed in multimedia work.

To solve it, just go to Synaptic and install the packages network-manager and network-manager-gnome .  Alternatively, you can run the following command on the terminal to install it (it will ask for your password, as you'll be using the sudo command):

```
sudo apt-get install network-manager network-manager-gnome
```

After that, the network manager icon should appear.

---

### Post by Mzwo on 2008-09-22
thanks very much, that did it. wlan up and working, panic avoided.

incidentally: any other packages that don't come with studio that i might want to have ;-)?

Mzwo

---

### Post by angelsguitar on 2008-09-22
> **Mzwo said:**
> thanks very much, that did it. wlan up and working, panic avoided.

incidentally: any other packages that don't come with studio that i might want to have ;-)?

Mzwo

Well, I installed OpenOffice because I use it very often.

There's Evolution too for email management.

But I will advice that you only install what you really need, because installing too much stuff, specially packages that run in the background (like Evolution, which checks for new emails on the background) would slow down the system and defeat the purpose of having a "lightweight" distro for multimedia work.

---

### Post by Mzwo on 2008-09-23
cheers. open office is a good idea, hadn't noticed it missing yet ... :-)

Mzwo

---

