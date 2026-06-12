---
title: "Ubuntu not liking HP DV6810us"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by Jim2029 on 2008-06-28
I just bought this laptop, a HP DV6810us. None of my Ubuntu's will run. None of them ever come up to a desktop. I have tried 6.06LTS ubuntu, 7.10 Kubuntu, and another ubuntu verson. I have not tried the new one yet. BUT Puppy Linux 4 boots and runs... 

In ubuntu, I get a video warning. I ahve tried in regular and safe graphics mode... and i have tried every setting. I have also tried the 32 bit as well as the 64 bit since this laptop has a AMD TL-60 Processor.

Any ideas? I have wipped vista and put XP on it, but its a matter of time before XP is no longer useable and I will NOT goto vista.

Thanks
Jim

---

### Post by schwascore on 2008-06-29
The link below should help you get started.  My wife has a DV6*** series and it took a while to get set up right but now the thing flies on 8.4.

[https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

---

### Post by Jim2029 on 2008-07-01
Thanks, I'll check it out.

---

### Post by Jim2029 on 2008-07-01
I tried all it says and still no luck.

noacpi nolacpi = Stuck at Loading scripts with a "_" under everything.

noacpi nolacpi noirqpoll nosmp = Freezes at Ubuntu Loading screen with the orange bar.

-noacpi -irqfixup Same as first.

Any others ideas?

---

### Post by ibuclaw on 2008-07-01
Are you trying 32 or 64bit version?

I managed to get my dv2750ea up pretty much hitchless (the only major alteration was the flashing of BIOS to the most recent version for my laptop to unlock certain features such as cpufreq).

Also, have you tried loading the LiveCD with safe settings?

Regards
Iain

---

### Post by Jim2029 on 2008-07-06
I have tried both 32 and 64 bit both in regular and safe mode. I just order a copy of the newest version in 64 bit. I have tried PuppyLinux 4 and it works just fine.

---

### Post by Jim2029 on 2008-07-15
8.04 64 bit came in the mail today and it BOOTS!!!! now how do I get my video to go bigger than 800x600? and it says its using restricted drivers for my wifi but I don't see my wifi anywhere... but bluetooth is working and there on the same card, i think.

---

### Post by phidia on 2008-07-15
Your going to want to install the nvidia propritary driver to get the screen rez you want and better graphics. That should be pretty simple-well I'm presuming your laptop has the nvidia geforce 7150M but HP has a lot of variety in that series.
You could open a terminal and paste this > lspci -v then post the output of that. The results of that command should provide your gpu and network card too.
Ok I looked at you sig _after_ I posted the above. Just try clicking System>Administration>Hardware Drivers. Your video card should show up there. Enable it and reboot.
Still provide the output of that command so we know for sure what network card you have.

BTW I have a similar HP laptop. If you have the atheros ar5007eg network card (which can be made to work thru madwifi or ndiswrapper) you may find resume from suspend is flakey-not working. That's been my experience anyway.

---

### Post by Jim2029 on 2008-07-18
Thanks for your help. For now I'm using VMWare and have it installed on a virtual machine using NAT for networking and its running great. Once I get more fimilar with installing things and fine linux versions for everything I use in windows I'll blow vista off this thing and install linux to the hard drive.

One thing I have a problem is where I live there is only dialup. Ubuntu 6.xx had a button to click to dialup onto the internet. I have noticed on the later versions that this is no longer there. How do you use dialup on the newer version of ubuntu? Right now its not a problem for me cause I can dialup in vista and NAT VMWare to it.

---

### Post by phidia on 2008-07-18
There is a dialup guide [here]("https://help.ubuntu.com/community/DialupAndFax"). One problem you can encounter though is that almost all internal modems now are designed to use the windows operating system-they're called controllerless modems because some hardware functions were turned over to the operating system. Many of these winmodems can be made to work, but if you are primarily using this at home I suggest you get a serial port external modem-they don't cost that much and are much easier to set up.

---

### Post by Jim2029 on 2008-07-20
all i have is USB ports and I ahve had my share of trouble of usb modems.

---

### Post by Jim2029 on 2008-07-20
> **phidia said:**
> Your going to want to install the nvidia propritary driver to get the screen rez you want and better graphics. That should be pretty simple-well I'm presuming your laptop has the nvidia geforce 7150M but HP has a lot of variety in that series.
You could open a terminal and paste this  then post the output of that. The results of that command should provide your gpu and network card too.
Ok I looked at you sig _after_ I posted the above. Just try clicking System>Administration>Hardware Drivers. Your video card should show up there. Enable it and reboot.
Still provide the output of that command so we know for sure what network card you have.

BTW I have a similar HP laptop. If you have the atheros ar5007eg network card (which can be made to work thru madwifi or ndiswrapper) you may find resume from suspend is flakey-not working. That's been my experience anyway.
I'm now longer using VMWare. I ahve done a full install.
here is what i get...
 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f6200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f6486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f6489000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at f6487000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f6489400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f03c:30cf
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	Memory behind bridge: f6100000-f61fffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 509
	I/O ports at 30f0 [size=8]
	I/O ports at 30e4 [size=4]
	I/O ports at 30e8 [size=8]
	I/O ports at 30e0 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at f6484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 508
	Memory at f6488000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30f8 [size=8]
	Memory at f6489c00 (32-bit, non-prefetchable) [size=256]
	Memory at f6489800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f2000000-f3ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: f6000000-f60fffff
	Capabilities: <access denied>

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at f6100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 7
	Memory at f6100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f6100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f6101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
now what?

---

