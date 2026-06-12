---
title: "[SOLVED] not enough free space!!!"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-08-11
Apparently i dont have enough free space on my pc even though I've just deleted over 20gigs of files programs are stil telling me that i dont have enough frre space! 

and i keep getting this error when i try and extract an archive

```
Write error in the file /home/carl/Desktop/pokemon/p-3x01.part1/pokemon johto league s03e01-dont touch that dile [fp].avi [R]etry, [A]bort 
Write error in the file /home/carl/Desktop/pokemon/p-3x01.part1/pokemon johto league s03e01-dont touch that dile [fp].avi
Inappropriate ioctl for device

```

please help

---

### Post by oldos2er on 2008-08-11
Have you run fsck lately?

---

### Post by kamitsukai on 2008-08-11
erm...whats fsck? (so thats a no...)

---

### Post by pparks1 on 2008-08-11
fsck is the check disk utility that scans the hard drive for errors, bad sectors, etc.

The error that you are seeing, doesn't seem like a typical "disk is full" error message to me.

---

### Post by Java Geek on 2008-08-11
Try emptying the trash can. Even when things are in there, it still uses memory. To empty right click/ empty

---

### Post by Zimmer on 2008-08-11
Hmm, most likely a filename parsing error in the extraction program. The filename in question has many spaces which might require quoting if typed in a command at the terminal. Not sure how you would resolve it, though. You are relying on the file extraction program to do the job. If you look hard enough you might find the correct terminal commands to unzip the file in question and be able to quote the file name in the command...
Also, possibility DMA not enabled (if supported on your drive)
Worth reading this to see if you have a problem here...
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by kamitsukai on 2008-08-11
"If you experience jumpy DVD playback, slow CD ripping, or a general slow down when accessing optical drive(s) it may be because DMA is not enabled. DMA, or Direct Memory Access, lets hard drives and CD/DVD drives access the system memory."

Im not expieriencing that...Ok how do i start fsck? if it finds problems will it fix them? is the data on my ubuntu install going to be ok? lol

Also would it be easier just to give up and re-install?

---

