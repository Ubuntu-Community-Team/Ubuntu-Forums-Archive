---
title: "how do i know which graphics card i am using?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Neil_The_Newbie on 2008-04-25
Well - I'm one of many who now have a problem with my screen resolution being messed up after updating. How do i find out which graphics card I am using? Any help would be very much appreciated folks.

---

### Post by Joeb454 on 2008-04-25
What computer do you have? I'm sure if it came preinstalled it would tell you somewhere.

Usually Ubuntu also picks up the correct graphics card.

---

### Post by Monicker on 2008-04-25
You can run "lspci -v" from a terminal and post the results here.  That should give information to determine what type of graphics card it is.

---

### Post by Neil_The_Newbie on 2008-04-25
Hmmm.. how green am i? I dont know its one my friend put together.

---

### Post by Neil_The_Newbie on 2008-04-25
Thank you. i did that in terminal and got this:

00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: 66MHz, fast devsel

00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: 66MHz, fast devsel

00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at e400 [size=32]
	Capabilities: <access denied>

00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at e9003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at e9004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at e9005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 570c
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at e9000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at d000 [size=8]
	Capabilities: <access denied>

00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
	Subsystem: Micro-Star International Co., Ltd. Unknown device 5700
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	I/O ports at d400 [size=256]
	I/O ports at d800 [size=128]
	Memory at e9001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e8000000-e8ffffff

00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f462:5700
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>

00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 32
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Memory behind bridge: e6000000-e7ffffff
	Prefetchable memory behind bridge: e4000000-e5ffffff

01:07.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 04 [Hayes/16750])
	Subsystem: PCTel Inc Unknown device 0001
	Flags: medium devsel, IRQ 16
	I/O ports at c000 [size=64]
	Capabilities: <access denied>

01:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04) (prog-if 10 [OHCI])
	Subsystem: Pinnacle Systems Inc. Unknown device 000e
	Flags: bus master, medium devsel, latency 32, IRQ 20
	Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 0221
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 10
	Memory at e6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e4000000 (32-bit, prefetchable) [size=32M]
	[virtual] Expansion ROM at e7000000 [disabled] [size=64K]
	Capabilities: <access denied>

---

### Post by martrn on 2008-04-25
You are Using a [http://www.nvidia.com/page/nforce.html]("http://www.nvidia.com/page/nforce.html") NVidia NForce 2 RIVA TNT2 Model 64 Graphics Card, that is sharing your memory with your system, (Possiable an inbuilt graphics card on the motherboard.

---

### Post by Neil_The_Newbie on 2008-04-25
thanks - i seem to have it working!

should i be able to use the fancy desktop effects with this type of card?

---

### Post by Eclipse. on 2008-04-25
I doubt it, the TNT2 card is really old, I had it in a old pc and couldn't get compiz or anything to work.

---

