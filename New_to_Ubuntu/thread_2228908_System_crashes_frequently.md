---
title: "System crashes frequently"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by mauro6 on 2014-06-10
Hi! My name is Mauro. I'm a new user of Ubuntu. First of all, english is not my mother tongue so excuse me for my bad grammar.
I was using Ubuntu 10.04 lts version several days ago and I've had the same problem twice. When I install this S.O, it works perfectly for a few days but since I actualice it S.O. crash. The issue happends when I run actualizations from ubuntu's gestor or terminal.  I was googling trying to find a solution but I can't find it. I add my computer logs since I actulice.
Plz help me.
My regards.
```

Jun 10 07:42:24 mauro rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="851" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun 10 07:42:32 mauro anacron[6897]: Job `cron.daily' terminated
Jun 10 07:42:32 mauro anacron[6897]: Normal exit (1 job run)
Jun 10 08:17:01 mauro CRON[7617]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 10 08:27:57 mauro kernel: Kernel logging (proc) stopped.
Jun 10 08:28:31 mauro kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jun 10 08:28:31 mauro rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="702" x-info="http://www.rsyslog.com"] (re)start
Jun 10 08:28:31 mauro rsyslogd: rsyslogd's groupid changed to 103
Jun 10 08:28:32 mauro rsyslogd: rsyslogd's userid changed to 101
Jun 10 08:28:31 mauro rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Jun 10 08:28:32 mauro kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 08:28:32 mauro kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 08:28:32 mauro kernel: [    0.000000] Linux version 2.6.32-61-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #124-Ubuntu SMP Wed Jun 4 23:03:14 UTC 2014 (Ubuntu 2.6.32-61.124-generic 2.6.32.62+drm33.26)
Jun 10 08:28:32 mauro kernel: [    0.000000] KERNEL supported cpus:
Jun 10 08:28:32 mauro kernel: [    0.000000]   Intel GenuineIntel
Jun 10 08:28:32 mauro kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 08:28:32 mauro kernel: [    0.000000]   NSC Geode by NSC
Jun 10 08:28:32 mauro kernel: [    0.000000]   Cyrix CyrixInstead
Jun 10 08:28:32 mauro kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 08:28:32 mauro kernel: [    0.000000]   Transmeta GenuineTMx86
Jun 10 08:28:32 mauro kernel: [    0.000000]   Transmeta TransmetaCPU
Jun 10 08:28:32 mauro kernel: [    0.000000]   UMC UMC UMC UMC
Jun 10 08:28:32 mauro kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 0000000020200000 - 0000000040004000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 0000000040004000 - 0000000040005000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 0000000040005000 - 00000000ccc0e000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000ccc0e000 - 00000000cd1ae000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cd1ae000 - 00000000cd1be000 (ACPI data)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cd1be000 - 00000000cd2e0000 (ACPI NVS)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cd2e0000 - 00000000cd85d000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cd85d000 - 00000000cd85e000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cd85e000 - 00000000cd8a1000 (ACPI NVS)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cd8a1000 - 00000000cdcc1000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cdcc1000 - 00000000cdff4000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cdff4000 - 00000000ce000000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000cf000000 - 00000000df200000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000011fe00000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000] DMI 2.7 present.
Jun 10 08:28:32 mauro kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Jun 10 08:28:32 mauro kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000] last_pfn = 0xce000 max_arch_pfn = 0x100000
Jun 10 08:28:32 mauro kernel: [    0.000000] MTRR default type: uncachable
Jun 10 08:28:32 mauro kernel: [    0.000000] MTRR fixed ranges enabled:
Jun 10 08:28:32 mauro kernel: [    0.000000]   00000-9FFFF write-back
Jun 10 08:28:32 mauro kernel: [    0.000000]   A0000-BFFFF uncachable
Jun 10 08:28:32 mauro kernel: [    0.000000]   C0000-CFFFF write-protect
Jun 10 08:28:32 mauro kernel: [    0.000000]   D0000-E7FFF uncachable
Jun 10 08:28:32 mauro kernel: [    0.000000]   E8000-FFFFF write-protect
Jun 10 08:28:32 mauro kernel: [    0.000000] MTRR variable ranges enabled:
Jun 10 08:28:32 mauro kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Jun 10 08:28:32 mauro kernel: [    0.000000]   1 base 100000000 mask FE0000000 write-back
Jun 10 08:28:32 mauro kernel: [    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
Jun 10 08:28:32 mauro kernel: [    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
Jun 10 08:28:32 mauro kernel: [    0.000000]   4 base 0CF000000 mask FFF000000 uncachable
Jun 10 08:28:32 mauro kernel: [    0.000000]   5 base 11FE00000 mask FFFE00000 uncachable
Jun 10 08:28:32 mauro kernel: [    0.000000]   6 disabled
Jun 10 08:28:32 mauro kernel: [    0.000000]   7 disabled
Jun 10 08:28:32 mauro kernel: [    0.000000]   8 disabled
Jun 10 08:28:32 mauro kernel: [    0.000000]   9 disabled
Jun 10 08:28:32 mauro kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jun 10 08:28:32 mauro kernel: [    0.000000] e820 update range: 00000000cf000000 - 0000000100000000 (usable) ==> (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jun 10 08:28:32 mauro kernel: [    0.000000] modified physical RAM map:
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 0000000000010000 - 000000000009d800 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 0000000000100000 - 0000000020000000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 0000000020000000 - 0000000020200000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 0000000020200000 - 0000000040004000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 0000000040004000 - 0000000040005000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 0000000040005000 - 00000000ccc0e000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000ccc0e000 - 00000000cd1ae000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cd1ae000 - 00000000cd1be000 (ACPI data)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cd1be000 - 00000000cd2e0000 (ACPI NVS)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cd2e0000 - 00000000cd85d000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cd85d000 - 00000000cd85e000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cd85e000 - 00000000cd8a1000 (ACPI NVS)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cd8a1000 - 00000000cdcc1000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cdcc1000 - 00000000cdff4000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cdff4000 - 00000000ce000000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000cf000000 - 00000000df200000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed04000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
Jun 10 08:28:32 mauro kernel: [    0.000000]  modified: 0000000100000000 - 000000011fe00000 (usable)
Jun 10 08:28:32 mauro kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Jun 10 08:28:32 mauro kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Jun 10 08:28:32 mauro kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Jun 10 08:28:32 mauro kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Jun 10 08:28:32 mauro kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Jun 10 08:28:32 mauro kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Jun 10 08:28:32 mauro kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
Jun 10 08:28:32 mauro kernel: [    0.000000] RAMDISK: 1789d000 - 1803fa22
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: RSDP 000f0490 00024 (v02 ALASKA)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: XSDT cd1b2078 00064 (v01 ALASKA    A M I 01072009 AMI  00010013)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: FACP cd1bbe20 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 0x10C to 0xF4 (20090903/tbfadt-288)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: DSDT cd1b2170 09CAA (v02 ALASKA    A M I 00000021 INTL 20051117)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: FACS cd2de080 00040
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: APIC cd1bbf30 00062 (v03 ALASKA    A M I 01072009 AMI  00010013)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: FPDT cd1bbf98 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: MCFG cd1bbfe0 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: HPET cd1bc020 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: SSDT cd1bc058 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: SSDT cd1bc3c8 00926 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: SSDT cd1bccf0 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 08:28:32 mauro kernel: [    0.000000] 2408MB HIGHMEM available.
Jun 10 08:28:32 mauro kernel: [    0.000000] 887MB LOWMEM available.
Jun 10 08:28:32 mauro kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Jun 10 08:28:32 mauro kernel: [    0.000000]   low ram: 0 - 377fe000
Jun 10 08:28:32 mauro kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Jun 10 08:28:32 mauro kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Jun 10 08:28:32 mauro kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #3 [0000100000 - 00008e7ef8]    TEXT DATA BSS ==> [0000100000 - 00008e7ef8]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #4 [001789d000 - 001803fa22]          RAMDISK ==> [001789d000 - 001803fa22]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #5 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #6 [00008e8000 - 00008eb296]              BRK ==> [00008e8000 - 00008eb296]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Jun 10 08:28:32 mauro kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Jun 10 08:28:32 mauro kernel: [    0.000000] found SMP MP-table at [c00fd720] fd720
Jun 10 08:28:32 mauro kernel: [    0.000000] Zone PFN ranges:
Jun 10 08:28:32 mauro kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jun 10 08:28:32 mauro kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Jun 10 08:28:32 mauro kernel: [    0.000000]   HighMem  0x000377fe -> 0x000ce000
Jun 10 08:28:32 mauro kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 08:28:32 mauro kernel: [    0.000000] early_node_map[7] active PFN ranges
Jun 10 08:28:32 mauro kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Jun 10 08:28:32 mauro kernel: [    0.000000]     0: 0x00000100 -> 0x00020000
Jun 10 08:28:32 mauro kernel: [    0.000000]     0: 0x00020200 -> 0x00040004
Jun 10 08:28:32 mauro kernel: [    0.000000]     0: 0x00040005 -> 0x000ccc0e
Jun 10 08:28:32 mauro kernel: [    0.000000]     0: 0x000cd85d -> 0x000cd85e
Jun 10 08:28:32 mauro kernel: [    0.000000]     0: 0x000cd8a1 -> 0x000cdcc1
Jun 10 08:28:32 mauro kernel: [    0.000000]     0: 0x000cdff4 -> 0x000ce000
Jun 10 08:28:32 mauro kernel: [    0.000000] On node 0 totalpages: 839111
Jun 10 08:28:32 mauro kernel: [    0.000000] free_area_init_node: node 0, pgdat c07a2800, node_mem_map c1001200
Jun 10 08:28:32 mauro kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jun 10 08:28:32 mauro kernel: [    0.000000]   DMA zone: 0 pages reserved
Jun 10 08:28:32 mauro kernel: [    0.000000]   DMA zone: 3949 pages, LIFO batch:0
Jun 10 08:28:32 mauro kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Jun 10 08:28:32 mauro kernel: [    0.000000]   Normal zone: 220974 pages, LIFO batch:31
Jun 10 08:28:32 mauro kernel: [    0.000000]   HighMem zone: 4817 pages used for memmap
Jun 10 08:28:32 mauro kernel: [    0.000000]   HighMem zone: 607595 pages, LIFO batch:31
Jun 10 08:28:32 mauro kernel: [    0.000000] Using APIC driver default
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 10 08:28:32 mauro kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 10 08:28:32 mauro kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 10 08:28:32 mauro kernel: [    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
Jun 10 08:28:32 mauro kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jun 10 08:28:32 mauro kernel: [    0.000000] nr_irqs_gsi: 24
Jun 10 08:28:32 mauro kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Jun 10 08:28:32 mauro kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Jun 10 08:28:32 mauro kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jun 10 08:28:32 mauro kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jun 10 08:28:32 mauro kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Jun 10 08:28:32 mauro kernel: [    0.000000] Allocating PCI resources starting at df200000 (gap: df200000:18e00000)
Jun 10 08:28:32 mauro kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jun 10 08:28:32 mauro kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jun 10 08:28:32 mauro kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36056 r0 d21288 u2097152
Jun 10 08:28:32 mauro kernel: [    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
Jun 10 08:28:32 mauro kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Jun 10 08:28:32 mauro kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 832518
Jun 10 08:28:32 mauro kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-61-generic root=UUID=d66d60ee-b416-4513-8d27-2ae36359b524 ro quiet splash
Jun 10 08:28:32 mauro kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jun 10 08:28:32 mauro kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 10 08:28:32 mauro kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 10 08:28:32 mauro kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 10 08:28:32 mauro kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 10 08:28:32 mauro kernel: [    0.000000] Initializing CPU#0
Jun 10 08:28:32 mauro kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Jun 10 08:28:32 mauro kernel: [    0.000000] allocated 16875200 bytes of page_cgroup
Jun 10 08:28:32 mauro kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jun 10 08:28:32 mauro kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000ce000)
Jun 10 08:28:32 mauro kernel: [    0.000000] Memory: 3295576k/3375104k available (4706k kernel code, 59780k reserved, 2128k data, 664k init, 2449648k highmem)
Jun 10 08:28:32 mauro kernel: [    0.000000] virtual kernel memory layout:
Jun 10 08:28:32 mauro kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Jun 10 08:28:32 mauro kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 10 08:28:32 mauro kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Jun 10 08:28:32 mauro kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Jun 10 08:28:32 mauro kernel: [    0.000000]       .init : 0xc07ad000 - 0xc0853000   ( 664 kB)
Jun 10 08:28:32 mauro kernel: [    0.000000]       .data : 0xc0598b57 - 0xc07acdc8   (2128 kB)
Jun 10 08:28:32 mauro kernel: [    0.000000]       .text : 0xc0100000 - 0xc0598b57   (4706 kB)
Jun 10 08:28:32 mauro kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jun 10 08:28:32 mauro kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jun 10 08:28:32 mauro kernel: [    0.000000] Hierarchical RCU implementation.
Jun 10 08:28:32 mauro kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Jun 10 08:28:32 mauro kernel: [    0.000000] Extended CMOS year: 2000
Jun 10 08:28:32 mauro kernel: [    0.000000] Console: colour VGA+ 80x25
Jun 10 08:28:32 mauro kernel: [    0.000000] console [tty0] enabled
Jun 10 08:28:32 mauro kernel: [    0.000000] hpet clockevent registered
Jun 10 08:28:32 mauro kernel: [    0.000000] Fast TSC calibration using PIT
Jun 10 08:28:32 mauro kernel: [    0.004000] Detected 2900.209 MHz processor.
Jun 10 08:28:32 mauro kernel: [    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 5800.41 BogoMIPS (lpj=11600836)
Jun 10 08:28:32 mauro kernel: [    0.000011] Security Framework initialized
Jun 10 08:28:32 mauro kernel: [    0.000023] AppArmor: AppArmor initialized
Jun 10 08:28:32 mauro kernel: [    0.000028] Mount-cache hash table entries: 512
Jun 10 08:28:32 mauro kernel: [    0.000095] Initializing cgroup subsys ns
Jun 10 08:28:32 mauro kernel: [    0.000097] Initializing cgroup subsys cpuacct
Jun 10 08:28:32 mauro kernel: [    0.000100] Initializing cgroup subsys memory
Jun 10 08:28:32 mauro kernel: [    0.000103] Initializing cgroup subsys devices
Jun 10 08:28:32 mauro kernel: [    0.000105] Initializing cgroup subsys freezer
Jun 10 08:28:32 mauro kernel: [    0.000106] Initializing cgroup subsys net_cls
Jun 10 08:28:32 mauro kernel: [    0.000120] CPU: Physical Processor ID: 0
Jun 10 08:28:32 mauro kernel: [    0.000121] CPU: Processor Core ID: 0
Jun 10 08:28:32 mauro kernel: [    0.000124] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 10 08:28:32 mauro kernel: [    0.000125] CPU: L2 cache: 256K
Jun 10 08:28:32 mauro kernel: [    0.000126] CPU: L3 cache: 3072K
Jun 10 08:28:32 mauro kernel: [    0.000130] mce: CPU supports 7 MCE banks
Jun 10 08:28:32 mauro kernel: [    0.000139] CPU0: Thermal monitoring enabled (TM1)
Jun 10 08:28:32 mauro kernel: [    0.000141] CPU 0 MCA banks CMCI:0 CMCI:1 CMCI:3 CMCI:5 CMCI:6
Jun 10 08:28:32 mauro kernel: [    0.000149] using mwait in idle threads.
Jun 10 08:28:32 mauro kernel: [    0.000151] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
Jun 10 08:28:32 mauro kernel: [    0.000155] ... version:                3
Jun 10 08:28:32 mauro kernel: [    0.000156] ... bit width:              48
Jun 10 08:28:32 mauro kernel: [    0.000157] ... generic registers:      8
Jun 10 08:28:32 mauro kernel: [    0.000158] ... value mask:             0000ffffffffffff
Jun 10 08:28:32 mauro kernel: [    0.000159] ... max period:             000000007fffffff
Jun 10 08:28:32 mauro kernel: [    0.000160] ... fixed-purpose events:   3
Jun 10 08:28:32 mauro kernel: [    0.000162] ... event mask:             00000007000000ff
Jun 10 08:28:32 mauro kernel: [    0.000165] Checking 'hlt' instruction... OK.
Jun 10 08:28:32 mauro kernel: [    0.014591] ACPI: Core revision 20090903
Jun 10 08:28:32 mauro kernel: [    0.035200] ftrace: converting mcount calls to 0f 1f 44 00 00
Jun 10 08:28:32 mauro kernel: [    0.035202] ftrace: allocating 21854 entries in 43 pages
Jun 10 08:28:32 mauro kernel: [    0.041269] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jun 10 08:28:32 mauro kernel: [    0.041593] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 10 08:28:32 mauro kernel: [    0.081268] CPU0: Intel(R) Pentium(R) CPU G2020 @ 2.90GHz stepping 09
Jun 10 08:28:32 mauro kernel: [    0.188402] Booting processor 1 APIC 0x2 ip 0x6000
Jun 10 08:28:32 mauro kernel: [    0.198676] Initializing CPU#1
Jun 10 08:28:32 mauro kernel: [    0.276305] CPU: Physical Processor ID: 0
Jun 10 08:28:32 mauro kernel: [    0.276306] CPU: Processor Core ID: 1
Jun 10 08:28:32 mauro kernel: [    0.276308] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 10 08:28:32 mauro kernel: [    0.276309] CPU: L2 cache: 256K
Jun 10 08:28:32 mauro kernel: [    0.276310] CPU: L3 cache: 3072K
Jun 10 08:28:32 mauro kernel: [    0.276321] CPU1: Thermal monitoring enabled (TM1)
Jun 10 08:28:32 mauro kernel: [    0.276322] CPU 1 MCA banks CMCI:0 CMCI:1 CMCI:3 SHD:5 SHD:6
Jun 10 08:28:32 mauro kernel: [    0.276414] CPU1: Intel(R) Pentium(R) CPU G2020 @ 2.90GHz stepping 09
Jun 10 08:28:32 mauro kernel: [    0.276420] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 10 08:28:32 mauro kernel: [    0.296431] Brought up 2 CPUs
Jun 10 08:28:32 mauro kernel: [    0.296433] Total of 2 processors activated (11600.23 BogoMIPS).
Jun 10 08:28:32 mauro kernel: [    0.297310] CPU0 attaching sched-domain:
Jun 10 08:28:32 mauro kernel: [    0.297313]  domain 0: span 0-1 level MC
Jun 10 08:28:32 mauro kernel: [    0.297314]   groups: 0 1
Jun 10 08:28:32 mauro kernel: [    0.297318] CPU1 attaching sched-domain:
Jun 10 08:28:32 mauro kernel: [    0.297319]  domain 0: span 0-1 level MC
Jun 10 08:28:32 mauro kernel: [    0.297321]   groups: 1 0
Jun 10 08:28:32 mauro kernel: [    0.297449] devtmpfs: initialized
Jun 10 08:28:32 mauro kernel: [    0.297671] regulator: core version 0.5
Jun 10 08:28:32 mauro kernel: [    0.297694] Time:  8:28:21  Date: 06/10/14
Jun 10 08:28:32 mauro kernel: [    0.297720] NET: Registered protocol family 16
Jun 10 08:28:32 mauro kernel: [    0.297769] Trying to unpack rootfs image as initramfs...
Jun 10 08:28:32 mauro kernel: [    0.297791] EISA bus registered
Jun 10 08:28:32 mauro kernel: [    0.297795] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Jun 10 08:28:32 mauro kernel: [    0.297797] ACPI: bus type pci registered
Jun 10 08:28:32 mauro kernel: [    0.297836] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
Jun 10 08:28:32 mauro kernel: [    0.297838] PCI: MCFG area at f8000000 reserved in E820
Jun 10 08:28:32 mauro kernel: [    0.297839] PCI: Using MMCONFIG for extended config space
Jun 10 08:28:32 mauro kernel: [    0.297840] PCI: Using configuration type 1 for base access
Jun 10 08:28:32 mauro kernel: [    0.300346] bio: create slab <bio-0> at 0
Jun 10 08:28:32 mauro kernel: [    0.301150] ACPI: EC: Look up EC in DSDT
Jun 10 08:28:32 mauro kernel: [    0.302808] ACPI: Executed 1 blocks of module-level executable AML code
Jun 10 08:28:32 mauro kernel: [    0.305057] ACPI Error (psargs-0359): [RAMB] Namespace lookup failure, AE_NOT_FOUND
Jun 10 08:28:32 mauro kernel: [    0.305061] ACPI Exception: AE_NOT_FOUND, Could not execute arguments for [RAMW] (Region) (20090903/nsinit-338)
Jun 10 08:28:32 mauro kernel: [    0.307244] ACPI: Interpreter enabled
Jun 10 08:28:32 mauro kernel: [    0.307247] ACPI: (supports S0 S3 S4 S5)
Jun 10 08:28:32 mauro kernel: [    0.307264] ACPI: Using IOAPIC for interrupt routing
Jun 10 08:28:32 mauro kernel: [    0.313284] ACPI: Power Resource [FN00] (off)
Jun 10 08:28:32 mauro kernel: [    0.313321] ACPI: Power Resource [FN01] (off)
Jun 10 08:28:32 mauro kernel: [    0.313357] ACPI: Power Resource [FN02] (off)
Jun 10 08:28:32 mauro kernel: [    0.313393] ACPI: Power Resource [FN03] (off)
Jun 10 08:28:32 mauro kernel: [    0.313429] ACPI: Power Resource [FN04] (off)
Jun 10 08:28:32 mauro kernel: [    0.313748] ACPI: No dock devices found.
Jun 10 08:28:32 mauro kernel: [    0.314251] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 10 08:28:32 mauro kernel: [    0.314327] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jun 10 08:28:32 mauro kernel: [    0.314329] pci 0000:00:01.0: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.314353] pci 0000:00:02.0: reg 10 64bit mmio: [0xf7800000-0xf7bfffff]
Jun 10 08:28:32 mauro kernel: [    0.314358] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xe0000000-0xefffffff]
Jun 10 08:28:32 mauro kernel: [    0.314361] pci 0000:00:02.0: reg 20 io port: [0xf000-0xf03f]
Jun 10 08:28:32 mauro kernel: [    0.314430] pci 0000:00:16.0: reg 10 64bit mmio: [0xf7c0a000-0xf7c0a00f]
Jun 10 08:28:32 mauro kernel: [    0.314488] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Jun 10 08:28:32 mauro kernel: [    0.314491] pci 0000:00:16.0: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.314543] pci 0000:00:1a.0: reg 10 32bit mmio: [0xf7c08000-0xf7c083ff]
Jun 10 08:28:32 mauro kernel: [    0.314612] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
Jun 10 08:28:32 mauro kernel: [    0.314615] pci 0000:00:1a.0: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.314652] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf7c00000-0xf7c03fff]
Jun 10 08:28:32 mauro kernel: [    0.314704] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jun 10 08:28:32 mauro kernel: [    0.314707] pci 0000:00:1b.0: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.314788] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jun 10 08:28:32 mauro kernel: [    0.314791] pci 0000:00:1c.0: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.314878] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jun 10 08:28:32 mauro kernel: [    0.314881] pci 0000:00:1c.5: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.314932] pci 0000:00:1d.0: reg 10 32bit mmio: [0xf7c07000-0xf7c073ff]
Jun 10 08:28:32 mauro kernel: [    0.315000] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
Jun 10 08:28:32 mauro kernel: [    0.315003] pci 0000:00:1d.0: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.315141] pci 0000:00:1f.2: reg 10 io port: [0xf0b0-0xf0b7]
Jun 10 08:28:32 mauro kernel: [    0.315146] pci 0000:00:1f.2: reg 14 io port: [0xf0a0-0xf0a3]
Jun 10 08:28:32 mauro kernel: [    0.315150] pci 0000:00:1f.2: reg 18 io port: [0xf090-0xf097]
Jun 10 08:28:32 mauro kernel: [    0.315155] pci 0000:00:1f.2: reg 1c io port: [0xf080-0xf083]
Jun 10 08:28:32 mauro kernel: [    0.315159] pci 0000:00:1f.2: reg 20 io port: [0xf060-0xf07f]
Jun 10 08:28:32 mauro kernel: [    0.315164] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf7c06000-0xf7c067ff]
Jun 10 08:28:32 mauro kernel: [    0.315203] pci 0000:00:1f.2: PME# supported from D3hot
Jun 10 08:28:32 mauro kernel: [    0.315206] pci 0000:00:1f.2: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.315230] pci 0000:00:1f.3: reg 10 64bit mmio: [0xf7c05000-0xf7c050ff]
Jun 10 08:28:32 mauro kernel: [    0.315242] pci 0000:00:1f.3: reg 20 io port: [0xf040-0xf05f]
Jun 10 08:28:32 mauro kernel: [    0.315370] pci 0000:03:00.0: reg 10 io port: [0xe000-0xe0ff]
Jun 10 08:28:32 mauro kernel: [    0.315393] pci 0000:03:00.0: reg 18 64bit mmio pref: [0xf0004000-0xf0004fff]
Jun 10 08:28:32 mauro kernel: [    0.315409] pci 0000:03:00.0: reg 20 64bit mmio pref: [0xf0000000-0xf0003fff]
Jun 10 08:28:32 mauro kernel: [    0.315493] pci 0000:03:00.0: supports D1 D2
Jun 10 08:28:32 mauro kernel: [    0.315495] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jun 10 08:28:32 mauro kernel: [    0.315500] pci 0000:03:00.0: PME# disabled
Jun 10 08:28:32 mauro kernel: [    0.315558] pci 0000:00:1c.5: bridge io port: [0xe000-0xefff]
Jun 10 08:28:32 mauro kernel: [    0.315566] pci 0000:00:1c.5: bridge 64bit mmio pref: [0xf0000000-0xf00fffff]
Jun 10 08:28:32 mauro kernel: [    0.315578] pci_bus 0000:00: on NUMA node 0
Jun 10 08:28:32 mauro kernel: [    0.315582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 10 08:28:32 mauro kernel: [    0.315780] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Jun 10 08:28:32 mauro kernel: [    0.315872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Jun 10 08:28:32 mauro kernel: [    0.315951] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
Jun 10 08:28:32 mauro kernel: [    0.320770] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
Jun 10 08:28:32 mauro kernel: [    0.320881] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 10 11 12 14 15)
Jun 10 08:28:32 mauro kernel: [    0.320990] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 *14 15)
Jun 10 08:28:32 mauro kernel: [    0.321097] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 *15)
Jun 10 08:28:32 mauro kernel: [    0.321203] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
Jun 10 08:28:32 mauro kernel: [    0.321311] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *10 11 12 14 15)
Jun 10 08:28:32 mauro kernel: [    0.321418] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
Jun 10 08:28:32 mauro kernel: [    0.321525] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
Jun 10 08:28:32 mauro kernel: [    0.321601] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jun 10 08:28:32 mauro kernel: [    0.321605] vgaarb: loaded
Jun 10 08:28:32 mauro kernel: [    0.321674] SCSI subsystem initialized
Jun 10 08:28:32 mauro kernel: [    0.321724] libata version 3.00 loaded.
Jun 10 08:28:32 mauro kernel: [    0.321762] usbcore: registered new interface driver usbfs
Jun 10 08:28:32 mauro kernel: [    0.321770] usbcore: registered new interface driver hub
Jun 10 08:28:32 mauro kernel: [    0.321783] usbcore: registered new device driver usb
Jun 10 08:28:32 mauro kernel: [    0.321864] ACPI: WMI: Mapper loaded
Jun 10 08:28:32 mauro kernel: [    0.321865] PCI: Using ACPI for IRQ routing
Jun 10 08:28:32 mauro kernel: [    0.321951] NetLabel: Initializing
Jun 10 08:28:32 mauro kernel: [    0.321952] NetLabel:  domain hash size = 128
Jun 10 08:28:32 mauro kernel: [    0.321953] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 10 08:28:32 mauro kernel: [    0.321961] NetLabel:  unlabeled traffic allowed by default
Jun 10 08:28:32 mauro kernel: [    0.321984] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
Jun 10 08:28:32 mauro kernel: [    0.321989] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
Jun 10 08:28:32 mauro kernel: [    0.324000] Switching to clocksource tsc
Jun 10 08:28:32 mauro kernel: [    0.325236] AppArmor: AppArmor Filesystem Enabled
Jun 10 08:28:32 mauro kernel: [    0.325242] pnp: PnP ACPI init
Jun 10 08:28:32 mauro kernel: [    0.325248] ACPI: bus type pnp registered
Jun 10 08:28:32 mauro kernel: [    0.327066] pnp: PnP ACPI: found 14 devices
Jun 10 08:28:32 mauro kernel: [    0.327067] ACPI: ACPI bus type pnp unregistered
Jun 10 08:28:32 mauro kernel: [    0.327069] PnPBIOS: Disabled by ACPI PNP
Jun 10 08:28:32 mauro kernel: [    0.327075] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327080] system 00:05: ioport range 0x680-0x69f has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327082] system 00:05: ioport range 0x1000-0x100f has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327083] system 00:05: ioport range 0xffff-0xffff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327085] system 00:05: ioport range 0xffff-0xffff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327086] system 00:05: ioport range 0x400-0x453 has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327088] system 00:05: ioport range 0x458-0x47f has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327089] system 00:05: ioport range 0x500-0x57f has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327091] system 00:05: ioport range 0x164e-0x164f has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327094] system 00:07: ioport range 0x454-0x457 has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327097] system 00:08: ioport range 0x290-0x29f has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327100] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327104] system 00:0c: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327106] system 00:0c: iomem range 0xfed10000-0xfed17fff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327107] system 00:0c: iomem range 0xfed18000-0xfed18fff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327109] system 00:0c: iomem range 0xfed19000-0xfed19fff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327111] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327112] system 00:0c: iomem range 0xfed20000-0xfed3ffff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327114] system 00:0c: iomem range 0xfed90000-0xfed93fff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327116] system 00:0c: iomem range 0xfed45000-0xfed8ffff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327117] system 00:0c: iomem range 0xff000000-0xffffffff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327119] system 00:0c: iomem range 0xfee00000-0xfeefffff could not be reserved
Jun 10 08:28:32 mauro kernel: [    0.327121] system 00:0c: iomem range 0xdf200000-0xdf200fff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327124] system 00:0d: iomem range 0x20000000-0x201fffff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.327125] system 00:0d: iomem range 0x40004000-0x40004fff has been reserved
Jun 10 08:28:32 mauro kernel: [    0.361720] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jun 10 08:28:32 mauro kernel: [    0.361722] pci 0000:00:01.0:   IO window: disabled
Jun 10 08:28:32 mauro kernel: [    0.361724] pci 0000:00:01.0:   MEM window: disabled
Jun 10 08:28:32 mauro kernel: [    0.361726] pci 0000:00:01.0:   PREFETCH window: disabled
Jun 10 08:28:32 mauro kernel: [    0.361729] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Jun 10 08:28:32 mauro kernel: [    0.361730] pci 0000:00:1c.0:   IO window: disabled
Jun 10 08:28:32 mauro kernel: [    0.361734] pci 0000:00:1c.0:   MEM window: disabled
Jun 10 08:28:32 mauro kernel: [    0.361737] pci 0000:00:1c.0:   PREFETCH window: disabled
Jun 10 08:28:32 mauro kernel: [    0.361742] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:03
Jun 10 08:28:32 mauro kernel: [    0.361744] pci 0000:00:1c.5:   IO window: 0xe000-0xefff
Jun 10 08:28:32 mauro kernel: [    0.361748] pci 0000:00:1c.5:   MEM window: disabled
Jun 10 08:28:32 mauro kernel: [    0.361752] pci 0000:00:1c.5:   PREFETCH window: 0x000000f0000000-0x000000f00fffff
Jun 10 08:28:32 mauro kernel: [    0.361765]   alloc irq_desc for 16 on node -1
Jun 10 08:28:32 mauro kernel: [    0.361767]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.361770] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 08:28:32 mauro kernel: [    0.361773] pci 0000:00:01.0: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.361779] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 10 08:28:32 mauro kernel: [    0.361783] pci 0000:00:1c.0: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.361790]   alloc irq_desc for 17 on node -1
Jun 10 08:28:32 mauro kernel: [    0.361791]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.361793] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jun 10 08:28:32 mauro kernel: [    0.361796] pci 0000:00:1c.5: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.361799] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jun 10 08:28:32 mauro kernel: [    0.361801] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Jun 10 08:28:32 mauro kernel: [    0.361803] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
Jun 10 08:28:32 mauro kernel: [    0.361805] pci_bus 0000:03: resource 2 pref mem [0xf0000000-0xf00fffff]
Jun 10 08:28:32 mauro kernel: [    0.361827] NET: Registered protocol family 2
Jun 10 08:28:32 mauro kernel: [    0.361877] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 10 08:28:32 mauro kernel: [    0.362016] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 10 08:28:32 mauro kernel: [    0.362226] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 10 08:28:32 mauro kernel: [    0.362336] TCP: Hash tables configured (established 131072 bind 65536)
Jun 10 08:28:32 mauro kernel: [    0.362338] TCP reno registered
Jun 10 08:28:32 mauro kernel: [    0.362377] NET: Registered protocol family 1
Jun 10 08:28:32 mauro kernel: [    0.362387] pci 0000:00:02.0: Boot video device
Jun 10 08:28:32 mauro kernel: [    0.362397]   alloc irq_desc for 23 on node -1
Jun 10 08:28:32 mauro kernel: [    0.362399]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.362401] pci 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 10 08:28:32 mauro kernel: [    0.362420] pci 0000:00:1a.0: PCI INT A disabled
Jun 10 08:28:32 mauro kernel: [    0.362429] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 10 08:28:32 mauro kernel: [    0.362440] pci 0000:00:1d.0: PCI INT A disabled
Jun 10 08:28:32 mauro kernel: [    0.362550] cpufreq-nforce2: No nForce2 chipset.
Jun 10 08:28:32 mauro kernel: [    0.362564] Scanning for low memory corruption every 60 seconds
Jun 10 08:28:32 mauro kernel: [    0.362623] audit: initializing netlink socket (disabled)
Jun 10 08:28:32 mauro kernel: [    0.362628] type=2000 audit(1402388901.232:1): initialized
Jun 10 08:28:32 mauro kernel: [    0.368548] highmem bounce pool size: 64 pages
Jun 10 08:28:32 mauro kernel: [    0.368551] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jun 10 08:28:32 mauro kernel: [    0.369326] VFS: Disk quotas dquot_6.5.2
Jun 10 08:28:32 mauro kernel: [    0.369356] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 10 08:28:32 mauro kernel: [    0.369642] fuse init (API version 7.13)
Jun 10 08:28:32 mauro kernel: [    0.369684] msgmni has been set to 1654
Jun 10 08:28:32 mauro kernel: [    0.369798] alg: No test for stdrng (krng)
Jun 10 08:28:32 mauro kernel: [    0.369827] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jun 10 08:28:32 mauro kernel: [    0.369828] io scheduler noop registered
Jun 10 08:28:32 mauro kernel: [    0.369830] io scheduler anticipatory registered
Jun 10 08:28:32 mauro kernel: [    0.369831] io scheduler deadline registered
Jun 10 08:28:32 mauro kernel: [    0.369849] io scheduler cfq registered (default)
Jun 10 08:28:32 mauro kernel: [    0.369917]   alloc irq_desc for 24 on node -1
Jun 10 08:28:32 mauro kernel: [    0.369918]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.369923] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
Jun 10 08:28:32 mauro kernel: [    0.369926] pcieport 0000:00:01.0: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.370002]   alloc irq_desc for 25 on node -1
Jun 10 08:28:32 mauro kernel: [    0.370003]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.370009] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
Jun 10 08:28:32 mauro kernel: [    0.370016] pcieport 0000:00:1c.0: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.370108]   alloc irq_desc for 26 on node -1
Jun 10 08:28:32 mauro kernel: [    0.370109]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.370115] pcieport 0000:00:1c.5: irq 26 for MSI/MSI-X
Jun 10 08:28:32 mauro kernel: [    0.370122] pcieport 0000:00:1c.5: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.370175] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 08:28:32 mauro kernel: [    0.370188] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jun 10 08:28:32 mauro kernel: [    0.370247] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jun 10 08:28:32 mauro kernel: [    0.370249] ACPI: Power Button [PWRB]
Jun 10 08:28:32 mauro kernel: [    0.370275] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Jun 10 08:28:32 mauro kernel: [    0.370277] ACPI: Power Button [PWRF]
Jun 10 08:28:32 mauro kernel: [    0.370390] fan PNP0C0B:00: registered as cooling_device0
Jun 10 08:28:32 mauro kernel: [    0.370394] ACPI: Fan [FAN0] (off)
Jun 10 08:28:32 mauro kernel: [    0.370466] fan PNP0C0B:01: registered as cooling_device1
Jun 10 08:28:32 mauro kernel: [    0.370469] ACPI: Fan [FAN1] (off)
Jun 10 08:28:32 mauro kernel: [    0.370539] fan PNP0C0B:02: registered as cooling_device2
Jun 10 08:28:32 mauro kernel: [    0.370542] ACPI: Fan [FAN2] (off)
Jun 10 08:28:32 mauro kernel: [    0.370613] fan PNP0C0B:03: registered as cooling_device3
Jun 10 08:28:32 mauro kernel: [    0.370616] ACPI: Fan [FAN3] (off)
Jun 10 08:28:32 mauro kernel: [    0.370685] fan PNP0C0B:04: registered as cooling_device4
Jun 10 08:28:32 mauro kernel: [    0.370687] ACPI: Fan [FAN4] (off)
Jun 10 08:28:32 mauro kernel: [    0.371480] ACPI: SSDT cd15b018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jun 10 08:28:32 mauro kernel: [    0.371982] Monitor-Mwait will be used to enter C-1 state
Jun 10 08:28:32 mauro kernel: [    0.371995] Monitor-Mwait will be used to enter C-2 state
Jun 10 08:28:32 mauro kernel: [    0.372006] Monitor-Mwait will be used to enter C-3 state
Jun 10 08:28:32 mauro kernel: [    0.372027] processor LNXCPU:00: registered as cooling_device5
Jun 10 08:28:32 mauro kernel: [    0.372385] ACPI: SSDT cd15ca98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
Jun 10 08:28:32 mauro kernel: [    0.372727] ACPI: SSDT cd15dc18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
Jun 10 08:28:32 mauro kernel: [    0.384581] processor LNXCPU:01: registered as cooling_device6
Jun 10 08:28:32 mauro kernel: [    0.387172] thermal LNXTHERM:01: registered as thermal_zone0
Jun 10 08:28:32 mauro kernel: [    0.387177] ACPI: Thermal Zone [TZ00] (28 C)
Jun 10 08:28:32 mauro kernel: [    0.387554] thermal LNXTHERM:02: registered as thermal_zone1
Jun 10 08:28:32 mauro kernel: [    0.387559] ACPI: Thermal Zone [TZ01] (30 C)
Jun 10 08:28:32 mauro kernel: [    0.388387] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jun 10 08:28:32 mauro kernel: [    0.389153] brd: module loaded
Jun 10 08:28:32 mauro kernel: [    0.389391] loop: module loaded
Jun 10 08:28:32 mauro kernel: [    0.389439] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Jun 10 08:28:32 mauro kernel: [    0.389649] Fixed MDIO Bus: probed
Jun 10 08:28:32 mauro kernel: [    0.389668] PPP generic driver version 2.4.2
Jun 10 08:28:32 mauro kernel: [    0.389685] tun: Universal TUN/TAP device driver, 1.6
Jun 10 08:28:32 mauro kernel: [    0.389686] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jun 10 08:28:32 mauro kernel: [    0.389728] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jun 10 08:28:32 mauro kernel: [    0.389739] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 10 08:28:32 mauro kernel: [    0.389748] ehci_hcd 0000:00:1a.0: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.389750] ehci_hcd 0000:00:1a.0: EHCI Host Controller
Jun 10 08:28:32 mauro kernel: [    0.389770] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun 10 08:28:32 mauro kernel: [    0.389790] ehci_hcd 0000:00:1a.0: debug port 2
Jun 10 08:28:32 mauro kernel: [    0.393669] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
Jun 10 08:28:32 mauro kernel: [    0.393680] ehci_hcd 0000:00:1a.0: irq 23, io mem 0xf7c08000
Jun 10 08:28:32 mauro kernel: [    0.396518] isapnp: Scanning for PnP cards...
Jun 10 08:28:32 mauro kernel: [    0.408377] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
Jun 10 08:28:32 mauro kernel: [    0.408440] usb usb1: configuration #1 chosen from 1 choice
Jun 10 08:28:32 mauro kernel: [    0.408456] hub 1-0:1.0: USB hub found
Jun 10 08:28:32 mauro kernel: [    0.408460] hub 1-0:1.0: 2 ports detected
Jun 10 08:28:32 mauro kernel: [    0.408487] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jun 10 08:28:32 mauro kernel: [    0.408497] ehci_hcd 0000:00:1d.0: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.408500] ehci_hcd 0000:00:1d.0: EHCI Host Controller
Jun 10 08:28:32 mauro kernel: [    0.408519] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jun 10 08:28:32 mauro kernel: [    0.408538] ehci_hcd 0000:00:1d.0: debug port 2
Jun 10 08:28:32 mauro kernel: [    0.412433] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
Jun 10 08:28:32 mauro kernel: [    0.412437] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7c07000
Jun 10 08:28:32 mauro kernel: [    0.427031] Freeing initrd memory: 7818k freed
Jun 10 08:28:32 mauro kernel: [    0.436252] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
Jun 10 08:28:32 mauro kernel: [    0.436317] usb usb2: configuration #1 chosen from 1 choice
Jun 10 08:28:32 mauro kernel: [    0.436333] hub 2-0:1.0: USB hub found
Jun 10 08:28:32 mauro kernel: [    0.436337] hub 2-0:1.0: 2 ports detected
Jun 10 08:28:32 mauro kernel: [    0.436366] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jun 10 08:28:32 mauro kernel: [    0.436375] uhci_hcd: USB Universal Host Controller Interface driver
Jun 10 08:28:32 mauro kernel: [    0.436428] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
Jun 10 08:28:32 mauro kernel: [    0.436430] PNP: PS/2 controller doesn't have KBD irq; using default 1
Jun 10 08:28:32 mauro kernel: [    0.438716] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 08:28:32 mauro kernel: [    0.438720] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 10 08:28:32 mauro kernel: [    0.438784] mice: PS/2 mouse device common for all mice
Jun 10 08:28:32 mauro kernel: [    0.438855] rtc_cmos 00:06: RTC can wake from S4
Jun 10 08:28:32 mauro kernel: [    0.438878] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
Jun 10 08:28:32 mauro kernel: [    0.438902] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Jun 10 08:28:32 mauro kernel: [    0.438959] device-mapper: uevent: version 1.0.3
Jun 10 08:28:32 mauro kernel: [    0.439018] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Jun 10 08:28:32 mauro kernel: [    0.439053] device-mapper: multipath: version 1.1.0 loaded
Jun 10 08:28:32 mauro kernel: [    0.439055] device-mapper: multipath round-robin: version 1.0.0 loaded
Jun 10 08:28:32 mauro kernel: [    0.439110] EISA: Probing bus 0 at eisa.0
Jun 10 08:28:32 mauro kernel: [    0.439113] Cannot allocate resource for EISA slot 1
Jun 10 08:28:32 mauro kernel: [    0.439127] EISA: Detected 0 cards.
Jun 10 08:28:32 mauro kernel: [    0.439196] cpuidle: using governor ladder
Jun 10 08:28:32 mauro kernel: [    0.439254] cpuidle: using governor menu
Jun 10 08:28:32 mauro kernel: [    0.439450] TCP cubic registered
Jun 10 08:28:32 mauro kernel: [    0.439528] NET: Registered protocol family 10
Jun 10 08:28:32 mauro kernel: [    0.439881] NET: Registered protocol family 17
Jun 10 08:28:32 mauro kernel: [    0.440383] Using IPI No-Shortcut mode
Jun 10 08:28:32 mauro kernel: [    0.440424] PM: Resume from disk failed.
Jun 10 08:28:32 mauro kernel: [    0.440431] registered taskstats version 1
Jun 10 08:28:32 mauro kernel: [    0.440651]   Magic number: 2:523:472
Jun 10 08:28:32 mauro kernel: [    0.440652]   hash matches /build/buildd/linux-2.6.32/drivers/base/power/main.c:471
Jun 10 08:28:32 mauro kernel: [    0.440684] acpi LNXSYSTM:00: hash matches
Jun 10 08:28:32 mauro kernel: [    0.440708] rtc_cmos 00:06: setting system clock to 2014-06-10 08:28:21 UTC (1402388901)
Jun 10 08:28:32 mauro kernel: [    0.440710] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 08:28:32 mauro kernel: [    0.440711] EDD information not available.
Jun 10 08:28:32 mauro kernel: [    0.720157] usb 1-1: new high speed USB device using ehci_hcd and address 2
Jun 10 08:28:32 mauro kernel: [    0.749007] isapnp: No Plug & Play device found
Jun 10 08:28:32 mauro kernel: [    0.749014] Freeing unused kernel memory: 664k freed
Jun 10 08:28:32 mauro kernel: [    0.749145] Write protecting the kernel text: 4708k
Jun 10 08:28:32 mauro kernel: [    0.749164] Write protecting the kernel read-only data: 1848k
Jun 10 08:28:32 mauro kernel: [    0.758326] udev: starting version 151
Jun 10 08:28:32 mauro kernel: [    0.786139] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jun 10 08:28:32 mauro kernel: [    0.786158] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 10 08:28:32 mauro kernel: [    0.786197] r8169 0000:03:00.0: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.786203] r8169 0000:03:00.0: unknown MAC, using family default
Jun 10 08:28:32 mauro kernel: [    0.786273]   alloc irq_desc for 27 on node -1
Jun 10 08:28:32 mauro kernel: [    0.786275]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.786287] r8169 0000:03:00.0: irq 27 for MSI/MSI-X
Jun 10 08:28:32 mauro kernel: [    0.786621] eth0: RTL8168b/8111b at 0xf8056000, 50:46:5d:09:7e:23, XID 08000800 IRQ 27
Jun 10 08:28:32 mauro kernel: [    0.793909] ahci 0000:00:1f.2: version 3.0
Jun 10 08:28:32 mauro kernel: [    0.793921]   alloc irq_desc for 19 on node -1
Jun 10 08:28:32 mauro kernel: [    0.793923]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.793927] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jun 10 08:28:32 mauro kernel: [    0.793954]   alloc irq_desc for 28 on node -1
Jun 10 08:28:32 mauro kernel: [    0.793955]   alloc kstat_irqs on node -1
Jun 10 08:28:32 mauro kernel: [    0.793961] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
Jun 10 08:28:32 mauro kernel: [    0.808278] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x11 impl SATA mode
Jun 10 08:28:32 mauro kernel: [    0.808282] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
Jun 10 08:28:32 mauro kernel: [    0.808285] ahci 0000:00:1f.2: setting latency timer to 64
Jun 10 08:28:32 mauro kernel: [    0.826554] scsi0 : ahci
Jun 10 08:28:32 mauro kernel: [    0.826856] scsi1 : ahci
Jun 10 08:28:32 mauro kernel: [    0.826920] scsi2 : ahci
Jun 10 08:28:32 mauro kernel: [    0.826975] scsi3 : ahci
Jun 10 08:28:32 mauro kernel: [    0.827029] scsi4 : ahci
Jun 10 08:28:32 mauro kernel: [    0.827253] ata1: SATA max UDMA/133 abar m2048@0xf7c06000 port 0xf7c06100 irq 28
Jun 10 08:28:32 mauro kernel: [    0.827254] ata2: DUMMY
Jun 10 08:28:32 mauro kernel: [    0.827255] ata3: DUMMY
Jun 10 08:28:32 mauro kernel: [    0.827256] ata4: DUMMY
Jun 10 08:28:32 mauro kernel: [    0.827257] ata5: SATA max UDMA/133 abar m2048@0xf7c06000 port 0xf7c06300 irq 28
Jun 10 08:28:32 mauro kernel: [    0.852521] usb 1-1: configuration #1 chosen from 1 choice
Jun 10 08:28:32 mauro kernel: [    0.852619] hub 1-1:1.0: USB hub found
Jun 10 08:28:32 mauro kernel: [    0.852721] hub 1-1:1.0: 4 ports detected
Jun 10 08:28:32 mauro kernel: [    0.964080] usb 2-1: new high speed USB device using ehci_hcd and address 2
Jun 10 08:28:32 mauro kernel: [    1.096430] usb 2-1: configuration #1 chosen from 1 choice
Jun 10 08:28:32 mauro kernel: [    1.096543] hub 2-1:1.0: USB hub found
Jun 10 08:28:32 mauro kernel: [    1.096650] hub 2-1:1.0: 6 ports detected
Jun 10 08:28:32 mauro kernel: [    1.148881] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 10 08:28:32 mauro kernel: [    1.149420] ata1.00: ACPI _SDD failed (AE 0x5)
Jun 10 08:28:32 mauro kernel: [    1.155891] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 08:28:32 mauro kernel: [    1.157966] ata5.00: ACPI _SDD failed (AE 0x5)
Jun 10 08:28:32 mauro kernel: [    1.371989] usb 2-1.3: new low speed USB device using ehci_hcd and address 3
Jun 10 08:28:32 mauro kernel: [    1.468768] usb 2-1.3: configuration #1 chosen from 1 choice
Jun 10 08:28:32 mauro kernel: [    1.475036] usbcore: registered new interface driver hiddev
Jun 10 08:28:32 mauro kernel: [    1.478215] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input3
Jun 10 08:28:32 mauro kernel: [    1.478261] generic-usb 0003:04F3:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 04f3:0103] on usb-0000:00:1d.0-1.3/input0
Jun 10 08:28:32 mauro kernel: [    1.483151] input: HID 04f3:0103 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input4
Jun 10 08:28:32 mauro kernel: [    1.483195] generic-usb 0003:04F3:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 04f3:0103] on usb-0000:00:1d.0-1.3/input1
Jun 10 08:28:32 mauro kernel: [    1.483206] usbcore: registered new interface driver usbhid
Jun 10 08:28:32 mauro kernel: [    1.483207] usbhid: v2.6:USB HID core driver
Jun 10 08:28:32 mauro kernel: [    6.474716] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 10 08:28:32 mauro kernel: [    6.474737] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 10 08:28:32 mauro kernel: [    6.475312] ata1.00: ACPI _SDD failed (AE 0x5)
Jun 10 08:28:32 mauro kernel: [    6.475315] ata1.00: ACPI: failed the second time, disabled
Jun 10 08:28:32 mauro kernel: [    6.475598] ata1.00: ATA-8: TOSHIBA DT01ACA050, MS1OA750, max UDMA/133
Jun 10 08:28:32 mauro kernel: [    6.475603] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jun 10 08:28:32 mauro kernel: [    6.476616] ata1.00: configured for UDMA/133
Jun 10 08:28:32 mauro kernel: [    6.476738] ata5.00: ACPI _SDD failed (AE 0x5)
Jun 10 08:28:32 mauro kernel: [    6.476740] ata5.00: ACPI: failed the second time, disabled
Jun 10 08:28:32 mauro kernel: [    6.476742] ata5.00: ATAPI: TSSTcorp CDDVDW SH-224BB, SB00, max UDMA/100
Jun 10 08:28:32 mauro kernel: [    6.476755] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA DT01ACA0 MS1O PQ: 0 ANSI: 5
Jun 10 08:28:32 mauro kernel: [    6.476845] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 08:28:32 mauro kernel: [    6.476948] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jun 10 08:28:32 mauro kernel: [    6.476960] sd 0:0:0:0: [sda] 4096-byte physical blocks
Jun 10 08:28:32 mauro kernel: [    6.477088] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 08:28:32 mauro kernel: [    6.477090] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 10 08:28:32 mauro kernel: [    6.477156] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 08:28:32 mauro kernel: [    6.477419]  sda:
Jun 10 08:28:32 mauro kernel: [    6.477569] ata5.00: configured for UDMA/100
Jun 10 08:28:32 mauro kernel: [    6.478750] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-224BB  SB00 PQ: 0 ANSI: 5
Jun 10 08:28:32 mauro kernel: [    6.483189] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 10 08:28:32 mauro kernel: [    6.483193] Uniform CD-ROM driver Revision: 3.20
Jun 10 08:28:32 mauro kernel: [    6.483265] sr 4:0:0:0: Attached scsi CD-ROM sr0
Jun 10 08:28:32 mauro kernel: [    6.483290] sr 4:0:0:0: Attached scsi generic sg1 type 5
Jun 10 08:28:32 mauro kernel: [    6.496929]  sda1 sda2 < sda5 >
Jun 10 08:28:32 mauro kernel: [    6.526117] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 08:28:32 mauro kernel: [    6.863588] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jun 10 08:28:32 mauro kernel: [    8.461081] Adding 9680888k swap on /dev/sda5.  Priority:-1 extents:1 across:9680888k 
Jun 10 08:28:32 mauro kernel: [    9.298156] udev: starting version 151
Jun 10 08:28:32 mauro kernel: [    9.936170] type=1505 audit(1402388910.996:2):  operation="profile_load" pid=669 name="/sbin/dhclient3"
Jun 10 08:28:32 mauro kernel: [    9.936231] type=1505 audit(1402388910.996:3):  operation="profile_load" pid=669 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 10 08:28:32 mauro kernel: [    9.936269] type=1505 audit(1402388910.996:4):  operation="profile_load" pid=669 name="/usr/lib/connman/scripts/dhclient-script"
Jun 10 08:28:32 mauro kernel: [    9.937674] type=1505 audit(1402388910.996:5):  operation="profile_replace" pid=668 name="/sbin/dhclient3"
Jun 10 08:28:32 mauro kernel: [    9.937732] type=1505 audit(1402388910.996:6):  operation="profile_replace" pid=668 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 10 08:28:32 mauro kernel: [    9.937770] type=1505 audit(1402388910.996:7):  operation="profile_replace" pid=668 name="/usr/lib/connman/scripts/dhclient-script"
Jun 10 08:28:32 mauro kernel: [   10.659728] vga16fb: initializing
Jun 10 08:28:32 mauro kernel: [   10.659730] vga16fb: mapped to 0xc00a0000
Jun 10 08:28:32 mauro kernel: [   10.659764] fb0: VGA16 VGA frame buffer device
Jun 10 08:28:32 mauro kernel: [   11.301970] lp: driver loaded but no devices found
Jun 10 08:28:32 mauro udev-configure-printer: add /module/lp
Jun 10 08:28:32 mauro udev-configure-printer: Failed to get parent
Jun 10 08:28:32 mauro kernel: [   11.526648] Console: switching to colour frame buffer device 80x30
Jun 10 08:28:32 mauro kernel: [   11.745513] psmouse serio1: ID: 10 00 64
Jun 10 08:28:33 mauro kernel: [   12.299210] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Jun 10 08:28:33 mauro kernel: [   12.451192]   alloc irq_desc for 22 on node -1
Jun 10 08:28:33 mauro kernel: [   12.451194]   alloc kstat_irqs on node -1
Jun 10 08:28:33 mauro kernel: [   12.451198] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jun 10 08:28:33 mauro kernel: [   12.451221] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jun 10 08:28:34 mauro kernel: [   13.634175] type=1505 audit(1402388914.695:8):  operation="profile_replace" pid=937 name="/sbin/dhclient3"
Jun 10 08:28:34 mauro kernel: [   13.634612] type=1505 audit(1402388914.695:9):  operation="profile_replace" pid=937 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jun 10 08:28:34 mauro kernel: [   13.634851] type=1505 audit(1402388914.695:10):  operation="profile_replace" pid=937 name="/usr/lib/connman/scripts/dhclient-script"
Jun 10 08:28:35 mauro kernel: [   14.099130] type=1505 audit(1402388915.159:11):  operation="profile_load" pid=936 name="/usr/share/gdm/guest-session/Xsession"
Jun 10 08:28:35 mauro avahi-daemon[951]: Found user 'avahi' (UID 104) and group 'avahi' (GID 111).
Jun 10 08:28:35 mauro avahi-daemon[951]: Successfully dropped root privileges.
Jun 10 08:28:35 mauro avahi-daemon[951]: avahi-daemon 0.6.25 starting up.
Jun 10 08:28:35 mauro NetworkManager: <info>  starting...
Jun 10 08:28:35 mauro avahi-daemon[951]: Successfully called chroot().
Jun 10 08:28:35 mauro avahi-daemon[951]: Successfully dropped remaining capabilities.
Jun 10 08:28:35 mauro NetworkManager: <info>  Trying to start the modem-manager...
Jun 10 08:28:36 mauro gdm-binary[942]: WARNING: Unable to load file '/etc/gdm/custom.conf': No existe el fichero o el directorio
Jun 10 08:28:36 mauro avahi-daemon[951]: No service file found in /etc/avahi/services.
Jun 10 08:28:36 mauro avahi-daemon[951]: Network interface enumeration completed.
Jun 10 08:28:36 mauro avahi-daemon[951]: Registering HINFO record with values 'I686'/'LINUX'.
Jun 10 08:28:36 mauro avahi-daemon[951]: Server startup complete. Host name is mauro.local. Local service cookie is 1085586856.
Jun 10 08:28:36 mauro kernel: [   15.297141] type=1505 audit(1402388916.359:12):  operation="profile_load" pid=949 name="/usr/lib/cups/backend/cups-pdf"
Jun 10 08:28:36 mauro kernel: [   15.297242] type=1505 audit(1402388916.359:13):  operation="profile_load" pid=949 name="/usr/sbin/cupsd"
Jun 10 08:28:36 mauro kernel: [   15.413022] type=1505 audit(1402388916.475:14):  operation="profile_load" pid=960 name="/usr/sbin/tcpdump"
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Longcheer
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Nokia
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Option High-Speed
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Generic
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Sierra
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Gobi
Jun 10 08:28:36 mauro modem-manager: Loaded plugin AnyData
Jun 10 08:28:36 mauro modem-manager: Loaded plugin ZTE
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Option
Jun 10 08:28:36 mauro modem-manager: Loaded plugin MotoC
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Ericsson MBM
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Novatel
Jun 10 08:28:36 mauro modem-manager: Loaded plugin Huawei
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: init!
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Jun 10 08:28:36 mauro NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0, iface: eth0)
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: end _init.
Jun 10 08:28:36 mauro NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jun 10 08:28:36 mauro NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jun 10 08:28:36 mauro NetworkManager: <info>  WiFi enabled by radio killswitch; enabled by state file
Jun 10 08:28:36 mauro NetworkManager: <info>  WWAN enabled by radio killswitch; enabled by state file
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: (141569264) ... get_connections.
Jun 10 08:28:36 mauro NetworkManager:    SCPlugin-Ifupdown: (141569264) ... get_connections (managed=false): return empty list.
Jun 10 08:28:36 mauro NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): carrier is OFF
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): now managed
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): bringing up device.
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): preparing device.
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jun 10 08:28:36 mauro NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/eth0
Jun 10 08:28:36 mauro kernel: [   15.669307] r8169: eth0: link up
Jun 10 08:28:36 mauro kernel: [   15.669313] r8169: eth0: link up
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Jun 10 08:28:36 mauro NetworkManager: <info>  modem-manager is now available
Jun 10 08:28:36 mauro NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jun 10 08:28:36 mauro NetworkManager: <info>  Trying to start the supplicant...
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun 10 08:28:36 mauro NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jun 10 08:28:36 mauro NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jun 10 08:28:36 mauro gdm-binary[942]: WARNING: Unable to find users: no seat-id found
Jun 10 08:28:37 mauro gdm-simple-slave[1030]: WARNING: Unable to load file '/etc/gdm/custom.conf': No existe el fichero o el directorio
Jun 10 08:28:37 mauro NetworkManager: <info>  dhclient started with pid 1032
Jun 10 08:28:37 mauro NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jun 10 08:28:37 mauro NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 10 08:28:37 mauro NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jun 10 08:28:37 mauro NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jun 10 08:28:37 mauro dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jun 10 08:28:37 mauro dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jun 10 08:28:37 mauro dhclient: All rights reserved.
Jun 10 08:28:37 mauro dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jun 10 08:28:37 mauro dhclient: 
Jun 10 08:28:37 mauro NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Jun 10 08:28:37 mauro dhclient: Listening on LPF/eth0/50:46:5d:09:7e:23
Jun 10 08:28:37 mauro dhclient: Sending on   LPF/eth0/50:46:5d:09:7e:23
Jun 10 08:28:37 mauro dhclient: Sending on   Socket/fallback
Jun 10 08:28:37 mauro kernel: [   16.472208] type=1505 audit(1402388917.532:15):  operation="profile_load" pid=938 name="/usr/bin/evince"
Jun 10 08:28:37 mauro kernel: [   16.472669] type=1505 audit(1402388917.532:16):  operation="profile_load" pid=938 name="/usr/bin/evince-previewer"
Jun 10 08:28:37 mauro kernel: [   16.472973] type=1505 audit(1402388917.532:17):  operation="profile_load" pid=938 name="/usr/bin/evince-thumbnailer"
Jun 10 08:28:38 mauro avahi-daemon[951]: Registering new address record for fe80::5246:5dff:fe09:7e23 on eth0.*.
Jun 10 08:28:38 mauro cron[1079]: (CRON) INFO (pidfile fd = 3)
Jun 10 08:28:38 mauro acpid: starting up with proc fs
Jun 10 08:28:38 mauro anacron[1090]: Anacron 2.3 started on 2014-06-10
Jun 10 08:28:39 mauro dhclient: DHCPDISCOVER on eth0 to xxx.xxx.xxx.xxx port 67 interval 4
Jun 10 08:28:39 mauro cron[1092]: (CRON) STARTUP (fork ok)
Jun 10 08:28:39 mauro init: apport pre-start process (1074) terminated with status 1
Jun 10 08:28:39 mauro init: apport post-stop process (1093) terminated with status 1
Jun 10 08:28:39 mauro cron[1092]: (CRON) INFO (Running @reboot jobs)
Jun 10 08:28:39 mauro acpid: 36 rules loaded
Jun 10 08:28:39 mauro acpid: waiting for events: event logging is off
Jun 10 08:28:39 mauro anacron[1090]: Normal exit (0 jobs run)
Jun 10 08:28:40 mauro kernel: [   19.442315] ppdev: user-space parallel port driver
Jun 10 08:28:42 mauro anacron[1262]: Anacron 2.3 started on 2014-06-10
Jun 10 08:28:42 mauro anacron[1262]: Normal exit (0 jobs run)
Jun 10 08:28:43 mauro dhclient: DHCPDISCOVER on eth0 to xxx.xxx.xxx.xxx port 67 interval 7
Jun 10 08:28:43 mauro gdm-session-worker[1279]: WARNING: Unable to load file '/etc/gdm/custom.conf': No existe el fichero o el directorio
Jun 10 08:28:44 mauro init: plymouth-stop pre-start process (1331) terminated with status 1
Jun 10 08:28:44 mauro anacron[1336]: Anacron 2.3 started on 2014-06-10
Jun 10 08:28:44 mauro anacron[1336]: Normal exit (0 jobs run)
Jun 10 08:28:44 mauro polkitd[1304]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jun 10 08:28:44 mauro rtkit-daemon[1346]: Sucessfully called chroot.
Jun 10 08:28:44 mauro rtkit-daemon[1346]: Sucessfully dropped privileges.
Jun 10 08:28:44 mauro rtkit-daemon[1346]: Sucessfully limited resources.
Jun 10 08:28:44 mauro rtkit-daemon[1346]: Running.
Jun 10 08:28:44 mauro rtkit-daemon[1346]: Canary thread running.
Jun 10 08:28:44 mauro rtkit-daemon[1346]: Watchdog thread running.
Jun 10 08:28:44 mauro rtkit-daemon[1346]: Sucessfully made thread 1344 of process 1344 (n/a) owned by '114' high priority at nice level -11.
Jun 10 08:28:44 mauro rtkit-daemon[1346]: Supervising 1 threads of 1 processes of 1 users.
Jun 10 08:28:45 mauro rtkit-daemon[1346]: Sucessfully made thread 1354 of process 1344 (n/a) owned by '114' RT at priority 5.
Jun 10 08:28:45 mauro rtkit-daemon[1346]: Supervising 2 threads of 1 processes of 1 users.
Jun 10 08:28:45 mauro rtkit-daemon[1346]: Sucessfully made thread 1355 of process 1344 (n/a) owned by '114' RT at priority 5.
Jun 10 08:28:45 mauro rtkit-daemon[1346]: Supervising 3 threads of 1 processes of 1 users.
Jun 10 08:28:45 mauro gdm-simple-greeter[1269]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jun 10 08:28:46 mauro acpid: client connected from 1394[108:114]
Jun 10 08:28:46 mauro acpid: 1 client rule loaded
Jun 10 08:28:47 mauro kernel: [   26.262329] eth0: no IPv6 routers present
Jun 10 08:28:50 mauro dhclient: DHCPDISCOVER on eth0 to xxx.xxx.xxx.xxx port 67 interval 14
Jun 10 08:29:04 mauro dhclient: DHCPDISCOVER on eth0 to xxx.xxx.xxx.xxx port 67 interval 14
Jun 10 08:29:04 mauro dhclient: DHCPOFFER of xxx.xxx.xxx.xxx from xxx.xxx.xxx.xxx
Jun 10 08:29:04 mauro dhclient: DHCPREQUEST of xxx.xxx.xxx.xxx on eth0 to xxx.xxx.xxx.xxx port 67
Jun 10 08:29:04 mauro dhclient: DHCPACK of xxx.xxx.xxx.xxx from xxx.xxx.xxx.xxx
Jun 10 08:29:04 mauro dhclient: bound to xxx.xxx.xxx.xxx -- renewal in 10691 seconds.
Jun 10 08:29:04 mauro NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Jun 10 08:29:04 mauro NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun 10 08:29:04 mauro NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun 10 08:29:04 mauro NetworkManager: <info>    address xxx.xxx.xxx.xxx
Jun 10 08:29:04 mauro NetworkManager: <info>    prefix 21 (xxx.xxx.xxx.xxx)
Jun 10 08:29:04 mauro NetworkManager: <info>    gateway xxx.xxx.xxx.xxx
Jun 10 08:29:04 mauro NetworkManager: <info>    nameserver 'xxx.xxx.xxx.xxx'
Jun 10 08:29:04 mauro NetworkManager: <info>    nameserver 'xxx.xxx.xxx.xxx'
Jun 10 08:29:04 mauro NetworkManager: <info>    domain name 'xxx.xxx.xxx.xxx'
Jun 10 08:29:04 mauro NetworkManager: <info>    wins 'xxx.xxx.xxx.xxx'
Jun 10 08:29:04 mauro NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun 10 08:29:04 mauro NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun 10 08:29:04 mauro NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun 10 08:29:04 mauro avahi-daemon[951]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.0.237.
Jun 10 08:29:04 mauro avahi-daemon[951]: New relevant interface eth0.IPv4 for mDNS.
Jun 10 08:29:04 mauro avahi-daemon[951]: Registering new address record for 192.168.0.237 on eth0.IPv4.
Jun 10 08:29:05 mauro NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Jun 10 08:29:05 mauro NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Jun 10 08:29:05 mauro NetworkManager: <info>  Activation (eth0) successful, device activated.
Jun 10 08:29:05 mauro NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun 10 11:27:39 mauro ntpdate[1442]: step time server 91.189.89.199 offset 10712.775496 sec
Jun 10 11:27:43 mauro gdm-session-worker[1279]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun 10 11:27:45 mauro dhclient: DHCPREQUEST of xxx.xxx.xxx.xxx on eth0 to xxx.xxx.xxx.xxx port 67
Jun 10 11:27:45 mauro dhclient: DHCPACK of xxx.xxx.xxx.xxx from xxx.xxx.xxx.xxx
Jun 10 11:27:45 mauro dhclient: bound to xxx.xxx.xxx.xxx -- renewal in 9520 seconds.
Jun 10 11:27:45 mauro NetworkManager: <info>  DHCP: device eth0 state changed bound -> renew
Jun 10 11:27:45 mauro NetworkManager: <info>    address xxx.xxx.xxx.xxx
Jun 10 11:27:45 mauro NetworkManager: <info>    prefix 21 (xxx.xxx.xxx.xxx)
Jun 10 11:27:45 mauro NetworkManager: <info>    gateway xxx.xxx.xxx.xxx
Jun 10 11:27:45 mauro NetworkManager: <info>    nameserver 'xxx.xxx.xxx.xxx'
Jun 10 11:27:45 mauro NetworkManager: <info>    nameserver 'xxx.xxx.xxx.xxx'
Jun 10 11:27:45 mauro NetworkManager: <info>    domain name 'xxx.xxx.xxx.xxx'
Jun 10 11:27:45 mauro NetworkManager: <info>    wins 'xxx.xxx.xxx.xxx'
Jun 10 11:27:46 mauro rtkit-daemon[1346]: Sucessfully made thread 1529 of process 1529 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 11:27:46 mauro rtkit-daemon[1346]: Supervising 4 threads of 2 processes of 2 users.
Jun 10 11:27:46 mauro rtkit-daemon[1346]: Sucessfully made thread 1537 of process 1529 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:27:46 mauro rtkit-daemon[1346]: Supervising 5 threads of 2 processes of 2 users.
Jun 10 11:27:46 mauro rtkit-daemon[1346]: Sucessfully made thread 1540 of process 1529 (n/a) owned by '1000' RT at priority 5.
Jun 10 11:27:46 mauro rtkit-daemon[1346]: Supervising 6 threads of 2 processes of 2 users.
Jun 10 11:27:47 mauro rtkit-daemon[1346]: Sucessfully made thread 1549 of process 1549 (n/a) owned by '1000' high priority at nice level -11.
Jun 10 11:27:47 mauro rtkit-daemon[1346]: Supervising 7 threads of 3 processes of 2 users.
Jun 10 11:27:47 mauro pulseaudio[1549]: pid.c: Daemon already running.
Jun 10 11:28:50 mauro AptDaemon: INFO: Initializing daemon
Jun 10 11:30:19 mauro avahi-daemon[951]: Invalid query packet.
Jun 10 11:30:59 mauro avahi-daemon[951]: last message repeated 7 times
Jun 10 11:34:50 mauro AptDaemon: INFO: Quiting due to inactivity
Jun 10 11:34:50 mauro AptDaemon: INFO: Shutdown was requested
Jun 10 12:17:01 mauro CRON[1919]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

---

### Post by Vladlenin5000 on 2014-06-10
Hi, welcome.

10.04 (desktop) is 'End of Life' while 10.04 (server) is still getting updates. You still get updates for all the common packeges between server and desktop but only those. This is a sure recipe for breaking things.

Bottom line: Install 14.04.

---

### Post by Bijan_Yusefi on 2014-06-10
It seems like The OS/S.O cant communicate with you directly to give you prompts.
In a sense it thinks your not answering it's requests, so it just goes and does what its programmed to do and make a choice of terminating and ending session.

---

### Post by Vladlenin5000 on 2014-06-10
> **Bijan_Yusefi said:**
> It seems like The OS/S.O cant communicate with you directly to give you prompts.
In a sense it thinks your not answering it's requests, so it just goes and does what its programmed to do and make a choice of terminating and ending session.

Sorry but no... The problem was already explained in my previous post. There are lots of similar cases discussed recently in this forum, just search 10.04 and/or Lucid if you need a clearer picture.
Again, please stop using a EoL version, it'll only get worse.

---

