---
title: "Update killed my wireless card"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Sprogg2001 on 2008-06-05
Last night Hardy installed an update kernel related I think, and since it rebooted my internal wireless card is missing it was working fine before.  On install it was detected without the need for ndis wrapper or restricted drivers.

I have tried using system info and ```
lspci -v | less
```
but this shows no wireless hardware at all. :confused:

what do I do to get wireless support back, please can you help?

---

### Post by philinux on 2008-06-05
Boot up, when you see grub stage 1.5 press esc.

When you get the grub loader page up select the previous kernel.

Then report the bug at launchpad.

Kernel 18 has broken wireless, wired internet , etc etc

---

### Post by cdtech on 2008-06-05
I've been working on this issue for a few day's now. Every one that used ndiswrapper has a broken wireless connection now. The way I got mine to work was to use version 4.80.53.0 of Broadcom's proprietary driver.

#blacklist bcm43xx and nothing extra you hear about. Reload modules ndiswrapper and then b43. I also set up my interfaces for static ip along with wpa2 security. I had an issue of timing out after 15 seconds or so and had to reload the modules then ifup just to get back on the net.

I'm still looking into what the problem consist of and a solution, although the above has me on the internet at least.

---

### Post by Sprogg2001 on 2008-06-05
> **cdtech said:**
> I've been working on this issue for a few day's now. Every one that used ndiswrapper has a broken wireless connection now. The way I got mine to work was to use version 4.80.53.0 of Broadcom's proprietary driver.

#blacklist bcm43xx and nothing extra you hear about. Reload modules ndiswrapper and then b43. I also set up my interfaces for static ip along with wpa2 security. I had an issue of timing out after 15 seconds or so and had to reload the modules then ifup just to get back on the net.

I'm still looking into what the problem consist of and a solution, although the above has me on the internet at least.

sorry cdtech as I mentioned before I don't think I use ndis wrapper to get wireless working so I don't think this apply's to me.

> Boot up, when you see grub stage 1.5 press esc.

When you get the grub loader page up select the previous kernel.

Then report the bug at launchpad.

Kernel 18 has broken wireless, wired internet , etc etc 

philinux I followed your advice booted up used grub to boot 2.6.24-17
Result still no wireless :confused:
So I used grub again booted to 2.6.24-16
Result still no wireless :confused:

I used a combination of sys info and lspci -v and could not see any evidence of a wireless network device on my system. However in network manager I could see the option to configure my wireless. I typed in my network password and presto its working.

Since this is a new laptop Ive only had it a week its a really cheap no name brand without documentation but It does have "internal wireless"
which is now working? 

**My question now is how is it working exactly what model wireless card do I have.** I know enough about computers to be able to break stuff with alarming regularity :biggrin: but I think I may have missed something.

Below is my lspci -v output 

thanks again for everyones help.

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
	Subsystem: Elitegroup Computer Systems Unknown device 5050
	Flags: bus master, medium devsel, latency 32
	Memory at a0000000 (32-bit, non-prefetchable) [size=256M]
	Capabilities: [c0] AGP version 3.5

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: b0000000-b00fffff
	Prefetchable memory behind bridge: c0000000-cfffffff

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 128, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1080 [size=16]
	Capabilities: [58] Power Management version 2

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at b0104000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at b0105000 (32-bit, non-prefetchable) [size=4K]

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at b0106000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 2

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at b0307000 (32-bit, non-prefetchable) [size=128]
	I/O ports at 1000 [size=128]
	Capabilities: [40] Power Management version 2

00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Silicon Integrated Systems [SiS] SATA Controller / IDE mode
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at 10c8 [size=8]
	I/O ports at 10bc [size=4]
	I/O ports at 10c0 [size=8]
	I/O ports at 10b8 [size=4]
	I/O ports at 10a0 [size=16]
	Capabilities: [58] Power Management version 2

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
	Subsystem: Elitegroup Computer Systems Unknown device 5a00
	Flags: bus master, medium devsel, latency 0, IRQ 22
	Memory at b0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10) (prog-if 00 [VGA controller])
	Subsystem: Elitegroup Computer Systems Unknown device 5050
	Flags: 66MHz, medium devsel, IRQ 9
	BIST result: 00
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0000000 (32-bit, non-prefetchable) [size=128K]
	I/O ports at 9000 [size=128]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] AGP version 3.0

```

P.S. How do I mark this thread as solved?

---

