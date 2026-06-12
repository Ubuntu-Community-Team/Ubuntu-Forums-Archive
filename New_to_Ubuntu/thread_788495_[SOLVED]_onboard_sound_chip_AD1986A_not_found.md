---
title: "[SOLVED] onboard sound chip AD1986A not found"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Nebelhom on 2008-05-09
Hi,

I got a slightly different problem to most other ppl with this chip.

System:
Running Hardy Heron (8.04)
Asus P5VD2-VM motherboard with AD1986A sound chip
GeForce 7600GS
Intel Core2 CPU
6420 @ 2.13GHz
2.00 GB RAM

after running a general lspci and lspic | grep -i audio, no output about sound card was given and gstreamer does not find anything although I installed various packages.
I am pretty certain that drivers arent missing, it's just that the kernel seems not to acknowledge that there is a sound card onboard of my motherboard.
There is no sound and I am sure the hardware isnt defect as it works in windows and when I had problems configuring my graphics card, I had sound sometimes when I didnt have a picture.

It would really helpful if people who have experience with this problem would give feedback.

Thanks already guys,

Nebelhom

---

### Post by Nebelhom on 2008-05-10
would ubuntu usually at least recognise that a device is present? I looked for drivers but it seems that the drivers list I found on the asus page only goes to ad1985 for linux so this type of chip card should be known, no?

---

### Post by happyhamster on 2008-05-10
Are there any messages in your logs about that soundcard? Try:

dmesg | grep codec -i
dmesg | grep 1986 -i
etc..

According to the ALSA guide, the card is supported by the snd-hda-intel module.

```

  Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
    single_cmd  - Use single immediate commands to communicate with
		codecs (for debugging only)
    disable_msi - Disable Message Signaled Interrupt (MSI)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

	  Model name	Description
	  ----------    -----------
	ALC880
	  3stack	3-jack in back and a headphone out
	  3stack-digout	3-jack in back, a HP out and a SPDIF out
	  5stack	5-jack in back, 2-jack in front
	  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
	  6stack	6-jack in back, 2-jack in front
	  6stack-digout	6-jack with a SPDIF out
	  w810		3-jack
	  z71v		3-jack (HP shared SPDIF)
	  asus		3-jack (ASUS Mobo)
	  asus-w1v	ASUS W1V
	  asus-dig	ASUS with SPDIF out
	  asus-dig2	ASUS with SPDIF out (using GPIO2)
	  uniwill	3-jack
	  F1734		2-jack
	  lg		LG laptop (m1 express dual)
	  lg-lw		LG LW20/LW25 laptop
	  tcl		TCL S700
	  clevo		Clevo laptops (m520G, m665n)
	  test		for testing/debugging purpose, almost all controls can be
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC260
	  hp		HP machines
	  hp-3013	HP machines (3013-variant)
	  fujitsu	Fujitsu S7020
	  acer		Acer TravelMate
	  basic		fixed pin assignment (old default model)
	  auto		auto-config reading BIOS (default)

	ALC262
	  fujitsu	Fujitsu Laptop
	  hp-bpc	HP xw4400/6400/8400/9400 laptops
	  benq		Benq ED8
	  basic		fixed pin assignment w/o SPDIF
	  auto		auto-config reading BIOS (default)

	ALC882/885
	  3stack-dig	3-jack with SPDIF I/O
	  6stck-dig	6-jack digital with SPDIF I/O
	  arima		Arima W820Di1
	  auto		auto-config reading BIOS (default)

	ALC883/888
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  auto		auto-config reading BIOS (default)

	ALC861/660
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack with SPDIF I/O
	  3stack-660	3-jack (for ALC660)
	  uniwill-m31	Uniwill M31 laptop
	  auto		auto-config reading BIOS (default)

	CMI9880
	  minimal	3-jack in back
	  min_fp	3-jack in back, 2-jack in front
	  full		6-jack in back, 2-jack in front
	  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
	  allout	5-jack in back, 2-jack in front, SPDIF out
	  auto		auto-config reading BIOS (default)

	AD1981
	  basic		3-jack (default)
	  hp		HP nx6320
	  thinkpad	Lenovo Thinkpad T60/X60/Z60

	AD1986A
	  6stack	6-jack, separate surrounds (default)
	  3stack	3-stack, shared surrounds
	  laptop	2-channel only (FSC V2060, Samsung M50)
	  laptop-eapd	2-channel with EAPD (Samsung R65, ASUS A6J)

	AD1988
	  6stack	6-jack
	  6stack-dig	ditto with SPDIF
	  3stack	3-jack
	  3stack-dig	ditto with SPDIF
	  laptop	3-jack with hp-jack automute
	  laptop-dig	ditto with SPDIF
	  auto		auto-config reading BIOS (default)

	STAC9200/9205/9220/9221/9254
	  ref		Reference board
	  3stack	D945 3stack
	  5stack	D945 5stack + SPDIF

	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF

	STAC9872
	  vaio		Setup for VAIO FE550G/SZ110
	  vaio-ar Setup for VAIO AR

    If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").

    Note 2: If you get click noises on output, try the module option
	    position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
	    register value without FIFO size correction as the current
	    DMA pointer.  position_fix=2 will make the driver to use
	    the position buffer instead of reading SD_LPIB register.
	    (Usually SD_LPLIB register is more accurate than the
	    position buffer.)

    NB: If you get many "azx_get_response timeout" messages at
    loading, it's likely a problem of interrupts (e.g. ACPI irq
    routing).  Try to boot with options like "pci=noacpi".  Also, you
    can try "single_cmd=1" module option.  This will switch the
    communication method between HDA controller and codecs to the
    single immediate commands instead of CORB/RIRB.  Basically, the
    single command mode is provided only for BIOS, and you won't get
    unsolicited events, too.  But, at least, this works independently
    from the irq.  Remember this is a last resort, and should be
    avoided as much as possible...
    
    The power-management is supported.
```

