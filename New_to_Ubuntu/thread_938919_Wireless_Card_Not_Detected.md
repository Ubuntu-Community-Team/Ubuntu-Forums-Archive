---
title: "Wireless Card Not Detected"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by madmonkeyz on 2008-10-05
Not feeling the love for the Netgear WPN311 PCI card. 
Ubuntu 8.04 does not detect the card at all.
I've tried several different methods listed in this forum to no avail.

I've verified that the card actually works (XP sp2). I tried using the AegisP.sys and AegisP.inf (from the windows install) only to receive an invalid driver in the applet. Even a reboot didn't help.

Later tried the NETGEAR installation (via WINE) which never completes fully it crashes at the end. Then manually pointing to the WPN311.inf files (the one in root installation folder  -> reboot -> no love) Tried inf from wine system32 inf folder as well.

Several variants of madwifi and a generic driver. No luck. Been at this for about 2 days at my wits end.

Looking for any kind of help I can get as this is my daughter's computer and she's started school. Thanks in advance for any help!

results from lspci:
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:86:9e:b7  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe86:9eb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1093 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1105353 (1.0 MB)  TX bytes:217179 (212.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97400 (95.1 KB)  TX bytes:97400 (95.1 KB)

---

### Post by madmonkeyz on 2008-10-05
Results from lspci -v:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80a5
	Flags: bus master, fast devsel, latency 0
	Memory at fe800000 (32-bit, prefetchable) [size=4M]
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. P5P800-MX Mainboard
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Memory at fe780000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at efe0 [size=8]
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ef00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ef20 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at ef40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ef80 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at fe77bc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fe500000-fe5fffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. P4P800/P5P800 series motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at fc00 [size=16]
	Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. P4P800 Mainboard
	Flags: medium devsel, IRQ 5
	I/O ports at 0400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80b0
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e800 [size=256]
	I/O ports at ee80 [size=64]
	Memory at fe77b800 (32-bit, non-prefetchable) [size=512]
	Memory at fe77b400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80f8
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at fe5ff000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at df00 [size=64]
	Capabilities: <access denied>

---

### Post by madmonkeyz on 2008-10-05
Results of dmesg:

[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   128816
[    0.000000] On node 0 totalpages: 128816
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 974 pages used for memmap
[    0.000000]   Normal zone: 123746 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAD70 checksum 0
[    0.000000] ACPI: RSDP 000FAD70, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1F730000, 0030 (r1 A M I  OEMRSDT   3000422 MSFT       97)
[    0.000000] ACPI: FACP 1F730200, 0081 (r1 A M I  OEMFACP   3000422 MSFT       97)
[    0.000000] ACPI: DSDT 1F7303F0, 36A7 (r1  PPVM1 PPVM1904      904 INTL  2002026)
[    0.000000] ACPI: FACS 1F740000, 0040
[    0.000000] ACPI: APIC 1F730390, 005C (r1 A M I  OEMAPIC   3000422 MSFT       97)
[    0.000000] ACPI: OEMB 1F740040, 003F (r1 A M I  OEMBIOS   3000422 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f800000:e0380000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e8000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127810
[    0.000000] Kernel command line: root=/dev/mapper/starfish-root ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2793.150 MHz processor.
[   20.050011] Console: colour VGA+ 80x25
[   20.050015] console [tty0] enabled
[   20.050196] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.050383] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.058821] Memory: 498180k/515264k available (2177k kernel code, 16532k reserved, 1006k data, 368k init, 0k highmem)
[   20.058830] virtual kernel memory layout:
[   20.058831]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   20.058832]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.058833]     vmalloc : 0xe0000000 - 0xff7fe000   ( 503 MB)
[   20.058834]     lowmem  : 0xc0000000 - 0xdf730000   ( 503 MB)
[   20.058835]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   20.058836]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   20.058837]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   20.058841] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.058875] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.138762] Calibrating delay using timer specific routine.. 5591.09 BogoMIPS (lpj=11182183)
[   20.138785] Security Framework initialized
[   20.138790] SELinux:  Disabled at boot.
[   20.138803] AppArmor: AppArmor initialized
[   20.138807] Failure registering capabilities with primary security module.
[   20.138816] Mount-cache hash table entries: 512
[   20.138938] Initializing cgroup subsys ns
[   20.138942] Initializing cgroup subsys cpuacct
[   20.138955] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   20.138965] monitor/mwait feature present.
[   20.138967] using mwait in idle threads.
[   20.138973] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.138976] CPU: L2 cache: 1024K
[   20.138979] CPU: Physical Processor ID: 0
[   20.138981] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   20.138992] Compat vDSO mapped to ffffe000.
[   20.139008] Checking 'hlt' instruction... OK.
[   20.155179] SMP alternatives: switching to UP code
[   20.157105] Early unpacking initramfs... done
[   20.494583] ACPI: Core revision 20070126
[   20.494631] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.496598] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   20.496618] SMP alternatives: switching to SMP code
[   20.497426] Booting processor 1/1 eip 3000
[   20.507542] Initializing CPU#1
[   20.586014] Calibrating delay using timer specific routine.. 5586.44 BogoMIPS (lpj=11172893)
[   20.586025] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   20.586033] monitor/mwait feature present.
[   20.586040] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.586043] CPU: L2 cache: 1024K
[   20.586046] CPU: Physical Processor ID: 0
[   20.586049] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   20.586439] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   20.586484] Total of 2 processors activated (11177.53 BogoMIPS).
[   20.586614] ENABLING IO-APIC IRQs
[   20.586790] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.733924] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   20.753909] Brought up 2 CPUs
[   20.753936] CPU0 attaching sched-domain:
[   20.753939]  domain 0: span 03
[   20.753942]   groups: 01 02
[   20.753946]   domain 1: span 03
[   20.753949]    groups: 03
[   20.753952] CPU1 attaching sched-domain:
[   20.753954]  domain 0: span 03
[   20.753956]   groups: 02 01
[   20.753959]   domain 1: span 03
[   20.753962]    groups: 03
[   20.754255] net_namespace: 64 bytes
[   20.754270] Booting paravirtualized kernel on bare hardware
[   20.754880] Time: 17:32:58  Date: 10/05/08
[   20.754908] NET: Registered protocol family 16
[   20.755215] EISA bus registered
[   20.755222] ACPI: bus type pci registered
[   20.755397] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[   20.755399] PCI: Using configuration type 1
[   20.755431] Setting up standard PCI resources
[   20.764848] ACPI: EC: Look up EC in DSDT
[   20.769902] ACPI: Interpreter enabled
[   20.769907] ACPI: (supports S0 S1 S3 S4 S5)
[   20.769929] ACPI: Using IOAPIC for interrupt routing
[   20.778100] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.778658] Force enabled HPET at base address 0xfed00000
[   20.778665] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   20.778669] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   20.778977] PCI: Transparent bridge - 0000:00:1e.0
[   20.779001] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.779114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   20.785593] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   20.785713] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.785829] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   20.785994] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.786111] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.786223] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.786337] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   20.786450] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   20.786626] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  B5, should be 87 [20070126]
[   20.786634] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.786679] pnp: PnP ACPI init
[   20.786689] ACPI: bus type pnp registered
[   20.791432] pnp: PnP ACPI: found 14 devices
[   20.791435] ACPI: ACPI bus type pnp unregistered
[   20.791440] PnPBIOS: Disabled by ACPI PNP
[   20.791785] PCI: Using ACPI for IRQ routing
[   20.791790] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.813811] NET: Registered protocol family 8
[   20.813814] NET: Registered protocol family 20
[   20.813941] hpet clockevent registered
[   20.813947] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   20.813953] hpet0: 3 64-bit timers, 14318180 Hz
[   20.814997] AppArmor: AppArmor Filesystem Enabled
[   20.817643] Time: tsc clocksource has been installed.
[   20.829839] system 00:0a: ioport range 0x680-0x6ff has been reserved
[   20.829843] system 00:0a: ioport range 0x290-0x297 has been reserved
[   20.829850] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[   20.829853] system 00:0b: ioport range 0x800-0x87f has been reserved
[   20.829856] system 00:0b: ioport range 0x480-0x4bf has been reserved
[   20.829860] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[   20.829863] system 00:0b: iomem range 0xffb00000-0xffbfffff could not be reserved
[   20.829870] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   20.829873] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[   20.829881] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   20.829884] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[   20.829887] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   20.829890] system 00:0d: iomem range 0x100000-0x1f7effff could not be reserved
[   20.829893] system 00:0d: iomem range 0xfff00000-0xffffffff could not be reserved
[   20.860438] PCI: Bridge: 0000:00:1e.0
[   20.860443]   IO window: d000-dfff
[   20.860449]   MEM window: fe500000-fe5fffff
[   20.860453]   PREFETCH window: disabled.
[   20.860468] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.860480] NET: Registered protocol family 2
[   20.897740] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   20.898015] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   20.898096] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   20.898174] TCP: Hash tables configured (established 16384 bind 16384)
[   20.898177] TCP reno registered
[   20.909793] checking if image is initramfs... it is
[   21.316813] Switched to high resolution mode on CPU 0
[   21.316959] Switched to high resolution mode on CPU 1
[   21.577959] Freeing initrd memory: 7920k freed
[   21.578974] audit: initializing netlink socket (disabled)
[   21.578989] audit(1223227978.400:1): initialized
[   21.581886] VFS: Disk quotas dquot_6.5.1
[   21.581993] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.582164] io scheduler noop registered
[   21.582167] io scheduler anticipatory registered
[   21.582169] io scheduler deadline registered
[   21.582186] io scheduler cfq registered (default)
[   21.582199] Boot video device is 0000:00:02.0
[   21.582279] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[   21.582670] isapnp: Scanning for PnP cards...
[   21.935900] isapnp: No Plug & Play device found
[   21.976172] Real Time Clock Driver v1.12ac
[   21.976304] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.976433] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.977297] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.978471] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.978557] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.978780] PNP: No PS/2 controller found. Probing ports directly.
[   21.981471] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.981478] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.011692] mice: PS/2 mouse device common for all mice
[   22.011864] EISA: Probing bus 0 at eisa.0
[   22.011905] EISA: Detected 0 cards.
[   22.011909] cpuidle: using governor ladder
[   22.011911] cpuidle: using governor menu
[   22.012001] NET: Registered protocol family 1
[   22.012032] Using IPI No-Shortcut mode
[   22.012066] registered taskstats version 1
[   22.012157]   Magic number: 12:679:541
[   22.012263] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.012265] EDD information not available.
[   22.012475] Freeing unused kernel memory: 368k freed
[   23.261925] fuse init (API version 7.9)
[   23.307666] device-mapper: uevent: version 1.0.3
[   23.307750] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   23.508459] usbcore: registered new interface driver usbfs
[   23.508503] usbcore: registered new interface driver hub
[   23.517056] usbcore: registered new device driver usb
[   23.529035] USB Universal Host Controller Interface driver v3.0
[   23.529114] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.529129] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.529135] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.529382] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   23.529414] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ef00
[   23.529620] usb usb1: configuration #1 chosen from 1 choice
[   23.529662] hub 1-0:1.0: USB hub found
[   23.529673] hub 1-0:1.0: 2 ports detected
[   23.632919] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   23.632936] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.632942] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.632980] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   23.633011] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ef20
[   23.633194] usb usb2: configuration #1 chosen from 1 choice
[   23.633236] hub 2-0:1.0: USB hub found
[   23.633245] hub 2-0:1.0: 2 ports detected
[   23.736760] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.736777] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.736783] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.736821] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   23.736852] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef40
[   23.737034] usb usb3: configuration #1 chosen from 1 choice
[   23.737076] hub 3-0:1.0: USB hub found
[   23.737086] hub 3-0:1.0: 2 ports detected
[   23.840579] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   23.840600] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   23.840607] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   23.840654] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   23.840684] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef80
[   23.840903] usb usb4: configuration #1 chosen from 1 choice
[   23.840948] hub 4-0:1.0: USB hub found
[   23.840959] hub 4-0:1.0: 2 ports detected
[   23.877864] SCSI subsystem initialized
[   23.944456] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   23.944479] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.944485] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.944553] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   23.948457] ehci_hcd 0000:00:1d.7: debug port 1
[   23.948468] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   23.948484] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfe77bc00
[   23.954577] libata version 3.00 loaded.
[   23.966029] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   23.966037] e100: Copyright(c) 1999-2006 Intel Corporation
[   23.976213] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   23.989220] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.989401] usb usb5: configuration #1 chosen from 1 choice
[   23.989443] hub 5-0:1.0: USB hub found
[   23.989454] hub 5-0:1.0: 8 ports detected
[   24.040170] Floppy drive(s): fd0 is 1.44M
[   24.068668] FDC 0 is a post-1991 82077
[   24.093281] ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   24.116608] e100: eth0: e100_probe: addr 0xfe5ff000, irq 20, MAC addr 00:0e:a6:86:9e:b7
[   24.116635] ata_piix 0000:00:1f.1: version 2.12
[   24.116653] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   24.116662] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   24.116708] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.125699] scsi0 : ata_piix
[   24.126804] scsi1 : ata_piix
[   24.128825] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   24.128831] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   24.349040] ata1.00: ATA-6: ST380011A, 3.06, max UDMA/100
[   24.349047] ata1.00: 156301488 sectors, multi 16: LBA48 
[   24.364103] ata1.00: configured for UDMA/100
[   24.652040] usb 5-7: new high speed USB device using ehci_hcd and address 3
[   24.684394] ata2.00: ATAPI: _NEC DVD_RW ND-2500A, 1.06, max UDMA/33
[   24.831517] usb 5-7: configuration #1 chosen from 1 choice
[   24.855970] ata2.00: configured for UDMA/33
[   24.856119] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        3.06 PQ: 0 ANSI: 5
[   24.857174] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-2500A  1.06 PQ: 0 ANSI: 5
[   24.877059] Driver 'sd' needs updating - please use bus_type methods
[   24.877192] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.877216] sd 0:0:0:0: [sda] Write Protect is off
[   24.877222] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.877257] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.877337] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   24.877356] sd 0:0:0:0: [sda] Write Protect is off
[   24.877361] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.877400] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.877410]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.886399]  sda1 sda2 < sda5 >
[   24.894543] sd 0:0:0:0: [sda] Attached SCSI disk
[   24.898289] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   24.898297] Uniform CD-ROM driver Revision: 3.20
[   24.898383] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   24.902436] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.902473] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   25.074301] usb 2-1: new full speed USB device using uhci_hcd and address 3
[   25.299053] usb 2-1: configuration #1 chosen from 1 choice
[   25.301959] hub 2-1:1.0: USB hub found
[   25.303916] hub 2-1:1.0: 4 ports detected
[   25.611316] usb 2-1.1: new low speed USB device using uhci_hcd and address 4
[   25.752192] usb 2-1.1: configuration #1 chosen from 1 choice
[   25.958658] usb 2-1.2: new low speed USB device using uhci_hcd and address 5
[   26.095538] usb 2-1.2: configuration #1 chosen from 1 choice
[   26.302008] usb 2-1.3: new low speed USB device using uhci_hcd and address 6
[   26.446877] usb 2-1.3: configuration #1 chosen from 1 choice
[   26.472750] usbcore: registered new interface driver libusual
[   26.481440] usbcore: registered new interface driver hiddev
[   26.482517] Initializing USB Mass Storage driver...
[   26.482907] scsi2 : SCSI emulation for USB Mass Storage devices
[   26.483031] usb-storage: device found at 3
[   26.483035] usb-storage: waiting for device to settle before scanning
[   26.495990] input: Generic USB+PS2 Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.1/2-1.1:1.0/input/input1
[   26.527821] input,hidraw0: USB HID v1.10 Keyboard [Generic USB+PS2 Keyboard] on usb-0000:00:1d.1-1.1
[   26.555605] input: Generic USB+PS2 Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.1/2-1.1:1.1/input/input2
[   26.563749] input,hidraw1: USB HID v1.10 Device [Generic USB+PS2 Keyboard] on usb-0000:00:1d.1-1.1
[   26.581878] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.2/2-1.2:1.0/input/input3
[   26.591727] input,hidraw2: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.1-1.2
[   26.616562] input: No brand SP02-A1 as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1.3/2-1.3:1.0/input/input4
[   26.635627] input,hidraw3: USB HID v1.10 Keyboard [No brand SP02-A1] on usb-0000:00:1d.1-1.3
[   26.644452] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint
[   26.644491] usbcore: registered new interface driver usbhid
[   26.644499] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   26.644503] usbcore: registered new interface driver usb-storage
[   26.644511] USB Mass Storage support registered.
[   26.764596] Attempting manual resume
[   26.764601] swsusp: Resume From Partition 254:1
[   26.764603] PM: Checking swsusp image.
[   26.764792] PM: Resume from disk failed.
[   26.783791] EXT3-fs: INFO: recovery required on readonly filesystem.
[   26.783796] EXT3-fs: write access will be enabled during recovery.
[   27.463724] kjournald starting.  Commit interval 5 seconds
[   27.463734] EXT3-fs: dm-0: orphan cleanup on readonly fs
[   27.463743] ext3_orphan_cleanup: deleting unreferenced inode 3260430
[   27.463769] EXT3-fs: dm-0: 1 orphan inode deleted
[   27.463772] EXT3-fs: recovery complete.
[   27.467633] EXT3-fs: mounted filesystem with ordered data mode.
[   31.476594] usb-storage: device scan complete
[   31.479706] scsi 2:0:0:0: Direct-Access     IN-WIN   iAPP  HS-CF      1.64 PQ: 0 ANSI: 0
[   31.482320] scsi 2:0:0:1: Direct-Access     IN-WIN   iAPP  HS-MS      1.64 PQ: 0 ANSI: 0
[   31.484939] scsi 2:0:0:2: Direct-Access     IN-WIN   iAPP  HS-SM      1.64 PQ: 0 ANSI: 0
[   31.487314] scsi 2:0:0:3: Direct-Access     IN-WIN   iAPP  HS-SD/MMC  1.64 PQ: 0 ANSI: 0
[   31.490587] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   31.490633] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   31.493818] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   31.493858] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   31.497068] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   31.497106] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   31.545981] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   31.546022] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   37.342313] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   37.809655] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.917304] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   38.033749] parport_pc 00:07: reported by Plug and Play ACPI
[   38.033798] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   38.081787] Linux agpgart interface v0.102
[   38.252622] iTCO_vendor_support: vendor-support=0
[   38.308520] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   38.308646] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   38.308691] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   38.412398] agpgart: Detected an Intel 865 Chipset.
[   38.412830] agpgart: Detected 8060K stolen memory.
[   38.424887] agpgart: AGP aperture is 128M @ 0xf0000000
[   38.695828] intel_rng: FWH not detected
[   38.866796] input: Power Button (FF) as /devices/virtual/input/input6
[   38.934427] ACPI: Power Button (FF) [PWRF]
[   38.934549] input: Power Button (CM) as /devices/virtual/input/input7
[   38.966366] ACPI: Power Button (CM) [PWRB]
[   40.308142] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   40.308179] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   40.361001] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   40.611670] usbcore: registered new interface driver lmpcm_usb
[   40.611679] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/misc/lmpcm_usb.c: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   40.727279] intel8x0_measure_ac97_clock: measured 52076 usecs
[   40.727285] intel8x0: clocking to 48000
[   42.039443] NET: Registered protocol family 17
[   42.830096] loop: module loaded
[   42.864883] lp0: using parport0 (interrupt-driven).
[   42.888902] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   42.938648] usbcore: registered new interface driver ndiswrapper
[   43.052542] Adding 1515512k swap on /dev/mapper/starfish-swap_1.  Priority:-1 extents:1 across:1515512k
[   43.634158] EXT3 FS on dm-0, internal journal
[   44.350657] NET: Registered protocol family 10
[   44.351192] lo: Disabled Privacy Extensions
[   44.473016] kjournald starting.  Commit interval 5 seconds
[   44.501099] EXT3 FS on sda1, internal journal
[   44.501106] EXT3-fs: mounted filesystem with ordered data mode.
[   44.993202] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.514439] No dock devices found.
[   47.456777] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   47.456786] apm: disabled - APM is not SMP safe.
[   48.367662] ppdev: user-space parallel port driver
[   48.669958] audit(1223228005.920:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5343 profile="/usr/sbin/cupsd" namespace="default"
[   52.421743] Bluetooth: Core ver 2.11
[   52.422278] NET: Registered protocol family 31
[   52.422286] Bluetooth: HCI device and connection manager initialized
[   52.422293] Bluetooth: HCI socket layer initialized
[   52.451822] Bluetooth: L2CAP ver 2.9
[   52.451830] Bluetooth: L2CAP socket layer initialized
[   52.517967] Bluetooth: RFCOMM socket layer initialized
[   52.517990] Bluetooth: RFCOMM TTY layer initialized
[   52.517994] Bluetooth: RFCOMM ver 1.8
[   55.175025] eth0: no IPv6 routers present
[   55.437156] [drm] Initialized drm 1.1.0 20060810
[   55.441357] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   55.441372] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   55.441480] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  526.226485] usbcore: deregistering interface driver ndiswrapper
[  893.735957] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  893.926859] wlan: 0.9.4
[  893.983612] ath_pci: 0.9.4

