---
title: "[SOLVED] Wireless does not associate"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by checksquid on 2008-07-25
Hello friendly forum folks,
I'm new to Ubuntu, so hopefully this will be a simple fix. I just got a new Lenovo T61 with Vista pre-installed, and I'm dual booting Ubuntu Hardy Heron on it. Everything is great except for one problem: the wireless can't seem to associate with my router consistently. It has only successfully connected a few times, always after I have plugged in ethernet, too, and fiddled with wireless settings a bit trying to follow advice in other threads. I haven't been able to narrow down what it is that makes it work--I don't think I've changed anything significant.

My router is totally open--no security at all.

Here is the output of iwevent as it tries to connect:
```
09:57:01.056650   ath0     Set ESSID:""
09:57:01.056907   ath0     Set Encryption key:off
09:57:02.485997   ath0     Scan request completed
09:57:02.569299   ath0     Set Mode:Managed
09:57:02.840294   ath0     Set ESSID:off/any
09:57:02.840334   ath0     Set ESSID:"Chocolatedessert"
09:57:12.523197   ath0     Scan request completed
09:57:12.523658   ath0     Set ESSID:"Chocolatedessert"
09:57:12.528814   ath0     New Access Point/Cell address:00:E0:98:D6:18:EB
09:57:57.715340   ath0     New Access Point/Cell address:Not-Associated
09:57:57.975413   ath0     Set ESSID:""
09:57:57.975451   ath0     Set Encryption key:off
09:58:17.454056   ath0     Scan request completed
```

Here's ifconfig:
```
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-91 dBm  Noise level=-91 dBm
          Rx invalid nwid:28839  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Here's the part of iwlist scan that covers my router:
```
ath0      Scan completed :
          Cell 01 - Address: 00:E0:98:D6:18:EB
                    ESSID:"Chocolatedessert"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-33 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