---

### Post by Nebelhom on 2008-05-10
Hi,

no unfortunately these commands give me the saem again, as in nothing. literally. command -> enter next input prompt.
I asked a friend who is quite experienced in using linux (not ubuntu in particular) and he found it very strange and had a dig around in my system and couldn't find my card... strangely.

>     If the default configuration doesn't work and one of the above
    matches with your device, report it together with the PCI
    subsystem ID (output of "lspci -nv") to ALSA BTS or alsa-devel
    ML (see the section "Links and Addresses").


I will try to find the contacts to alsa as said in the snd-hda-intel module and see what they say.

I dont know if it will help but I'll put the lspci output that I have down (i dont see an audio hardware)

Thanks for having a look at this and thanks for that code (now I know where to report to ;) )

Nebelhom

lspci:

```
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
04:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
04:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

---

### Post by happyhamster on 2008-05-10
A few things you could try to troubleshoot:

- Take a look in the computer's bios to see if onboard sound is enabled and if there are any settings you can change. HDA versus AC97 for example.

- If you have a live-cd around (gutsy, hardy), try booting it to see if it does recognize your card. 

- Try experimenting with a few bootparameters: acpi=noirq or acpi=off. You can add such a parameter in the grub menu when booting your system. From within that menu:

- Highlight the line "Ubuntu 8.04, kernel 2.6...." and press 'e' to edit.
- Now select the second line, "kernel /boot/vmlinuz...." and press 'e' again.
- You should see all boot parameters currently used (usually: ro quiet splash)
- Leave those parameters alone, just add acpi=noirq. Make sure there's a space between splash and acpi=noirq.
- Accept with the enter key.
- You're back to the previous page: press 'b' to boot.

- Check if anything has changed for the better. This procedure is pretty safe, because it's only temporary: at next boot, everything will be as before.

I'm not sure if I can be of any further help, but could you perhaps attach the entire dmesg log? Just issue:

dmesg > dmesg.txt

This will put the entire dmesg output into a text file for ease-of-use.

Oh, and this could be interesting as well:

cat /proc/interrupts

---

### Post by Nebelhom on 2008-05-11
I'm gonna try these ideas now. Thx! let's hope it works and below are the dmesg and proc.

> - Try experimenting with a few bootparameters: acpi=noirq or acpi=off. You can add such a parameter in the grub menu when booting your system.

as you will see in the dmesg. I have acpi=off already, prob due to the way I had to run my installation (noapic nolapic pci=noacpi acpi=off). should I just change the acpi=off to acpi=noirq?

```
[    0.000000] Linux version 2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] Command line: root=UUID=f3b205f2-a2c9-4c6a-b22d-1384f5751bb7 ro quiet splash noapic nolapic pci=noacpi acpi=off
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007fee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524000
[    0.000000] On node 0 totalpages: 523903
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1208 pages reserved
[    0.000000]   DMA zone: 2735 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7108 pages used for memmap
[    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: OEM00000 MPTABLE: Product ID: PROD00000000 MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] I/O APIC #4 at 0xFEC00000.
[    0.000000] I/O APIC #5 at 0xFECC0000.
[    0.000000] Setting APIC routing to flat
[    0.000000] Processors: 2
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 515531
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=f3b205f2-a2c9-4c6a-b22d-1384f5751bb7 ro quiet splash noapic nolapic pci=noacpi acpi=off
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PIT
[    0.000000] time.c: Detected 2128.084 MHz processor.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Checking aperture...
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2053704k/2096000k available (2466k kernel code, 41908k reserved, 1309k data, 316k init)
[    0.000000] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] Calibrating delay using timer specific routine.. 4260.45 BogoMIPS (lpj=8520919)
[    0.000000] Security Framework initialized
[    0.000000] SELinux:  Disabled at boot.
[    0.000000] AppArmor: AppArmor initialized
[    0.000000] Failure registering capabilities with primary security module.
[    0.000000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.000000] Mount-cache hash table entries: 256
[    0.000000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000000] CPU: L2 cache: 4096K
[    0.000000] CPU 0/0 -> Node 0
[    0.000000] using mwait in idle threads.
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 0
[    0.000000] CPU0: Thermal monitoring enabled (TM1)
[    0.000000] SMP alternatives: switching to UP code
[    0.000000] Early unpacking initramfs... done
[    0.000000] Using local APIC timer interrupts.
[    0.000000] APIC timer calibration result 16625673
[    0.000000] Detected 16.625 MHz APIC timer.
[    0.000000] SMP alternatives: switching to SMP code
[    0.000000] Booting processor 1/2 APIC 0x1
[    0.000000] Initializing CPU#1
[    0.000000] Calibrating delay using timer specific routine.. 4256.19 BogoMIPS (lpj=8512382)
[    0.000000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000000] CPU: L2 cache: 4096K
[    0.000000] CPU 1/1 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 1
[    0.000000] CPU1: Thermal monitoring enabled (TM1)
[    0.000000] Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
[    0.000000] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.000000] Brought up 2 CPUs
[    0.000000] CPU0 attaching sched-domain:
[    0.000000]  domain 0: span 03
[    0.000000]   groups: 01 02
[    0.000000]   domain 1: span 03
[    0.000000]    groups: 03
[    0.000000] CPU1 attaching sched-domain:
[    0.000000]  domain 0: span 03
[    0.000000]   groups: 02 01
[    0.000000]   domain 1: span 03
[    0.000000]    groups: 03
[    0.000000] net_namespace: 120 bytes
[    0.000000] Time: 11:23:15  Date: 05/11/08
[    0.000000] NET: Registered protocol family 16
[    0.000000] PCI: Using configuration type 1
[    0.000000] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.000000] mtrr: probably your BIOS does not setup all CPUs.
[    0.000000] mtrr: corrected configuration.
[    0.000000] ACPI: Interpreter disabled.
[    0.000000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.000000] pnp: PnP ACPI: disabled
[    0.000000] PCI: Probing PCI hardware
[    0.000000] PCI: Probing PCI hardware (bus 00)
[    0.000000] PCI: Transparent bridge - 0000:00:13.1
[    0.000000] NET: Registered protocol family 8
[    0.000000] NET: Registered protocol family 20
[    0.000000] PCI-GART: No AMD northbridge found.
[    0.000000] AppArmor: AppArmor Filesystem Enabled
[    0.000000] PCI: Bridge: 0000:00:01.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:02.0
[    0.000000]   IO window: a000-afff
[    0.000000]   MEM window: dc000000-deffffff
[    0.000000]   PREFETCH window: c0000000-cfffffff
[    0.000000] PCI: Bridge: 0000:00:03.0
[    0.000000]   IO window: b000-cfff
[    0.000000]   MEM window: dfe00000-dfefffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:13.1
[    0.000000]   IO window: 9000-9fff
[    0.000000]   MEM window: dfd00000-dfdfffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:13.1 to 64
[    0.000000] NET: Registered protocol family 2
[    0.000000] Time: tsc clocksource has been installed.
[    0.000000] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.000000] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.000000] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.000000] TCP: Hash tables configured (established 262144 bind 65536)
[    0.000000] TCP reno registered
[    0.000000] checking if image is initramfs... it is
[    0.000000] Freeing initrd memory: 8212k freed
[    0.000000] audit: initializing netlink socket (disabled)
[    0.000000] audit(1210504996.308:1): initialized
[    0.000000] VFS: Disk quotas dquot_6.5.1
[    0.000000] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.000000] io scheduler noop registered
[    0.000000] io scheduler anticipatory registered
[    0.000000] io scheduler deadline registered
[    0.000000] io scheduler cfq registered (default)
[    0.000000] PCI: VIA PCI bridge detected. Disabling DAC.
[    0.000000] Boot video device is 0000:02:00.0
[    0.000000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:02.0:pcie00]
[    0.000000] Allocate Port Service[0000:00:02.0:pcie02]
[    0.000000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:03.0:pcie00]
[    0.000000] Allocate Port Service[0000:00:03.0:pcie02]
[    0.000000] Real Time Clock Driver v1.12ac
[    0.000000] Linux agpgart interface v0.102
[    0.000000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    0.000000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.000000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.000000] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.000000] PNP: No PS/2 controller found. Probing ports directly.
[    0.000000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.000000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.000000] mice: PS/2 mouse device common for all mice
[    0.000000] cpuidle: using governor ladder
[    0.000000] cpuidle: using governor menu
[    0.000000] NET: Registered protocol family 1
[    0.000000] registered taskstats version 1
[    0.000000]   Magic number: 8:806:377
[    0.000000] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.000000] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.000000] EDD information not available.
[    0.000000] Freeing unused kernel memory: 316k freed
[    0.000000] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.000000] fuse init (API version 7.9)
[    0.000000] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    0.000000] SCSI subsystem initialized
[    0.000000] libata version 3.00 loaded.
[    0.000000] sata_via 0000:00:0f.0: version 2.3
[    0.000000] sata_via 0000:00:0f.0: routed to hard irq line 11
[    0.000000] scsi0 : sata_via
[    0.000000] scsi1 : sata_via
[    0.000000] ata1: SATA max UDMA/133 cmd 0xfc00 ctl 0xf800 bmdma 0xec00 irq 11
[    0.000000] ata2: SATA max UDMA/133 cmd 0xf400 ctl 0xf000 bmdma 0xec08 irq 11
[    0.000000] usbcore: registered new interface driver usbfs
[    0.000000] usbcore: registered new interface driver hub
[    0.000000] usbcore: registered new device driver usb
[    0.000000] USB Universal Host Controller Interface driver v3.0
[    0.000000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.000000] ata1.00: ATA-7: WDC WD3200AAJS-00RYA0, 12.01B01, max UDMA/133
[    0.000000] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (not used)
[    0.000000] ata1.00: configured for UDMA/133
[    0.000000] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    0.000000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-0 12.0 PQ: 0 ANSI: 5
[    0.000000] pata_via 0000:00:0f.1: version 0.3.3
[    0.000000] scsi2 : pata_via
[    0.000000] scsi3 : pata_via
[    0.000000] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    0.000000] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    0.000000] ata3.00: ATAPI: LITE-ON DVDRW LH-20A1H, LL06, max UDMA/66
[    0.000000] ata3.00: limited to UDMA/33 due to 40-wire cable
[    0.000000] ata3.00: configured for UDMA/33
[    0.000000] scsi 2:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL06 PQ: 0 ANSI: 5
[    0.000000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.000000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    0.000000] uhci_hcd 0000:00:10.0: irq 10, io base 0x0000e000
[    0.000000] usb usb1: configuration #1 chosen from 1 choice
[    0.000000] hub 1-0:1.0: USB hub found
[    0.000000] hub 1-0:1.0: 2 ports detected
[    0.000000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.000000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    0.000000] uhci_hcd 0000:00:10.1: irq 5, io base 0x0000dc00
[    0.000000] usb usb2: configuration #1 chosen from 1 choice
[    0.000000] hub 2-0:1.0: USB hub found
[    0.000000] hub 2-0:1.0: 2 ports detected
[    0.000000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.000000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    0.000000] uhci_hcd 0000:00:10.2: irq 3, io base 0x0000d800
[    0.000000] usb usb3: configuration #1 chosen from 1 choice
[    0.000000] hub 3-0:1.0: USB hub found
[    0.000000] hub 3-0:1.0: 2 ports detected
[    0.000000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    0.000000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    0.000000] uhci_hcd 0000:00:10.3: irq 11, io base 0x0000d400
[    0.000000] usb usb4: configuration #1 chosen from 1 choice
[    0.000000] hub 4-0:1.0: USB hub found
[    0.000000] hub 4-0:1.0: 2 ports detected
[    0.000000] ahci 0000:03:00.0: version 3.0
[    0.000000] PCI: Disallowing DAC for device 0000:03:00.0
[    0.000000] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    0.000000] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    0.000000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    0.000000] scsi4 : ahci
[    0.000000] scsi5 : ahci
[    0.000000] ata5: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe100 irq 11
[    0.000000] ata6: SATA max UDMA/133 abar m8192@0xdfefe000 port 0xdfefe180 irq 11
[    0.000000] ata5: SATA link down (SStatus 0 SControl 300)
[    0.000000] ata6: SATA link down (SStatus 0 SControl 300)
[    0.000000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    0.000000] PCI: Disallowing DAC for device 0000:04:07.0
[    0.000000] eth0: RTL8169sc/8110sc at 0xffffc20000896000, 00:1a:92:7c:2f:8f, XID 18000000 IRQ 10
[    0.000000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    0.000000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    0.000000] ehci_hcd 0000:00:10.4: irq 3, io mem 0xdffff000
[    0.000000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    0.000000] usb usb5: configuration #1 chosen from 1 choice
[    0.000000] hub 5-0:1.0: USB hub found
[    0.000000] hub 5-0:1.0: 8 ports detected
[    0.000000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[3]  MMIO=[dfdff000-dfdff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    0.000000] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[    0.000000] PCI: No IRQ known for interrupt pin B of device 0000:03:00.1. Please try using pci=biosirq.
[    0.000000] PCI: Setting latency timer of device 0000:03:00.1 to 64
[    0.000000] PCI: No IRQ known for interrupt pin B of device 0000:03:00.1. Please try using pci=biosirq.
[    0.000000] PCI: Setting latency timer of device 0000:03:00.1 to 64
[    0.000000] scsi6 : pata_jmicron
[    0.000000] Driver 'sd' needs updating - please use bus_type methods
[    0.000000] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    0.000000] sd 0:0:0:0: [sda] Write Protect is off
[    0.000000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.000000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    0.000000] sd 0:0:0:0: [sda] Write Protect is off
[    0.000000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.000000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000]  sda:<6>scsi7 : pata_jmicron
[    0.000000] ata7: PATA max UDMA/100 cmd 0xcc00 ctl 0xc800 bmdma 0xbc00
[    0.000000] ata8: PATA max UDMA/100 cmd 0xc400 ctl 0xc000 bmdma 0xbc08
[    0.000000] Driver 'sr' needs updating - please use bus_type methods
[    0.000000]  sda1 sda2 < sda5 sda6 sda7 >
[    0.000000] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.000000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.000000] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    0.000000] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.000000] Uniform CD-ROM driver Revision: 3.20
[    0.000000] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    0.000000] Attempting manual resume
[    0.000000] swsusp: Resume From Partition 8:7
[    0.000000] PM: Checking swsusp image.
[    0.000000] PM: Resume from disk failed.
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00110666000021e9]
[    0.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.000000] input: PC Speaker as /devices/platform/pcspkr/input/input2
[    0.000000] nvidia: module license 'NVIDIA' taints kernel.
[    0.000000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    0.000000] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[    0.000000] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[    0.000000] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE]
[    0.000000] parport0: irq 7 detected
[    0.000000] lp0: using parport0 (polling).
[    0.000000] Adding 2152668k swap on /dev/sda7.  Priority:-1 extents:1 across:2152668k
[    0.000000] EXT3 FS on sda6, internal journal
[    0.000000] ip_tables: (C) 2000-2006 Netfilter Core Team
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[    0.000000] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[    0.000000] ppdev: user-space parallel port driver
[    0.000000] audit(1210501411.978:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4434 profile="/usr/sbin/cupsd" namespace="default"
[    0.000000] r8169: eth0: link up
[    0.000000] Bluetooth: Core ver 2.11
[    0.000000] NET: Registered protocol family 31
[    0.000000] Bluetooth: HCI device and connection manager initialized
[    0.000000] Bluetooth: HCI socket layer initialized
[    0.000000] Bluetooth: L2CAP ver 2.9
[    0.000000] Bluetooth: L2CAP socket layer initialized
[    0.000000] Bluetooth: RFCOMM socket layer initialized
[    0.000000] Bluetooth: RFCOMM TTY layer initialized
[    0.000000] Bluetooth: RFCOMM ver 1.8
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] NET: Registered protocol family 17
[    0.000000] NET: Registered protocol family 10
[    0.000000] lo: Disabled Privacy Extensions
[    0.000000] eth0: no IPv6 routers present
```

```
          CPU0       CPU1       
  0:        118          0    XT-PIC-XT        timer
  1:        127          0    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  3:          2          0    XT-PIC-XT        uhci_hcd:usb3, ehci_hcd:usb5, ohci1394
  4:          1          0    XT-PIC-XT      
  5:          0          0    XT-PIC-XT        uhci_hcd:usb2
  7:          7          0    XT-PIC-XT      
  8:          0          0    XT-PIC-XT        rtc
 10:       1271          0    XT-PIC-XT        uhci_hcd:usb1, eth0
 11:      43662          0    XT-PIC-XT        sata_via, uhci_hcd:usb4, ahci, nvidia
 12:      25798          0    XT-PIC-XT        i8042
 14:       3762          0    XT-PIC-XT        libata
 15:          0          0    XT-PIC-XT        libata