### Post by kamitsukai on 2008-08-11
Heres my Dmesg:

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
[    0.000000] Detected 2200.036 MHz processor.
[   16.957570] spurious 8259A interrupt: IRQ7.
[   16.960706] Console: colour VGA+ 80x25
[   16.960709] console [tty0] enabled
[   16.960993] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.961303] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.023115] Memory: 1805472k/1833920k available (2177k kernel code, 27248k reserved, 1006k data, 368k init, 916416k highmem)
[   17.023122] virtual kernel memory layout:
[   17.023123]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.023124]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.023125]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.023126]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.023127]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   17.023128]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   17.023129]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   17.023131] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.023161] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   17.023283] hpet clockevent registered
[   17.103209] Calibrating delay using timer specific routine.. 4404.38 BogoMIPS (lpj=8808777)
[   17.103227] Security Framework initialized
[   17.103231] SELinux:  Disabled at boot.
[   17.103243] AppArmor: AppArmor initialized
[   17.103246] Failure registering capabilities with primary security module.
[   17.103253] Mount-cache hash table entries: 512
[   17.103345] Initializing cgroup subsys ns
[   17.103348] Initializing cgroup subsys cpuacct
[   17.103356] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   17.103363] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.103365] CPU: L2 Cache: 512K (64 bytes/line)
[   17.103367] CPU 0(2) -> Core 0
[   17.103369] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   17.103377] Compat vDSO mapped to ffffe000.
[   17.103385] Checking 'hlt' instruction... OK.
[   17.119425] SMP alternatives: switching to UP code
[   17.120437] Early unpacking initramfs... done
[   17.444195] ACPI: Core revision 20070126
[   17.444250] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.447366] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   17.447380] SMP alternatives: switching to SMP code
[   17.447749] Booting processor 1/1 eip 3000
[   17.458080] Initializing CPU#1
[   17.535118] Calibrating delay using timer specific routine.. 4400.02 BogoMIPS (lpj=8800042)
[   17.535123] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   17.535129] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.535131] CPU: L2 Cache: 512K (64 bytes/line)
[   17.535133] CPU 1(2) -> Core 1
[   17.535134] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   17.535004] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   17.535019] Total of 2 processors activated (8804.40 BogoMIPS).
[   17.535250] ENABLING IO-APIC IRQs
[   17.535476] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.682733] Brought up 2 CPUs
[   17.682775] CPU0 attaching sched-domain:
[   17.682777]  domain 0: span 03
[   17.682779]   groups: 01 02
[   17.682781] CPU1 attaching sched-domain:
[   17.682783]  domain 0: span 03
[   17.682784]   groups: 02 01
[   17.682949] net_namespace: 64 bytes
[   17.682954] Booting paravirtualized kernel on bare hardware
[   17.683352] Time: 16:25:14  Date: 08/11/08
[   17.683373] NET: Registered protocol family 16
[   17.683525] EISA bus registered
[   17.683528] ACPI: bus type pci registered
[   17.689078] PCI: PCI BIOS revision 3.00 entry at 0xfa1d0, last bus=8
[   17.689080] PCI: Using configuration type 1
[   17.689086] Setting up standard PCI resources
[   17.693441] ACPI: EC: Look up EC in DSDT
[   17.698486] ACPI: Interpreter enabled
[   17.698488] ACPI: (supports S0 S1 S4 S5)
[   17.698499] ACPI: Using IOAPIC for interrupt routing
[   17.706921] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   17.707558] PCI: Transparent bridge - 0000:00:08.0
[   17.707934] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.708131] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   17.758830] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.758984] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.759136] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.759287] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.759439] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.759590] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.759740] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.759892] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.760043] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.760196] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[   17.760348] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   17.760501] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   17.760656] ACPI: PCI Interrupt Link [LU1B] (IRQs *5 7 9 10 11 14 15)
[   17.760808] ACPI: PCI Interrupt Link [LU2B] (IRQs 5 7 9 *10 11 14 15)
[   17.760960] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 11 14 *15)
[   17.761112] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   17.761263] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.761416] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   17.761567] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   17.761720] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   17.761900] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   17.762075] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   17.762249] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   17.762422] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   17.762601] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   17.762775] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   17.762949] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   17.763122] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   17.763296] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[   17.763470] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[   17.763644] ACPI: PCI Interrupt Link [AUB2] (IRQs 20 21 22 23) *0
[   17.763819] ACPI: PCI Interrupt Link [AU1B] (IRQs 20 21 22 23) *0
[   17.763994] ACPI: PCI Interrupt Link [AU2B] (IRQs 20 21 22 23) *0
[   17.764169] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   17.764342] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   17.764517] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   17.764691] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   17.764865] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   17.765039] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   17.765214] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   17.765331] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.765356] pnp: PnP ACPI init
[   17.765362] ACPI: bus type pnp registered
[   17.766096] ACPI Error (psargs-0355): [GUR_._BAS] Namespace lookup failure, AE_NOT_FOUND
[   17.766101] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.MBIO._CRS] (Node f7c4a078), AE_NOT_FOUND
[   17.769999] pnpacpi: exceeded the max number of mem resources: 12
[   17.770055] pnp: PnP ACPI: found 13 devices
[   17.770057] ACPI: ACPI bus type pnp unregistered
[   17.770060] PnPBIOS: Disabled by ACPI PNP
[   17.770233] PCI: Using ACPI for IRQ routing
[   17.770237] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.866466] NET: Registered protocol family 8
[   17.866468] NET: Registered protocol family 20
[   17.866495] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   17.866499] hpet0: 3 32-bit timers, 25000000 Hz
[   17.867535] AppArmor: AppArmor Filesystem Enabled
[   17.870457] Time: hpet clocksource has been installed.
[   17.870469] Switched to high resolution mode on CPU 0
[   17.870892] Switched to high resolution mode on CPU 1
[   17.878444] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   17.878446] system 00:02: ioport range 0x800-0x87f has been reserved
[   17.878449] system 00:02: ioport range 0x290-0x297 has been reserved
[   17.878456] system 00:0b: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   17.878461] system 00:0c: iomem range 0xf0000-0xfffff could not be reserved
[   17.878464] system 00:0c: iomem range 0xfeff0000-0xfeff00ff could not be reserved
[   17.878467] system 00:0c: iomem range 0x6fef0000-0x6fefffff could not be reserved
[   17.878469] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[   17.878472] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   17.878474] system 00:0c: iomem range 0x100000-0x6feeffff could not be reserved
[   17.878476] system 00:0c: iomem range 0x70000000-0x7fffffff could not be reserved
[   17.878479] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   17.878482] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
[   17.878484] system 00:0c: iomem range 0xfefff000-0xfeffffff could not be reserved
[   17.878487] system 00:0c: iomem range 0xfff80000-0xfff80fff could not be reserved
[   17.878489] system 00:0c: iomem range 0xfff90000-0xfffbffff could not be reserved
[   17.908817] PCI: Bridge: 0000:00:08.0
[   17.908820]   IO window: c000-cfff
[   17.908823]   MEM window: fd000000-fd0fffff
[   17.908825]   PREFETCH window: fdf00000-fdffffff
[   17.908828] PCI: Bridge: 0000:00:0b.0
[   17.908830]   IO window: b000-bfff
[   17.908832]   MEM window: fde00000-fdefffff
[   17.908834]   PREFETCH window: fdd00000-fddfffff
[   17.908836] PCI: Bridge: 0000:00:0c.0
[   17.908837]   IO window: a000-afff
[   17.908839]   MEM window: fdc00000-fdcfffff
[   17.908841]   PREFETCH window: fdb00000-fdbfffff
[   17.908844] PCI: Bridge: 0000:00:0d.0
[   17.908845]   IO window: 9000-9fff
[   17.908847]   MEM window: fda00000-fdafffff
[   17.908849]   PREFETCH window: fd900000-fd9fffff
[   17.908851] PCI: Bridge: 0000:00:0e.0
[   17.908853]   IO window: 8000-8fff
[   17.908855]   MEM window: fd800000-fd8fffff
[   17.908857]   PREFETCH window: fd700000-fd7fffff
[   17.908859] PCI: Bridge: 0000:00:0f.0
[   17.908861]   IO window: 7000-7fff
[   17.908863]   MEM window: fd600000-fd6fffff
[   17.908865]   PREFETCH window: fd500000-fd5fffff
[   17.908867] PCI: Bridge: 0000:00:10.0
[   17.908869]   IO window: 6000-6fff
[   17.908871]   MEM window: fd400000-fd4fffff
[   17.908873]   PREFETCH window: fd300000-fd3fffff
[   17.908875] PCI: Bridge: 0000:00:11.0
[   17.908877]   IO window: 5000-5fff
[   17.908879]   MEM window: fd200000-fd2fffff
[   17.908881]   PREFETCH window: fd100000-fd1fffff
[   17.908890] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   17.908898] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   17.908903] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   17.908909] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   17.908914] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   17.908919] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   17.908924] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   17.908929] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   17.908940] NET: Registered protocol family 2
[   17.946405] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.946644] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.947235] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   17.947507] TCP: Hash tables configured (established 131072 bind 65536)
[   17.947510] TCP reno registered
[   17.958447] checking if image is initramfs... it is
[   18.585014] Freeing initrd memory: 7924k freed
[   18.586050] audit: initializing netlink socket (disabled)
[   18.586063] audit(1218471914.452:1): initialized
[   18.586209] highmem bounce pool size: 64 pages
[   18.587816] VFS: Disk quotas dquot_6.5.1
[   18.587874] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.587973] io scheduler noop registered
[   18.587975] io scheduler anticipatory registered
[   18.587976] io scheduler deadline registered
[   18.587984] io scheduler cfq registered (default)
[   18.588012] pci 0000:00:00.0: Enabling HT MSI Mapping
[   18.619094] pci 0000:00:07.0: Enabling HT MSI Mapping
[   18.619106] pci 0000:00:08.0: Enabling HT MSI Mapping
[   18.619119] pci 0000:00:09.0: Enabling HT MSI Mapping
[   18.619134] pci 0000:00:0a.0: Enabling HT MSI Mapping
[   18.619146] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   18.619159] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   18.619172] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   18.619185] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   18.619198] pci 0000:00:0f.0: Enabling HT MSI Mapping
[   18.619211] pci 0000:00:10.0: Enabling HT MSI Mapping
[   18.619224] pci 0000:00:11.0: Enabling HT MSI Mapping
[   18.619236] Boot video device is 0000:00:12.0
[   18.619331] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   18.619350] assign_interrupt_mode Found MSI capability
[   18.619366] Allocate Port Service[0000:00:0b.0:pcie00]
[   18.619419] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.619437] assign_interrupt_mode Found MSI capability
[   18.619451] Allocate Port Service[0000:00:0c.0:pcie00]
[   18.619500] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   18.619518] assign_interrupt_mode Found MSI capability
[   18.619531] Allocate Port Service[0000:00:0d.0:pcie00]
[   18.619580] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   18.619598] assign_interrupt_mode Found MSI capability
[   18.619611] Allocate Port Service[0000:00:0e.0:pcie00]
[   18.619659] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   18.619677] assign_interrupt_mode Found MSI capability
[   18.619690] Allocate Port Service[0000:00:0f.0:pcie00]
[   18.619739] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   18.619757] assign_interrupt_mode Found MSI capability
[   18.619770] Allocate Port Service[0000:00:10.0:pcie00]
[   18.619818] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   18.619837] assign_interrupt_mode Found MSI capability
[   18.619849] Allocate Port Service[0000:00:11.0:pcie00]
[   18.620030] isapnp: Scanning for PnP cards...
[   18.972308] isapnp: No Plug & Play device found
[   18.996508] Real Time Clock Driver v1.12ac
[   18.996680] hpet_resources: 0xfeff0000 is busy
[   18.996713] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.996828] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.997319] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.997986] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.998044] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.998170] PNP: No PS/2 controller found. Probing ports directly.
[   18.998523] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.998528] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.010678] mice: PS/2 mouse device common for all mice
[   19.010784] EISA: Probing bus 0 at eisa.0
[   19.010789] Cannot allocate resource for EISA slot 1
[   19.010798] Cannot allocate resource for EISA slot 5
[   19.010800] Cannot allocate resource for EISA slot 6
[   19.010802] Cannot allocate resource for EISA slot 7
[   19.010803] Cannot allocate resource for EISA slot 8
[   19.010805] EISA: Detected 0 cards.
[   19.010807] cpuidle: using governor ladder
[   19.010809] cpuidle: using governor menu
[   19.010878] NET: Registered protocol family 1
[   19.010900] Using IPI No-Shortcut mode
[   19.010928] registered taskstats version 1
[   19.011030]   Magic number: 4:908:438
[   19.011153] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.011155] EDD information not available.
[   19.011358] Freeing unused kernel memory: 368k freed
[   20.237040] fuse init (API version 7.9)
[   20.251232] ACPI: Fan [FAN] (on)
[   20.257115] ACPI: Thermal Zone [THRM] (40 C)
[   20.704679] usbcore: registered new interface driver usbfs
[   20.704701] usbcore: registered new interface driver hub
[   20.704948] usbcore: registered new device driver usb
[   20.705796] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.706133] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 23
[   20.706141] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [AUBA] -> GSI 23 (level, low) -> IRQ 16
[   20.706151] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   20.706154] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   20.706399] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   20.706413] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfe02f000
[   20.734274] SCSI subsystem initialized
[   20.751106] libata version 3.00 loaded.
[   20.761573] usb usb1: configuration #1 chosen from 1 choice
[   20.761592] hub 1-0:1.0: USB hub found
[   20.761599] hub 1-0:1.0: 6 ports detected
[   20.863788] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 22
[   20.863799] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [AU1B] -> GSI 22 (level, low) -> IRQ 17
[   20.863813] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   20.863816] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   20.863838] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[   20.863852] ohci_hcd 0000:00:04.0: irq 17, io mem 0xfe02d000
[   20.907232] FDC 0 is a post-1991 82077
[   20.921393] usb usb2: configuration #1 chosen from 1 choice
[   20.921414] hub 2-0:1.0: USB hub found
[   20.921420] hub 2-0:1.0: 6 ports detected
[   21.023685] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 21
[   21.023695] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [AUB2] -> GSI 21 (level, low) -> IRQ 18
[   21.023705] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   21.023708] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   21.023730] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[   21.023754] ehci_hcd 0000:00:02.1: debug port 1
[   21.023758] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   21.023767] ehci_hcd 0000:00:02.1: irq 18, io mem 0xfe02e000
[   21.167068] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   21.179042] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.179132] usb usb3: configuration #1 chosen from 1 choice
[   21.179153] hub 3-0:1.0: USB hub found
[   21.179158] hub 3-0:1.0: 6 ports detected
[   21.283329] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 20
[   21.283339] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [AU2B] -> GSI 20 (level, low) -> IRQ 19
[   21.283351] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   21.283354] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   21.283375] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[   21.283399] ehci_hcd 0000:00:04.1: debug port 1
[   21.283402] PCI: cache line size of 64 is not supported by device 0000:00:04.1
[   21.283411] ehci_hcd 0000:00:04.1: irq 19, io mem 0xfe02c000
[   21.294925] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.294998] usb usb4: configuration #1 chosen from 1 choice
[   21.295016] hub 4-0:1.0: USB hub found
[   21.295021] hub 4-0:1.0: 6 ports detected
[   21.399143] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   21.399460] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   21.399463] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 16
[   21.399468] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   21.602620] usb 3-2: new high speed USB device using ehci_hcd and address 2
[   21.735904] usb 3-2: configuration #1 chosen from 1 choice
[   21.735963] hub 3-2:1.0: USB hub found
[   21.736070] hub 3-2:1.0: 2 ports detected
[   21.918731] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:e0:4d:62:51:07
[   21.918737] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   21.921552] ahci 0000:00:09.0: version 3.0
[   21.921869] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[   21.921872] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [APSI] -> GSI 22 (level, low) -> IRQ 17
[   22.039292] usb 3-2.1: new high speed USB device using ehci_hcd and address 3
[   22.153501] usb 3-2.1: configuration #1 chosen from 1 choice
[   22.354991] usb 3-2.2: new high speed USB device using ehci_hcd and address 4
[   22.463216] usb 3-2.2: configuration #1 chosen from 1 choice
[   22.463273] hub 3-2.2:1.0: USB hub found
[   22.463382] hub 3-2.2:1.0: 4 ports detected
[   22.781839] usb 3-2.2.1: new high speed USB device using ehci_hcd and address 5
[   22.883069] usb 3-2.2.1: configuration #1 chosen from 1 choice
[   22.883125] hub 3-2.2.1:1.0: USB hub found
[   22.883234] hub 3-2.2.1:1.0: 3 ports detected
[   22.921294] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   22.921299] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio
[   22.921302] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.921592] scsi0 : ahci
[   22.921823] scsi1 : ahci
[   22.921940] scsi2 : ahci
[   22.922052] scsi3 : ahci
[   22.922120] ata1: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 216
[   22.922122] ata2: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 216
[   22.922125] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 216
[   22.922127] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 216
[   23.185456] usb 3-2.2.4: new low speed USB device using ehci_hcd and address 6
[   23.240973] ata1: SATA link down (SStatus 0 SControl 300)
[   23.279935] usb 3-2.2.4: configuration #1 chosen from 1 choice
[   23.481178] usb 3-2.2.1.2: new low speed USB device using ehci_hcd and address 7
[   23.560654] ata2: SATA link down (SStatus 0 SControl 300)
[   23.580283] usb 3-2.2.1.2: configuration #1 chosen from 1 choice
[   23.581839] usbcore: registered new interface driver hiddev
[   23.584353] input: HID 062a:0000 as /devices/pci0000:00/0000:00:02.1/usb3/3-2/3-2.2/3-2.2.4/3-2.2.4:1.0/input/input1
[   23.598014] input,hidraw0: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:02.1-2.2.4
[   23.602110] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:02.1/usb3/3-2/3-2.2/3-2.2.1/3-2.2.1.2/3-2.2.1.2:1.0/input/input2
[   23.625948] input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:02.1-2.2.1.2
[   23.628948] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:02.1/usb3/3-2/3-2.2/3-2.2.1/3-2.2.1.2/3-2.2.1.2:1.1/input/input3
[   23.645920] input,hidraw2: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:02.1-2.2.1.2
[   23.645931] usbcore: registered new interface driver usbhid
[   23.645934] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   23.880324] ata3: SATA link down (SStatus 0 SControl 300)
[   24.519659] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   24.520859] ata4.00: ATA-7: Hitachi HDS721616PLA380, P22OABEA, max UDMA/133
[   24.520864] ata4.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   24.521876] ata4.00: configured for UDMA/133
[   24.521642] scsi 3:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[   24.524642] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.527494] pata_amd 0000:00:06.0: version 0.3.10
[   24.527521] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.527890] scsi4 : pata_amd
[   24.527933] scsi5 : pata_amd
[   24.528443] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   24.528445] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   24.534638] Driver 'sd' needs updating - please use bus_type methods
[   24.534709] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   24.534720] sd 3:0:0:0: [sda] Write Protect is off
[   24.534722] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.534737] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.534777] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   24.534785] sd 3:0:0:0: [sda] Write Protect is off
[   24.534787] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.534799] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.534802]  sda: sda2 < sda5 sda6 >
[   24.566633] sd 3:0:0:0: [sda] Attached SCSI disk
[   24.570516] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   24.734159] Attempting manual resume
[   24.734163] swsusp: Resume From Partition 8:6
[   24.734164] PM: Checking swsusp image.
[   24.734282] PM: Resume from disk failed.
[   24.770914] kjournald starting.  Commit interval 5 seconds
[   24.771268] EXT3-fs: mounted filesystem with ordered data mode.
[   24.847639] ata5.00: ATAPI: Optiarc DVD RW AD-5200A, 1.03, max UDMA/66
[   25.023369] ata5.00: configured for UDMA/66
[   25.023400] ata6: port disabled. ignoring.
[   25.025375] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-5200A  1.03 PQ: 0 ANSI: 5
[   25.025463] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   30.600909] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   30.706771] parport_pc 00:0a: reported by Plug and Play ACPI
[   30.706815] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   30.732703] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.762749] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.850507] input: Power Button (FF) as /devices/virtual/input/input5
[   30.986073] Linux agpgart interface v0.102
[   31.013032] ACPI: Power Button (FF) [PWRF]
[   31.013082] input: Power Button (CM) as /devices/virtual/input/input6
[   31.080959] ACPI: Power Button (CM) [PWRB]
[   31.081008] input: Sleep Button (CM) as /devices/virtual/input/input7
[   31.144913] ACPI: Sleep Button (CM) [SLPB]
[   31.258217] nvidia: module license 'NVIDIA' taints kernel.
[   32.105627] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   32.105632] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [AAZA] -> GSI 21 (level, low) -> IRQ 18
[   32.105650] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   32.139931] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   32.180116] Driver 'sr' needs updating - please use bus_type methods
[   32.208716] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   32.208721] Uniform CD-ROM driver Revision: 3.20
[   32.208770] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   32.355740] ACPI: WMI-Acer: Mapper loaded
[   32.363888] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[   32.363893] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [AIGP] -> GSI 20 (level, low) -> IRQ 19
[   32.363899] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   32.364089] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   32.548833] Linux video capture interface: v2.00
[   32.633684] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[   32.634015] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   32.657563] usbcore: registered new interface driver uvcvideo
[   32.657568] USB Video Class driver (v0.1.0)
[   32.823370] usbcore: registered new interface driver snd-usb-audio
[   33.945191] lp0: using parport0 (interrupt-driven).
[   34.004739] Adding 915664k swap on /dev/sda6.  Priority:-1 extents:1 across:915664k
[   34.562783] EXT3 FS on sda5, internal journal
[   34.762713] device-mapper: uevent: version 1.0.3
[   34.762740] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   36.052902] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.565724] No dock devices found.
[   36.840188] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (2 cpu cores) (version 2.20.00)
[   36.839919] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xa
[   36.839923] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xc
[   36.839926] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xe
[   36.839928] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   37.970199] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   37.970204] apm: disabled - APM is not SMP safe.
[   38.477342] ppdev: user-space parallel port driver
[   38.620527] audit(1218468334.765:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5488 profile="/usr/sbin/cupsd" namespace="default"
[   40.378614] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   40.378618] vboxdrv: Successfully done.
[   40.378620] vboxdrv: Found 2 processor cores.
[   40.378639] vboxdrv: fAsync=1 u64DiffCores=663342.
[   40.379565] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   40.379567] vboxdrv: Successfully loaded version 1.6.4 (interface 0x00080000).
[   40.480346] Clocksource tsc unstable (delta = -130930384 ns)
[   41.393014] Bluetooth: Core ver 2.11
[   41.393231] NET: Registered protocol family 31
[   41.393234] Bluetooth: HCI device and connection manager initialized
[   41.393237] Bluetooth: HCI socket layer initialized
[   41.412334] Bluetooth: L2CAP ver 2.9
[   41.412338] Bluetooth: L2CAP socket layer initialized
[   41.450848] Bluetooth: RFCOMM socket layer initialized
[   41.451054] Bluetooth: RFCOMM TTY layer initialized
[   41.451056] Bluetooth: RFCOMM ver 1.8
[   42.863167] NET: Registered protocol family 17
[   43.518977] /dev/vmmon[6032]: Module vmmon: registered with major=10 minor=165
[   43.519001] /dev/vmmon[6032]: Module vmmon: initialized
[   44.030381] /dev/vmnet: open called by PID 6094 (vmnet-bridge)
[   44.030589] /dev/vmnet: hub 0 does not exist, allocating memory.
[   44.030764] /dev/vmnet: port on hub 0 successfully opened
[   44.030928] bridge-eth0: enabling the bridge
[   44.031058] bridge-eth0: up
[   44.031148] bridge-eth0: already up
[   44.031151] bridge-eth0: attached
[   44.178757] NET: Registered protocol family 10
[   44.179135] lo: Disabled Privacy Extensions
[   44.182582] /dev/vmnet: open called by PID 6108 (vmnet-natd)
[   44.182591] /dev/vmnet: hub 8 does not exist, allocating memory.
[   44.182601] /dev/vmnet: port on hub 8 successfully opened
[   44.503813] /dev/vmnet: open called by PID 6204 (vmnet-netifup)
[   44.503825] /dev/vmnet: hub 1 does not exist, allocating memory.
[   44.503835] /dev/vmnet: port on hub 1 successfully opened
[   44.505318] /dev/vmnet: open called by PID 6205 (vmnet-netifup)
[   44.505332] /dev/vmnet: port on hub 8 successfully opened
[   44.807152] /dev/vmnet: open called by PID 6238 (vmnet-dhcpd)
[   44.807164] /dev/vmnet: port on hub 8 successfully opened
[   44.808120] /dev/vmnet: open called by PID 6234 (vmnet-dhcpd)
[   44.808132] /dev/vmnet: port on hub 1 successfully opened
[   48.816130] eth0: no IPv6 routers present
[   49.081313] vmnet8: no IPv6 routers present
[   49.158676] vmnet1: no IPv6 routers present