```

and here's my dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007deb0000 (usable)
[    0.000000]  BIOS-e820: 000000007deb0000 - 000000007decc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007decc000 - 000000007df00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007df00000 - 000000007e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 1118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6900
[    0.000000] Entering add_active_range(0, 0, 515760) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   515760
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   515760
[    0.000000] On node 0 totalpages: 515760
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2237 pages used for memmap
[    0.000000]   HighMem zone: 284147 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F68D0 checksum 0
[    0.000000] ACPI: RSDP 000F68D0, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT 7DEBB77F, 0094 (r1 LENOVO TP-7L        2210  LTP        0)
[    0.000000] ACPI: FACP 7DEBB900, 00F4 (r3 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20070126]
[    0.000000] ACPI: DSDT 7DEBBD1D, FED1 (r1 LENOVO TP-7L        2210 MSFT  3000000)
[    0.000000] ACPI: FACS 7DEE4000, 0040
[    0.000000] ACPI: SSDT 7DEBBAB4, 0269 (r1 LENOVO TP-7L        2210 MSFT  3000000)
[    0.000000] ACPI: ECDT 7DECBBEE, 0052 (r1 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: TCPA 7DECBC40, 0032 (r2 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: APIC 7DECBC72, 0068 (r1 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: MCFG 7DECBCDA, 003C (r1 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: HPET 7DECBD16, 0038 (r1 LENOVO TP-7L        2210 LNVO        1)
[    0.000000] ACPI: SLIC 7DECBDF0, 0176 (r1 LENOVO TP-7L        2210  LTP        0)
[    0.000000] ACPI: BOOT 7DECBF66, 0028 (r1 LENOVO TP-7L        2210  LTP        1)
[    0.000000] ACPI: ASF! 7DECBF8E, 0072 (r16 LENOVO TP-7L        2210 PTL         1)
[    0.000000] ACPI: SSDT 7DEE26D9, 025F (r1 LENOVO TP-7L        2210 INTL 20050513)
[    0.000000] ACPI: SSDT 7DEE2938, 00A6 (r1 LENOVO TP-7L        2210 INTL 20050513)
[    0.000000] ACPI: SSDT 7DEE29DE, 04F7 (r1 LENOVO TP-7L        2210 INTL 20050513)
[    0.000000] ACPI: SSDT 7DEE2ED5, 01D8 (r1 LENOVO TP-7L        2210 INTL 20050513)
[    0.000000] ACPI: DMI detected: Lenovo ThinkPad T61
[    0.000000] ACPI: Added _OSI(Linux)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:7 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 7:7 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7e000000:72000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 00000000000d4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 511731
[    0.000000] Kernel command line: root=UUID=51ae60cb-650f-4d17-97e7-adbaef090332 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2094.881 MHz processor.
[   14.516572] Console: colour VGA+ 80x25
[   14.516578] console [tty0] enabled
[   14.517054] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.517624] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.697572] Memory: 2033336k/2063040k available (2177k kernel code, 28448k reserved, 1006k data, 368k init, 1145536k highmem)
[   14.697587] virtual kernel memory layout:
[   14.697589]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   14.697591]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.697594]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.697596]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.697598]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   14.697600]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   14.697602]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   14.697608] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.697677] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.697826] hpet clockevent registered
[   14.777696] Calibrating delay using timer specific routine.. 4196.67 BogoMIPS (lpj=8393347)
[   14.777735] Security Framework initialized
[   14.777745] SELinux:  Disabled at boot.
[   14.777769] AppArmor: AppArmor initialized
[   14.777776] Failure registering capabilities with primary security module.
[   14.777791] Mount-cache hash table entries: 512
[   14.778003] Initializing cgroup subsys ns
[   14.778011] Initializing cgroup subsys cpuacct
[   14.778031] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0008e3bd 00000000 00000001 00000001
[   14.778045] monitor/mwait feature present.
[   14.778048] using mwait in idle threads.
[   14.778055] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.778060] CPU: L2 cache: 3072K
[   14.778065] CPU: Physical Processor ID: 0
[   14.778068] CPU: Processor Core ID: 0
[   14.778071] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0008e3bd 00000000 00000001 00000001
[   14.778089] Compat vDSO mapped to ffffe000.
[   14.778113] Checking 'hlt' instruction... OK.
[   14.794500] SMP alternatives: switching to UP code
[   14.798091] Early unpacking initramfs... done
[   15.527609] ACPI: Core revision 20070126
[   15.527774] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.579010] CPU0: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz stepping 06
[   15.579038] SMP alternatives: switching to SMP code
[   15.580612] Booting processor 1/1 eip 3000
[   15.591741] Initializing CPU#1
[   15.668312] Calibrating delay using timer specific routine.. 4189.71 BogoMIPS (lpj=8379426)
[   15.668325] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0008e3bd 00000000 00000001 00000001
[   15.668335] monitor/mwait feature present.
[   15.668340] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.668344] CPU: L2 cache: 3072K
[   15.668348] CPU: Physical Processor ID: 0
[   15.668350] CPU: Processor Core ID: 1
[   15.668353] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0008e3bd 00000000 00000001 00000001
[   15.669723] CPU1: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz stepping 06
[   15.669766] Total of 2 processors activated (8386.38 BogoMIPS).
[   15.669980] ENABLING IO-APIC IRQs
[   15.670241] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.816085] checking TSC synchronization [CPU#0 -> CPU#1]:
[   15.836066] Measured 345366 cycles TSC warp between CPUs, turning off TSC clock.
[   15.836070] Marking TSC unstable due to: check_tsc_sync_source failed.
[   15.836089] Brought up 2 CPUs
[   15.836130] CPU0 attaching sched-domain:
[   15.836135]  domain 0: span 03
[   15.836138]   groups: 01 02
[   15.836144] CPU1 attaching sched-domain:
[   15.836147]  domain 0: span 03
[   15.836150]   groups: 02 01
[   15.836712] net_namespace: 64 bytes
[   15.836725] Booting paravirtualized kernel on bare hardware
[   15.837627] Time:  9:54:20  Date: 07/25/08
[   15.837676] NET: Registered protocol family 16
[   15.838029] EISA bus registered
[   15.838038] ACPI: bus type pci registered
[   15.838864] PCI: PCI BIOS revision 3.00 entry at 0xfdda7, last bus=24
[   15.838868] PCI: Using configuration type 1
[   15.838886] Setting up standard PCI resources
[   15.845945] ACPI: EC: EC description table is found, configuring boot EC
[   15.856088] ACPI: BIOS _OSI(Linux) query honored via DMI
[   15.857442] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.940800] ACPI: Interpreter enabled
[   15.940807] ACPI: (supports S0 S3 S4 S5)
[   15.940838] ACPI: Using IOAPIC for interrupt routing
[   15.960155] ACPI: EC: GPE = 0x12, I/O: command/status = 0x66, data = 0x62
[   15.960161] ACPI: EC: driver started in poll mode
[   15.960545] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.963238] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   15.963248] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   15.966718] PCI: Transparent bridge - 0000:00:1e.0
[   15.966971] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.967406] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   15.967706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[   15.967998] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   15.968289] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[   15.968579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[   15.968875] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[   15.969170] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   15.978122] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11)
[   15.978606] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[   15.979084] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[   15.979560] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[   15.980043] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[   15.980520] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[   15.980994] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[   15.981470] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[   15.981814] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.981970] ACPI: Power Resource [PUBS] (on)
[   15.982100] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.982156] pnp: PnP ACPI init
[   15.982170] ACPI: bus type pnp registered
[   15.984968] pnpacpi: exceeded the max number of mem resources: 12
[   15.992469] pnp: PnP ACPI: found 11 devices
[   15.992475] ACPI: ACPI bus type pnp unregistered
[   15.992480] PnPBIOS: Disabled by ACPI PNP
[   15.993058] PCI: Using ACPI for IRQ routing
[   15.993063] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.399275] NET: Registered protocol family 8
[   16.399280] NET: Registered protocol family 20
[   16.399344] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.399353] hpet0: 3 64-bit timers, 14318180 Hz
[   16.400410] AppArmor: AppArmor Filesystem Enabled
[   16.402888] Time: hpet clocksource has been installed.
[   16.402910] Switched to high resolution mode on CPU 0
[   16.403272] Switched to high resolution mode on CPU 1
[   16.412043] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   16.412049] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[   16.412054] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[   16.412060] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[   16.412065] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[   16.412071] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[   16.412077] system 00:00: iomem range 0x0-0x0 could not be reserved
[   16.412082] system 00:00: iomem range 0x0-0x0 could not be reserved
[   16.412087] system 00:00: iomem range 0x0-0x0 could not be reserved
[   16.412092] system 00:00: iomem range 0xe0000-0xe3fff has been reserved
[   16.412098] system 00:00: iomem range 0xe4000-0xe7fff has been reserved
[   16.412103] system 00:00: iomem range 0xe8000-0xebfff has been reserved
[   16.412116] system 00:02: ioport range 0x164e-0x164f has been reserved
[   16.412122] system 00:02: ioport range 0x1000-0x107f has been reserved
[   16.412127] system 00:02: ioport range 0x1180-0x11bf has been reserved
[   16.412132] system 00:02: ioport range 0x800-0x80f has been reserved
[   16.412138] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[   16.412143] system 00:02: ioport range 0x1600-0x165f could not be reserved
[   16.412150] system 00:02: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   16.412156] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   16.412162] system 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   16.412168] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   16.412174] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   16.412180] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[   16.442993] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:01:00.0
[   16.442998] PCI: Bridge: 0000:00:01.0
[   16.443002]   IO window: 2000-2fff
[   16.443010]   MEM window: d4000000-d6ffffff
[   16.443016]   PREFETCH window: e0000000-efffffff
[   16.443023] PCI: Bridge: 0000:00:1c.0
[   16.443030]   IO window: 3000-3fff
[   16.443047]   MEM window: fc000000-fdffffff
[   16.443056]   PREFETCH window: f8000000-f80fffff
[   16.443073] PCI: Bridge: 0000:00:1c.1
[   16.443080]   IO window: 4000-4fff
[   16.443096]   MEM window: dc100000-df2fffff
[   16.443108]   PREFETCH window: dfd00000-dfdfffff
[   16.443120] PCI: Bridge: 0000:00:1c.2
[   16.443127]   IO window: 5000-5fff
[   16.443143]   MEM window: d8000000-d9ffffff
[   16.443154]   PREFETCH window: dfa00000-dfafffff
[   16.443170] PCI: Bridge: 0000:00:1c.3
[   16.443177]   IO window: 6000-6fff
[   16.443192]   MEM window: d0000000-d1ffffff
[   16.443203]   PREFETCH window: df700000-df7fffff
[   16.443215] PCI: Bridge: 0000:00:1c.4
[   16.443222]   IO window: 7000-7fff
[   16.443238]   MEM window: cc000000-cdffffff
[   16.443247]   PREFETCH window: df400000-df4fffff
[   16.443270] PCI: Bus 22, cardbus bridge: 0000:15:00.0
[   16.443274]   IO window: 00008000-000080ff
[   16.443287]   IO window: 00008400-000084ff
[   16.443299]   PREFETCH window: f4000000-f7ffffff
[   16.443310]   MEM window: 80000000-83ffffff
[   16.443323] PCI: Bridge: 0000:00:1e.0
[   16.443330]   IO window: 8000-bfff
[   16.443344]   MEM window: f8100000-fbffffff
[   16.443356]   PREFETCH window: f4000000-f7ffffff
[   16.443393] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.443403] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.443466] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 20 (level, low) -> IRQ 17
[   16.443477] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.443539] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 21 (level, low) -> IRQ 18
[   16.443554] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.443614] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 22 (level, low) -> IRQ 19
[   16.443628] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   16.443687] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 23 (level, low) -> IRQ 20
[   16.443701] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.443761] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 20 (level, low) -> IRQ 17
[   16.443773] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   16.443802] PCI: Enabling device 0000:00:1e.0 (0005 -> 0007)
[   16.443819] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.443861] ACPI: PCI Interrupt 0000:15:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.443889] NET: Registered protocol family 2
[   16.479958] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.480365] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.481195] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.481573] TCP: Hash tables configured (established 131072 bind 65536)
[   16.481578] TCP reno registered
[   16.492053] checking if image is initramfs... it is
[   17.925075] Freeing initrd memory: 7322k freed
[   17.925179] Simple Boot Flag at 0x35 set to 0x1
[   17.926533] audit: initializing netlink socket (disabled)
[   17.926554] audit(1216979661.812:1): initialized
[   17.926755] highmem bounce pool size: 64 pages
[   17.930686] VFS: Disk quotas dquot_6.5.1
[   17.930826] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.931082] io scheduler noop registered
[   17.931087] io scheduler anticipatory registered
[   17.931090] io scheduler deadline registered
[   17.931112] io scheduler cfq registered (default)
[   17.931403] Boot video device is 0000:01:00.0
[   17.931618] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.931691] assign_interrupt_mode Found MSI capability
[   17.931750] Allocate Port Service[0000:00:01.0:pcie00]
[   17.931818] Allocate Port Service[0000:00:01.0:pcie02]
[   17.931983] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.932152] assign_interrupt_mode Found MSI capability
[   17.932270] Allocate Port Service[0000:00:1c.0:pcie00]
[   17.932333] Allocate Port Service[0000:00:1c.0:pcie02]
[   17.932576] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.932731] assign_interrupt_mode Found MSI capability
[   17.932849] Allocate Port Service[0000:00:1c.1:pcie00]
[   17.932915] Allocate Port Service[0000:00:1c.1:pcie02]
[   17.933167] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.933321] assign_interrupt_mode Found MSI capability
[   17.933439] Allocate Port Service[0000:00:1c.2:pcie00]
[   17.933507] Allocate Port Service[0000:00:1c.2:pcie02]
[   17.933754] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   17.933911] assign_interrupt_mode Found MSI capability
[   17.934026] Allocate Port Service[0000:00:1c.3:pcie00]
[   17.934089] Allocate Port Service[0000:00:1c.3:pcie02]
[   17.934345] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   17.934502] assign_interrupt_mode Found MSI capability
[   17.934617] Allocate Port Service[0000:00:1c.4:pcie00]
[   17.934682] Allocate Port Service[0000:00:1c.4:pcie02]
[   17.935238] isapnp: Scanning for PnP cards...
[   18.293257] isapnp: No Plug & Play device found
[   18.344424] Real Time Clock Driver v1.12ac
[   18.344600] hpet_resources: 0xfed00000 is busy
[   18.344680] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.347007] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.347135] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.347323] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   18.355938] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.355946] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.379656] mice: PS/2 mouse device common for all mice
[   18.379871] EISA: Probing bus 0 at eisa.0
[   18.379886] Cannot allocate resource for EISA slot 1
[   18.379892] Cannot allocate resource for EISA slot 2
[   18.379896] Cannot allocate resource for EISA slot 3
[   18.379900] Cannot allocate resource for EISA slot 4
[   18.379904] Cannot allocate resource for EISA slot 5
[   18.379908] Cannot allocate resource for EISA slot 6
[   18.379912] Cannot allocate resource for EISA slot 7
[   18.379916] Cannot allocate resource for EISA slot 8
[   18.379919] EISA: Detected 0 cards.
[   18.379924] cpuidle: using governor ladder
[   18.379927] cpuidle: using governor menu
[   18.380068] NET: Registered protocol family 1
[   18.380115] Using IPI No-Shortcut mode
[   18.380160] registered taskstats version 1
[   18.380409]   Magic number: 0:728:930
[   18.380443]   hash matches device ptyxf
[   18.380502] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.380506] EDD information not available.
[   18.380838] Freeing unused kernel memory: 368k freed
[   18.383768] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.817532] fuse init (API version 7.9)
[   19.859995] ACPI: SSDT 7DEE1B32, 02C4 (r1  PmRef  Cpu0Ist      100 INTL 20050513)
[   19.860627] ACPI: SSDT 7DEE1E7B, 085E (r1  PmRef  Cpu0Cst      100 INTL 20050513)
[   19.866215] Monitor-Mwait will be used to enter C-1 state
[   19.866222] Monitor-Mwait will be used to enter C-2 state
[   19.866227] Monitor-Mwait will be used to enter C-3 state
[   19.866478] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.866487] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.866961] ACPI: SSDT 7DEE1A6A, 00C8 (r1  PmRef  Cpu1Ist      100 INTL 20050513)
[   19.867562] ACPI: SSDT 7DEE1DF6, 0085 (r1  PmRef  Cpu1Cst      100 INTL 20050513)
[   19.871650] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   19.871660] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.876076] ACPI: Thermal Zone [THM0] (51 C)
[   19.879266] ACPI: Thermal Zone [THM1] (46 C)
[   20.184218] usbcore: registered new interface driver usbfs
[   20.184262] usbcore: registered new interface driver hub
[   20.184344] usbcore: registered new device driver usb
[   20.233004] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   20.233010] Copyright (c) 1999-2006 Intel Corporation.
[   20.233206] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 20 (level, low) -> IRQ 17
[   20.233230] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   20.246431] USB Universal Host Controller Interface driver v3.0
[   20.262501] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1c:25:be:7f:a3
[   20.361917] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   20.361963] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 17
[   20.361984] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   20.361994] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   20.362355] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   20.362414] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001860
[   20.362658] usb usb1: configuration #1 chosen from 1 choice
[   20.362705] hub 1-0:1.0: USB hub found
[   20.362714] hub 1-0:1.0: 2 ports detected
[   20.464973] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[   20.464997] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   20.465007] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   20.465050] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   20.465105] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001880
[   20.465319] usb usb2: configuration #1 chosen from 1 choice
[   20.465363] hub 2-0:1.0: USB hub found
[   20.465372] hub 2-0:1.0: 2 ports detected
[   20.568776] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   20.568798] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.568808] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.568852] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   20.568915] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[   20.569132] usb usb3: configuration #1 chosen from 1 choice
[   20.569177] hub 3-0:1.0: USB hub found
[   20.569186] hub 3-0:1.0: 2 ports detected
[   20.672593] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 21
[   20.672614] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.672624] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.672670] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   20.672730] uhci_hcd 0000:00:1d.1: irq 21, io base 0x000018c0
[   20.672944] usb usb4: configuration #1 chosen from 1 choice
[   20.672989] hub 4-0:1.0: USB hub found
[   20.672999] hub 4-0:1.0: 2 ports detected
[   20.776465] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 22
[   20.776489] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   20.776499] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   20.776544] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   20.776597] uhci_hcd 0000:00:1d.2: irq 22, io base 0x000018e0
[   20.776813] usb usb5: configuration #1 chosen from 1 choice
[   20.776860] hub 5-0:1.0: USB hub found
[   20.776870] hub 5-0:1.0: 2 ports detected
[   20.880664] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 19
[   20.880692] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   20.880701] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   20.880753] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   20.884696] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   20.884715] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfe226c00
[   20.900023] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.900217] usb usb6: configuration #1 chosen from 1 choice
[   20.900265] hub 6-0:1.0: USB hub found
[   20.900276] hub 6-0:1.0: 4 ports detected
[   20.973483] SCSI subsystem initialized
[   21.004239] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 23
[   21.004265] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.004274] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.004327] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   21.008278] ehci_hcd 0000:00:1d.7: debug port 1
[   21.008296] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   21.008313] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe227000
[   21.022647] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.022852] usb usb7: configuration #1 chosen from 1 choice
[   21.022900] hub 7-0:1.0: USB hub found
[   21.022911] hub 7-0:1.0: 6 ports detected
[   21.030129] libata version 3.00 loaded.
[   21.127010] ACPI: PCI Interrupt 0000:15:00.1[B] -> GSI 17 (level, low) -> IRQ 21
[   21.179765] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   21.184195] ahci 0000:00:1f.2: version 3.0
[   21.184247] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 16 (level, low) -> IRQ 16
[   21.184357] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
[   21.184363] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   21.965299] Clocksource tsc unstable (delta = -139801937 ns)
[   21.976012] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x7 impl SATA mode
[   21.976021] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   21.976035] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.976431] scsi0 : ahci
[   21.976857] scsi1 : ahci
[   21.977157] scsi2 : ahci
[   21.977274] ata1: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 217
[   21.977283] ata2: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226180 irq 217
[   21.977289] ata3: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 217
[   22.005255] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c0000655a41]
[   22.031937] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.036388] ata1.00: ATA-7: WDC WD800BEVS-08RST2, 08.01G08, max UDMA/133
[   22.036396] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   22.036968] ata1.00: configured for UDMA/133
[   22.065157] ata2: SATA link down (SStatus 0 SControl 0)
[   22.097046] ata3: SATA link down (SStatus 0 SControl 300)
[   22.097590] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BEVS-08 08.0 PQ: 0 ANSI: 5
[   22.098116] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[   22.098175] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.098203] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   22.104647] ata_piix 0000:00:1f.1: version 2.12
[   22.104671] ACPI: PCI Interrupt 0000:00:1f.1[C] -> GSI 16 (level, low) -> IRQ 16
[   22.104729] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.104844] scsi3 : ata_piix
[   22.104952] scsi4 : ata_piix
[   22.106570] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1830 irq 14
[   22.106576] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1838 irq 15
[   22.117449] Driver 'sd' needs updating - please use bus_type methods
[   22.117565] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   22.117588] sd 0:0:0:0: [sda] Write Protect is off
[   22.117594] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.117625] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.117712] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   22.117735] sd 0:0:0:0: [sda] Write Protect is off
[   22.117740] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.117775] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.117782]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[   22.132389] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.142883] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.236254] ata4.00: ATAPI: DVD/CDRW UJDA775, CB03, max UDMA/33
[   22.284157] ata4.00: configured for UDMA/33
[   22.284344] ata5: port disabled. ignoring.
[   22.285963] scsi 3:0:0:0: CD-ROM            MATSHITA DVD/CDRW UJDA775 CB03 PQ: 0 ANSI: 5
[   22.286117] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   22.301300] Driver 'sr' needs updating - please use bus_type methods
[   22.306606] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   22.306613] Uniform CD-ROM driver Revision: 3.20
[   22.306707] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   22.384433] Attempting manual resume
[   22.384439] swsusp: Resume From Partition 8:5
[   22.384442] PM: Checking swsusp image.
[   22.384638] PM: Resume from disk failed.
[   22.415526] kjournald starting.  Commit interval 5 seconds
[   22.415726] EXT3-fs: mounted filesystem with ordered data mode.
[   26.693442] Linux agpgart interface v0.102
[   26.941020] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.021174] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.148915] input: Power Button (FF) as /devices/virtual/input/input2
[   27.172502] ACPI: Power Button (FF) [PWRF]
[   27.172631] input: Lid Switch as /devices/virtual/input/input3
[   27.173176] ACPI: Lid Switch [LID]
[   27.173312] input: Sleep Button (CM) as /devices/virtual/input/input4
[   27.193632] ACPI: Sleep Button (CM) [SLPB]
[   27.516138] ACPI: WMI-Acer: Mapper loaded
[   28.067572] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   28.084025] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   28.087330] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input6
[   28.107965] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   29.021190] ath_hal: module license 'Proprietary' taints kernel.
[   29.073080] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   29.165093] ACPI: PCI Interrupt 0000:00:1b.0[B] -> GSI 17 (level, low) -> IRQ 21
[   29.165106] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   29.165142] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   29.200823] ACPI: AC Adapter [AC] (off-line)
[   29.324755] wlan: 0.9.4
[   29.392632] ath_pci: 0.9.4
[   29.456321] ACPI: Battery Slot [BAT0] (battery present)
[   29.570709] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 21
[   29.570734] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   30.122591] iTCO_vendor_support: vendor-support=0
[   30.144555] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.144752] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   30.144844] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.575466] ricoh-mmc: Ricoh MMC Controller disabling driver
[   30.575472] ricoh-mmc: Copyright(c) Philip Langdale
[   30.607405] sdhci: Secure Digital Host Controller Interface driver
[   30.607411] sdhci: Copyright(c) Pierre Ossman
[   31.278930] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   31.648349] ath_rate_sample: 1.2 (0.9.4)
[   31.649144] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   31.649159] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   31.649168] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   31.649185] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   31.649193] wifi0: mac 10.3 phy 6.1 radio 10.2
[   31.649201] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   31.649205] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   31.649209] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   31.649213] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   31.649217] wifi0: Use hw queue 8 for CAB traffic
[   31.649220] wifi0: Use hw queue 9 for beacons
[   31.709481] wifi0: Atheros 5212: mem=0xdf2f0000, irq=21
[   31.709764] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   31.837177] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   31.837185] Socket status: 30000006
[   31.837190] pcmcia: parent PCI bridge I/O window: 0x8000 - 0xbfff
[   31.837196] cs: IO port probe 0x8000-0xbfff: clean.
[   31.839461] pcmcia: parent PCI bridge Memory window: 0xf8100000 - 0xfbffffff
[   31.839466] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xf7ffffff
[   31.842058] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   31.842092] ricoh-mmc: Controller is now disabled.
[   31.842146] sdhci: SDHCI controller found at 0000:15:00.2 [1180:0822] (rev 21)
[   31.842194] ACPI: PCI Interrupt 0000:15:00.2[C] -> GSI 18 (level, low) -> IRQ 22
[   31.842225] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   31.842241] PCI: Setting latency timer of device 0000:15:00.2 to 64
[   31.842314] mmc0: SDHCI at 0xf8101800 irq 22 DMA
[   31.849392] Non-volatile memory driver v1.2
[   31.979695] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04791/0x300000
[   31.979705] serio: Synaptics pass-through port at isa0060/serio1/input0
[   32.019985] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   32.075431] thinkpad_acpi: ThinkPad ACPI Extras v0.17
[   32.075436] thinkpad_acpi: http://ibm-acpi.sf.net/
[   32.075440] thinkpad_acpi: ThinkPad BIOS 7LETC1WW (2.21 ), EC 7KHT24WW-1.08
[   32.075444] thinkpad_acpi: Lenovo ThinkPad T61
[   32.076051] thinkpad_acpi: radio switch found; radios are enabled
[   32.085899] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   32.086380] input: ThinkPad Extra Buttons as /devices/virtual/input/input9
[   33.683308] cs: IO port probe 0x100-0x3af: clean.
[   33.686600] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   33.687971] cs: IO port probe 0x820-0x8ff: clean.
[   33.689138] cs: IO port probe 0xc00-0xcf7: clean.
[   33.690557] cs: IO port probe 0xa00-0xaff: clean.
[   33.884202] lp: driver loaded but no devices found
[   34.106419] Adding 975200k swap on /dev/sda5.  Priority:-1 extents:1 across:975200k
[   34.167615] EXT3 FS on sda3, internal journal
[   35.007829] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.773862] ACPI: ACPI Dock Station Driver 
[   35.776811] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: found ejectable bay
[   35.776824] ACPI: \_SB_.PCI0.IDE0.PRIM.MSTR: Adding notify handler
[   35.776870] ACPI: Error installing bay notify handler
[   35.776877] ACPI: Bay [\_SB_.PCI0.IDE0.PRIM.MSTR] Added
[   36.632506] apm: BIOS not found.
[   36.725497] ppdev: user-space parallel port driver
[   36.802821] audit(1216994087.818:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5212 profile="/usr/sbin/cupsd" namespace="default"
[   36.821184] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   36.912564] input: /usr/sbin/thinkpad-keys as /devices/virtual/input/input10
[   37.025121] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input11
[   37.953637] Bluetooth: Core ver 2.11
[   37.954011] NET: Registered protocol family 31
[   37.954017] Bluetooth: HCI device and connection manager initialized
[   37.954024] Bluetooth: HCI socket layer initialized
[   38.002545] Bluetooth: L2CAP ver 2.9
[   38.002549] Bluetooth: L2CAP socket layer initialized
[   38.062141] Bluetooth: RFCOMM socket layer initialized
[   38.062160] Bluetooth: RFCOMM TTY layer initialized
[   38.062164] Bluetooth: RFCOMM ver 1.8
[   46.893640] NET: Registered protocol family 10
[   46.894387] lo: Disabled Privacy Extensions
[   46.895542] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   54.486771] CPU0 attaching NULL sched-domain.
[   54.486782] CPU1 attaching NULL sched-domain.
[   54.498079] CPU0 attaching sched-domain:
[   54.498090]  domain 0: span 03
[   54.498094]   groups: 01 02
[   54.498100]   domain 1: span 03
[   54.498103]    groups: 03
[   54.498108] CPU1 attaching sched-domain:
[   54.498111]  domain 0: span 03
[   54.498114]   groups: 02 01
[   54.498121]   domain 1: span 03
[   54.498124]    groups: 03
[   55.590144] NET: Registered protocol family 17
[   57.290743] ath0: no IPv6 routers present
[   75.927457] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[   78.455972] ath0: no IPv6 routers present
[   94.750486] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[   94.750501] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[   94.754670] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   97.596291] eth0: no IPv6 routers present
[  101.906521] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  104.043360] ath0: no IPv6 routers present
[  118.413029] eth0: no IPv6 routers present
[  122.667772] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  124.594180] ath0: no IPv6 routers present
[  138.247246] eth0: no IPv6 routers present
[  142.588339] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  143.317419] ath0: no IPv6 routers present
[  150.563270] eth0: no IPv6 routers present
[  152.819890] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  154.272552] ath0: no IPv6 routers present
[  159.776349] eth0: no IPv6 routers present

```