NMI:          0          0   Non-maskable interrupts
LOC:      87273      87244   Local timer interrupts
RES:       2533       2494   Rescheduling interrupts
CAL:         95        241   function call interrupts
TLB:        435        505   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
SPU:          0          0   Spurious interrupts
ERR:          5
```

---

### Post by Nebelhom on 2008-05-11
I tried your ideas.

BIOS:

I found in Onboard Device configuration:
HDA Controller     [Auto] or [Disabled]

and in PCIPnP:

Assign IRQ for VGA     [Enabled]

I assumed that these are meaningful in someway. I didnt try them out cos from previous painful experience I know that I can really mess my PC up when playing around somewhere where I have no clue what it does.

Your idea of editing the Kernel:

sent me to a BASH screen saying this:

<acpi acpi=off

I changed it to noirq, but that didnt change anything :(

I had to switch all these parameters off because otherwise I couldnt avoid the blackscreen during installation :(. (sorry if this was important but I know so little I really dont know what is important and what isnt)

when loading the liveCD I had to change quiet splash to nosplash and add noapic nolapic pci=noacpi acpi=off before I could enter it (I used a hardy liveCD).

On start this gave me the following error message:

> There was an error starting the GNOME settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the the network connection was broken

I don't know if this is important, but on reboot I get the following error message:

```
Network: nm_dbus_signal_device_status_change: assertion 'cb_data -> data -> dbus_connection' failed
```

but then it reboots

On shutdown I get an error message which ask me to make sure some Daemon has to be enabled. and I have to manually switch it off. sorry for inaccuracy, next time this happens I will write down the exact wording.

sorry I didnt mention this before. I wanted to tackle this problem once I finished with the sound. one at a time and all that but maybe these two are interconnected.

hope that gives a better insight.

thanks for the help

---

### Post by Nebelhom on 2008-05-11
> I don't know if this is important, but on reboot I get the following error message:

Code:

Network: nm_dbus_signal_device_status_change: assertion 'cb_data -> data -> dbus_connection' failed

but then it reboots


ok forget that. that seems to be a different thing. it happens because I have acpi=off

( [https://answers.launchpad.net/ubuntu/+question/16914](https://answers.launchpad.net/ubuntu/+question/16914) )

---

### Post by happyhamster on 2008-05-11
> **Nebelhom said:**
> I tried your ideas.

BIOS:

I found in Onboard Device configuration:
HDA Controller     [Auto] or [Disabled]

and in PCIPnP:

Assign IRQ for VGA     [Enabled]

I assumed that these are meaningful in someway. I didnt try them out cos from previous painful experience I know that I can really mess my PC up when playing around somewhere where I have no clue what it does.
Agreed. Don't mess with the bios unless you're absolutely sure you won't break stuff.

> 
Your idea of editing the Kernel:

sent me to a BASH screen saying this:

<acpi acpi=off

I changed it to noirq, but that didnt change anything :(

Both pci=noacpi and acpi=off already incorporate acpi=noirq I believe.

> 
I had to switch all these parameters off because otherwise I couldnt avoid the blackscreen during installation :(. (sorry if this was important but I know so little I really dont know what is important and what isnt)

when loading the liveCD I had to change quiet splash to nosplash and add noapic nolapic pci=noacpi acpi=off before I could enter it (I used a hardy liveCD).

That's the main problem I think. Those parameters are pretty intrusive and should only be used as a last resort (if possible). For example: the output of "cat /proc/interrupts" shows that effectively only 1 processor core is used. I'm pretty sure the noapic nolapic parameters are to blame there. And I wouldn't be surprised if those parameters also keep the onboard sound from working.

Anyway, I'm speculating here, so take the above with a grain of salt. (This has raised above my skill-level I'm afraid.)

If I were in your shoes, first thing I would do is trying to get the live cd to boot *without* the need for noapic and nolapic, and preferably the acpi stuff as well. For example: boot the live-cd with just 1 of those parameters, instead of all 4 of them. Other parameters you could try:

pci=routeirq
pci=biosirq
irqpoll

I would also take a look at upgrading the pc's bios. HOWEVER, upgrading the bios could potentially brick your pc, might void your warranty, etc., so if you decide to go that road, make sure to thoroughly read up on that topic first. 

Finally, you might want to file a bug report at launchpad.
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Good luck.

---

### Post by Nebelhom on 2008-05-11
> If I were in your shoes, first thing I would do is trying to get the live cd to boot *without* the need for noapic and nolapic, and preferably the acpi stuff as well. For example: boot the live-cd with just 1 of those parameters, instead of all 4 of them. Other parameters you could try:

pci=routeirq
pci=biosirq
irqpoll

hi,

I've tested the livecd startup. so far, I could single out the parameters to 

```
nosplash pci=noacpi acpi=off
```

I just like to know what the last two mean. just so that I can kinda know what I'm doing and maybe act accordingly. oh btw the sound is still off.

...do these commands make sense that they work... and the last thing is, how do I switch noapic nolapic off in my hardy config?

---

### Post by happyhamster on 2008-05-11
> **Nebelhom said:**
> hi,

I've tested the livecd startup. so far, I could single out the parameters to 

```
nosplash pci=noacpi acpi=off
```

I just like to know what the last two mean. just so that I can kinda know what I'm doing and maybe act accordingly. oh btw the sound is still off.
Acpi takes care of powermanagement stuff (hibernate/suspend and such) and it is also used to assign interrupts (to get the hardware to communicate properly). If it's disabled, powermanagement will probably not be available and interrupts are assigned by using bios-settings (and the problem with that is that quite a lot of biosses are utter crap).

That's how I understand it anyway.

> 
...do these commands make sense that they work... and the last thing is, how do I switch noapic nolapic off in my hardy config?
Safest way to test if it works for your current installation is to delete "noapic nolapic" from within the grub menu again. See one of the above posts for the procedure.

- And only when you're sure it's safe, should you make the change permanent by editing menu.lst:

gksudo gedit /boot/grub/menu.lst

- The line you're interested in will be somewhat at the end of that file.

---

### Post by Nebelhom on 2008-05-12
I FIXED IT!!!!!!! THERE IS SOUND!!!!

:guitar::mrgreen::-({|=:biggrin:=D>:guitar::popcorn:

---

### Post by Nebelhom on 2008-05-12
...right ok... now to the reason how this was done.

I am still not quite sure why this worked.

All I did was delete all that noapic nolapic pci=noacpi apci=off and gave it a try.
All I expected was a black screen (Note: ever since I installed my nvidia drivers correctly I havent seen a black screen once).

So why does my liveCD install only work with all the above written in essentially taking out a certain part of my hardware and once my nvidia drivers are installed, I can delete this all so that I can make the other part functioning again.

I essentially had to temporarily sacrifice a bishop to obtain a queen, if one wants to take a metaphorical approach here.

The big Q in this one is then... Why?

what do I do now to make it last?

Just delete the things I deleted temporarily in the menu.ls and save?

And last but by all means not least, a big THANK YOU goes out to the one and only happyhamster! Without your help, I'd still be sitting here not knowing what to do... and subsequently crying in frustration ;) I'd kiss you if I could... so best never tell me where you live :lolflag:

---

### Post by happyhamster on 2008-05-13
> **Nebelhom said:**
> ...right ok... now to the reason how this was done.

I am still not quite sure why this worked.

All I did was delete all that noapic nolapic pci=noacpi apci=off and gave it a try.
All I expected was a black screen (Note: ever since I installed my nvidia drivers correctly I havent seen a black screen once).

So why does my liveCD install only work with all the above written in essentially taking out a certain part of my hardware and once my nvidia drivers are installed, I can delete this all so that I can make the other part functioning again.
I don't know :)

If you're not tired of testing this further, try booting the live-cd in safe graphics mode (F4), or press F6 and add: vga=771 

[edit: better is probably to use: vga=ask. It will list the available video modes]

> 
what do I do now to make it last?

Just delete the things I deleted temporarily in the menu.ls and save?
To make the changes permanent, you'll have to edit menu.lst, yes.

Make sure things really do work fine though. Try booting without those parameters (temporarily removing them from within the grub menu again), while booting under different circumstances. For example: booting while an usb-stick is connected or not. Booting with a dvd in the dvd-drive or not. Etc.

When you're sure everything's fine, start with making a backup of menu.lst:

cp /boot/grub/menu.lst  ~/menu.lst.original

- Then edit:

gksudo gedit /boot/grub/menu.lst

- Save and reboot. The changes should be visible in the grub menu now.

> 
And last but by all means not least, a big THANK YOU goes out to the one and only happyhamster! Without your help, I'd still be sitting here not knowing what to do... and subsequently crying in frustration ;) I'd kiss you if I could... so best never tell me where you live :lolflag:
I'll keep that in mind :)


- BTW, could you perhaps show the output of:

cat /proc/interrupts

- after booting without noapic, nolapic, etc. ? I'm just curious.

---

### Post by Nebelhom on 2008-05-13
I thought you might be curious and to be honest I checked that one as well straight away. They do not seem too different to my eye, but maybe it is different to you.
let me know what you think. maybe there is something still a bit odd. how does a typical duo core cat /proc/interrupts look like?

right here is before I changed it:

```
          CPU0       CPU1       
  0:        118          0    XT-PIC-XT        timer
  1:        127          0    XT-PIC-XT        i8042
  2:          0          0    XT-PIC-XT        cascade
  3:          2          0    XT-PIC-XT        uhci_hcd:usb3, ehci_hcd:usb5, ohci1394
  4:          1          0    XT-PIC-XT      
  5:          0          0    XT-PIC-XT        uhci_hcd:usb2
  7:          7          0    XT-PIC-XT      
  8:          0          0    XT-PIC-XT        rtc
 10:       1271          0    XT-PIC-XT        uhci_hcd:usb1, eth0
 11:      43662          0    XT-PIC-XT        sata_via, uhci_hcd:usb4, ahci, nvidia
 12:      25798          0    XT-PIC-XT        i8042
 14:       3762          0    XT-PIC-XT        libata
 15:          0          0    XT-PIC-XT        libata
