---
title: "wireless internet connection"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-09-14
hellow,

how can i run a wireless internet connection?

mvg
Dadsgé

---

### Post by Zzl1xndd on 2008-09-14
Normally if your wireless card is connected its as simple as clicking on the network manager and connecting to whatever networks are available. 

If you are unable to connect that way you likely need some type of driver or there is some extra configuration you will need to do, and in that case we will need a little more info. Like the Make and Model of your Laptop/desktop or preferably the make and model of the Wireless card.

---

### Post by bobnutfield on 2008-09-14
You use a wireless card to connect to a router that is connected to the internet.....

Seriously, though, you will need to provide a lot more information to get help on that.

What wireless card to do you have?  Are you currently wired to a router?

---

### Post by Dadsgé on 2008-09-14
now i'm wired to internet

model of my laptop:
asus eee (the one of 4GB)
and I dont know the name of my wireless card... 
U can probably halp me find it :)

---

### Post by Zzl1xndd on 2008-09-14
My buddy got everything working on his Eee using the info over at eeeuser.com.

Hope this helps

[http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly?s=ubuntu](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly?s=ubuntu)

---

### Post by bobnutfield on 2008-09-14
Type in a terminal:

> sudo lspci | grep network

---

### Post by nothingspecial on 2008-09-14
Open a terminal (in your menus accessories > terminal) and copy and paste -

```
lspci -v
```

Copy and paste what it tells you here.

---

### Post by Dadsgé on 2008-09-14
ah nice site :o
all my problems are explaned there :P
really thanx ;)

---

### Post by Zzl1xndd on 2008-09-14
Not a problem, I have 3 friends that have Eee's and they all got them working with the same set of instructions. Oh and if that did fix your problem please mark this as solved.

---

### Post by Dadsgé on 2008-09-14
i did the lspci -v thing
gives me this:
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7f00000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ec00 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f7ec0000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d9
	Flags: bus master, fast devsel, latency 0
	Memory at f7f80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82a1
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f7eb8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fbf00000-fbffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
	Memory behind bridge: f8000000-fbefffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f6ffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e400 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at e480 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f7eb7c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
	Subsystem: ASUSTeK Computer Inc. Unknown device 82d8
	Flags: medium devsel
	I/O ports at 0400 [size=32]

03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8233
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbfc0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at fbfa0000 [disabled] [size=128K]
	Capabilities: <access denied>


---

### Post by bobnutfield on 2008-09-14
Your ethernet (wired) is listed, but I don't see a wireless chipset.  Try:

> sudo lsusb

to see if it is an internal wireless USB chipset.  Some are.  Not familiar with EEEPC, but I believe it does come with wireless.

---

### Post by Dadsgé on 2008-09-14
ok, if i follow that instruction:
> Bus 005 Device 002: ID 0951:1606 Kingston Technology 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


---