If you have any ideas, please let me know. I really am a noobie, but happy to read up on things if anyone can point me in the right direction.
Thanks in advance for any help!

---

### Post by checksquid on 2008-07-25
Forgot to mention: the wireless works fine in Vista, so I don't think it's a hardware or router problem.

---

### Post by match002001 on 2008-07-25
Is this an Atheros Wireless card?

---

### Post by moore.bryan on 2008-07-25
i'm assuming you've already installed the restricted drivers, since you can intermittently connect; correct? and you're using an atheros card, so there might be some snags...

try this and see what happens:
```

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
sudo iwconfig ath0 essid "Chocolatedessert"
sudo iwconfig ath0 mode Managed
sudo dhclient ath0

```
====
EDIT:
oh, and are you using [network-manager]("http://en.wikipedia.org/wiki/Network-manager") or [wicd]("http://wicd.sourceforge.net/")?

---

### Post by match002001 on 2008-07-25
What you can also try and do if that does not work is to go to System > Preferences > Network and see if you can configure the wireless network in there.

that's the easiest way....

If you don't see the wireless network to configure in there you can go to terminal and type in 

```
modprobe wlan0
```

then type:

```
iwconfig
```

then see if the wlan is in there.

Hope this helps

---

### Post by checksquid on 2008-07-25
Wow! Thanks for the quick responses!
I tried
```

sudo ifconfig ath0 down
sudo dhclient -r ath0
sudo ifconfig ath0 up
sudo iwconfig ath0 essid "Chocolatedessert"
sudo iwconfig ath0 mode Managed
sudo dhclient ath0

```

