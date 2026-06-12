---
title: "network adaptor problems"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by daveart on 2008-09-03
Hi Im a newbee to linux I have installed ubuntu 8.04 to run side by side with windows xp I have a network adaptor and a netgear wireless router attached to which was working fine until I install ubuntu now it niether works in windows or linux in windows I now have a no start code 10. I have tried always that I know of to get it working to no avail I can not even uninsatll ubuntu. Can any one give me any sugestions.

Thanks Dave

---

### Post by nothingspecial on 2008-09-03
We need some more info. Open a terminal (accessories > terminal) and type 
```
lspci -v
```
Then copy the output here.

---

### Post by daveart on 2008-09-03
This is the terminal output, hope this is what you wanted.


00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, 66MHz, medium devsel, latency 8 
	Memory at f8000000 (32-bit, prefetchable) [size=64M] 
	Capabilities: <access denied> 

00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 0 

00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 0 

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge 
	Flags: bus master, medium devsel, latency 0 

00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 0 

00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 0 

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode]) 
	Flags: bus master, 66MHz, medium devsel, latency 0 
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
	I/O behind bridge: 0000a000-0000cfff 
	Memory behind bridge: ff500000-ff5fffff 
	Prefetchable memory behind bridge: b7f00000-f7efffff 
	Capabilities: <access denied> 

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO]) 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 64, IRQ 16 
	I/O ports at ec00 [size=8] 
	I/O ports at e880 [size=4] 
	I/O ports at e800 [size=8] 
	I/O ports at e480 [size=4] 
	I/O ports at e400 [size=16] 
	I/O ports at e000 [size=256] 
	Capabilities: <access denied> 

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP]) 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 32, IRQ 16 
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8] 
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1] 
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8] 
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1] 
	I/O ports at fc00 [size=16] 
	Capabilities: <access denied> 

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI]) 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 64, IRQ 17 
	I/O ports at dc00 [size=32] 
	Capabilities: <access denied> 

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI]) 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 64, IRQ 17 
	I/O ports at d880 [size=32] 
	Capabilities: <access denied> 

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI]) 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 64, IRQ 17 
	I/O ports at d800 [size=32] 
	Capabilities: <access denied> 

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI]) 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 64, IRQ 17 
	I/O ports at d480 [size=32] 
	Capabilities: <access denied> 

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI]) 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, medium devsel, latency 64, IRQ 17 
	Memory at ff6ffc00 (32-bit, non-prefetchable) [size=256] 
	Capabilities: <access denied> 

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] 
	Subsystem: Elitegroup Computer Systems Unknown device 1623 
	Flags: bus master, stepping, medium devsel, latency 0 
	Capabilities: <access denied> 

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60) 
	Subsystem: Elitegroup Computer Systems Unknown device aa51 
	Flags: medium devsel, IRQ 18 
	I/O ports at d000 [size=256] 
	Capabilities: <access denied> 

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600] (prog-if 00 [VGA controller]) 
	Subsystem: Hightech Information System Ltd. Unknown device 4152 
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19 
	Memory at e0000000 (32-bit, prefetchable) [size=256M] 
	I/O ports at c000 [size=256] 
	Memory at ff5f0000 (32-bit, non-prefetchable) [size=64K] 
	Expansion ROM at ff5c0000 [disabled] [size=128K] 
	Capabilities: <access denied> 

01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary) 
	Subsystem: Hightech Information System Ltd. Unknown device 4153 
	Flags: bus master, 66MHz, medium devsel, latency 64 
	Memory at d0000000 (32-bit, prefetchable) [size=256M] 
	Memory at ff5e0000 (32-bit, non-prefetchable) [size=64K] 
	Capabilities: <access denied>

---

### Post by nothingspecial on 2008-09-03
Sorry, is it a usb wireless device, in that case 

```
lsusb
```

(ls is asking the terminal to list something, so lsusb is asking the terminal to tell you everything plugged into your usb sockets, likewise lspci)

What I`m trying to find out is what sort of wireless device you have to see if we can fix it.

---

### Post by daveart on 2008-09-03
I have a Via Technologies Rhino II network adaptor which is not usb. The only usbs are for the printer, mouse and ext hard drive and are working fine.
Any help gratefully received!

---

### Post by nothingspecial on 2008-09-03
Ok this is strange because I can`t see your wireless card in the output of lspci.

Can you post the output of
```

lshw -C Network
```

---

### Post by daveart on 2008-09-03
Hi I have run lshw -C network
in the terminal and all I got back was lshw version formats and options etc. Nothing about network or anything else really.

Dave

---

### Post by daveart on 2008-09-05
Hi I seem to have the network up and running but it is a bit hit and miss, as when I shut down or switch to windows xp, I loose my network again in both linux and xp. The only way I have managed to get it back is to crash widows and pull the power lead out then wait a minute or two before reconnecting, then it all re-appears, and ideas waht is going on.

Much appreciate it
Daveart

---

