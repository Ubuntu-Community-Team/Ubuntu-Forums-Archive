---
title: "usb ports don't work"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by drdedd on 2008-09-02
I've loaded Hardy Heron on an Acer 5102 that my son discarded when Windows crashed the whole box. Everything seems to work well, except no external usb devices are detected, and the system log returns an error message on start-up of "maybe usb cable is bad?" Here's the "lsusb -v". 


dave@dave-laptop:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Capabilities: <access denied>

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Capabilities: <access denied>

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	Capabilities: <access denied>

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: 66MHz, medium devsel
	I/O ports at 8400 [size=16]
	Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 82 [Master PriP])
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=06, subordinate=08, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c0200000-c02fffff

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

01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>

06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at a000 [size=256]
	Memory at c0210000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: AMBIT Microsystem Corp. Unknown device 0418
	Flags: bus master, medium devsel, latency 168, IRQ 22
	Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at c0211000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=07, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001

06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at c0210400 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>

06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at c0210800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at c0210c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>

06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Unknown device 009f
	Flags: medium devsel, IRQ 23
	Memory at c0210100 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

---

### Post by crispy_420 on 2008-09-02
Did you try from LiveCD?

---

### Post by drdedd on 2008-09-03
Thanks for the response; I tried LiveCD, but no usb devices were found. Earlier I contacted Acer support, but they are Windows-based only. Their advice was to remove the usb controller through the device manager, reboot, and let the system re-install the controller. Looking at the "lsusb -v", I'm concerned about the "access denied" message, but I readily admit to being new to this process -

---

### Post by crispy_420 on 2008-09-03
So they gave you Windows based help. 

What type of USB devices have you tried?

---

### Post by drdedd on 2008-09-03
Digital camera, 2G FAT32 stick, mouse, wireless mouse & keyboard, external HD

---

### Post by crispy_420 on 2008-09-03
Well that covers just about every option...

Could these be a root access issue? You do have sudo rights?

---

### Post by drdedd on 2008-09-03
I have used "sudo" commands, but this is new territory for me. It's a good time to teach myself.

---

### Post by drdedd on 2008-09-04
As a follow-on to the results of my "lsusb-v", I've tried to compare my results with other usb threads. This segment seems to be part of the problem:

"can't get hub descriptor: Operation not permitted
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)"

Any thoughts, please?

Also, proc/bus/usb/devices" does not exist as a directory.

---

### Post by crispy_420 on 2008-09-04
Seems this guy got it running fine with Debian (close enough):

[http://www.burghardt.pl/2007/11/debian-gnulinux-on-acer-aspire-5102wlmi/](http://www.burghardt.pl/2007/11/debian-gnulinux-on-acer-aspire-5102wlmi/)

He also has contact info for him if you are interested.

I'm sorry I can not help more but if I come across something else of interest, I will pass it on to you.

Here are some success stories, maybe contact one of these guys via forums and compare command line outputs or see if they had issues:

[http://ubuntuforums.org/showthread.php?t=263997](http://ubuntuforums.org/showthread.php?t=263997)

---

### Post by drdedd on 2008-09-05
Thanks for the leads - I'll let you know. Aside from my lack of familiarity with the programming issues, I'm also dealing with a potentially damaged box. I'd like to pursue programming before I start to rip out parts. For what it's worth,Ubuntu is a remarkable program, since it got this machine to boot up, where Windows couldn't - that's impressive, aside from the other components which are very effective.

---

### Post by crispy_420 on 2008-09-06
Have you tried any other distros?

Look at Elive, it also is debian based and provides great hardware support:

[http://distrowatch.com/table.php?distribution=elive](http://distrowatch.com/table.php?distribution=elive)

I used it on a low-end/old Dell and it just worked, some issues, but it worked great. This old guy is Intel 700MHz, 320MB RAM, 20GB HD, Atheros wireless, etc.

---

### Post by cwmoser on 2008-09-06
Try:

sudo  modprobe  -r  ehci-hcd



I just started playing with a 7 port USB hub and was having problems too.

What I found from searching the web is that there is bug in the current Linux kernel dealing with "ehci-hcd" and should be fix with the 2.6.27 kernel. I have Ubuntu Hardy and it uses kernel 2.6.24.

A temporary fix is to issue this:

sudo modprobe -r ehci-hcd

every time you boot Ubuntu. What I read is that ehci-hcd handles USB 2.0 and without ehci-hcd you will have degraded to USB 1.1.

Also, I found that while my two USB thumb drives and camera Smart Media reader works just fine in my new USB Hub, I found that neither of my USB hard drives would work. So, for the time being, I got my USB hard drives connected to direct ports in my PC - i.e. not using the hub.

Carl
cwmoser is online now Report Post   	Edit/Delete Message

---