after the last command and got two lines of "wifi0: unknown hardware address type 801", then some stuff about ath0 ending in:
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I believe I'm using network manager. I'm not sure where to look, but if I click on the network icon at the top of the screen the dialog looks like network-manager from the links you sent.

I tried going to System-->Administration-->Network, disabling roaming mode, and putting in my ESSID with automatic configuration (DHCP). I didn't know what to do about "Password type" since I have no security, so I left it on WPA personal and didn't put anything in the password field. Anyway, that did not make a successful connection.

It is an Atheros card. I believe the restricted drivers are installed. In lsmod there are ath_hal and ath_pci; is that it?

---

### Post by checksquid on 2008-07-25
Odd, I switched back to roaming mode and it now thinks it has connected to my router--the icon at the top of the screen shows wireless bars and the tool-tip says I have a 97% connection. But I can't seem to get anything (like google) in firefox.
iwgetid ath0 returns ath0 ESSID:"".

---

### Post by checksquid on 2008-07-25
My router is no longer in the list of wireless networks. I restarted, but it still isn't there. If I boot into Vista I can connect, and another computer right next to mine is connected to the router wirelessly with no problem.

---

### Post by checksquid on 2008-07-25
When I enter modprobe wlan0, I get "FATAL: Module wlan0 not found."
When I enter iwconfig, I get the following:
lo    no wireless extensions
eth0  no wireless extensions
wifi0 no wireless extensions
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-91 dBm  Noise level=-91 dBm
          Rx invalid nwid:28839  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by match002001 on 2008-07-25