NMI:          0          0   Non-maskable interrupts
LOC:      87273      87244   Local timer interrupts
RES:       2533       2494   Rescheduling interrupts
CAL:         95        241   function call interrupts
TLB:        435        505   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
SPU:          0          0   Spurious interrupts
ERR:          5

```

and this is after:

```
nebelhom@Barad-Moll:~$ cat /proc/interrupts
           CPU0       CPU1       
  0:        129          0   IO-APIC-edge      timer
  1:        735          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  6:          5          0   IO-APIC-edge      floppy
  7:          0          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc
  9:          0          0   IO-APIC-fasteoi   acpi
 12:      11738          0   IO-APIC-edge      i8042
 14:       1695          0   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 17:        871          0   IO-APIC-fasteoi   HDA Intel
 18:          3          0   IO-APIC-fasteoi   ohci1394
 20:        701          0   IO-APIC-fasteoi   uhci_hcd:usb1, eth0
 21:       8888          0   IO-APIC-fasteoi   sata_via, uhci_hcd:usb3, ehci_hcd:usb5
 22:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 23:      16464          0   IO-APIC-fasteoi   uhci_hcd:usb4
 24:      16464          0   IO-APIC-fasteoi   nvidia
 28:          0          0   IO-APIC-fasteoi   ahci
 29:          0          0   IO-APIC-fasteoi   libata
