---
title: "CPU Locks Up"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by fattymatty on 2008-11-29
My CPU Locks up constantly it could be after loging in or upto 15-30 minutes after but usaually within 5 minutes or less ive looked at log but cant see anything but maybe im missing something

here is the syslog
Nov 28 22:39:58 matt-desktop syslogd 1.5.0#1ubuntu1: restart.
Nov 28 22:39:58 matt-desktop kernel: Inspecting /boot/System.map-2.6.24-21-generic
Nov 28 22:39:58 matt-desktop kernel: Loaded 28513 symbols from /boot/System.map-2.6.24-21-generic.
Nov 28 22:39:58 matt-desktop kernel: Symbols match kernel version 2.6.24.
Nov 28 22:39:58 matt-desktop kernel: Loaded 23911 symbols from 94 modules.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:09:30 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Command line: root=UUID=efe6bafc-03e3-4240-95d9-f685c7752862 ro quiet splash
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] end_pfn_map = 1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] DMI 2.4 present.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F81B0 checksum 0
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: RSDP 000F81B0, 0024 (r2 ATI   )
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: XSDT CFEE3100, 004C (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: FACP CFEE8440, 00F4 (r3 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: DSDT CFEE3280, 5155 (r1 ATI    ASUSACPI     1000 MSFT  3000000)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: FACS CFEE0000, 0040
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: SSDT CFEE8680, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: HPET CFEE8900, 0038 (r1 ATI    ASUSACPI 42302E31 AWRD       98)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: MCFG CFEE8980, 003C (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: APIC CFEE8580, 0084 (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] CPU has 2 num_cores
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] No NUMA configuration found
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Zone PFN ranges:
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA             0 ->     4096
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA32        4096 ->  1048576
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Normal    1048576 ->  1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Movable zone start PFN for each node
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:        0 ->      159
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:      256 ->   851680
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:  1048576 ->  1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] On node 0 totalpages: 1048191
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA zone: 1222 pages reserved
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA zone: 2721 pages, LIFO batch:0
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Normal zone: 2688 pages used for memmap
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Normal zone: 193920 pages, LIFO batch:31
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Processor #1
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Setting APIC routing to flat
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: HPET id: 0x8200 base: 0xfed00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfee0000 - 00000000cfee3000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfee3000 - 00000000cfef0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfef0000 - 00000000cff00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cff00000 - 00000000e0000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029945
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Policy zone: Normal
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Kernel command line: root=UUID=efe6bafc-03e3-4240-95d9-f685c7752862 ro quiet splash
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing CPU#0
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] hpet clockevent registered
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] TSC calibrated against HPET
Nov 28 22:39:58 matt-desktop kernel: [   17.205040] Marking TSC unstable due to TSCs unsynchronized
Nov 28 22:39:58 matt-desktop kernel: [   17.205042] time.c: Detected 2099.924 MHz processor.
Nov 28 22:39:58 matt-desktop kernel: [   17.206136] Console: colour VGA+ 80x25
Nov 28 22:39:58 matt-desktop kernel: [   17.206139] console [tty0] enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.206157] Checking aperture...
Nov 28 22:39:58 matt-desktop kernel: [   17.206159] CPU 0: aperture @ 348000000 size 32 MB
Nov 28 22:39:58 matt-desktop kernel: [   17.206161] Aperture too small (32 MB)
Nov 28 22:39:58 matt-desktop kernel: [   17.215150] No AGP bridge found
Nov 28 22:39:58 matt-desktop kernel: [   17.215152] Your BIOS doesn't leave a aperture memory hole
Nov 28 22:39:58 matt-desktop kernel: [   17.215153] Please enable the IOMMU option in the BIOS setup
Nov 28 22:39:58 matt-desktop kernel: [   17.215155] This costs you 64 MB of RAM
Nov 28 22:39:58 matt-desktop kernel: [   17.240082] Mapping aperture over 65536 KB of RAM @ 4000000
Nov 28 22:39:58 matt-desktop kernel: [   17.240087] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000
Nov 28 22:39:58 matt-desktop kernel: [   17.271260] Memory: 4046344k/4980736k available (2490k kernel code, 146420k reserved, 1318k data, 320k init)
Nov 28 22:39:58 matt-desktop kernel: [   17.271291] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Nov 28 22:39:58 matt-desktop kernel: [   17.350831] Calibrating delay using timer specific routine.. 4202.95 BogoMIPS (lpj=8405905)
Nov 28 22:39:58 matt-desktop kernel: [   17.350859] Security Framework initialized
Nov 28 22:39:58 matt-desktop kernel: [   17.350864] SELinux:  Disabled at boot.
Nov 28 22:39:58 matt-desktop kernel: [   17.350876] AppArmor: AppArmor initialized
Nov 28 22:39:58 matt-desktop kernel: [   17.350879] Failure registering capabilities with primary security module.
Nov 28 22:39:58 matt-desktop kernel: [   17.351170] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.353105] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.354044] Mount-cache hash table entries: 256
Nov 28 22:39:58 matt-desktop kernel: [   17.354155] Initializing cgroup subsys ns
Nov 28 22:39:58 matt-desktop kernel: [   17.354158] Initializing cgroup subsys cpuacct
Nov 28 22:39:58 matt-desktop kernel: [   17.354170] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.354173] CPU: L2 Cache: 512K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.354175] CPU 0/0 -> Node 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354177] CPU: Physical Processor ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354179] CPU: Processor Core ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354198] SMP alternatives: switching to UP code
Nov 28 22:39:58 matt-desktop kernel: [   17.354709] Early unpacking initramfs... done
Nov 28 22:39:58 matt-desktop kernel: [   17.646497] ACPI: Core revision 20070126
Nov 28 22:39:58 matt-desktop kernel: [   17.646544] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 28 22:39:58 matt-desktop kernel: [   17.703526] Using local APIC timer interrupts.
Nov 28 22:39:58 matt-desktop kernel: [   17.751090] APIC timer calibration result 12499545
Nov 28 22:39:58 matt-desktop kernel: [   17.751092] Detected 12.499 MHz APIC timer.
Nov 28 22:39:58 matt-desktop kernel: [   17.751176] SMP alternatives: switching to SMP code
Nov 28 22:39:58 matt-desktop kernel: [   17.751575] Booting processor 1/2 APIC 0x1
Nov 28 22:39:58 matt-desktop kernel: [   17.761858] Initializing CPU#1
Nov 28 22:39:58 matt-desktop kernel: [   17.839195] Calibrating delay using timer specific routine.. 4199.90 BogoMIPS (lpj=8399803)
Nov 28 22:39:58 matt-desktop kernel: [   17.839201] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.839203] CPU: L2 Cache: 512K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.839205] CPU 1/1 -> Node 0
Nov 28 22:39:58 matt-desktop kernel: [   17.839207] CPU: Physical Processor ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.839208] CPU: Processor Core ID: 1
Nov 28 22:39:58 matt-desktop kernel: [   17.839302] AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
Nov 28 22:39:58 matt-desktop kernel: [   17.839159] Brought up 2 CPUs
Nov 28 22:39:58 matt-desktop kernel: [   17.839277] CPU0 attaching sched-domain:
Nov 28 22:39:58 matt-desktop kernel: [   17.839279]  domain 0: span 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839281]   groups: 01 02
Nov 28 22:39:58 matt-desktop kernel: [   17.839284]   domain 1: span 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839285]    groups: 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839287] CPU1 attaching sched-domain:
Nov 28 22:39:58 matt-desktop kernel: [   17.839288]  domain 0: span 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839289]   groups: 02 01
Nov 28 22:39:58 matt-desktop kernel: [   17.839292]   domain 1: span 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839293]    groups: 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839496] net_namespace: 120 bytes
Nov 28 22:39:58 matt-desktop kernel: [   17.839867] Time:  6:39:36  Date: 11/29/08
Nov 28 22:39:58 matt-desktop kernel: [   17.839896] NET: Registered protocol family 16
Nov 28 22:39:58 matt-desktop kernel: [   17.840071] ACPI: bus type pci registered
Nov 28 22:39:58 matt-desktop kernel: [   17.840137] PCI: Using configuration type 1
Nov 28 22:39:58 matt-desktop kernel: [   17.841303] ACPI: EC: Look up EC in DSDT
Nov 28 22:39:58 matt-desktop kernel: [   17.845663] ACPI: Interpreter enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.845666] ACPI: (supports S0 S1 S4 S5)
Nov 28 22:39:58 matt-desktop kernel: [   17.845679] ACPI: Using IOAPIC for interrupt routing
Nov 28 22:39:58 matt-desktop kernel: [   17.850054] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 28 22:39:58 matt-desktop kernel: [   17.850220] pci 0000:00:12.0: set SATA to AHCI mode
Nov 28 22:39:58 matt-desktop kernel: [   17.851435] PCI: Transparent bridge - 0000:00:14.4
Nov 28 22:39:58 matt-desktop kernel: [   17.851458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 28 22:39:58 matt-desktop kernel: [   17.851654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Nov 28 22:39:58 matt-desktop kernel: [   17.851750] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Nov 28 22:39:58 matt-desktop kernel: [   17.851824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Nov 28 22:39:58 matt-desktop kernel: [   17.870737] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.870832] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.870924] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871022] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871114] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871206] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11)
Nov 28 22:39:58 matt-desktop kernel: [   17.871298] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
Nov 28 22:39:58 matt-desktop kernel: [   17.871389] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871500] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 28 22:39:58 matt-desktop kernel: [   17.871528] pnp: PnP ACPI init
Nov 28 22:39:58 matt-desktop kernel: [   17.871535] ACPI: bus type pnp registered
Nov 28 22:39:58 matt-desktop kernel: [   17.874129] pnpacpi: exceeded the max number of mem resources: 12
Nov 28 22:39:58 matt-desktop kernel: [   17.874179] pnp: PnP ACPI: found 14 devices
Nov 28 22:39:58 matt-desktop kernel: [   17.874181] ACPI: ACPI bus type pnp unregistered
Nov 28 22:39:58 matt-desktop kernel: [   17.874393] PCI: Using ACPI for IRQ routing
Nov 28 22:39:58 matt-desktop kernel: [   17.874396] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 28 22:39:58 matt-desktop kernel: [   17.882977] NET: Registered protocol family 8
Nov 28 22:39:58 matt-desktop kernel: [   17.882979] NET: Registered protocol family 20
Nov 28 22:39:58 matt-desktop kernel: [   17.883052] PCI-DMA: Disabling AGP.
Nov 28 22:39:58 matt-desktop kernel: [   17.883416] PCI-DMA: aperture base @ 4000000 size 65536 KB
Nov 28 22:39:58 matt-desktop kernel: [   17.883420] PCI-DMA: using GART IOMMU.
Nov 28 22:39:58 matt-desktop kernel: [   17.883422] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Nov 28 22:39:58 matt-desktop kernel: [   17.883635] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov 28 22:39:58 matt-desktop kernel: [   17.883639] hpet0: 4 32-bit timers, 14318180 Hz
Nov 28 22:39:58 matt-desktop kernel: [   17.884688] AppArmor: AppArmor Filesystem Enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.886925] Time: hpet clocksource has been installed.
Nov 28 22:39:58 matt-desktop kernel: [   17.886939] Switched to high resolution mode on CPU 0
Nov 28 22:39:58 matt-desktop kernel: [   17.887271] Switched to high resolution mode on CPU 1
Nov 28 22:39:58 matt-desktop kernel: [   17.894924] system 00:01: ioport range 0x4100-0x411f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894927] system 00:01: ioport range 0x228-0x22f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894929] system 00:01: ioport range 0x40b-0x40b has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894931] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894934] system 00:01: ioport range 0xc00-0xc01 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894936] system 00:01: ioport range 0xc14-0xc14 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894938] system 00:01: ioport range 0xc50-0xc52 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894940] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894942] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894945] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894947] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894949] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894954] system 00:01: ioport range 0x4000-0x40fe has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894957] system 00:01: ioport range 0x4210-0x4217 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894959] system 00:01: ioport range 0xb10-0xb1f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894968] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894970] system 00:07: ioport range 0x220-0x225 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894980] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894986] system 00:0d: iomem range 0xcf600-0xcffff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894988] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894990] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894993] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894995] system 00:0d: iomem range 0xcfef0000-0xcffeffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894998] system 00:0d: iomem range 0xfed00000-0xfed000ff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895001] system 00:0d: iomem range 0xcfee0000-0xcfefffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895003] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895005] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895008] system 00:0d: iomem range 0x100000-0xcfedffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895010] system 00:0d: iomem range 0x0-0x0 could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895012] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895392] PCI: Bridge: 0000:00:02.0
Nov 28 22:39:58 matt-desktop kernel: [   17.895394]   IO window: d000-dfff
Nov 28 22:39:58 matt-desktop kernel: [   17.895397]   MEM window: fdb00000-fdbfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895399]   PREFETCH window: d0000000-dfffffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895403] PCI: Bridge: 0000:00:07.0
Nov 28 22:39:58 matt-desktop kernel: [   17.895405]   IO window: e000-efff
Nov 28 22:39:58 matt-desktop kernel: [   17.895407]   MEM window: fdf00000-fdffffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895409]   PREFETCH window: fdc00000-fdcfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895413] PCI: Bridge: 0000:00:14.4
Nov 28 22:39:58 matt-desktop kernel: [   17.895415]   IO window: c000-cfff
Nov 28 22:39:58 matt-desktop kernel: [   17.895420]   MEM window: fde00000-fdefffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895423]   PREFETCH window: fdd00000-fddfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895439] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   17.895446] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   17.895461] NET: Registered protocol family 2
Nov 28 22:39:58 matt-desktop kernel: [   17.930974] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.932183] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.935814] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.936297] TCP: Hash tables configured (established 524288 bind 65536)
Nov 28 22:39:58 matt-desktop kernel: [   17.936301] TCP reno registered
Nov 28 22:39:58 matt-desktop kernel: [   17.946962] checking if image is initramfs... it is
Nov 28 22:39:58 matt-desktop kernel: [   18.515725] Freeing initrd memory: 7549k freed
Nov 28 22:39:58 matt-desktop kernel: [   18.520419] audit: initializing netlink socket (disabled)
Nov 28 22:39:58 matt-desktop kernel: [   18.520429] audit(1227940776.264:1): initialized
Nov 28 22:39:58 matt-desktop kernel: [   18.522301] VFS: Disk quotas dquot_6.5.1
Nov 28 22:39:58 matt-desktop kernel: [   18.522370] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   18.522486] io scheduler noop registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522488] io scheduler anticipatory registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522489] io scheduler deadline registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522585] io scheduler cfq registered (default)
Nov 28 22:39:58 matt-desktop kernel: [   18.782182] Boot video device is 0000:01:00.0
Nov 28 22:39:58 matt-desktop kernel: [   18.782329] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   18.782345] assign_interrupt_mode Found MSI capability
Nov 28 22:39:58 matt-desktop kernel: [   18.782364] Allocate Port Service[0000:00:02.0:pcie00]
Nov 28 22:39:58 matt-desktop kernel: [   18.782421] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   18.782437] assign_interrupt_mode Found MSI capability
Nov 28 22:39:58 matt-desktop kernel: [   18.782452] Allocate Port Service[0000:00:07.0:pcie00]
Nov 28 22:39:58 matt-desktop kernel: [   18.808223] Real Time Clock Driver v1.12ac
Nov 28 22:39:58 matt-desktop kernel: [   18.808375] hpet_resources: 0xfed00000 is busy
Nov 28 22:39:58 matt-desktop kernel: [   18.808404] Linux agpgart interface v0.102
Nov 28 22:39:58 matt-desktop kernel: [   18.808406] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 28 22:39:58 matt-desktop kernel: [   18.808547] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 22:39:58 matt-desktop kernel: [   18.809095] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 22:39:58 matt-desktop kernel: [   18.810033] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 28 22:39:58 matt-desktop kernel: [   18.810096] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 28 22:39:58 matt-desktop kernel: [   18.810180] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Nov 28 22:39:58 matt-desktop kernel: [   18.810182] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Nov 28 22:39:58 matt-desktop kernel: [   18.810275] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 28 22:39:58 matt-desktop kernel: [   18.825716] mice: PS/2 mouse device common for all mice
Nov 28 22:39:58 matt-desktop kernel: [   18.825750] cpuidle: using governor ladder
Nov 28 22:39:58 matt-desktop kernel: [   18.825752] cpuidle: using governor menu
Nov 28 22:39:58 matt-desktop kernel: [   18.825887] NET: Registered protocol family 1
Nov 28 22:39:58 matt-desktop kernel: [   18.825974] registered taskstats version 1
Nov 28 22:39:58 matt-desktop kernel: [   18.826093]   Magic number: 0:976:671
Nov 28 22:39:58 matt-desktop kernel: [   18.826202] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Nov 28 22:39:58 matt-desktop kernel: [   18.826205] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 28 22:39:58 matt-desktop kernel: [   18.826207] EDD information not available.
Nov 28 22:39:58 matt-desktop kernel: [   18.826214] Freeing unused kernel memory: 320k freed
Nov 28 22:39:58 matt-desktop kernel: [   18.826595] Write protecting the kernel read-only data: 1036k
Nov 28 22:39:58 matt-desktop kernel: [   18.854326] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 28 22:39:58 matt-desktop kernel: [   20.012699] fuse init (API version 7.9)
Nov 28 22:39:58 matt-desktop kernel: [   20.025134] ACPI: Fan [FAN] (on)
Nov 28 22:39:58 matt-desktop kernel: [   20.029538] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 28 22:39:58 matt-desktop kernel: [   20.029550] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 28 22:39:58 matt-desktop kernel: [   20.030823] ACPI: Thermal Zone [THRM] (40 C)
Nov 28 22:39:58 matt-desktop kernel: [   20.384272] usbcore: registered new interface driver usbfs
Nov 28 22:39:58 matt-desktop kernel: [   20.384167] SCSI subsystem initialized
Nov 28 22:39:58 matt-desktop kernel: [   20.390145] usbcore: registered new interface driver hub
Nov 28 22:39:58 matt-desktop kernel: [   20.393883] usbcore: registered new device driver usb
Nov 28 22:39:58 matt-desktop kernel: [   20.396075] r8169 Gigabit Ethernet driver 2.2LK loaded
Nov 28 22:39:58 matt-desktop kernel: [   20.396105] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 19
Nov 28 22:39:58 matt-desktop kernel: [   20.396124] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   20.396367] eth0: RTL8168b/8111b at 0xffffc20001032000, 00:1f:c6:c4:a8:fa, XID 38000000 IRQ 509
Nov 28 22:39:58 matt-desktop kernel: [   20.397851] libata version 3.00 loaded.
Nov 28 22:39:58 matt-desktop kernel: [   20.399466] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 28 22:39:58 matt-desktop kernel: [   20.399509] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   20.399675] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.399939] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Nov 28 22:39:58 matt-desktop kernel: [   20.399967] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Nov 28 22:39:58 matt-desktop kernel: [   20.433381] Floppy drive(s): fd0 is 1.44M
Nov 28 22:39:58 matt-desktop kernel: [   20.451212] FDC 0 is a post-1991 82077
Nov 28 22:39:58 matt-desktop kernel: [   20.460283] usb usb1: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.460306] hub 1-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.460316] hub 1-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.564093] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Nov 28 22:39:58 matt-desktop kernel: [   20.564268] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.564327] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Nov 28 22:39:58 matt-desktop kernel: [   20.564349] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Nov 28 22:39:58 matt-desktop kernel: [   20.624020] usb usb2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.624040] hub 2-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.624050] hub 2-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.727851] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:39:58 matt-desktop kernel: [   20.728019] ohci_hcd 0000:00:13.2: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.728076] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Nov 28 22:39:58 matt-desktop kernel: [   20.728102] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Nov 28 22:39:58 matt-desktop kernel: [   20.787789] usb usb3: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.787809] hub 3-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.787818] hub 3-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.891629] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Nov 28 22:39:58 matt-desktop kernel: [   20.891799] ohci_hcd 0000:00:13.3: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.891857] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Nov 28 22:39:58 matt-desktop kernel: [   20.891874] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Nov 28 22:39:58 matt-desktop kernel: [   20.951592] usb usb4: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.951615] hub 4-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.951625] hub 4-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   21.054917] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:39:58 matt-desktop kernel: [   21.055087] ohci_hcd 0000:00:13.4: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   21.055147] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Nov 28 22:39:58 matt-desktop kernel: [   21.055166] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Nov 28 22:39:58 matt-desktop kernel: [   21.114853] usb usb5: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   21.114875] hub 5-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   21.114884] hub 5-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   21.214485] ahci 0000:00:12.0: version 3.0
Nov 28 22:39:58 matt-desktop kernel: [   21.214518] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
Nov 28 22:39:58 matt-desktop kernel: [   21.214697] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Nov 28 22:39:58 matt-desktop kernel: [   21.214703] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Nov 28 22:39:58 matt-desktop kernel: [   21.525963] usb 5-2: new low speed USB device using ohci_hcd and address 2
Nov 28 22:39:58 matt-desktop kernel: [   21.753023] usb 5-2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   21.766572] usbcore: registered new interface driver hiddev
Nov 28 22:39:58 matt-desktop kernel: [   21.773072] input: Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000 as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input2
Nov 28 22:39:58 matt-desktop kernel: [   21.802333] input,hidraw0: USB HID v1.11 Mouse [Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000] on usb-0000:00:13.4-2
Nov 28 22:39:58 matt-desktop kernel: [   21.802345] usbcore: registered new interface driver usbhid
Nov 28 22:39:58 matt-desktop kernel: [   21.802348] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Nov 28 22:39:58 matt-desktop kernel: [   22.217065] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov 28 22:39:58 matt-desktop kernel: [   22.217070] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Nov 28 22:39:58 matt-desktop kernel: [   22.218026] scsi0 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218313] scsi1 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218455] scsi2 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218594] scsi3 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218663] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218667] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218671] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218674] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.692386] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   22.861287] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L09, max UDMA/100, ATAPI AN
Nov 28 22:39:58 matt-desktop kernel: [   23.029131] ata1.00: configured for UDMA/100
Nov 28 22:39:58 matt-desktop kernel: [   23.339497] ata2: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.651069] ata3: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.962643] ata4: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.964011] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L09 PQ: 0 ANSI: 5
Nov 28 22:39:58 matt-desktop kernel: [   23.965004] ACPI: PCI Interrupt 0000:03:06.2[B] -> GSI 22 (level, low) -> IRQ 22
Nov 28 22:39:58 matt-desktop kernel: [   23.966241] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Nov 28 22:39:58 matt-desktop kernel: [   23.966405] ehci_hcd 0000:00:13.5: EHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   23.966461] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Nov 28 22:39:58 matt-desktop kernel: [   23.966503] ehci_hcd 0000:00:13.5: debug port 1
Nov 28 22:39:58 matt-desktop kernel: [   23.966520] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Nov 28 22:39:58 matt-desktop kernel: [   24.015082] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 28 22:39:58 matt-desktop kernel: [   24.014913] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 28 22:39:58 matt-desktop kernel: [   24.015022] usb usb6: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   24.015044] hub 6-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   24.015052] hub 6-0:1.0: 10 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   24.015405] usb 5-2: USB disconnect, address 2
Nov 28 22:39:58 matt-desktop kernel: [   24.022517] Driver 'sr' needs updating - please use bus_type methods
Nov 28 22:39:58 matt-desktop kernel: [   24.031125] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 28 22:39:58 matt-desktop kernel: [   24.031130] Uniform CD-ROM driver Revision: 3.20
Nov 28 22:39:58 matt-desktop kernel: [   24.031177] sr 0:0:0:0: Attached scsi CD-ROM sr0
Nov 28 22:39:58 matt-desktop kernel: [   24.035040] sr 0:0:0:0: Attached scsi generic sg0 type 5
Nov 28 22:39:58 matt-desktop kernel: [   24.118621] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   24.119495] scsi4 : pata_atiixp
Nov 28 22:39:58 matt-desktop kernel: [   24.120061] scsi5 : pata_atiixp
Nov 28 22:39:58 matt-desktop kernel: [   24.120491] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
Nov 28 22:39:58 matt-desktop kernel: [   24.120494] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
Nov 28 22:39:58 matt-desktop kernel: [   24.338563] ata5.00: ATA-6: ST3160021A, 8.11, max UDMA/100
Nov 28 22:39:58 matt-desktop kernel: [   24.338566] ata5.00: 312581808 sectors, multi 1: LBA48 
Nov 28 22:39:58 matt-desktop kernel: [   24.338576] ata5.00: limited to UDMA/33 due to 40-wire cable
Nov 28 22:39:58 matt-desktop kernel: [   24.354510] ata5.00: configured for UDMA/33
Nov 28 22:39:58 matt-desktop kernel: [   24.510985] scsi 4:0:0:0: Direct-Access     ATA      ST3160021A       8.11 PQ: 0 ANSI: 5
Nov 28 22:39:58 matt-desktop kernel: [   24.511053] scsi 4:0:0:0: Attached scsi generic sg1 type 0
Nov 28 22:39:58 matt-desktop kernel: [   24.519622] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 28 22:39:58 matt-desktop kernel: [   24.519628] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 28 22:39:58 matt-desktop kernel: [   24.541416] Driver 'sd' needs updating - please use bus_type methods
Nov 28 22:39:58 matt-desktop kernel: [   24.541500] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov 28 22:39:58 matt-desktop kernel: [   24.541509] sd 4:0:0:0: [sda] Write Protect is off
Nov 28 22:39:58 matt-desktop kernel: [   24.541512] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 28 22:39:58 matt-desktop kernel: [   24.541525] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 28 22:39:58 matt-desktop kernel: [   24.541563] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov 28 22:39:58 matt-desktop kernel: [   24.541571] sd 4:0:0:0: [sda] Write Protect is off
Nov 28 22:39:58 matt-desktop kernel: [   24.541572] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 28 22:39:58 matt-desktop kernel: [   24.541584] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 28 22:39:58 matt-desktop kernel: [   24.541587]  sda: sda1 sda2 < sda5 >
Nov 28 22:39:58 matt-desktop kernel: [   24.573016] sd 4:0:0:0: [sda] Attached SCSI disk
Nov 28 22:39:58 matt-desktop kernel: [   24.665904] usb 5-2: new low speed USB device using ohci_hcd and address 3
Nov 28 22:39:58 matt-desktop kernel: [   24.848219] Attempting manual resume
Nov 28 22:39:58 matt-desktop kernel: [   24.848223] swsusp: Resume From Partition 8:5
Nov 28 22:39:58 matt-desktop kernel: [   24.848224] PM: Checking swsusp image.
Nov 28 22:39:58 matt-desktop kernel: [   24.848527] PM: Resume from disk failed.
Nov 28 22:39:58 matt-desktop kernel: [   24.880556] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 28 22:39:58 matt-desktop kernel: [   24.880560] EXT3-fs: write access will be enabled during recovery.
Nov 28 22:39:58 matt-desktop kernel: [   24.892914] usb 5-2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   24.902011] input: Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000 as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input3
Nov 28 22:39:58 matt-desktop kernel: [   24.926095] input,hidraw0: USB HID v1.11 Mouse [Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000] on usb-0000:00:13.4-2
Nov 28 22:39:58 matt-desktop kernel: [   25.285674] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c015103eaa7]
Nov 28 22:39:58 matt-desktop kernel: [   25.428215] kjournald starting.  Commit interval 5 seconds
Nov 28 22:39:58 matt-desktop kernel: [   25.428230] EXT3-fs: sda1: orphan cleanup on readonly fs
Nov 28 22:39:58 matt-desktop kernel: [   25.428236] ext3_orphan_cleanup: deleting unreferenced inode 606297
Nov 28 22:39:58 matt-desktop kernel: [   25.428260] EXT3-fs: sda1: 1 orphan inode deleted
Nov 28 22:39:58 matt-desktop kernel: [   25.428262] EXT3-fs: recovery complete.
Nov 28 22:39:58 matt-desktop kernel: [   25.442180] EXT3-fs: mounted filesystem with ordered data mode.
Nov 28 22:39:58 matt-desktop kernel: [   35.029771] input: PC Speaker as /devices/platform/pcspkr/input/input4
Nov 28 22:39:58 matt-desktop kernel: [   35.585166] parport_pc 00:0a: reported by Plug and Play ACPI
Nov 28 22:39:58 matt-desktop kernel: [   35.585199] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Nov 28 22:39:58 matt-desktop kernel: [   35.674740] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 28 22:39:58 matt-desktop kernel: [   35.711237] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 28 22:39:58 matt-desktop kernel: [   35.795452] input: Power Button (FF) as /devices/virtual/input/input5
Nov 28 22:39:58 matt-desktop kernel: [   35.838585] gameport: EMU10K1 is pci0000:03:06.1/gameport0, io 0xce00, speed 607kHz
Nov 28 22:39:58 matt-desktop kernel: [   35.855225] ACPI: Power Button (FF) [PWRF]
Nov 28 22:39:58 matt-desktop kernel: [   35.855284] input: Power Button (CM) as /devices/virtual/input/input6
Nov 28 22:39:58 matt-desktop kernel: [   35.919133] ACPI: Power Button (CM) [PWRB]
Nov 28 22:39:58 matt-desktop kernel: [   35.945160] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Nov 28 22:39:58 matt-desktop kernel: [   36.231814] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 28 22:39:58 matt-desktop kernel: [   36.250659] [fglrx] Maximum main memory to use for locked dma buffers: 3797 MBytes.
Nov 28 22:39:58 matt-desktop kernel: [   36.250689] [fglrx] ASYNCIO init succeed!
Nov 28 22:39:58 matt-desktop kernel: [   36.250972] [fglrx] PAT is enabled successfully!
Nov 28 22:39:58 matt-desktop kernel: [   36.250998] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Nov 28 22:39:58 matt-desktop kernel: [   36.490050] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   36.556714] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov 28 22:39:58 matt-desktop kernel: [   36.563192] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 ZS [SB0350]
Nov 28 22:39:58 matt-desktop kernel: [   37.602403] lp0: using parport0 (interrupt-driven).
Nov 28 22:39:58 matt-desktop kernel: [   37.716151] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k
Nov 28 22:39:58 matt-desktop kernel: [   38.271599] EXT3 FS on sda1, internal journal
Nov 28 22:39:58 matt-desktop kernel: [   39.308038] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 28 22:39:58 matt-desktop kernel: [   39.602862] No dock devices found.
Nov 28 22:39:58 matt-desktop kernel: [   39.937700] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (2 cpu cores) (version 2.20.00)
Nov 28 22:39:58 matt-desktop kernel: [   39.937503] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xa
Nov 28 22:39:58 matt-desktop kernel: [   39.937507] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xb
Nov 28 22:39:58 matt-desktop kernel: [   39.937509] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xd
Nov 28 22:39:58 matt-desktop kernel: [   39.937511] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Nov 28 22:39:59 matt-desktop NetworkManager: <info>  starting... 
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Successfully dropped root privileges.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: avahi-daemon 0.6.22 starting up.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Successfully called chroot().
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Successfully dropped remaining capabilities.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: No service file found in /etc/avahi/services.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Network interface enumeration completed.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Registering HINFO record with values 'X86_64'/'LINUX'.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Server startup complete. Host name is matt-desktop.local. Local service cookie is 3091598547.
Nov 28 22:39:59 matt-desktop atieventsd[5129]: ATI External Events Daemon started... 
Nov 28 22:39:59 matt-desktop atieventsd[5129]: Event daemon control socket created 
Nov 28 22:39:59 matt-desktop atieventsd[5129]: acpid connection established 
Nov 28 22:39:59 matt-desktop kernel: [   41.066516] ppdev: user-space parallel port driver
Nov 28 22:39:59 matt-desktop kernel: [   41.247176] audit(1227940799.749:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5155 profile="/usr/sbin/cupsd" namespace="default"
Nov 28 22:39:59 matt-desktop dhcdbd: Started up.
Nov 28 22:40:00 matt-desktop kernel: [   41.941185] Clocksource tsc unstable (delta = -261917412 ns)
Nov 28 22:40:01 matt-desktop kernel: [   42.384723] r8169: eth0: link up
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  Deactivating device eth0. 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Nov 28 22:40:01 matt-desktop NetworkManager: <debug> [1227940801.692607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_20A1S'). 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Nov 28 22:40:02 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) started... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 28 22:40:03 matt-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Nov 28 22:40:03 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 28 22:40:03 matt-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 28 22:40:04 matt-desktop hcid[5489]: Bluetooth HCI daemon
Nov 28 22:40:04 matt-desktop kernel: [   43.612850] Bluetooth: Core ver 2.11
Nov 28 22:40:04 matt-desktop kernel: [   43.613341] NET: Registered protocol family 31
Nov 28 22:40:04 matt-desktop kernel: [   43.613346] Bluetooth: HCI device and connection manager initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.613350] Bluetooth: HCI socket layer initialized
Nov 28 22:40:04 matt-desktop hcid[5489]: Starting SDP server
Nov 28 22:40:04 matt-desktop kernel: [   43.625083] Bluetooth: L2CAP ver 2.9
Nov 28 22:40:04 matt-desktop kernel: [   43.625088] Bluetooth: L2CAP socket layer initialized
Nov 28 22:40:04 matt-desktop hcid[5489]: Created local server at unix:abstract=/var/run/dbus-EDn0fNI9HF,guid=ccf73519aa8f01c387fa58624930e3c4
Nov 28 22:40:04 matt-desktop NetworkManager: <debug> [1227940804.310109] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 28 22:40:04 matt-desktop input[5508]: Bluetooth Input daemon
Nov 28 22:40:04 matt-desktop input[5508]: Registered input manager path:/org/bluez/input
Nov 28 22:40:04 matt-desktop audio[5505]: Bluetooth Audio daemon
Nov 28 22:40:04 matt-desktop audio[5505]: Unix socket created: 5
Nov 28 22:40:04 matt-desktop audio[5505]: audio.conf: Key file does not have key 'Enable'
Nov 28 22:40:04 matt-desktop audio[5505]: audio.conf: Key file does not have key 'Disable'
Nov 28 22:40:04 matt-desktop kernel: [   43.664575] Bluetooth: RFCOMM socket layer initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.664591] Bluetooth: RFCOMM TTY layer initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.664593] Bluetooth: RFCOMM ver 1.8
Nov 28 22:40:04 matt-desktop audio[5505]: add_service_record: got record id 0x10000
Nov 28 22:40:04 matt-desktop audio[5505]: audio.conf: Key file does not have key 'Disable'
Nov 28 22:40:04 matt-desktop audio[5505]: audio.conf: Key file does not have group 'A2DP'
Nov 28 22:40:04 matt-desktop last message repeated 3 times
Nov 28 22:40:04 matt-desktop audio[5505]: SEP 0x62d1f0 registered: type:0 codec:0 seid:1
Nov 28 22:40:04 matt-desktop audio[5505]: add_service_record: got record id 0x10001
Nov 28 22:40:04 matt-desktop audio[5505]: add_service_record: got record id 0x10002
Nov 28 22:40:04 matt-desktop audio[5505]: add_service_record: got record id 0x10003
Nov 28 22:40:04 matt-desktop audio[5505]: Registered manager path:/org/bluez/audio
Nov 28 22:40:04 matt-desktop kernel: [   43.679466] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:40:04 matt-desktop anacron[5534]: Anacron 2.3 started on 2008-11-28
Nov 28 22:40:04 matt-desktop anacron[5534]: Will run job `cron.daily' in 5 min.
Nov 28 22:40:04 matt-desktop anacron[5534]: Jobs will be executed sequentially
Nov 28 22:40:04 matt-desktop /usr/sbin/cron[5561]: (CRON) INFO (pidfile fd = 3)
Nov 28 22:40:04 matt-desktop /usr/sbin/cron[5562]: (CRON) STARTUP (fork ok)
Nov 28 22:40:04 matt-desktop /usr/sbin/cron[5562]: (CRON) INFO (Running @reboot jobs)
Nov 28 22:40:04 matt-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Nov 28 22:40:05 matt-desktop kernel: [   43.980825] NET: Registered protocol family 17
Nov 28 22:40:05 matt-desktop dhclient: DHCPREQUEST of 192.168.0.197 on eth0 to 255.255.255.255 port 67
Nov 28 22:40:05 matt-desktop dhclient: DHCPACK of 192.168.0.197 from 192.168.0.1
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.197.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: New relevant interface eth0.IPv4 for mDNS.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Registering new address record for 192.168.0.197 on eth0.IPv4.
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov 28 22:40:05 matt-desktop dhclient: bound to 192.168.0.197 -- renewal in 3273749 seconds.
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    address 192.168.0.197 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    netmask 255.255.255.0 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    broadcast 192.168.0.255 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    gateway 192.168.0.1 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    nameserver 64.59.144.16 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    nameserver 64.59.144.17 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    domain name 'vs.shawcable.net' 
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Withdrawing address record for 192.168.0.197 on eth0.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.197.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.197.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: New relevant interface eth0.IPv4 for mDNS.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Registering new address record for 192.168.0.197 on eth0.IPv4.
Nov 28 22:40:05 matt-desktop kernel: [   44.396785] [fglrx] Reserve Block - 0 offset =  0X1fffb000 length = 0X5000
Nov 28 22:40:05 matt-desktop kernel: [   44.396790] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Nov 28 22:40:05 matt-desktop kernel: [   44.396792] [fglrx] Reserve Block - 2 offset =  0Xffc0000 length = 0X40000
Nov 28 22:40:05 matt-desktop kernel: [   44.426803] [fglrx] interrupt source 20008000 successfully enabled
Nov 28 22:40:05 matt-desktop kernel: [   44.426808] [fglrx] enable ID = 0x00000008
Nov 28 22:40:05 matt-desktop kernel: [   44.426815] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Nov 28 22:40:06 matt-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Nov 28 22:40:06 matt-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 28 22:40:06 matt-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Nov 28 22:40:06 matt-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Nov 28 22:40:06 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 28 22:40:06 matt-desktop kernel: [   44.910680] NET: Registered protocol family 10
Nov 28 22:40:06 matt-desktop kernel: [   44.910915] lo: Disabled Privacy Extensions
Nov 28 22:40:10 matt-desktop ntpdate[5732]: step time server 91.189.94.4 offset 2.331724 sec
Nov 28 22:40:10 matt-desktop avahi-daemon[5109]: Registering new address record for fe80::21f:c6ff:fec4:a8fa on eth0.*.
Nov 28 22:40:15 matt-desktop kernel: [   48.567982] hda-intel: Invalid position buffer, using LPIB read method instead.
Nov 28 22:40:19 matt-desktop kernel: [   50.353795] eth0: no IPv6 routers present
Nov 28 22:40:58 matt-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Nov 28 22:40:58 matt-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

and messages log

Nov 28 22:39:58 matt-desktop syslogd 1.5.0#1ubuntu1: restart.
Nov 28 22:39:58 matt-desktop kernel: Inspecting /boot/System.map-2.6.24-21-generic
Nov 28 22:39:58 matt-desktop kernel: Loaded 28513 symbols from /boot/System.map-2.6.24-21-generic.
Nov 28 22:39:58 matt-desktop kernel: Symbols match kernel version 2.6.24.
Nov 28 22:39:58 matt-desktop kernel: Loaded 23911 symbols from 94 modules.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Tue Oct 21 23:09:30 UTC 2008 (Ubuntu 2.6.24-21.43-generic)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Command line: root=UUID=efe6bafc-03e3-4240-95d9-f685c7752862 ro quiet splash
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] end_pfn_map = 1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] DMI 2.4 present.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F81B0 checksum 0
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: RSDP 000F81B0, 0024 (r2 ATI   )
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: XSDT CFEE3100, 004C (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: FACP CFEE8440, 00F4 (r3 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: DSDT CFEE3280, 5155 (r1 ATI    ASUSACPI     1000 MSFT  3000000)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: FACS CFEE0000, 0040
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: SSDT CFEE8680, 0206 (r1 PTLTD  POWERNOW        1  LTP        1)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: HPET CFEE8900, 0038 (r1 ATI    ASUSACPI 42302E31 AWRD       98)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: MCFG CFEE8980, 003C (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: APIC CFEE8580, 0084 (r1 ATI    ASUSACPI 42302E31 AWRD        0)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] CPU has 2 num_cores
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] No NUMA configuration found
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Faking a node at 0000000000000000-0000000130000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 256, 851680) 1 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 1048576, 1245184) 2 entries of 3200 used
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Zone PFN ranges:
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA             0 ->     4096
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA32        4096 ->  1048576
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Normal    1048576 ->  1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Movable zone start PFN for each node
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] early_node_map[3] active PFN ranges
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:        0 ->      159
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:      256 ->   851680
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]     0:  1048576 ->  1245184
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] On node 0 totalpages: 1048191
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA zone: 1222 pages reserved
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA zone: 2721 pages, LIFO batch:0
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   DMA32 zone: 833304 pages, LIFO batch:31
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Normal zone: 2688 pages used for memmap
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Normal zone: 193920 pages, LIFO batch:31
Nov 28 22:39:58 matt-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ATI board detected. Disabling timer routing over 8254.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x4008
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Processor #0 (Bootup-CPU)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Processor #1
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Setting APIC routing to flat
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] ACPI: HPET id: 0x8200 base: 0xfed00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfee0000 - 00000000cfee3000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfee3000 - 00000000cfef0000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cfef0000 - 00000000cff00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000cff00000 - 00000000e0000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 0000000100000000
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029945
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Policy zone: Normal
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Kernel command line: root=UUID=efe6bafc-03e3-4240-95d9-f685c7752862 ro quiet splash
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] Initializing CPU#0
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] hpet clockevent registered
Nov 28 22:39:58 matt-desktop kernel: [    0.000000] TSC calibrated against HPET
Nov 28 22:39:58 matt-desktop kernel: [   17.205040] Marking TSC unstable due to TSCs unsynchronized
Nov 28 22:39:58 matt-desktop kernel: [   17.205042] time.c: Detected 2099.924 MHz processor.
Nov 28 22:39:58 matt-desktop kernel: [   17.206136] Console: colour VGA+ 80x25
Nov 28 22:39:58 matt-desktop kernel: [   17.206139] console [tty0] enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.206157] Checking aperture...
Nov 28 22:39:58 matt-desktop kernel: [   17.206159] CPU 0: aperture @ 348000000 size 32 MB
Nov 28 22:39:58 matt-desktop kernel: [   17.206161] Aperture too small (32 MB)
Nov 28 22:39:58 matt-desktop kernel: [   17.215150] No AGP bridge found
Nov 28 22:39:58 matt-desktop kernel: [   17.215152] Your BIOS doesn't leave a aperture memory hole
Nov 28 22:39:58 matt-desktop kernel: [   17.215153] Please enable the IOMMU option in the BIOS setup
Nov 28 22:39:58 matt-desktop kernel: [   17.215155] This costs you 64 MB of RAM
Nov 28 22:39:58 matt-desktop kernel: [   17.240082] Mapping aperture over 65536 KB of RAM @ 4000000
Nov 28 22:39:58 matt-desktop kernel: [   17.240087] swsusp: Registered nosave memory region: 0000000004000000 - 0000000008000000
Nov 28 22:39:58 matt-desktop kernel: [   17.271260] Memory: 4046344k/4980736k available (2490k kernel code, 146420k reserved, 1318k data, 320k init)
Nov 28 22:39:58 matt-desktop kernel: [   17.271291] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Nov 28 22:39:58 matt-desktop kernel: [   17.350831] Calibrating delay using timer specific routine.. 4202.95 BogoMIPS (lpj=8405905)
Nov 28 22:39:58 matt-desktop kernel: [   17.350859] Security Framework initialized
Nov 28 22:39:58 matt-desktop kernel: [   17.350864] SELinux:  Disabled at boot.
Nov 28 22:39:58 matt-desktop kernel: [   17.350876] AppArmor: AppArmor initialized
Nov 28 22:39:58 matt-desktop kernel: [   17.350879] Failure registering capabilities with primary security module.
Nov 28 22:39:58 matt-desktop kernel: [   17.351170] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.353105] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.354044] Mount-cache hash table entries: 256
Nov 28 22:39:58 matt-desktop kernel: [   17.354155] Initializing cgroup subsys ns
Nov 28 22:39:58 matt-desktop kernel: [   17.354158] Initializing cgroup subsys cpuacct
Nov 28 22:39:58 matt-desktop kernel: [   17.354170] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.354173] CPU: L2 Cache: 512K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.354175] CPU 0/0 -> Node 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354177] CPU: Physical Processor ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354179] CPU: Processor Core ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.354198] SMP alternatives: switching to UP code
Nov 28 22:39:58 matt-desktop kernel: [   17.354709] Early unpacking initramfs... done
Nov 28 22:39:58 matt-desktop kernel: [   17.646497] ACPI: Core revision 20070126
Nov 28 22:39:58 matt-desktop kernel: [   17.646544] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 28 22:39:58 matt-desktop kernel: [   17.703526] Using local APIC timer interrupts.
Nov 28 22:39:58 matt-desktop kernel: [   17.751090] APIC timer calibration result 12499545
Nov 28 22:39:58 matt-desktop kernel: [   17.751092] Detected 12.499 MHz APIC timer.
Nov 28 22:39:58 matt-desktop kernel: [   17.751176] SMP alternatives: switching to SMP code
Nov 28 22:39:58 matt-desktop kernel: [   17.751575] Booting processor 1/2 APIC 0x1
Nov 28 22:39:58 matt-desktop kernel: [   17.761858] Initializing CPU#1
Nov 28 22:39:58 matt-desktop kernel: [   17.839195] Calibrating delay using timer specific routine.. 4199.90 BogoMIPS (lpj=8399803)
Nov 28 22:39:58 matt-desktop kernel: [   17.839201] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.839203] CPU: L2 Cache: 512K (64 bytes/line)
Nov 28 22:39:58 matt-desktop kernel: [   17.839205] CPU 1/1 -> Node 0
Nov 28 22:39:58 matt-desktop kernel: [   17.839207] CPU: Physical Processor ID: 0
Nov 28 22:39:58 matt-desktop kernel: [   17.839208] CPU: Processor Core ID: 1
Nov 28 22:39:58 matt-desktop kernel: [   17.839302] AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ stepping 01
Nov 28 22:39:58 matt-desktop kernel: [   17.839159] Brought up 2 CPUs
Nov 28 22:39:58 matt-desktop kernel: [   17.839277] CPU0 attaching sched-domain:
Nov 28 22:39:58 matt-desktop kernel: [   17.839279]  domain 0: span 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839281]   groups: 01 02
Nov 28 22:39:58 matt-desktop kernel: [   17.839284]   domain 1: span 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839285]    groups: 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839287] CPU1 attaching sched-domain:
Nov 28 22:39:58 matt-desktop kernel: [   17.839288]  domain 0: span 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839289]   groups: 02 01
Nov 28 22:39:58 matt-desktop kernel: [   17.839292]   domain 1: span 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839293]    groups: 03
Nov 28 22:39:58 matt-desktop kernel: [   17.839496] net_namespace: 120 bytes
Nov 28 22:39:58 matt-desktop kernel: [   17.839867] Time:  6:39:36  Date: 11/29/08
Nov 28 22:39:58 matt-desktop kernel: [   17.839896] NET: Registered protocol family 16
Nov 28 22:39:58 matt-desktop kernel: [   17.840071] ACPI: bus type pci registered
Nov 28 22:39:58 matt-desktop kernel: [   17.840137] PCI: Using configuration type 1
Nov 28 22:39:58 matt-desktop kernel: [   17.841303] ACPI: EC: Look up EC in DSDT
Nov 28 22:39:58 matt-desktop kernel: [   17.845663] ACPI: Interpreter enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.845666] ACPI: (supports S0 S1 S4 S5)
Nov 28 22:39:58 matt-desktop kernel: [   17.845679] ACPI: Using IOAPIC for interrupt routing
Nov 28 22:39:58 matt-desktop kernel: [   17.850054] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 28 22:39:58 matt-desktop kernel: [   17.850220] pci 0000:00:12.0: set SATA to AHCI mode
Nov 28 22:39:58 matt-desktop kernel: [   17.851435] PCI: Transparent bridge - 0000:00:14.4
Nov 28 22:39:58 matt-desktop kernel: [   17.851458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 28 22:39:58 matt-desktop kernel: [   17.851654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
Nov 28 22:39:58 matt-desktop kernel: [   17.851750] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Nov 28 22:39:58 matt-desktop kernel: [   17.851824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
Nov 28 22:39:58 matt-desktop kernel: [   17.870737] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.870832] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.870924] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871022] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871114] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871206] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11)
Nov 28 22:39:58 matt-desktop kernel: [   17.871298] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
Nov 28 22:39:58 matt-desktop kernel: [   17.871389] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
Nov 28 22:39:58 matt-desktop kernel: [   17.871500] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 28 22:39:58 matt-desktop kernel: [   17.871528] pnp: PnP ACPI init
Nov 28 22:39:58 matt-desktop kernel: [   17.871535] ACPI: bus type pnp registered
Nov 28 22:39:58 matt-desktop kernel: [   17.874129] pnpacpi: exceeded the max number of mem resources: 12
Nov 28 22:39:58 matt-desktop kernel: [   17.874179] pnp: PnP ACPI: found 14 devices
Nov 28 22:39:58 matt-desktop kernel: [   17.874181] ACPI: ACPI bus type pnp unregistered
Nov 28 22:39:58 matt-desktop kernel: [   17.874393] PCI: Using ACPI for IRQ routing
Nov 28 22:39:58 matt-desktop kernel: [   17.874396] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 28 22:39:58 matt-desktop kernel: [   17.882977] NET: Registered protocol family 8
Nov 28 22:39:58 matt-desktop kernel: [   17.882979] NET: Registered protocol family 20
Nov 28 22:39:58 matt-desktop kernel: [   17.883052] PCI-DMA: Disabling AGP.
Nov 28 22:39:58 matt-desktop kernel: [   17.883416] PCI-DMA: aperture base @ 4000000 size 65536 KB
Nov 28 22:39:58 matt-desktop kernel: [   17.883420] PCI-DMA: using GART IOMMU.
Nov 28 22:39:58 matt-desktop kernel: [   17.883422] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Nov 28 22:39:58 matt-desktop kernel: [   17.883635] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Nov 28 22:39:58 matt-desktop kernel: [   17.883639] hpet0: 4 32-bit timers, 14318180 Hz
Nov 28 22:39:58 matt-desktop kernel: [   17.884688] AppArmor: AppArmor Filesystem Enabled
Nov 28 22:39:58 matt-desktop kernel: [   17.886925] Time: hpet clocksource has been installed.
Nov 28 22:39:58 matt-desktop kernel: [   17.886939] Switched to high resolution mode on CPU 0
Nov 28 22:39:58 matt-desktop kernel: [   17.887271] Switched to high resolution mode on CPU 1
Nov 28 22:39:58 matt-desktop kernel: [   17.894924] system 00:01: ioport range 0x4100-0x411f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894927] system 00:01: ioport range 0x228-0x22f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894929] system 00:01: ioport range 0x40b-0x40b has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894931] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894934] system 00:01: ioport range 0xc00-0xc01 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894936] system 00:01: ioport range 0xc14-0xc14 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894938] system 00:01: ioport range 0xc50-0xc52 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894940] system 00:01: ioport range 0xc6c-0xc6d has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894942] system 00:01: ioport range 0xc6f-0xc6f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894945] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894947] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894949] system 00:01: ioport range 0xcd4-0xcdf has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894954] system 00:01: ioport range 0x4000-0x40fe has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894957] system 00:01: ioport range 0x4210-0x4217 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894959] system 00:01: ioport range 0xb10-0xb1f has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894968] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894970] system 00:07: ioport range 0x220-0x225 has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894980] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894986] system 00:0d: iomem range 0xcf600-0xcffff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894988] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894990] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894993] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894995] system 00:0d: iomem range 0xcfef0000-0xcffeffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.894998] system 00:0d: iomem range 0xfed00000-0xfed000ff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895001] system 00:0d: iomem range 0xcfee0000-0xcfefffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895003] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895005] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895008] system 00:0d: iomem range 0x100000-0xcfedffff could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895010] system 00:0d: iomem range 0x0-0x0 could not be reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895012] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
Nov 28 22:39:58 matt-desktop kernel: [   17.895392] PCI: Bridge: 0000:00:02.0
Nov 28 22:39:58 matt-desktop kernel: [   17.895394]   IO window: d000-dfff
Nov 28 22:39:58 matt-desktop kernel: [   17.895397]   MEM window: fdb00000-fdbfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895399]   PREFETCH window: d0000000-dfffffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895403] PCI: Bridge: 0000:00:07.0
Nov 28 22:39:58 matt-desktop kernel: [   17.895405]   IO window: e000-efff
Nov 28 22:39:58 matt-desktop kernel: [   17.895407]   MEM window: fdf00000-fdffffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895409]   PREFETCH window: fdc00000-fdcfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895413] PCI: Bridge: 0000:00:14.4
Nov 28 22:39:58 matt-desktop kernel: [   17.895415]   IO window: c000-cfff
Nov 28 22:39:58 matt-desktop kernel: [   17.895420]   MEM window: fde00000-fdefffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895423]   PREFETCH window: fdd00000-fddfffff
Nov 28 22:39:58 matt-desktop kernel: [   17.895439] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   17.895446] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   17.895461] NET: Registered protocol family 2
Nov 28 22:39:58 matt-desktop kernel: [   17.930974] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.932183] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.935814] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   17.936297] TCP: Hash tables configured (established 524288 bind 65536)
Nov 28 22:39:58 matt-desktop kernel: [   17.936301] TCP reno registered
Nov 28 22:39:58 matt-desktop kernel: [   17.946962] checking if image is initramfs... it is
Nov 28 22:39:58 matt-desktop kernel: [   18.515725] Freeing initrd memory: 7549k freed
Nov 28 22:39:58 matt-desktop kernel: [   18.520419] audit: initializing netlink socket (disabled)
Nov 28 22:39:58 matt-desktop kernel: [   18.520429] audit(1227940776.264:1): initialized
Nov 28 22:39:58 matt-desktop kernel: [   18.522301] VFS: Disk quotas dquot_6.5.1
Nov 28 22:39:58 matt-desktop kernel: [   18.522370] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Nov 28 22:39:58 matt-desktop kernel: [   18.522486] io scheduler noop registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522488] io scheduler anticipatory registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522489] io scheduler deadline registered
Nov 28 22:39:58 matt-desktop kernel: [   18.522585] io scheduler cfq registered (default)
Nov 28 22:39:58 matt-desktop kernel: [   18.782182] Boot video device is 0000:01:00.0
Nov 28 22:39:58 matt-desktop kernel: [   18.782329] PCI: Setting latency timer of device 0000:00:02.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   18.782345] assign_interrupt_mode Found MSI capability
Nov 28 22:39:58 matt-desktop kernel: [   18.782364] Allocate Port Service[0000:00:02.0:pcie00]
Nov 28 22:39:58 matt-desktop kernel: [   18.782421] PCI: Setting latency timer of device 0000:00:07.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   18.782437] assign_interrupt_mode Found MSI capability
Nov 28 22:39:58 matt-desktop kernel: [   18.782452] Allocate Port Service[0000:00:07.0:pcie00]
Nov 28 22:39:58 matt-desktop kernel: [   18.808223] Real Time Clock Driver v1.12ac
Nov 28 22:39:58 matt-desktop kernel: [   18.808375] hpet_resources: 0xfed00000 is busy
Nov 28 22:39:58 matt-desktop kernel: [   18.808404] Linux agpgart interface v0.102
Nov 28 22:39:58 matt-desktop kernel: [   18.808406] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 28 22:39:58 matt-desktop kernel: [   18.808547] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 22:39:58 matt-desktop kernel: [   18.809095] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Nov 28 22:39:58 matt-desktop kernel: [   18.810033] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 28 22:39:58 matt-desktop kernel: [   18.810096] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 28 22:39:58 matt-desktop kernel: [   18.810180] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Nov 28 22:39:58 matt-desktop kernel: [   18.810182] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Nov 28 22:39:58 matt-desktop kernel: [   18.810275] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 28 22:39:58 matt-desktop kernel: [   18.825716] mice: PS/2 mouse device common for all mice
Nov 28 22:39:58 matt-desktop kernel: [   18.825750] cpuidle: using governor ladder
Nov 28 22:39:58 matt-desktop kernel: [   18.825752] cpuidle: using governor menu
Nov 28 22:39:58 matt-desktop kernel: [   18.825887] NET: Registered protocol family 1
Nov 28 22:39:58 matt-desktop kernel: [   18.825974] registered taskstats version 1
Nov 28 22:39:58 matt-desktop kernel: [   18.826093]   Magic number: 0:976:671
Nov 28 22:39:58 matt-desktop kernel: [   18.826202] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Nov 28 22:39:58 matt-desktop kernel: [   18.826205] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 28 22:39:58 matt-desktop kernel: [   18.826207] EDD information not available.
Nov 28 22:39:58 matt-desktop kernel: [   18.826214] Freeing unused kernel memory: 320k freed
Nov 28 22:39:58 matt-desktop kernel: [   18.826595] Write protecting the kernel read-only data: 1036k
Nov 28 22:39:58 matt-desktop kernel: [   18.854326] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 28 22:39:58 matt-desktop kernel: [   20.012699] fuse init (API version 7.9)
Nov 28 22:39:58 matt-desktop kernel: [   20.025134] ACPI: Fan [FAN] (on)
Nov 28 22:39:58 matt-desktop kernel: [   20.029538] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 28 22:39:58 matt-desktop kernel: [   20.029550] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 28 22:39:58 matt-desktop kernel: [   20.030823] ACPI: Thermal Zone [THRM] (40 C)
Nov 28 22:39:58 matt-desktop kernel: [   20.384272] usbcore: registered new interface driver usbfs
Nov 28 22:39:58 matt-desktop kernel: [   20.384167] SCSI subsystem initialized
Nov 28 22:39:58 matt-desktop kernel: [   20.390145] usbcore: registered new interface driver hub
Nov 28 22:39:58 matt-desktop kernel: [   20.393883] usbcore: registered new device driver usb
Nov 28 22:39:58 matt-desktop kernel: [   20.396075] r8169 Gigabit Ethernet driver 2.2LK loaded
Nov 28 22:39:58 matt-desktop kernel: [   20.396105] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 19
Nov 28 22:39:58 matt-desktop kernel: [   20.396124] PCI: Setting latency timer of device 0000:02:00.0 to 64
Nov 28 22:39:58 matt-desktop kernel: [   20.396367] eth0: RTL8168b/8111b at 0xffffc20001032000, 00:1f:c6:c4:a8:fa, XID 38000000 IRQ 509
Nov 28 22:39:58 matt-desktop kernel: [   20.397851] libata version 3.00 loaded.
Nov 28 22:39:58 matt-desktop kernel: [   20.399466] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 28 22:39:58 matt-desktop kernel: [   20.399509] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   20.399675] ohci_hcd 0000:00:13.0: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.399939] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
Nov 28 22:39:58 matt-desktop kernel: [   20.399967] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
Nov 28 22:39:58 matt-desktop kernel: [   20.433381] Floppy drive(s): fd0 is 1.44M
Nov 28 22:39:58 matt-desktop kernel: [   20.451212] FDC 0 is a post-1991 82077
Nov 28 22:39:58 matt-desktop kernel: [   20.460283] usb usb1: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.460306] hub 1-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.460316] hub 1-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.564093] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 17
Nov 28 22:39:58 matt-desktop kernel: [   20.564268] ohci_hcd 0000:00:13.1: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.564327] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
Nov 28 22:39:58 matt-desktop kernel: [   20.564349] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
Nov 28 22:39:58 matt-desktop kernel: [   20.624020] usb usb2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.624040] hub 2-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.624050] hub 2-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.727851] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:39:58 matt-desktop kernel: [   20.728019] ohci_hcd 0000:00:13.2: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.728076] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
Nov 28 22:39:58 matt-desktop kernel: [   20.728102] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
Nov 28 22:39:58 matt-desktop kernel: [   20.787789] usb usb3: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.787809] hub 3-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.787818] hub 3-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   20.891629] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
Nov 28 22:39:58 matt-desktop kernel: [   20.891799] ohci_hcd 0000:00:13.3: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   20.891857] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
Nov 28 22:39:58 matt-desktop kernel: [   20.891874] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
Nov 28 22:39:58 matt-desktop kernel: [   20.951592] usb usb4: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   20.951615] hub 4-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   20.951625] hub 4-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   21.054917] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:39:58 matt-desktop kernel: [   21.055087] ohci_hcd 0000:00:13.4: OHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   21.055147] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
Nov 28 22:39:58 matt-desktop kernel: [   21.055166] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
Nov 28 22:39:58 matt-desktop kernel: [   21.114853] usb usb5: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   21.114875] hub 5-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   21.114884] hub 5-0:1.0: 2 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   21.214485] ahci 0000:00:12.0: version 3.0
Nov 28 22:39:58 matt-desktop kernel: [   21.214518] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 22
Nov 28 22:39:58 matt-desktop kernel: [   21.214697] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
Nov 28 22:39:58 matt-desktop kernel: [   21.214703] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
Nov 28 22:39:58 matt-desktop kernel: [   21.525963] usb 5-2: new low speed USB device using ohci_hcd and address 2
Nov 28 22:39:58 matt-desktop kernel: [   21.753023] usb 5-2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   21.766572] usbcore: registered new interface driver hiddev
Nov 28 22:39:58 matt-desktop kernel: [   21.773072] input: Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000 as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input2
Nov 28 22:39:58 matt-desktop kernel: [   21.802333] input,hidraw0: USB HID v1.11 Mouse [Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000] on usb-0000:00:13.4-2
Nov 28 22:39:58 matt-desktop kernel: [   21.802345] usbcore: registered new interface driver usbhid
Nov 28 22:39:58 matt-desktop kernel: [   21.802348] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Nov 28 22:39:58 matt-desktop kernel: [   22.217065] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Nov 28 22:39:58 matt-desktop kernel: [   22.217070] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
Nov 28 22:39:58 matt-desktop kernel: [   22.218026] scsi0 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218313] scsi1 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218455] scsi2 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218594] scsi3 : ahci
Nov 28 22:39:58 matt-desktop kernel: [   22.218663] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218667] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218671] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.218674] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
Nov 28 22:39:58 matt-desktop kernel: [   22.692386] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   22.861287] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L09, max UDMA/100, ATAPI AN
Nov 28 22:39:58 matt-desktop kernel: [   23.029131] ata1.00: configured for UDMA/100
Nov 28 22:39:58 matt-desktop kernel: [   23.339497] ata2: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.651069] ata3: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.962643] ata4: SATA link down (SStatus 0 SControl 300)
Nov 28 22:39:58 matt-desktop kernel: [   23.964011] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L09 PQ: 0 ANSI: 5
Nov 28 22:39:58 matt-desktop kernel: [   23.965004] ACPI: PCI Interrupt 0000:03:06.2[B] -> GSI 22 (level, low) -> IRQ 22
Nov 28 22:39:58 matt-desktop kernel: [   23.966241] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 19
Nov 28 22:39:58 matt-desktop kernel: [   23.966405] ehci_hcd 0000:00:13.5: EHCI Host Controller
Nov 28 22:39:58 matt-desktop kernel: [   23.966461] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
Nov 28 22:39:58 matt-desktop kernel: [   23.966503] ehci_hcd 0000:00:13.5: debug port 1
Nov 28 22:39:58 matt-desktop kernel: [   23.966520] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
Nov 28 22:39:58 matt-desktop kernel: [   24.015082] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Nov 28 22:39:58 matt-desktop kernel: [   24.014913] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 28 22:39:58 matt-desktop kernel: [   24.015022] usb usb6: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   24.015044] hub 6-0:1.0: USB hub found
Nov 28 22:39:58 matt-desktop kernel: [   24.015052] hub 6-0:1.0: 10 ports detected
Nov 28 22:39:58 matt-desktop kernel: [   24.015405] usb 5-2: USB disconnect, address 2
Nov 28 22:39:58 matt-desktop kernel: [   24.022517] Driver 'sr' needs updating - please use bus_type methods
Nov 28 22:39:58 matt-desktop kernel: [   24.031125] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 28 22:39:58 matt-desktop kernel: [   24.031130] Uniform CD-ROM driver Revision: 3.20
Nov 28 22:39:58 matt-desktop kernel: [   24.031177] sr 0:0:0:0: Attached scsi CD-ROM sr0
Nov 28 22:39:58 matt-desktop kernel: [   24.035040] sr 0:0:0:0: Attached scsi generic sg0 type 5
Nov 28 22:39:58 matt-desktop kernel: [   24.118621] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   24.119495] scsi4 : pata_atiixp
Nov 28 22:39:58 matt-desktop kernel: [   24.120061] scsi5 : pata_atiixp
Nov 28 22:39:58 matt-desktop kernel: [   24.120491] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf900 irq 14
Nov 28 22:39:58 matt-desktop kernel: [   24.120494] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf908 irq 15
Nov 28 22:39:58 matt-desktop kernel: [   24.338563] ata5.00: ATA-6: ST3160021A, 8.11, max UDMA/100
Nov 28 22:39:58 matt-desktop kernel: [   24.338566] ata5.00: 312581808 sectors, multi 1: LBA48 
Nov 28 22:39:58 matt-desktop kernel: [   24.338576] ata5.00: limited to UDMA/33 due to 40-wire cable
Nov 28 22:39:58 matt-desktop kernel: [   24.354510] ata5.00: configured for UDMA/33
Nov 28 22:39:58 matt-desktop kernel: [   24.510985] scsi 4:0:0:0: Direct-Access     ATA      ST3160021A       8.11 PQ: 0 ANSI: 5
Nov 28 22:39:58 matt-desktop kernel: [   24.511053] scsi 4:0:0:0: Attached scsi generic sg1 type 0
Nov 28 22:39:58 matt-desktop kernel: [   24.519622] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Nov 28 22:39:58 matt-desktop kernel: [   24.519628] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Nov 28 22:39:58 matt-desktop kernel: [   24.541416] Driver 'sd' needs updating - please use bus_type methods
Nov 28 22:39:58 matt-desktop kernel: [   24.541500] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov 28 22:39:58 matt-desktop kernel: [   24.541509] sd 4:0:0:0: [sda] Write Protect is off
Nov 28 22:39:58 matt-desktop kernel: [   24.541512] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 28 22:39:58 matt-desktop kernel: [   24.541525] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 28 22:39:58 matt-desktop kernel: [   24.541563] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Nov 28 22:39:58 matt-desktop kernel: [   24.541571] sd 4:0:0:0: [sda] Write Protect is off
Nov 28 22:39:58 matt-desktop kernel: [   24.541572] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 28 22:39:58 matt-desktop kernel: [   24.541584] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 28 22:39:58 matt-desktop kernel: [   24.541587]  sda: sda1 sda2 < sda5 >
Nov 28 22:39:58 matt-desktop kernel: [   24.573016] sd 4:0:0:0: [sda] Attached SCSI disk
Nov 28 22:39:58 matt-desktop kernel: [   24.665904] usb 5-2: new low speed USB device using ohci_hcd and address 3
Nov 28 22:39:58 matt-desktop kernel: [   24.848219] Attempting manual resume
Nov 28 22:39:58 matt-desktop kernel: [   24.848223] swsusp: Resume From Partition 8:5
Nov 28 22:39:58 matt-desktop kernel: [   24.848224] PM: Checking swsusp image.
Nov 28 22:39:58 matt-desktop kernel: [   24.848527] PM: Resume from disk failed.
Nov 28 22:39:58 matt-desktop kernel: [   24.880556] EXT3-fs: INFO: recovery required on readonly filesystem.
Nov 28 22:39:58 matt-desktop kernel: [   24.880560] EXT3-fs: write access will be enabled during recovery.
Nov 28 22:39:58 matt-desktop kernel: [   24.892914] usb 5-2: configuration #1 chosen from 1 choice
Nov 28 22:39:58 matt-desktop kernel: [   24.902011] input: Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000 as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input3
Nov 28 22:39:58 matt-desktop kernel: [   24.926095] input,hidraw0: USB HID v1.11 Mouse [Microsoft Corporation Microsoft \Uffffffff Laser Mouse 6000] on usb-0000:00:13.4-2
Nov 28 22:39:58 matt-desktop kernel: [   25.285674] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c015103eaa7]
Nov 28 22:39:58 matt-desktop kernel: [   25.428215] kjournald starting.  Commit interval 5 seconds
Nov 28 22:39:58 matt-desktop kernel: [   25.428230] EXT3-fs: sda1: orphan cleanup on readonly fs
Nov 28 22:39:58 matt-desktop kernel: [   25.428236] ext3_orphan_cleanup: deleting unreferenced inode 606297
Nov 28 22:39:58 matt-desktop kernel: [   25.428260] EXT3-fs: sda1: 1 orphan inode deleted
Nov 28 22:39:58 matt-desktop kernel: [   25.428262] EXT3-fs: recovery complete.
Nov 28 22:39:58 matt-desktop kernel: [   25.442180] EXT3-fs: mounted filesystem with ordered data mode.
Nov 28 22:39:58 matt-desktop kernel: [   35.029771] input: PC Speaker as /devices/platform/pcspkr/input/input4
Nov 28 22:39:58 matt-desktop kernel: [   35.585166] parport_pc 00:0a: reported by Plug and Play ACPI
Nov 28 22:39:58 matt-desktop kernel: [   35.585199] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Nov 28 22:39:58 matt-desktop kernel: [   35.674740] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 28 22:39:58 matt-desktop kernel: [   35.711237] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 28 22:39:58 matt-desktop kernel: [   35.795452] input: Power Button (FF) as /devices/virtual/input/input5
Nov 28 22:39:58 matt-desktop kernel: [   35.838585] gameport: EMU10K1 is pci0000:03:06.1/gameport0, io 0xce00, speed 607kHz
Nov 28 22:39:58 matt-desktop kernel: [   35.855225] ACPI: Power Button (FF) [PWRF]
Nov 28 22:39:58 matt-desktop kernel: [   35.855284] input: Power Button (CM) as /devices/virtual/input/input6
Nov 28 22:39:58 matt-desktop kernel: [   35.919133] ACPI: Power Button (CM) [PWRB]
Nov 28 22:39:58 matt-desktop kernel: [   35.945160] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Nov 28 22:39:58 matt-desktop kernel: [   36.231814] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Nov 28 22:39:58 matt-desktop kernel: [   36.250659] [fglrx] Maximum main memory to use for locked dma buffers: 3797 MBytes.
Nov 28 22:39:58 matt-desktop kernel: [   36.250689] [fglrx] ASYNCIO init succeed!
Nov 28 22:39:58 matt-desktop kernel: [   36.250972] [fglrx] PAT is enabled successfully!
Nov 28 22:39:58 matt-desktop kernel: [   36.250998] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Nov 28 22:39:58 matt-desktop kernel: [   36.490050] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
Nov 28 22:39:58 matt-desktop kernel: [   36.556714] ACPI: PCI Interrupt 0000:03:06.0[A] -> GSI 21 (level, low) -> IRQ 21
Nov 28 22:39:58 matt-desktop kernel: [   36.563192] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 2 ZS [SB0350]
Nov 28 22:39:58 matt-desktop kernel: [   37.602403] lp0: using parport0 (interrupt-driven).
Nov 28 22:39:58 matt-desktop kernel: [   37.716151] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k
Nov 28 22:39:58 matt-desktop kernel: [   38.271599] EXT3 FS on sda1, internal journal
Nov 28 22:39:58 matt-desktop kernel: [   39.308038] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 28 22:39:58 matt-desktop kernel: [   39.602862] No dock devices found.
Nov 28 22:39:58 matt-desktop kernel: [   39.937700] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ processors (2 cpu cores) (version 2.20.00)
Nov 28 22:39:58 matt-desktop kernel: [   39.937503] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xa
Nov 28 22:39:58 matt-desktop kernel: [   39.937507] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xb
Nov 28 22:39:58 matt-desktop kernel: [   39.937509] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xd
Nov 28 22:39:58 matt-desktop kernel: [   39.937511] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Nov 28 22:39:59 matt-desktop NetworkManager: <info>  starting... 
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Successfully dropped root privileges.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: avahi-daemon 0.6.22 starting up.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Successfully called chroot().
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Successfully dropped remaining capabilities.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: No service file found in /etc/avahi/services.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Network interface enumeration completed.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Registering HINFO record with values 'X86_64'/'LINUX'.
Nov 28 22:39:59 matt-desktop avahi-daemon[5109]: Server startup complete. Host name is matt-desktop.local. Local service cookie is 3091598547.
Nov 28 22:39:59 matt-desktop atieventsd[5129]: ATI External Events Daemon started... 
Nov 28 22:39:59 matt-desktop atieventsd[5129]: Event daemon control socket created 
Nov 28 22:39:59 matt-desktop atieventsd[5129]: acpid connection established 
Nov 28 22:39:59 matt-desktop kernel: [   41.066516] ppdev: user-space parallel port driver
Nov 28 22:39:59 matt-desktop kernel: [   41.247176] audit(1227940799.749:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5155 profile="/usr/sbin/cupsd" namespace="default"
Nov 28 22:39:59 matt-desktop dhcdbd: Started up.
Nov 28 22:40:00 matt-desktop kernel: [   41.941185] Clocksource tsc unstable (delta = -261917412 ns)
Nov 28 22:40:01 matt-desktop kernel: [   42.384723] r8169: eth0: link up
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  Deactivating device eth0. 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Nov 28 22:40:01 matt-desktop NetworkManager: <debug> [1227940801.692607] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_20A1S'). 
Nov 28 22:40:01 matt-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Nov 28 22:40:02 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) started... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Nov 28 22:40:02 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Nov 28 22:40:03 matt-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Nov 28 22:40:03 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Nov 28 22:40:03 matt-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Nov 28 22:40:04 matt-desktop hcid[5489]: Bluetooth HCI daemon
Nov 28 22:40:04 matt-desktop kernel: [   43.612850] Bluetooth: Core ver 2.11
Nov 28 22:40:04 matt-desktop kernel: [   43.613341] NET: Registered protocol family 31
Nov 28 22:40:04 matt-desktop kernel: [   43.613346] Bluetooth: HCI device and connection manager initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.613350] Bluetooth: HCI socket layer initialized
Nov 28 22:40:04 matt-desktop hcid[5489]: Starting SDP server
Nov 28 22:40:04 matt-desktop kernel: [   43.625083] Bluetooth: L2CAP ver 2.9
Nov 28 22:40:04 matt-desktop kernel: [   43.625088] Bluetooth: L2CAP socket layer initialized
Nov 28 22:40:04 matt-desktop hcid[5489]: Created local server at unix:abstract=/var/run/dbus-EDn0fNI9HF,guid=ccf73519aa8f01c387fa58624930e3c4
Nov 28 22:40:04 matt-desktop NetworkManager: <debug> [1227940804.310109] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Nov 28 22:40:04 matt-desktop input[5508]: Bluetooth Input daemon
Nov 28 22:40:04 matt-desktop input[5508]: Registered input manager path:/org/bluez/input
Nov 28 22:40:04 matt-desktop audio[5505]: Bluetooth Audio daemon
Nov 28 22:40:04 matt-desktop audio[5505]: Unix socket created: 5
Nov 28 22:40:04 matt-desktop audio[5505]: audio.conf: Key file does not have key 'Enable'
Nov 28 22:40:04 matt-desktop audio[5505]: audio.conf: Key file does not have key 'Disable'
Nov 28 22:40:04 matt-desktop kernel: [   43.664575] Bluetooth: RFCOMM socket layer initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.664591] Bluetooth: RFCOMM TTY layer initialized
Nov 28 22:40:04 matt-desktop kernel: [   43.664593] Bluetooth: RFCOMM ver 1.8
Nov 28 22:40:04 matt-desktop audio[5505]: add_service_record: got record id 0x10000
Nov 28 22:40:04 matt-desktop audio[5505]: audio.conf: Key file does not have key 'Disable'
Nov 28 22:40:04 matt-desktop audio[5505]: audio.conf: Key file does not have group 'A2DP'
Nov 28 22:40:04 matt-desktop last message repeated 3 times
Nov 28 22:40:04 matt-desktop audio[5505]: SEP 0x62d1f0 registered: type:0 codec:0 seid:1
Nov 28 22:40:04 matt-desktop audio[5505]: add_service_record: got record id 0x10001
Nov 28 22:40:04 matt-desktop audio[5505]: add_service_record: got record id 0x10002
Nov 28 22:40:04 matt-desktop audio[5505]: add_service_record: got record id 0x10003
Nov 28 22:40:04 matt-desktop audio[5505]: Registered manager path:/org/bluez/audio
Nov 28 22:40:04 matt-desktop kernel: [   43.679466] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Nov 28 22:40:04 matt-desktop anacron[5534]: Anacron 2.3 started on 2008-11-28
Nov 28 22:40:04 matt-desktop anacron[5534]: Will run job `cron.daily' in 5 min.
Nov 28 22:40:04 matt-desktop anacron[5534]: Jobs will be executed sequentially
Nov 28 22:40:04 matt-desktop /usr/sbin/cron[5561]: (CRON) INFO (pidfile fd = 3)
Nov 28 22:40:04 matt-desktop /usr/sbin/cron[5562]: (CRON) STARTUP (fork ok)
Nov 28 22:40:04 matt-desktop /usr/sbin/cron[5562]: (CRON) INFO (Running @reboot jobs)
Nov 28 22:40:04 matt-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Nov 28 22:40:05 matt-desktop kernel: [   43.980825] NET: Registered protocol family 17
Nov 28 22:40:05 matt-desktop dhclient: DHCPREQUEST of 192.168.0.197 on eth0 to 255.255.255.255 port 67
Nov 28 22:40:05 matt-desktop dhclient: DHCPACK of 192.168.0.197 from 192.168.0.1
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.197.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: New relevant interface eth0.IPv4 for mDNS.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Registering new address record for 192.168.0.197 on eth0.IPv4.
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov 28 22:40:05 matt-desktop dhclient: bound to 192.168.0.197 -- renewal in 3273749 seconds.
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    address 192.168.0.197 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    netmask 255.255.255.0 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    broadcast 192.168.0.255 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    gateway 192.168.0.1 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    nameserver 64.59.144.16 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    nameserver 64.59.144.17 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>    domain name 'vs.shawcable.net' 
Nov 28 22:40:05 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Nov 28 22:40:05 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Withdrawing address record for 192.168.0.197 on eth0.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.197.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Interface eth0.IPv4 no longer relevant for mDNS.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.197.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: New relevant interface eth0.IPv4 for mDNS.
Nov 28 22:40:05 matt-desktop avahi-daemon[5109]: Registering new address record for 192.168.0.197 on eth0.IPv4.
Nov 28 22:40:05 matt-desktop kernel: [   44.396785] [fglrx] Reserve Block - 0 offset =  0X1fffb000 length = 0X5000
Nov 28 22:40:05 matt-desktop kernel: [   44.396790] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
Nov 28 22:40:05 matt-desktop kernel: [   44.396792] [fglrx] Reserve Block - 2 offset =  0Xffc0000 length = 0X40000
Nov 28 22:40:05 matt-desktop kernel: [   44.426803] [fglrx] interrupt source 20008000 successfully enabled
Nov 28 22:40:05 matt-desktop kernel: [   44.426808] [fglrx] enable ID = 0x00000008
Nov 28 22:40:05 matt-desktop kernel: [   44.426815] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Nov 28 22:40:06 matt-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Nov 28 22:40:06 matt-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Nov 28 22:40:06 matt-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Nov 28 22:40:06 matt-desktop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Nov 28 22:40:06 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Nov 28 22:40:06 matt-desktop kernel: [   44.910680] NET: Registered protocol family 10
Nov 28 22:40:06 matt-desktop kernel: [   44.910915] lo: Disabled Privacy Extensions
Nov 28 22:40:10 matt-desktop ntpdate[5732]: step time server 91.189.94.4 offset 2.331724 sec
Nov 28 22:40:10 matt-desktop avahi-daemon[5109]: Registering new address record for fe80::21f:c6ff:fec4:a8fa on eth0.*.
Nov 28 22:40:15 matt-desktop kernel: [   48.567982] hda-intel: Invalid position buffer, using LPIB read method instead.
Nov 28 22:40:19 matt-desktop kernel: [   50.353795] eth0: no IPv6 routers present
Nov 28 22:40:58 matt-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Nov 28 22:40:58 matt-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by ragingpenguin on 2008-11-29
try using top or gnome-system-monitor to see what process is pegging your cpu and post the results

---