Yuck I had so many problems with my Atheros card, specially with Arklinux. 

yeah that WEP key is pretty important. You might want to log into your router and get that key. For that I would recommend you either google your router's setup or pull out the trusty manual that came with the router. 

Another question:

Do you see other wireless networks around you or is it just a dead zone?

---

### Post by match002001 on 2008-07-25
> **checksquid said:**
> When I enter modprobe wlan0, I get "FATAL: Module wlan0 not found."
When I enter iwconfig, I get the following:
lo    no wireless extensions
eth0  no wireless extensions
wifi0 no wireless extensions
ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-91 dBm  Noise level=-91 dBm
          Rx invalid nwid:28839  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

AH HAH!

Go through Synaptics and get ndiswrapper.

Then find the Atheros driver for windows so that you can get the wlan0 to work. (all you need is the *.inf file really)

in the terminal type this:

```
ndiswrapper -i /PATH TO *.INF FILE/
```

then:

```
modprobe wlan0
```

finally:

```
iwconfig
```

wlan0 should show up in the list then you would use the network setup to get that connected. sadly you still need that WEP key.

---

### Post by checksquid on 2008-07-25
The router has WEP disabled. (I usually just use MAC filtering, but I have that turned off for now.) Does Ubuntu require WEP to be on?
I do see other networks in the area. There is one unsecured network besides mine, but I can't connect to it either. (Other computers can.)

In the mean time, I tried installing Wicd, but that didn't seem to work, so I reinstalled network-manager. I can see my router as an option again now, but still can't connect.

Thanks for your help so far! Any other things I could check?

Edit:
Sorry--I hadn't seen your previous message. Let me look at that and post the result. :)

---

### Post by match002001 on 2008-07-25
You do not need WEP enabled but it's probably a good idea. MAC filtering isn't that secure. you might have to configure it through iwconfig by typing this in the terminal:

```
iwconfig wlan0 essid NETWORK_NAME key WEP_KEY(IF YOU SET IT UP THAT WAY) channel WHATEVER_CHANNEL_YOU_HAVE_YOUR_ROUTER_SET_TO
```

that should at least get you connected to the router.

---

### Post by checksquid on 2008-07-25
Fantastic! I set up ndiswrapper, got the the driver from Lenovo, and now it's working. Linux, here I come!
Thanks again for your help.

---

### Post by match002001 on 2008-07-25
not a problem

---