NMI:          0          0   Non-maskable interrupts
LOC:      18213      17964   Local timer interrupts
RES:       2570       2534   Rescheduling interrupts
CAL:        136        255   function call interrupts
TLB:        417        481   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
SPU:          0          0   Spurious interrupts
ERR:          0

```

---

### Post by happyhamster on 2008-05-13
```
 17:        871          0   IO-APIC-fasteoi   HDA Intel
```
```
ERR:          0
```
That's good news :)

> 
how does a typical duo core cat /proc/interrupts look like?
I assumed it should look somewhat like this (my own AMD dual core; both cores show interrupt counts):
```
           CPU0       CPU1       
  0:        157          0   IO-APIC-edge      timer
  1:         41      10828   IO-APIC-edge      i8042
  8:          0          3   IO-APIC-edge      rtc
  9:          1          0   IO-APIC-fasteoi   acpi
 12:       4631    1207839   IO-APIC-edge      i8042
 14:        569     293929   IO-APIC-edge      ide0
 19:       1029     190774   IO-APIC-fasteoi   ohci_hcd:usb1, EMU10K1
 20:          0          3   IO-APIC-fasteoi   ohci_hcd:usb2, ohci1394
 21:          0          0   IO-APIC-fasteoi   ohci_hcd:usb3
 22:          0          0   IO-APIC-fasteoi   ehci_hcd:usb4
 23:          0        656   IO-APIC-fasteoi   sata_uli
 24:       2992     852140   IO-APIC-fasteoi   ahci
 25:      32689   19135155   IO-APIC-fasteoi   eth0
 26:       6431    2730000   IO-APIC-fasteoi   nvidia
NMI:          0          0 
LOC:   16758858   11596346 
ERR:          0
MIS:          0

```
But now I'm not sure anymore.

Does your system-monitor show 2 working cores? (System-->Administration-->System Monitor-->Resources)

---

### Post by happyhamster on 2008-05-13
Never mind, my bad, it's likely absolutely normal. I just found this thread:
[http://www.linuxquestions.org/questions/slackware-14/interrupts-being-processed-by-only-1-cpu-581661/](http://www.linuxquestions.org/questions/slackware-14/interrupts-being-processed-by-only-1-cpu-581661/)

Seems that the distribution of interrupts over cores can vary wildly per processor/system.

Anyway, congrats on getting the sound to work.

---