```

---

### Post by kamitsukai on 2008-08-11
Oops double post...

---

### Post by hyper_ch on 2008-08-11
```

df -l

```

will show you all partitions, what size they are, how much is used.

---

### Post by kamitsukai on 2008-08-11
```
carl@carl-bedroom:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5            154147972 147919272     13800 100% /
varrun                  907288       148    907140   1% /var/run
varlock                 907288         0    907288   0% /var/lock
udev                    907288        48    907240   1% /dev
devshm                  907288       184    907104   1% /dev/shm
lrm                     907288     39760    867528   5% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon     154147972 147919272     13800 100% /home/carl/.gvfs

```

If I'm reading this right it says that I'm using 100%? thats impossible

My home folder only has 33gig's in it so unless the filesystem on Ubuntu has suddenly gone down hill...

is it possible that maybe some of my downloads have temp data lying around? yet even so I deleted over 20gigs of video from my home folder only about an hour ago so why is it still at 100%???

---

### Post by kamitsukai on 2008-08-11
> **Java Geek said:**
> Try emptying the trash can. Even when things are in there, it still uses memory. To empty right click/ empty

Always the simple things, i clicked empty wastebasket from the dock which told me that it was empty when actually it was so full that i just deleted 4 files and i now have 60gigs of free space:lolflag:

---

### Post by Elfy on 2008-08-11
Have you checked roots trash? - Really should refresh before posting :)

---

### Post by bodhi.zazen on 2008-08-11
> **kamitsukai said:**
> Always the simple things, i clicked empty wastebasket from the dock which told me that it was empty when actually it was so full that i just deleted 4 files and i now have 60gigs of free space:lolflag:

Woot ... :guitar:

Please mark this thread as solved, it saves the time of many volunteers looking to help 
[indent]... and users looking for solutions.[/indent]

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Second, please as a heads up, rather then posting long output (like dmesg) directly, post it as an attachment (.txt).

---

