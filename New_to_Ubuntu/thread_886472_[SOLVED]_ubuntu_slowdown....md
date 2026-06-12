---
title: "[SOLVED] ubuntu slowdown..."
date: 2008-08-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-08-11
[U][B]
Problem 1[/B][/U]
I'm having some problems with my Ubuntu hardy install...it's got a bit laggy and it will take maybe a couple of minutes to load Firefox sometimes...
[B][U]
Problem 2[/U][/B]
I've noticed that when I'm extracting large amounts of split archives (45+) i cant do anything else on PC because it will just freeze even though Conky says that it's hardly using any system resources! and i have 2gig's of ram and a 4.2ghz dualcore processor 

[B][U]Problem 3
[/U][/B]
When I click on a video file nothing will happen even though Smplayer is set to default it wont load, I have to open Smplayer separately and then open the video from the player window also if i right click on the video and select "open with" and choose vlc the same thing happens, only mplayer will work from clicking on the video!


Thanks in advance!

---

### Post by AdamWood on 2008-08-11
for problems 1 & 2, have you checked dmesg to make sure there are no hard disk read errors?

Open a Terminal from the Applications->Accessories menu

```

dmesg
or to save for attaching here
dmesg > dmesg.log 

```

---

### Post by kamitsukai on 2008-08-11
I'm not really sure what I'm looking for so I've included the log file in this post :)

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fef0000 (usable)
[    0.000000]  BIOS-e820: 000000006fef0000 - 000000006fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006fef3000 - 000000006ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000070000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 894MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3be0
[    0.000000] Entering add_active_range(0, 0, 458480) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   458480
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   458480
[    0.000000] On node 0 totalpages: 458480
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1789 pages used for memmap
[    0.000000]   HighMem zone: 227315 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.5 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7CD0 checksum 0
[    0.000000] ACPI: RSDP 000F7CD0, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 6FEF3000, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: FACP 6FEF3080, 0074 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
[    0.000000] ACPI: DSDT 6FEF3100, 6951 (r1 NVIDIA NVDAACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 6FEF1800, 0040
[    0.000000] ACPI: SSDT 6FEF9B00, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 6FEF9D40, 0038 (r1 Nvidia NVDAACPI 42302E31 NVDA       98)
[    0.000000] ACPI: MCFG 6FEF9D80, 003C (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: APIC 6FEF9A80, 0072 (r1 Nvidia NVDAACPI 42302E31 NVDA        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454899
[    0.000000] Kernel command line: root=UUID=4960185f-65a4-4451-b181-27d0866b6fad ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.179 MHz processor.
[   17.223658] spurious 8259A interrupt: IRQ7.
[   17.226800] Console: colour VGA+ 80x25
[   17.226803] console [tty0] enabled
[   17.227087] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.227397] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.289212] Memory: 1805472k/1833920k available (2177k kernel code, 27248k reserved, 1006k data, 368k init, 916416k highmem)
[   17.289219] virtual kernel memory layout:
[   17.289220]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.289221]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.289222]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.289223]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.289224]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   17.289225]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   17.289226]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   17.289228] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.289258] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   17.289380] hpet clockevent registered
[   17.369305] Calibrating delay using timer specific routine.. 4404.37 BogoMIPS (lpj=8808753)
[   17.369323] Security Framework initialized
[   17.369328] SELinux:  Disabled at boot.
[   17.369340] AppArmor: AppArmor initialized
[   17.369343] Failure registering capabilities with primary security module.
[   17.369350] Mount-cache hash table entries: 512
[   17.369442] Initializing cgroup subsys ns
[   17.369445] Initializing cgroup subsys cpuacct
[   17.369453] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   17.369460] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.369463] CPU: L2 Cache: 512K (64 bytes/line)
[   17.369465] CPU 0(2) -> Core 0
[   17.369466] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   17.369474] Compat vDSO mapped to ffffe000.
[   17.369483] Checking 'hlt' instruction... OK.
[   17.385522] SMP alternatives: switching to UP code
[   17.386535] Early unpacking initramfs... done
[   17.710282] ACPI: Core revision 20070126
[   17.710337] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.713453] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   17.713467] SMP alternatives: switching to SMP code
[   17.713835] Booting processor 1/1 eip 3000
[   17.724194] Initializing CPU#1
[   17.801242] Calibrating delay using timer specific routine.. 4400.02 BogoMIPS (lpj=8800058)
[   17.801248] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   17.801254] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.801256] CPU: L2 Cache: 512K (64 bytes/line)
[   17.801257] CPU 1(2) -> Core 1
[   17.801259] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   17.801078] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   17.801093] Total of 2 processors activated (8804.40 BogoMIPS).
[   17.801324] ENABLING IO-APIC IRQs
[   17.801550] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.948830] Brought up 2 CPUs
[   17.948872] CPU0 attaching sched-domain:
[   17.948874]  domain 0: span 03
[   17.948875]   groups: 01 02
[   17.948878] CPU1 attaching sched-domain:
[   17.948879]  domain 0: span 03
[   17.948881]   groups: 02 01
[   17.949045] net_namespace: 64 bytes
[   17.949051] Booting paravirtualized kernel on bare hardware
[   17.949449] Time: 12:19:13  Date: 08/11/08
[   17.949470] NET: Registered protocol family 16
[   17.949622] EISA bus registered
[   17.949626] ACPI: bus type pci registered
[   17.955174] PCI: PCI BIOS revision 3.00 entry at 0xfa1d0, last bus=8
[   17.955176] PCI: Using configuration type 1
[   17.955182] Setting up standard PCI resources
[   17.959540] ACPI: EC: Look up EC in DSDT
[   17.964584] ACPI: Interpreter enabled
[   17.964586] ACPI: (supports S0 S1 S4 S5)
[   17.964597] ACPI: Using IOAPIC for interrupt routing
[   17.973024] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.973663] PCI: Transparent bridge - 0000:00:08.0
[   17.974040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.974236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   18.024940] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.025093] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.025245] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.025396] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.025548] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.025699] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.025849] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.026000] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.026152] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.026305] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[   18.026457] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   18.026609] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   18.026764] ACPI: PCI Interrupt Link [LU1B] (IRQs *5 7 9 10 11 14 15)
[   18.026916] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 *10 11 14 15)
[   18.027068] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[   18.027220] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   18.027371] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.027524] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   18.027675] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   18.027827] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   18.028007] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   18.028182] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   18.028355] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   18.028529] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   18.028708] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   18.028882] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   18.029055] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   18.029228] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   18.029402] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[   18.029576] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[   18.029750] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[   18.029925] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[   18.030099] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[   18.030274] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   18.030447] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   18.030622] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   18.030796] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   18.030970] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   18.031144] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   18.031319] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   18.031436] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.031460] pnp: PnP ACPI init
[   18.031466] ACPI: bus type pnp registered
[   18.032200] ACPI Error (psargs-0355): [GUR_._BAS] Namespace lookup failure, AE_NOT_FOUND
[   18.032205] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.MBIO._CRS] (Node f7c4a078), AE_NOT_FOUND
[   18.036107] pnpacpi: exceeded the max number of mem resources: 12
[   18.036164] pnp: PnP ACPI: found 13 devices
[   18.036166] ACPI: ACPI bus type pnp unregistered
[   18.036169] PnPBIOS: Disabled by ACPI PNP
[   18.036344] PCI: Using ACPI for IRQ routing
[   18.036347] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.132564] NET: Registered protocol family 8
[   18.132566] NET: Registered protocol family 20
[   18.132593] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   18.132597] hpet0: 3 32-bit timers, 25000000 Hz
[   18.133633] AppArmor: AppArmor Filesystem Enabled
[   18.136554] Time: hpet clocksource has been installed.
[   18.136566] Switched to high resolution mode on CPU 0
[   18.137016] Switched to high resolution mode on CPU 1
[   18.144539] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   18.144542] system 00:02: ioport range 0x800-0x87f has been reserved
[   18.144544] system 00:02: ioport range 0x290-0x297 has been reserved
[   18.144552] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   18.144557] system 00:0c: iomem range 0xf0000-0xfffff could not be reserved
[   18.144560] system 00:0c: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[   18.144562] system 00:0c: iomem range 0x6fef0000-0x6fefffff could not be reserved
[   18.144565] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[   18.144567] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   18.144569] system 00:0c: iomem range 0x100000-0x6feeffff could not be reserved
[   18.144572] system 00:0c: iomem range 0x70000000-0x7fffffff could not be reserved
[   18.144575] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   18.144577] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
[   18.144580] system 00:0c: iomem range 0xfefff000-0xfeffffff could not be reserved
[   18.144582] system 00:0c: iomem range 0xfff80000-0xfff80fff could not be reserved
[   18.144585] system 00:0c: iomem range 0xfff90000-0xfffbffff could not be reserved
[   18.174910] PCI: Bridge: 0000:00:08.0
[   18.174912]   IO window: c000-cfff
[   18.174915]   MEM window: fd000000-fd0fffff
[   18.174918]   PREFETCH window: fdf00000-fdffffff
[   18.174920] PCI: Bridge: 0000:00:0b.0
[   18.174922]   IO window: b000-bfff
[   18.174924]   MEM window: fde00000-fdefffff
[   18.174926]   PREFETCH window: fdd00000-fddfffff
[   18.174928] PCI: Bridge: 0000:00:0c.0
[   18.174930]   IO window: a000-afff
[   18.174932]   MEM window: fdc00000-fdcfffff
[   18.174934]   PREFETCH window: fdb00000-fdbfffff
[   18.174936] PCI: Bridge: 0000:00:0d.0
[   18.174938]   IO window: 9000-9fff
[   18.174940]   MEM window: fda00000-fdafffff
[   18.174942]   PREFETCH window: fd900000-fd9fffff
[   18.174944] PCI: Bridge: 0000:00:0e.0
[   18.174945]   IO window: 8000-8fff
[   18.174948]   MEM window: fd800000-fd8fffff
[   18.174950]   PREFETCH window: fd700000-fd7fffff
[   18.174952] PCI: Bridge: 0000:00:0f.0
[   18.174953]   IO window: 7000-7fff
[   18.174955]   MEM window: fd600000-fd6fffff
[   18.174957]   PREFETCH window: fd500000-fd5fffff
[   18.174960] PCI: Bridge: 0000:00:10.0
[   18.174961]   IO window: 6000-6fff
[   18.174963]   MEM window: fd400000-fd4fffff
[   18.174965]   PREFETCH window: fd300000-fd3fffff
[   18.174967] PCI: Bridge: 0000:00:11.0
[   18.174969]   IO window: 5000-5fff
[   18.174971]   MEM window: fd200000-fd2fffff
[   18.174973]   PREFETCH window: fd100000-fd1fffff
[   18.174982] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   18.174990] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   18.174995] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.175001] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.175006] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   18.175012] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   18.175017] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   18.175022] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   18.175032] NET: Registered protocol family 2
[   18.212502] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.212740] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.213334] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.213607] TCP: Hash tables configured (established 131072 bind 65536)
[   18.213609] TCP reno registered
[   18.224544] checking if image is initramfs... it is
[   18.851090] Freeing initrd memory: 7924k freed
[   18.852155] audit: initializing netlink socket (disabled)
[   18.852167] audit(1218457153.444:1): initialized
[   18.852314] highmem bounce pool size: 64 pages
[   18.853923] VFS: Disk quotas dquot_6.5.1
[   18.853982] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.854079] io scheduler noop registered
[   18.854081] io scheduler anticipatory registered
[   18.854083] io scheduler deadline registered
[   18.854091] io scheduler cfq registered (default)
[   18.854118] pci 0000:00:00.0: Enabling HT MSI Mapping
[   18.885218] pci 0000:00:07.0: Enabling HT MSI Mapping
[   18.885231] pci 0000:00:08.0: Enabling HT MSI Mapping
[   18.885244] pci 0000:00:09.0: Enabling HT MSI Mapping
[   18.885258] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   18.885271] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   18.885284] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   18.885297] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   18.885310] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   18.885323] pci 0000:00:0f.0: Enabling HT MSI Mapping
[   18.885336] pci 0000:00:10.0: Enabling HT MSI Mapping
[   18.885349] pci 0000:00:11.0: Enabling HT MSI Mapping
[   18.885361] Boot video device is 0000:00:12.0
[   18.885457] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   18.885476] assign_interrupt_mode Found MSI capability
[   18.885493] Allocate Port Service[0000:00:0b.0:pcie00]
[   18.885545] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.885564] assign_interrupt_mode Found MSI capability
[   18.885577] Allocate Port Service[0000:00:0c.0:pcie00]
[   18.885626] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.885644] assign_interrupt_mode Found MSI capability
[   18.885657] Allocate Port Service[0000:00:0d.0:pcie00]
[   18.885706] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   18.885724] assign_interrupt_mode Found MSI capability
[   18.885737] Allocate Port Service[0000:00:0e.0:pcie00]
[   18.885785] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   18.885804] assign_interrupt_mode Found MSI capability
[   18.885817] Allocate Port Service[0000:00:0f.0:pcie00]
[   18.885865] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   18.885884] assign_interrupt_mode Found MSI capability
[   18.885896] Allocate Port Service[0000:00:10.0:pcie00]
[   18.885945] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   18.885963] assign_interrupt_mode Found MSI capability
[   18.885976] Allocate Port Service[0000:00:11.0:pcie00]
[   18.886157] isapnp: Scanning for PnP cards...
[   19.238430] isapnp: No Plug & Play device found
[   19.262588] Real Time Clock Driver v1.12ac
[   19.262760] hpet_resources: 0xfeff0000 is busy
[   19.262793] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.262906] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.263399] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.264062] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.264120] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.264246] PNP: No PS/2 controller found. Probing ports directly.
[   19.264599] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.264603] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.276802] mice: PS/2 mouse device common for all mice
[   19.276908] EISA: Probing bus 0 at eisa.0
[   19.276913] Cannot allocate resource for EISA slot 1
[   19.276922] Cannot allocate resource for EISA slot 5
[   19.276924] Cannot allocate resource for EISA slot 6
[   19.276926] Cannot allocate resource for EISA slot 7
[   19.276928] Cannot allocate resource for EISA slot 8
[   19.276929] EISA: Detected 0 cards.
[   19.276932] cpuidle: using governor ladder
[   19.276933] cpuidle: using governor menu
[   19.277002] NET: Registered protocol family 1
[   19.277023] Using IPI No-Shortcut mode
[   19.277050] registered taskstats version 1
[   19.277151]   Magic number: 4:381:329
[   19.277238]   hash matches device tty50
[   19.277278] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.277279] EDD information not available.
[   19.277483] Freeing unused kernel memory: 368k freed
[   20.504426] fuse init (API version 7.9)
[   20.517849] ACPI: Fan [FAN] (on)
[   20.524216] ACPI: Thermal Zone [THRM] (40 C)
[   20.724628] usbcore: registered new interface driver usbfs
[   20.724648] usbcore: registered new interface driver hub
[   20.724670] usbcore: registered new device driver usb
[   20.726041] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 23
[   20.726049] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [AUB2] -> GSI 23 (level, low) -> IRQ 16
[   20.726060] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   20.726063] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   20.726310] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   20.726336] ehci_hcd 0000:00:02.1: debug port 1
[   20.726340] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   20.726350] ehci_hcd 0000:00:02.1: irq 16, io mem 0xfe02e000
[   20.726126] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.735259] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.735372] usb usb1: configuration #1 chosen from 1 choice
[   20.735391] hub 1-0:1.0: USB hub found
[   20.735397] hub 1-0:1.0: 6 ports detected
[   20.839429] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[   20.839538] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 22
[   20.839547] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [AU2B] -> GSI 22 (level, low) -> IRQ 17
[   20.839558] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   20.839561] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   20.839581] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   20.839610] ehci_hcd 0000:00:04.1: debug port 1
[   20.839613] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   20.839623] ehci_hcd 0000:00:04.1: irq 17, io mem 0xfe02c000
[   20.851140] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.851246] usb usb2: configuration #1 chosen from 1 choice
[   20.851267] hub 2-0:1.0: USB hub found
[   20.851273] hub 2-0:1.0: 6 ports detected
[   20.955089] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 21
[   20.955100] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [AUBA] -> GSI 21 (level, low) -> IRQ 18
[   20.955112] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   20.955115] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   20.955147] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[   20.955162] ohci_hcd 0000:00:02.0: irq 18, io mem 0xfe02f000
[   21.015677] usb usb3: configuration #1 chosen from 1 choice
[   21.015699] hub 3-0:1.0: USB hub found
[   21.015706] hub 3-0:1.0: 6 ports detected
[   21.045372] SCSI subsystem initialized
[   21.078252] libata version 3.00 loaded.
[   21.079350] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   21.121862] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 20
[   21.121872] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [AU1B] -> GSI 20 (level, low) -> IRQ 19
[   21.121884] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   21.121887] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   21.121910] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[   21.121925] ohci_hcd 0000:00:04.0: irq 19, io mem 0xfe02d000
[   21.179506] usb usb4: configuration #1 chosen from 1 choice
[   21.179527] hub 4-0:1.0: USB hub found
[   21.179534] hub 4-0:1.0: 6 ports detected
[   21.186672] FDC 0 is a post-1991 82077
[   21.211345] usb 1-2: configuration #1 chosen from 1 choice
[   21.211409] hub 1-2:1.0: USB hub found
[   21.211516] hub 1-2:1.0: 2 ports detected
[   21.285415] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   21.285731] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   21.285734] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   21.285739] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.514740] usb 1-2.1: new high speed USB device using ehci_hcd and address 3
[   21.628950] usb 1-2.1: configuration #1 chosen from 1 choice
[   21.801213] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:e0:4d:62:51:07
[   21.801218] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   21.801528] ahci 0000:00:09.0: version 3.0
[   21.801841] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[   21.801844] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[   21.826195] usb 1-2.2: new high speed USB device using ehci_hcd and address 4
[   21.933661] usb 1-2.2: configuration #1 chosen from 1 choice
[   21.933723] hub 1-2.2:1.0: USB hub found
[   21.933832] hub 1-2.2:1.0: 4 ports detected
[   22.236803] usb 1-2.2.1: new high speed USB device using ehci_hcd and address 5
[   22.353515] usb 1-2.2.1: configuration #1 chosen from 1 choice
[   22.353744] hub 1-2.2.1:1.0: USB hub found
[   22.353877] hub 1-2.2.1:1.0: 3 ports detected
[   22.656406] usb 1-2.2.4: new low speed USB device using ehci_hcd and address 6
[   22.766377] usb 1-2.2.4: configuration #1 chosen from 1 choice
[   22.807777] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   22.807782] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[   22.807785] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.808084] scsi0 : ahci
[   22.808247] scsi1 : ahci
[   22.808372] scsi2 : ahci
[   22.808495] scsi3 : ahci
[   22.808562] ata1: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 216
[   22.808565] ata2: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 216
[   22.808567] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 216
[   22.808569] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 216
[   22.968112] usb 1-2.2.1.2: new low speed USB device using ehci_hcd and address 7
[   23.066721] usb 1-2.2.1.2: configuration #1 chosen from 1 choice
[   23.068031] usbcore: registered new interface driver hiddev
[   23.070412] input: HID 062a:0000 as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2.4/1-2.2.4:1.0/input/input1
[   23.087549] input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:02.1-2.2.4
[   23.091151] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2.1/1-2.2.1.2/1-2.2.1.2:1.0/input/input2
[   23.119480] input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:02.1-2.2.1.2
[   23.122394] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2.2/1-2.2.1/1-2.2.1.2/1-2.2.1.2:1.1/input/input3
[   23.124837] ata1: SATA link down (SStatus 0 SControl 300)
[   23.136845] input,hidraw2: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:02.1-2.2.1.2
[   23.136860] usbcore: registered new interface driver usbhid
[   23.136863] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   23.443509] ata2: SATA link down (SStatus 0 SControl 300)
[   23.763176] ata3: SATA link down (SStatus 0 SControl 300)
[   24.403510] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   24.404350] ata4.00: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[   24.404353] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   24.405357] ata4.00: configured for UDMA/133
[   24.405077] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[   24.405593] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.408483] pata_amd 0000:00:06.0: version 0.3.10
[   24.408516] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.408874] scsi4 : pata_amd
[   24.408916] scsi5 : pata_amd
[   24.409397] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   24.409399] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   24.434956] Driver 'sd' needs updating - please use bus_type methods
[   24.435031] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   24.435042] sd 3:0:0:0: [sda] Write Protect is off
[   24.435044] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.435058] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.435099] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   24.435106] sd 3:0:0:0: [sda] Write Protect is off
[   24.435108] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.435120] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.435123]  sda: sda2 < sda5 sda6 >
[   24.466440] sd 3:0:0:0: [sda] Attached SCSI disk
[   24.470250] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   24.628950] Attempting manual resume
[   24.628953] swsusp: Resume From Partition 8:6
[   24.628955] PM: Checking swsusp image.
[   24.629069] PM: Resume from disk failed.
[   24.671057] kjournald starting.  Commit interval 5 seconds
[   24.671071] EXT3-fs: mounted filesystem with ordered data mode.
[   24.727472] ata5.00: ATAPI: Optiarc DVD RW AD-5200A, 1.03, max UDMA/66
[   24.899236] ata5.00: configured for UDMA/66
[   24.899267] ata6: port disabled. ignoring.
[   24.900845] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-5200A  1.03 PQ: 0 ANSI: 5
[   24.900909] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   30.637767] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   30.659508] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.669937] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.721572] parport_pc 00:0a: reported by Plug and Play ACPI
[   30.721617] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   30.830060] Linux agpgart interface v0.102
[   30.913817] input: Power Button (FF) as /devices/virtual/input/input5
[   31.023250] nvidia: module license 'NVIDIA' taints kernel.
[   31.047343] ACPI: Power Button (FF) [PWRF]
[   31.047401] input: Power Button (CM) as /devices/virtual/input/input6
[   31.349203] Driver 'sr' needs updating - please use bus_type methods
[   31.355014] ACPI: Power Button (CM) [PWRB]
[   31.355064] input: Sleep Button (CM) as /devices/virtual/input/input7
[   31.356493] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   31.356496] Uniform CD-ROM driver Revision: 3.20
[   31.356535] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   31.418961] ACPI: Sleep Button (CM) [SLPB]
[   31.932130] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
[   31.932135] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [AIGP] -> GSI 21 (level, low) -> IRQ 18
[   31.932141] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   31.932323] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   32.247873] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   32.247878] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [AAZA] -> GSI 20 (level, low) -> IRQ 19
[   32.247897] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   32.282155] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   32.387831] ACPI: WMI-Acer: Mapper loaded
[   32.675901] usbcore: registered new interface driver snd-usb-audio
[   32.676451] Linux video capture interface: v2.00
[   32.752961] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[   32.753335] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   32.776379] usbcore: registered new interface driver uvcvideo
[   32.776385] USB Video Class driver (v0.1.0)
[   33.737673] lp0: using parport0 (interrupt-driven).
[   33.796160] Adding 915664k swap on /dev/sda6.  Priority:-1 extents:1 across:915664k
[   34.356176] EXT3 FS on sda5, internal journal
[   34.546826] device-mapper: uevent: version 1.0.3
[   34.546862] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   35.837048] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.310439] No dock devices found.
[   36.590300] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   36.589984] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xa
[   36.589988] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xc
[   36.589990] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xe
[   36.589992] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   37.596144] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   37.596150] apm: disabled - APM is not SMP safe.
[   38.069827] ppdev: user-space parallel port driver
[   38.187365] audit(1218453572.563:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5500 profile="/usr/sbin/cupsd" namespace="default"
[   39.553023] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   39.553029] vboxdrv: Successfully done.
[   39.553031] vboxdrv: Found 2 processor cores.
[   39.553050] vboxdrv: fAsync=1 u64DiffCores=769291.
[   39.553088] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   39.553091] vboxdrv: Successfully loaded version 1.6.4 (interface 0x00080000).
[   39.598870] Clocksource tsc unstable (delta = -270578216 ns)
[   40.574987] Bluetooth: Core ver 2.11
[   40.575345] NET: Registered protocol family 31
[   40.575349] Bluetooth: HCI device and connection manager initialized
[   40.575354] Bluetooth: HCI socket layer initialized
[   40.593761] Bluetooth: L2CAP ver 2.9
[   40.593765] Bluetooth: L2CAP socket layer initialized
[   40.628897] Bluetooth: RFCOMM socket layer initialized
[   40.628912] Bluetooth: RFCOMM TTY layer initialized
[   40.628914] Bluetooth: RFCOMM ver 1.8
[   42.044279] NET: Registered protocol family 17
[   42.647063] /dev/vmmon[6023]: Module vmmon: registered with major=10 minor=165
[   42.647413] /dev/vmmon[6023]: Module vmmon: initialized
[   43.159913] /dev/vmnet: open called by PID 6050 (vmnet-bridge)
[   43.159923] /dev/vmnet: hub 0 does not exist, allocating memory.
[   43.159932] /dev/vmnet: port on hub 0 successfully opened
[   43.159948] bridge-eth0: enabling the bridge
[   43.159952] bridge-eth0: up
[   43.159953] bridge-eth0: already up
[   43.159955] bridge-eth0: attached
[   43.186401] /dev/vmnet: open called by PID 6056 (vmnet-netifup)
[   43.186411] /dev/vmnet: hub 1 does not exist, allocating memory.
[   43.186421] /dev/vmnet: port on hub 1 successfully opened
[   43.187809] /dev/vmnet: open called by PID 6065 (vmnet-netifup)
[   43.187818] /dev/vmnet: hub 8 does not exist, allocating memory.
[   43.187827] /dev/vmnet: port on hub 8 successfully opened
[   43.215641] /dev/vmnet: open called by PID 6066 (vmnet-natd)
[   43.215654] /dev/vmnet: port on hub 8 successfully opened
[   43.300492] /dev/vmnet: open called by PID 6088 (vmnet-dhcpd)
[   43.300513] /dev/vmnet: port on hub 8 successfully opened
[   43.322236] /dev/vmnet: open called by PID 6089 (vmnet-dhcpd)
[   43.322249] /dev/vmnet: port on hub 1 successfully opened
[   45.626376] NET: Registered protocol family 10
[   45.626874] lo: Disabled Privacy Extensions
[   50.201990] vmnet1: no IPv6 routers present
[   50.218789] vmnet8: no IPv6 routers present
[   50.365459] eth0: no IPv6 routers present
```

---

### Post by AdamWood on 2008-08-11
Did you run the dmesg command during or just after one of these slowdowns? I probably should have mentioned that running it just after booting up doesn't usually give much useful info.

On the other hand, if this was run after a slowdown then I'm probably jumping to the wrong conclusion and we'll have to look for another explanation.

---

### Post by bobbob1016 on 2008-08-11
Just my 2 cents, I didn't know they made 4.2ghz processors, did you overclock?  Or was that a typo?  It's my understanding that overclocking makes the CPU less stable.  It could be what's causing the slowdown.  As in the kernel is coping with the instability by slowing the computer instead of actually crashing.  It could be finding more speed than it expects or something like that.  If you did overclock, you could try going down a bit, and seeing if that helps with the archives.

I know my explanation of the slowdowns is bad, but it is possible the idea still works.

---

### Post by kamitsukai on 2008-08-11
Nope didnt overclock and it isnt a typo :P

---