---

### Post by madmonkeyz on 2008-10-05
Additional information - any ideas? Anyone?

lspci -v | grep subordinate:

Bus: primary=00, secondary=01, subordinate=01, sec-latency=64

sudo lshw:

 description: Desktop Computer
    product: To Be Filled By O.E.M.
    vendor: To Be Filled By O.E.M. by More String
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.1 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: P4P800-VM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: DIMM3
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1012.002 (03/22/2004)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          slot: CPU 1
          size: 2800MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 36
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 256MiB
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 02
                serial: 00:0e:a6:86:9e:b7
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.4 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: ST380011A
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 3.06
                serial: 5JV2RYBV
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9b279b27
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: f5578c0c-2734-41b3-81ab-52212af3b6e3
                   size: 243MiB
                   capacity: 243MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-09-30 09:50:06 filesystem=ext3 modified=2008-10-05 14:38:24 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-10-05 14:38:24 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux LVM Physical Volume partition
                      physical id: 5
                      logical name: /dev/sda5
                      serial: rZCSul-Zf6l-jWDP-e239-u4vO-ZuOy-zdQomU
                      size: 74GiB
                      capacity: 74GiB
                      capabilities: multi lvm2
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-2500A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.06
                serial: [_NEC    DVD_RW ND-2500A 1.0603121900
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
     *-scsi
          physical id: 1
          bus info: usb@5:7
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             product: iAPP  HS-CF
             vendor: IN-WIN
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 1.64
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             product: iAPP  HS-MS
             vendor: IN-WIN
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/sdc
             version: 1.64
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             product: iAPP  HS-SM
             vendor: IN-WIN
             physical id: 0.0.2
             bus info: scsi@2:0.0.2
             logical name: /dev/sdd
             version: 1.64
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             product: iAPP  HS-SD/MMC
             vendor: IN-WIN
             physical id: 0.0.3
             bus info: scsi@2:0.0.3
             logical name: /dev/sde
             version: 1.64
             capabilities: removable
           *-medium
                physical id: 0
                logical name: /dev/sde

---

### Post by madmonkeyz on 2008-10-05
lsmod |grep ath:

ath_pci               100896  0 
wlan                  206960  1 ath_pci
ath_hal               192592  1 ath_pci

---

### Post by HellNoire on 2008-10-05
Have you installed NDISwrapper?

As well, not all the wireless cards are supported under Linux yet. I know I have one of these unsupported cards myself.

---

### Post by madmonkeyz on 2008-10-05
I have installed ndiswrapper -> I tried loading WPN311.inf (from the Wine installation) and Aegisp.inf (from the windows installation),

I suspect it is something more insidious -> as the card isn't detected at all by the O/S. Following the ["Troubleshooting Guide"]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check") I am unable to get by section 3.1.2. Non-recognized Card.

**sudo pccardctl ident**

returns nothing

I really hoped that I was missing something simple (being a genuine noob) but I am not so certain.

I don't really know what else to do for my daughter except install XP which I am loathe to do but I have been unable to find a workaround for this issue.

Thanks for the advice. Do you have any truly plug-n-play Wireless PCI Adapter suggestions for Ubuntu 8.04 and Netgear RangeMax Wireless Router?

---

### Post by gandaran on 2008-10-05
I believe your card is supported by ubuntu, which did you install first the wireless card or ubuntu?
take a look at this thread maybe it'll help [http://ubuntuforums.org/showthread.php?t=888326](http://ubuntuforums.org/showthread.php?t=888326)

---

### Post by madmonkeyz on 2008-10-05
I installed Ubuntu first. We got the wireless card earlier this week. Thanks for the reply I will be sure to check it out. Posting this link in hopes that it helps someone else. [Get Wireless Working]("http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html")

---

### Post by madmonkeyz on 2008-10-05
I did stumble across this link before -> I could not locate which package that the following was referring to though. If you know I will gladly try anything at this point.

[COLOR="Blue"]I believe your card uses the Atheros 5212 chipset. The drivers are included in linux-restricted-modules. I suggest opening System -> Administration -> Synaptic and find the latest version of it and Mark for Reinstallation. Click Apply and let it hum. Does that bring your wireless to life?[/COLOR]

Atheros is not listed for me, there are no proprietary drivers being used.

[COLOR="Blue"]You might also check System -> Administration -> Hardware Drivers and see if your Atheros is listed and enabled[/COLOR].

[COLOR="Blue"]If none of these steps help, post back.[/COLOR]

Thanks for the research.

---

### Post by gandaran on 2008-10-05
well, if everything else you do fails then reinstall ubuntu, I'm sure it'll work.

---

### Post by madmonkeyz on 2008-10-05
That's a genius idea. Will have to re-install all her "goodies" but at least she'll be on-line. Would you recommend keeping the ethernet connection "plugged-in" as well during the reinstall? Or is that a recipe for disaster?

---

### Post by Kevbert on 2008-10-05
An ethernet connected cable is a good idea as it's possible that any newly detected devices may have their firmware drivers installed automatically.

---

### Post by gandaran on 2008-10-05
yes, keep the internet working during the install process, you'll be able to see if it's working if it starts to download the updates at the near end of install process

edit:
didn't read your post correctly, unplug the ethernet cable leave just the wireless on

---

### Post by madmonkeyz on 2008-10-05
Alrighty then. I'm reinstalling -> hope all goes well will post-back with details. Thanks to everyone who took some time out of their day to help out.

---

### Post by madmonkeyz on 2008-10-05
Fresh installation of 8.04 Alternate (with ethernet connected - started before I saw the edit) still not detecting the Wireless PCI card.

Checking the online [Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check")

No wireless network in connections (attached screenshot showing this).

lshw dump doesn't show the adapter. sudo pccardctl ident lists nothing (see below).

My only option is to:

[COLOR="Blue"]      If you get no output then the memory on the card cannot be read. Now we need to open a configuration file and add this information to it:

        gksudo gedit /etc/pcmcia/config.opts

      the information you add should look like this, with your own data substituted. 

      card ""Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN"
        manfid 0x0271, 0x0012
        function: 6 (network)
        bind "ath_pci"[/COLOR]

I have no idea what (if anything I should put in here) - or if it will even work. Any insights will be greatly appreciated. Thanks in advance.

lshw:
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 503MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl cid
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82865G Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: c2
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82562EZ 10/100 Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:01:08.0
                logical name: eth0
                version: 02
                serial: 00:0e:a6:86:9e:b7
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.1.4 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
        *-isa
             description: ISA bridge
             product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801EB/ER (ICH5/ICH5R) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-serial UNCLAIMED
             description: SMBus
             product: 82801EB/ER (ICH5/ICH5R) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
star@starfish:~$ sudo pccardctl ident
[sudo] password for star: 
star@starfish:~$

---

### Post by madmonkeyz on 2008-10-05
I am resorting to Plan B. Thanks again to everyone - I will keep checking in to see if there is any information to help get this working. Would love to see some more details in the On-line Troubleshooting Guide.

---

### Post by madmonkeyz on 2008-10-05
I could kick my own @$$. I shut down the box to remove the card - for a win installation and I saw that the card wasn't seated properly. I should have known better than to doubt ubuntu. Thanks all for the assistance. A definate PEBAC error.

---

