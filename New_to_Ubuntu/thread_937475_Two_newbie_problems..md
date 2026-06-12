---
title: "Two newbie problems."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Haruki-kun on 2008-10-03
Hi! I'm a new user. I'm dual-booting Ubuntu and Windows XP Pro. I tried to use that thread near the top for help, but I was unable to... :(

Now, see, I have two problems.

**Problem Number 1:**
This one is Network-related. I noticed that I was unable to connect to any Wireless Network. (This is an Acer Laptop.) I checked how to, went to the network menu, but the Wireless Network wasn't appearing where I understood it was supposed to. I talked to a friend of mine via the Internet about it, but he uses a Desktop, so he never had that problem. He suggested that the Network Card might be off, so I booted Ubuntu and checked the usually-flashing network light. It was off. Unfortunately, pushing the button next to the light didn't do anything, so my friend told me I had to configure it manually, which neither of us knows how to do. Can anyone explain to me how this is done?

**Problem Number 2:**
Graphics-Related. I noticed that the resolution was.... well, everything looked too big and zoomed in. (I'm not sure if that's called big or small resolution.) The same friend told me where to change the resolution, so I did. Unfortunately, there were only two options, the one that I was using, and the other one, which zooms me in so much I can't even see the bottom of the menu... He said then I had to manually configure the Video Card, which is, again, something I don't know how to do. Can anyone help me out here?

Those are the two main problems I currently have. Can you guys help me please? Thanks a lot!

---

### Post by Ptero-4 on 2008-10-03
For both problems:
Type ```
lspci -v
```
in the terminal (Applications, Accesories, Terminal) and paste the result.
That info will allow us to know which wifi and video card you got and which drivers may be needed.

---

### Post by Haruki-kun on 2008-10-03
Alright, here's the result:

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1d00 [size=256]

00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
	Subsystem: nVidia Corporation Unknown device cb84
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f4200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at f4486000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at f4489000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at f4487000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f4489400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f025:0127
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 30c0 [size=16]
	Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at f4480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: f4100000-f41fffff
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 221
	I/O ports at 30f0 [size=8]
	I/O ports at 30e4 [size=4]
	I/O ports at 30e8 [size=8]
	I/O ports at 30e0 [size=4]
	I/O ports at 30d0 [size=16]
	Memory at f4484000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220
	Memory at f4488000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30f8 [size=8]
	Memory at f4489c00 (32-bit, non-prefetchable) [size=256]
	Memory at f4489800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: f4000000-f40fffff
	Capabilities: <access denied>

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
	Memory at f3000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f2000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at f0000000 [disabled] [size=128K]
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

01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at f4100000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f4100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f4100c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Acer Incorporated [ALI] Unknown device 0127
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f4101000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Unknown device 1a32:0105
	Flags: fast devsel, IRQ 18
	Memory at f4000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

---

### Post by Haruki-kun on 2008-10-05
Can anyone help me? I really need help here. :(

---

### Post by Jazzy_Jeff on 2008-10-05
Have you gone into System>Administration>Hardware Drivers. You should be able to get it working through there. I am using an acer as well.

---

### Post by divinequran on 2008-10-05
Use **modprobe** command and make sure that the required modules are installed properly.

If you cant find the particular module, try to get the required rpm from your vendor or download in from any other site and install the required module.

---

### Post by Ptero-4 on 2008-10-05
Your graphics card can work via the restricted drivers, or using the application "envy" to install the proper Nvidia drivers (you got a GeForce 7000M), your ethernet should probably work too (dunno, never had an Nvidia branded netowrk card, had sungem, rtl8139 and marvell, all three supported OOTB by the kernel).

---

### Post by tariquepark on 2008-10-05
hi there
try this thread for your wireless
[http://ubuntuforums.org/showthread.php?t=816780&highlight=AR242x+ATHEROS](http://ubuntuforums.org/showthread.php?t=816780&highlight=AR242x+ATHEROS)
as for your graphics go
Applications > System > Hardware Drivers
and enable them there. it will download the packages it needs automatically then ask you to reboot

cheers

---

### Post by Haruki-kun on 2008-10-05
> **Jazzy_Jeff said:**
> Have you gone into System>Administration>Hardware Drivers. You should be able to get it working through there. I am using an acer as well.

I got [this.]("http://i163.photobucket.com/albums/t288/Vaarsuvius89/Screenshot-1.png") What should I do now?

> **tariquepark said:**
> hi there
try this thread for your wireless
[http://ubuntuforums.org/showthread.php?t=816780&highlight=AR242x+ATHEROS](http://ubuntuforums.org/showthread.php?t=816780&highlight=AR242x+ATHEROS)
as for your graphics go
Applications > System > Hardware Drivers
and enable them there. it will download the packages it needs automatically then ask you to reboot

cheers

OK, this thread told me first to try to get the build-essential, but my result was:
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

Also, I got a 404 from trying to enable the Graphics driver.

---

### Post by tariquepark on 2008-10-05
are you on the net with a lan cable?
can you run in a terminal
uname -a

---

### Post by Haruki-kun on 2008-10-05
Currently, I'm using an Ethernet cable. Result of running uname-a:
Linux juan-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

---

### Post by hyper_ch on 2008-10-05
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

### Post by tariquepark on 2008-10-05
ok in a terminal try
sudo apt-get update
sudo apt-get install build-essientials

if you get errors check that multiverse and universe repositorys are enabled
Aplications > System > Software Sources
also you can select from a load of different servers so choose one thats close to you geographically speaking

---

### Post by Haruki-kun on 2008-10-05
> **tariquepark said:**
> ok in a terminal try
sudo apt-get update
sudo apt-get install build-essientials

if you get errors check that multiverse and universe repositorys are enabled
Applications > System > Software Sources
also you can select from a load of different servers so choose one thats close to you geographically speaking

I keep getting the error message... and I can't find the repositories you mentioned. I just managed to download two applications successfully, aMSN and Inkscape, but I still can't get the Wireless to work, OR the Graphics card...

hyper_ch: Heh... good point. Changed the Thread title. :redface:
EDIT: Looks like title doesn't change... I'll keep it in mind for next time, though, thanks.

---

### Post by howlingmadhowie on 2008-10-05
you can switch the graphics card on in the hardware drivers window you opened earlier by clicking on the middle checkbox (the one next to nvidia)

---

### Post by Haruki-kun on 2008-10-05
> **howlingmadhowie said:**
> you can switch the graphics card on in the hardware drivers window you opened earlier by clicking on the middle checkbox (the one next to nvidia)

WHOOO!!! It worked!

One problem down, just one more to go.

Question: It says I have... 125 updates now available. Is that normal?

---

### Post by howlingmadhowie on 2008-10-05
> **Haruki-kun said:**
> WHOOO!!! It worked!

One problem down, just one more to go.

Question: It says I have... 125 updates now available. Is that normal?

yeah, that's normal. the install disks were created a number of months ago and new functionalities and bugfixes have come through since then. it would be a good idea to install the updates now.

---

