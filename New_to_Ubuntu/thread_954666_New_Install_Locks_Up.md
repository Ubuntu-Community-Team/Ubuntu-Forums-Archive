---
title: "New Install Locks Up"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by the_duality on 2008-10-21
Hey everyone. Just started my Computer Science degree and as such I installed ubuntu on my main machine to use for Java programming etc. My problem is this:

The install went fine - but the problems occur when I connect to the web. The connection works fine, but then as soon as I try to update Ubuntu or the repository listings, the machine hangs. Accessing certain websites does the same thing. Usually half way through downloading the update packages, the machine locks up and I have to perform a hard reset. Everything usually works fine until I try to download something like that.

Any ideas or help would be appreciated, I would quite like to work in Linux (as programs I write have to compile and run in Linux as well as Windows - so having my own linux install is handy).

I have installed it a couple of times on my laptop with no issues as such, but it does not seem to like my desktop. I am not sure what is causing the problem, so I don't know what you need me to post to help fix it. Any ideas and help would be greatly appreciated!

PS. Trying to download the ATI card driver (via the prompt in ubuntu about un-supported drivers) returns a 404 not found error when trying to download the package. Any help there also would be great :)

Regards,

Duality

---

### Post by Titan8990 on 2008-10-21
Report the results of the following:

cat /var/log/syslog

cat /var/log/syslog.0


Have you tried envyng for your drivers?


sudo apt-get install envyng-gtk

---

### Post by the_duality on 2008-10-21
Syslog.0 did not exist, but here is the output from syslog:


```
Oct 20 16:53:51 matt-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct 20 16:53:51 matt-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Oct 20 16:53:51 matt-desktop kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Oct 20 16:53:51 matt-desktop kernel: Symbols match kernel version 2.6.24.
Oct 20 16:53:51 matt-desktop kernel: Loaded 19345 symbols from 98 modules.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] 896MB LOWMEM available.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] found SMP MP-table at 000f5360
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Zone PFN ranges:
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   DMA             0 ->     4096
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   HighMem    229376 ->   524000
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]     0:        0 ->   524000
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] On node 0 totalpages: 524000
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
Oct 20 16:53:51 matt-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] DMI 2.4 present.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6CF0 checksum 0
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: RSDP 000F6CF0, 0014 (r0 GBT   )
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: DSDT 7FEE3180, 49F4 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: HPET 7FEE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: MCFG 7FEE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: APIC 7FEE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: SSDT 7FEE7DC0, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: SSDT 7FEE8250, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519907
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Kernel command line: root=UUID=6c75aea6-38fc-4a0b-a141-d73c7506188f ro quiet splash
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Initializing CPU#0
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 20 16:53:51 matt-desktop kernel: [    0.000000] Detected 1809.044 MHz processor.
Oct 20 16:53:51 matt-desktop kernel: [   20.936440] Console: colour VGA+ 80x25
Oct 20 16:53:51 matt-desktop kernel: [   20.936444] console [tty0] enabled
Oct 20 16:53:51 matt-desktop kernel: [   20.936667] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 20 16:53:51 matt-desktop kernel: [   20.936927] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 20 16:53:51 matt-desktop kernel: [   21.024944] Memory: 2065688k/2096000k available (2177k kernel code, 29084k reserved, 1006k data, 368k init, 1178496k highmem)
Oct 20 16:53:51 matt-desktop kernel: [   21.024950] virtual kernel memory layout:
Oct 20 16:53:51 matt-desktop kernel: [   21.024951]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 20 16:53:51 matt-desktop kernel: [   21.024952]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 20 16:53:51 matt-desktop kernel: [   21.024953]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 20 16:53:51 matt-desktop kernel: [   21.024954]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 20 16:53:51 matt-desktop kernel: [   21.024955]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 20 16:53:51 matt-desktop kernel: [   21.024956]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Oct 20 16:53:51 matt-desktop kernel: [   21.024957]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Oct 20 16:53:51 matt-desktop kernel: [   21.024960] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 20 16:53:51 matt-desktop kernel: [   21.024998] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Oct 20 16:53:51 matt-desktop kernel: [   21.025134] hpet clockevent registered
Oct 20 16:53:51 matt-desktop kernel: [   21.105130] Calibrating delay using timer specific routine.. 3620.93 BogoMIPS (lpj=7241860)
Oct 20 16:53:51 matt-desktop kernel: [   21.105156] Security Framework initialized
Oct 20 16:53:51 matt-desktop kernel: [   21.105160] SELinux:  Disabled at boot.
Oct 20 16:53:51 matt-desktop kernel: [   21.105170] AppArmor: AppArmor initialized
Oct 20 16:53:51 matt-desktop kernel: [   21.105173] Failure registering capabilities with primary security module.
Oct 20 16:53:51 matt-desktop kernel: [   21.105180] Mount-cache hash table entries: 512
Oct 20 16:53:51 matt-desktop kernel: [   21.105282] Initializing cgroup subsys ns
Oct 20 16:53:51 matt-desktop kernel: [   21.105285] Initializing cgroup subsys cpuacct
Oct 20 16:53:51 matt-desktop kernel: [   21.105294] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Oct 20 16:53:51 matt-desktop kernel: [   21.105301] monitor/mwait feature present.
Oct 20 16:53:51 matt-desktop kernel: [   21.105302] using mwait in idle threads.
Oct 20 16:53:51 matt-desktop kernel: [   21.105306] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 20 16:53:51 matt-desktop kernel: [   21.105308] CPU: L2 cache: 2048K
Oct 20 16:53:51 matt-desktop kernel: [   21.105310] CPU: Physical Processor ID: 0
Oct 20 16:53:51 matt-desktop kernel: [   21.105311] CPU: Processor Core ID: 0
Oct 20 16:53:51 matt-desktop kernel: [   21.105313] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Oct 20 16:53:51 matt-desktop kernel: [   21.105321] Compat vDSO mapped to ffffe000.
Oct 20 16:53:51 matt-desktop kernel: [   21.105331] Checking 'hlt' instruction... OK.
Oct 20 16:53:51 matt-desktop kernel: [   21.121584] SMP alternatives: switching to UP code
Oct 20 16:53:51 matt-desktop kernel: [   21.123149] Early unpacking initramfs... done
Oct 20 16:53:51 matt-desktop kernel: [   21.453982] ACPI: Core revision 20070126
Oct 20 16:53:51 matt-desktop kernel: [   21.454020] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 20 16:53:51 matt-desktop kernel: [   21.579626] CPU0: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
Oct 20 16:53:51 matt-desktop kernel: [   21.579643] SMP alternatives: switching to SMP code
Oct 20 16:53:51 matt-desktop kernel: [   21.580363] Booting processor 1/1 eip 3000
Oct 20 16:53:51 matt-desktop kernel: [   21.590525] Initializing CPU#1
Oct 20 16:53:51 matt-desktop kernel: [   21.669062] Calibrating delay using timer specific routine.. 3618.00 BogoMIPS (lpj=7236015)
Oct 20 16:53:51 matt-desktop kernel: [   21.669068] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Oct 20 16:53:51 matt-desktop kernel: [   21.669073] monitor/mwait feature present.
Oct 20 16:53:51 matt-desktop kernel: [   21.669076] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 20 16:53:51 matt-desktop kernel: [   21.669078] CPU: L2 cache: 2048K
Oct 20 16:53:51 matt-desktop kernel: [   21.669080] CPU: Physical Processor ID: 0
Oct 20 16:53:51 matt-desktop kernel: [   21.669081] CPU: Processor Core ID: 1
Oct 20 16:53:51 matt-desktop kernel: [   21.669082] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Oct 20 16:53:51 matt-desktop kernel: [   21.669586] CPU1: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
Oct 20 16:53:51 matt-desktop kernel: [   21.669606] Total of 2 processors activated (7238.93 BogoMIPS).
Oct 20 16:53:51 matt-desktop kernel: [   21.669749] ENABLING IO-APIC IRQs
Oct 20 16:53:51 matt-desktop kernel: [   21.669914] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 20 16:53:51 matt-desktop kernel: [   21.817149] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 20 16:53:51 matt-desktop kernel: [   21.837162] Brought up 2 CPUs
Oct 20 16:53:51 matt-desktop kernel: [   21.837184] CPU0 attaching sched-domain:
Oct 20 16:53:51 matt-desktop kernel: [   21.837187]  domain 0: span 03
Oct 20 16:53:51 matt-desktop kernel: [   21.837188]   groups: 01 02
Oct 20 16:53:51 matt-desktop kernel: [   21.837191] CPU1 attaching sched-domain:
Oct 20 16:53:51 matt-desktop kernel: [   21.837193]  domain 0: span 03
Oct 20 16:53:51 matt-desktop kernel: [   21.837194]   groups: 02 01
Oct 20 16:53:51 matt-desktop kernel: [   21.837412] net_namespace: 64 bytes
Oct 20 16:53:51 matt-desktop kernel: [   21.837424] Booting paravirtualized kernel on bare hardware
Oct 20 16:53:51 matt-desktop kernel: [   21.837838] Time: 16:53:34  Date: 10/20/08
Oct 20 16:53:51 matt-desktop kernel: [   21.837863] NET: Registered protocol family 16
Oct 20 16:53:51 matt-desktop kernel: [   21.838047] EISA bus registered
Oct 20 16:53:51 matt-desktop kernel: [   21.838051] ACPI: bus type pci registered
Oct 20 16:53:51 matt-desktop kernel: [   21.844074] PCI: PCI BIOS revision 3.00 entry at 0xfb430, last bus=5
Oct 20 16:53:51 matt-desktop kernel: [   21.844076] PCI: Using configuration type 1
Oct 20 16:53:51 matt-desktop kernel: [   21.844100] Setting up standard PCI resources
Oct 20 16:53:51 matt-desktop kernel: [   21.844790] mtrr: your CPUs had inconsistent variable MTRR settings
Oct 20 16:53:51 matt-desktop kernel: [   21.844792] mtrr: probably your BIOS does not setup all CPUs.
Oct 20 16:53:51 matt-desktop kernel: [   21.844794] mtrr: corrected configuration.
Oct 20 16:53:51 matt-desktop kernel: [   21.846049] ACPI: EC: Look up EC in DSDT
Oct 20 16:53:51 matt-desktop kernel: [   21.850000] ACPI: Interpreter enabled
Oct 20 16:53:51 matt-desktop kernel: [   21.850006] ACPI: (supports S0 S1 S4 S5)
Oct 20 16:53:51 matt-desktop kernel: [   21.850024] ACPI: Using IOAPIC for interrupt routing
Oct 20 16:53:51 matt-desktop kernel: [   21.854420] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 20 16:53:51 matt-desktop kernel: [   21.855077] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Oct 20 16:53:51 matt-desktop kernel: [   21.855081] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Oct 20 16:53:51 matt-desktop kernel: [   21.855951] PCI: Transparent bridge - 0000:00:1e.0
Oct 20 16:53:51 matt-desktop kernel: [   21.855983] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 20 16:53:51 matt-desktop kernel: [   21.856121] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Oct 20 16:53:51 matt-desktop kernel: [   21.856192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Oct 20 16:53:51 matt-desktop kernel: [   21.856263] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Oct 20 16:53:51 matt-desktop kernel: [   21.856332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Oct 20 16:53:51 matt-desktop kernel: [   21.866758] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 20 16:53:51 matt-desktop kernel: [   21.866853] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 16:53:51 matt-desktop kernel: [   21.866951] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Oct 20 16:53:51 matt-desktop kernel: [   21.867043] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Oct 20 16:53:51 matt-desktop kernel: [   21.867136] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 16:53:51 matt-desktop kernel: [   21.867229] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
Oct 20 16:53:51 matt-desktop kernel: [   21.867321] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Oct 20 16:53:51 matt-desktop kernel: [   21.867414] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 16:53:51 matt-desktop kernel: [   21.867541] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 20 16:53:51 matt-desktop kernel: [   21.867571] pnp: PnP ACPI init
Oct 20 16:53:51 matt-desktop kernel: [   21.867578] ACPI: bus type pnp registered
Oct 20 16:53:51 matt-desktop kernel: [   21.869705] pnpacpi: exceeded the max number of mem resources: 12
Oct 20 16:53:51 matt-desktop kernel: [   21.869845] pnp: PnP ACPI: found 12 devices
Oct 20 16:53:51 matt-desktop kernel: [   21.869847] ACPI: ACPI bus type pnp unregistered
Oct 20 16:53:51 matt-desktop kernel: [   21.869851] PnPBIOS: Disabled by ACPI PNP
Oct 20 16:53:51 matt-desktop kernel: [   21.870071] PCI: Using ACPI for IRQ routing
Oct 20 16:53:51 matt-desktop kernel: [   21.870074] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 20 16:53:51 matt-desktop kernel: [   21.937304] NET: Registered protocol family 8
Oct 20 16:53:51 matt-desktop kernel: [   21.937307] NET: Registered protocol family 20
Oct 20 16:53:51 matt-desktop kernel: [   21.937350] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 20 16:53:51 matt-desktop kernel: [   21.937356] hpet0: 3 64-bit timers, 14318180 Hz
Oct 20 16:53:51 matt-desktop kernel: [   21.938392] AppArmor: AppArmor Filesystem Enabled
Oct 20 16:53:51 matt-desktop kernel: [   21.941210] Time: tsc clocksource has been installed.
Oct 20 16:53:51 matt-desktop kernel: [   21.941225] Switched to high resolution mode on CPU 0
Oct 20 16:53:51 matt-desktop kernel: [   21.941319] Switched to high resolution mode on CPU 1
Oct 20 16:53:51 matt-desktop kernel: [   21.954262] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954266] system 00:01: ioport range 0x290-0x29f has been reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954270] system 00:01: ioport range 0x800-0x87f has been reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954273] system 00:01: ioport range 0x290-0x294 has been reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954277] system 00:01: ioport range 0x880-0x88f has been reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954290] system 00:08: ioport range 0x400-0x4bf could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954299] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954307] system 00:0a: iomem range 0xcf600-0xcffff has been reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954312] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954315] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954319] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954323] system 00:0a: iomem range 0x7fee0000-0x7fefffff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954327] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954331] system 00:0a: iomem range 0x100000-0x7fedffff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954335] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954339] system 00:0a: iomem range 0xfed10000-0xfed1dfff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954343] system 00:0a: iomem range 0xfed20000-0xfed8ffff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954347] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.954351] system 00:0a: iomem range 0xffb00000-0xffb7ffff could not be reserved
Oct 20 16:53:51 matt-desktop kernel: [   21.984809] PCI: Bridge: 0000:00:01.0
Oct 20 16:53:51 matt-desktop kernel: [   21.984812]   IO window: 8000-8fff
Oct 20 16:53:51 matt-desktop kernel: [   21.984815]   MEM window: f4000000-f5ffffff
Oct 20 16:53:51 matt-desktop kernel: [   21.984818]   PREFETCH window: e0000000-efffffff
Oct 20 16:53:51 matt-desktop kernel: [   21.984821] PCI: Bridge: 0000:00:1c.0
Oct 20 16:53:51 matt-desktop kernel: [   21.984824]   IO window: 7000-7fff
Oct 20 16:53:51 matt-desktop kernel: [   21.984827]   MEM window: disabled.
Oct 20 16:53:51 matt-desktop kernel: [   21.984831]   PREFETCH window: disabled.
Oct 20 16:53:51 matt-desktop kernel: [   21.984835] PCI: Bridge: 0000:00:1c.3
Oct 20 16:53:51 matt-desktop kernel: [   21.984837]   IO window: 9000-afff
Oct 20 16:53:51 matt-desktop kernel: [   21.984841]   MEM window: f8000000-f80fffff
Oct 20 16:53:51 matt-desktop kernel: [   21.984844]   PREFETCH window: disabled.
Oct 20 16:53:51 matt-desktop kernel: [   21.984849] PCI: Bridge: 0000:00:1c.4
Oct 20 16:53:51 matt-desktop kernel: [   21.984851]   IO window: b000-bfff
Oct 20 16:53:51 matt-desktop kernel: [   21.984855]   MEM window: f6000000-f7ffffff
Oct 20 16:53:51 matt-desktop kernel: [   21.984859]   PREFETCH window: 80000000-800fffff
Oct 20 16:53:51 matt-desktop kernel: [   21.984863] PCI: Bridge: 0000:00:1e.0
Oct 20 16:53:51 matt-desktop kernel: [   21.984864]   IO window: disabled.
Oct 20 16:53:51 matt-desktop kernel: [   21.984868]   MEM window: f8100000-f81fffff
Oct 20 16:53:51 matt-desktop kernel: [   21.984871]   PREFETCH window: disabled.
Oct 20 16:53:51 matt-desktop kernel: [   21.984885] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 16:53:51 matt-desktop kernel: [   21.984890] PCI: Setting latency timer of device 0000:00:01.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   21.984907] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 16:53:51 matt-desktop kernel: [   21.984912] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   21.984928] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Oct 20 16:53:51 matt-desktop kernel: [   21.984933] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 20 16:53:51 matt-desktop kernel: [   21.984948] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 16:53:51 matt-desktop kernel: [   21.984953] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Oct 20 16:53:51 matt-desktop kernel: [   21.984962] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   21.984972] NET: Registered protocol family 2
Oct 20 16:53:51 matt-desktop kernel: [   22.022277] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 20 16:53:51 matt-desktop kernel: [   22.022536] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 20 16:53:51 matt-desktop kernel: [   22.022936] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 20 16:53:51 matt-desktop kernel: [   22.023144] TCP: Hash tables configured (established 131072 bind 65536)
Oct 20 16:53:51 matt-desktop kernel: [   22.023147] TCP reno registered
Oct 20 16:53:51 matt-desktop kernel: [   22.034367] checking if image is initramfs... it is
Oct 20 16:53:51 matt-desktop kernel: [   22.686984] Freeing initrd memory: 7702k freed
Oct 20 16:53:51 matt-desktop kernel: [   22.687736] audit: initializing netlink socket (disabled)
Oct 20 16:53:51 matt-desktop kernel: [   22.687749] audit(1224521614.416:1): initialized
Oct 20 16:53:51 matt-desktop kernel: [   22.687955] highmem bounce pool size: 64 pages
Oct 20 16:53:51 matt-desktop kernel: [   22.689865] VFS: Disk quotas dquot_6.5.1
Oct 20 16:53:51 matt-desktop kernel: [   22.689935] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 20 16:53:51 matt-desktop kernel: [   22.690064] io scheduler noop registered
Oct 20 16:53:51 matt-desktop kernel: [   22.690066] io scheduler anticipatory registered
Oct 20 16:53:51 matt-desktop kernel: [   22.690068] io scheduler deadline registered
Oct 20 16:53:51 matt-desktop kernel: [   22.690081] io scheduler cfq registered (default)
Oct 20 16:53:51 matt-desktop kernel: [   22.690187] Boot video device is 0000:01:00.0
Oct 20 16:53:51 matt-desktop kernel: [   22.690292] PCI: Setting latency timer of device 0000:00:01.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   22.690326] assign_interrupt_mode Found MSI capability
Oct 20 16:53:51 matt-desktop kernel: [   22.690355] Allocate Port Service[0000:00:01.0:pcie00]
Oct 20 16:53:51 matt-desktop kernel: [   22.690428] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   22.690466] assign_interrupt_mode Found MSI capability
Oct 20 16:53:51 matt-desktop kernel: [   22.690497] Allocate Port Service[0000:00:1c.0:pcie00]
Oct 20 16:53:51 matt-desktop kernel: [   22.690528] Allocate Port Service[0000:00:1c.0:pcie02]
Oct 20 16:53:51 matt-desktop kernel: [   22.690606] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 20 16:53:51 matt-desktop kernel: [   22.690643] assign_interrupt_mode Found MSI capability
Oct 20 16:53:51 matt-desktop kernel: [   22.690674] Allocate Port Service[0000:00:1c.3:pcie00]
Oct 20 16:53:51 matt-desktop kernel: [   22.690705] Allocate Port Service[0000:00:1c.3:pcie02]
Oct 20 16:53:51 matt-desktop kernel: [   22.690781] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Oct 20 16:53:51 matt-desktop kernel: [   22.690819] assign_interrupt_mode Found MSI capability
Oct 20 16:53:51 matt-desktop kernel: [   22.690849] Allocate Port Service[0000:00:1c.4:pcie00]
Oct 20 16:53:51 matt-desktop kernel: [   22.690880] Allocate Port Service[0000:00:1c.4:pcie02]
Oct 20 16:53:51 matt-desktop kernel: [   22.691109] isapnp: Scanning for PnP cards...
Oct 20 16:53:51 matt-desktop kernel: [   23.044315] isapnp: No Plug & Play device found
Oct 20 16:53:51 matt-desktop kernel: [   23.068492] Real Time Clock Driver v1.12ac
Oct 20 16:53:51 matt-desktop kernel: [   23.068601] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 20 16:53:51 matt-desktop kernel: [   23.068720] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 16:53:51 matt-desktop kernel: [   23.069278] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 16:53:51 matt-desktop kernel: [   23.070004] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 20 16:53:51 matt-desktop kernel: [   23.070346] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 20 16:53:51 matt-desktop kernel: [   23.070482] PNP: No PS/2 controller found. Probing ports directly.
Oct 20 16:53:51 matt-desktop kernel: [   23.070822] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 20 16:53:51 matt-desktop kernel: [   23.070829] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 20 16:53:51 matt-desktop kernel: [   23.093360] mice: PS/2 mouse device common for all mice
Oct 20 16:53:51 matt-desktop kernel: [   23.093468] EISA: Probing bus 0 at eisa.0
Oct 20 16:53:51 matt-desktop kernel: [   23.093491] Cannot allocate resource for EISA slot 7
Oct 20 16:53:51 matt-desktop kernel: [   23.093493] Cannot allocate resource for EISA slot 8
Oct 20 16:53:51 matt-desktop kernel: [   23.093495] EISA: Detected 0 cards.
Oct 20 16:53:51 matt-desktop kernel: [   23.093497] cpuidle: using governor ladder
Oct 20 16:53:51 matt-desktop kernel: [   23.093499] cpuidle: using governor menu
Oct 20 16:53:51 matt-desktop kernel: [   23.093574] NET: Registered protocol family 1
Oct 20 16:53:51 matt-desktop kernel: [   23.093598] Using IPI No-Shortcut mode
Oct 20 16:53:51 matt-desktop kernel: [   23.093625] registered taskstats version 1
Oct 20 16:53:51 matt-desktop kernel: [   23.093736]   Magic number: 12:563:894
Oct 20 16:53:51 matt-desktop kernel: [   23.093761]   hash matches device ptyy4
Oct 20 16:53:51 matt-desktop kernel: [   23.093789] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 20 16:53:51 matt-desktop kernel: [   23.093791] EDD information not available.
Oct 20 16:53:51 matt-desktop kernel: [   23.093946] Freeing unused kernel memory: 368k freed
Oct 20 16:53:51 matt-desktop kernel: [   24.294372] fuse init (API version 7.9)
Oct 20 16:53:51 matt-desktop kernel: [   24.312561] ACPI: Processor [CPU0] (supports 2 throttling states)
Oct 20 16:53:51 matt-desktop kernel: [   24.312684] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
Oct 20 16:53:51 matt-desktop kernel: [   24.312825] ACPI: Processor [CPU1] (supports 2 throttling states)
Oct 20 16:53:51 matt-desktop kernel: [   24.312839] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 20 16:53:51 matt-desktop kernel: [   24.312849] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 20 16:53:51 matt-desktop kernel: [   24.429614] usbcore: registered new interface driver usbfs
Oct 20 16:53:51 matt-desktop kernel: [   24.429636] usbcore: registered new interface driver hub
Oct 20 16:53:51 matt-desktop kernel: [   24.429661] usbcore: registered new device driver usb
Oct 20 16:53:51 matt-desktop kernel: [   24.430677] USB Universal Host Controller Interface driver v3.0
Oct 20 16:53:51 matt-desktop kernel: [   24.430719] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 16:53:51 matt-desktop kernel: [   24.430729] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   24.430733] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Oct 20 16:53:51 matt-desktop kernel: [   24.430952] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Oct 20 16:53:51 matt-desktop kernel: [   24.430979] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c000
Oct 20 16:53:51 matt-desktop kernel: [   24.431096] usb usb1: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   24.431119] hub 1-0:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   24.431123] hub 1-0:1.0: 2 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   24.533950] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Oct 20 16:53:51 matt-desktop kernel: [   24.533961] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Oct 20 16:53:51 matt-desktop kernel: [   24.533965] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Oct 20 16:53:51 matt-desktop kernel: [   24.533989] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Oct 20 16:53:51 matt-desktop kernel: [   24.534014] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000c400
Oct 20 16:53:51 matt-desktop kernel: [   24.534123] usb usb2: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   24.534150] hub 2-0:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   24.534155] hub 2-0:1.0: 2 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   24.622133] SCSI subsystem initialized
Oct 20 16:53:51 matt-desktop kernel: [   24.637930] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Oct 20 16:53:51 matt-desktop kernel: [   24.637942] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   24.637946] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 20 16:53:51 matt-desktop kernel: [   24.637972] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Oct 20 16:53:51 matt-desktop kernel: [   24.637999] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000c800
Oct 20 16:53:51 matt-desktop kernel: [   24.638105] usb usb3: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   24.638127] hub 3-0:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   24.638132] hub 3-0:1.0: 2 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   24.658714] libata version 3.00 loaded.
Oct 20 16:53:51 matt-desktop kernel: [   24.741916] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 16:53:51 matt-desktop kernel: [   24.741930] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Oct 20 16:53:51 matt-desktop kernel: [   24.741934] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 20 16:53:51 matt-desktop kernel: [   24.741959] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Oct 20 16:53:51 matt-desktop kernel: [   24.741989] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000cc00
Oct 20 16:53:51 matt-desktop kernel: [   24.742097] usb usb4: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   24.742120] hub 4-0:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   24.742125] hub 4-0:1.0: 2 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   24.773850] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 20 16:53:51 matt-desktop kernel: [   24.845907] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Oct 20 16:53:51 matt-desktop kernel: [   24.845919] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Oct 20 16:53:51 matt-desktop kernel: [   24.845923] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 20 16:53:51 matt-desktop kernel: [   24.845946] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Oct 20 16:53:51 matt-desktop kernel: [   24.845972] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d000
Oct 20 16:53:51 matt-desktop kernel: [   24.846082] usb usb5: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   24.846106] hub 5-0:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   24.846112] hub 5-0:1.0: 2 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   24.940063] usb 1-2: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   24.949914] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
Oct 20 16:53:51 matt-desktop kernel: [   24.949928] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Oct 20 16:53:51 matt-desktop kernel: [   24.949931] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Oct 20 16:53:51 matt-desktop kernel: [   24.949954] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Oct 20 16:53:51 matt-desktop kernel: [   24.953852] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Oct 20 16:53:51 matt-desktop kernel: [   24.953858] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xf8205000
Oct 20 16:53:51 matt-desktop kernel: [   24.968795] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 20 16:53:51 matt-desktop kernel: [   24.968907] usb usb6: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   24.968932] hub 6-0:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   24.968938] hub 6-0:1.0: 4 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   25.073878] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Oct 20 16:53:51 matt-desktop kernel: [   25.073892] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Oct 20 16:53:51 matt-desktop kernel: [   25.073896] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 20 16:53:51 matt-desktop kernel: [   25.073919] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Oct 20 16:53:51 matt-desktop kernel: [   25.077833] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Oct 20 16:53:51 matt-desktop kernel: [   25.077839] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf8204000
Oct 20 16:53:51 matt-desktop kernel: [   25.092772] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 20 16:53:51 matt-desktop kernel: [   25.092887] usb usb7: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   25.092912] hub 7-0:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   25.092917] hub 7-0:1.0: 6 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   25.197085] ahci 0000:03:00.0: version 3.0
Oct 20 16:53:51 matt-desktop kernel: [   25.197114] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Oct 20 16:53:51 matt-desktop kernel: [   25.520762] usb 1-2: USB disconnect, address 2
Oct 20 16:53:51 matt-desktop kernel: [   25.520783] usbcore: registered new interface driver hiddev
Oct 20 16:53:51 matt-desktop kernel: [   25.760696] usb 1-2: new low speed USB device using uhci_hcd and address 3
Oct 20 16:53:51 matt-desktop kernel: [   25.932025] usb 1-2: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   26.172672] usb 7-5: new high speed USB device using ehci_hcd and address 2
Oct 20 16:53:51 matt-desktop kernel: [   26.200671] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Oct 20 16:53:51 matt-desktop kernel: [   26.200676] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Oct 20 16:53:51 matt-desktop kernel: [   26.200684] PCI: Setting latency timer of device 0000:03:00.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   26.200847] scsi0 : ahci
Oct 20 16:53:51 matt-desktop kernel: [   26.201019] scsi1 : ahci
Oct 20 16:53:51 matt-desktop kernel: [   26.201080] ata1: SATA max UDMA/133 abar m8192@0xf8000000 port 0xf8000100 irq 17
Oct 20 16:53:51 matt-desktop kernel: [   26.201084] ata2: SATA max UDMA/133 abar m8192@0xf8000000 port 0xf8000180 irq 17
Oct 20 16:53:51 matt-desktop kernel: [   26.305052] usb 7-5: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   26.305207] hub 7-5:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   26.305301] hub 7-5:1.0: 4 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   26.520616] ata1: SATA link down (SStatus 0 SControl 300)
Oct 20 16:53:51 matt-desktop kernel: [   26.661108] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input1
Oct 20 16:53:51 matt-desktop kernel: [   26.680652] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1a.0-2
Oct 20 16:53:51 matt-desktop kernel: [   26.840572] ata2: SATA link down (SStatus 0 SControl 300)
Oct 20 16:53:51 matt-desktop kernel: [   26.840635] ata_piix 0000:00:1f.2: version 2.12
Oct 20 16:53:51 matt-desktop kernel: [   26.840642] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Oct 20 16:53:51 matt-desktop kernel: [   26.852645] usb 7-5.4: new full speed USB device using ehci_hcd and address 4
Oct 20 16:53:51 matt-desktop kernel: [   26.941882] usb 7-5.4: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   26.942231] usbcore: registered new interface driver usbhid
Oct 20 16:53:51 matt-desktop kernel: [   26.942235] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 20 16:53:51 matt-desktop kernel: [   26.997587] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 16:53:51 matt-desktop kernel: [   26.997627] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Oct 20 16:53:51 matt-desktop kernel: [   26.997684] scsi2 : ata_piix
Oct 20 16:53:51 matt-desktop kernel: [   26.997872] scsi3 : ata_piix
Oct 20 16:53:51 matt-desktop kernel: [   26.998339] ata3: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Oct 20 16:53:51 matt-desktop kernel: [   26.998342] ata4: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Oct 20 16:53:51 matt-desktop kernel: [   27.172691] ata3.00: HPA unlocked: 488279137 -> 488281250, native 488281250
Oct 20 16:53:51 matt-desktop kernel: [   27.172699] ata3.00: ATA-7: Maxtor 7L250S0, BANC1G10, max UDMA/133
Oct 20 16:53:51 matt-desktop kernel: [   27.172704] ata3.00: 488281250 sectors, multi 16: LBA48 NCQ (not used)
Oct 20 16:53:51 matt-desktop kernel: [   27.181567] usb 5-2: new full speed USB device using uhci_hcd and address 2
Oct 20 16:53:51 matt-desktop kernel: [   27.190720] ata3.00: configured for UDMA/133
Oct 20 16:53:51 matt-desktop kernel: [   27.355299] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 7L250S0   BANC PQ: 0 ANSI: 5
Oct 20 16:53:51 matt-desktop kernel: [   27.355369] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Oct 20 16:53:51 matt-desktop kernel: [   27.355393] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 16:53:51 matt-desktop kernel: [   27.355421] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Oct 20 16:53:51 matt-desktop kernel: [   27.355464] scsi4 : ata_piix
Oct 20 16:53:51 matt-desktop kernel: [   27.355504] scsi5 : ata_piix
Oct 20 16:53:51 matt-desktop kernel: [   27.355900] ata5: SATA max UDMA/133 cmd 0xd800 ctl 0xdc00 bmdma 0xe800 irq 17
Oct 20 16:53:51 matt-desktop kernel: [   27.355903] ata6: SATA max UDMA/133 cmd 0xe000 ctl 0xe400 bmdma 0xe808 irq 17
Oct 20 16:53:51 matt-desktop kernel: [   27.362950] usb 5-2: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   27.368861] hub 5-2:1.0: USB hub found
Oct 20 16:53:51 matt-desktop kernel: [   27.369826] hub 5-2:1.0: 3 ports detected
Oct 20 16:53:51 matt-desktop kernel: [   27.681804] usb 5-2.1: new full speed USB device using uhci_hcd and address 3
Oct 20 16:53:51 matt-desktop kernel: [   27.683241] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
Oct 20 16:53:51 matt-desktop kernel: [   27.683248] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
Oct 20 16:53:51 matt-desktop kernel: [   27.683281] PCI: Setting latency timer of device 0000:03:00.1 to 64
Oct 20 16:53:51 matt-desktop kernel: [   27.683295] ACPI: PCI interrupt for device 0000:03:00.1 disabled
Oct 20 16:53:51 matt-desktop kernel: [   27.689167] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
Oct 20 16:53:51 matt-desktop kernel: [   27.689200] PCI: Setting latency timer of device 0000:03:00.1 to 64
Oct 20 16:53:51 matt-desktop kernel: [   27.690879] scsi6 : pata_jmicron
Oct 20 16:53:51 matt-desktop kernel: [   27.690932] Driver 'sd' needs updating - please use bus_type methods
Oct 20 16:53:51 matt-desktop kernel: [   27.691002] sd 2:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Oct 20 16:53:51 matt-desktop kernel: [   27.691014] sd 2:0:0:0: [sda] Write Protect is off
Oct 20 16:53:51 matt-desktop kernel: [   27.691016] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 20 16:53:51 matt-desktop kernel: [   27.691031] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 16:53:51 matt-desktop kernel: [   27.691077] sd 2:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Oct 20 16:53:51 matt-desktop kernel: [   27.691087] sd 2:0:0:0: [sda] Write Protect is off
Oct 20 16:53:51 matt-desktop kernel: [   27.691089] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 20 16:53:51 matt-desktop kernel: [   27.691104] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 16:53:51 matt-desktop kernel: [   27.691107]  sda:<6>scsi7 : pata_jmicron
Oct 20 16:53:51 matt-desktop kernel: [   27.691667] ata7: PATA max UDMA/100 cmd 0x9000 ctl 0x9400 bmdma 0xa000 irq 16
Oct 20 16:53:51 matt-desktop kernel: [   27.691670] ata8: PATA max UDMA/100 cmd 0x9800 ctl 0x9c00 bmdma 0xa008 irq 16
Oct 20 16:53:51 matt-desktop kernel: [   27.712070]  sda1 sda2 sda3 sda4
Oct 20 16:53:51 matt-desktop kernel: [   27.734164] sd 2:0:0:0: [sda] Attached SCSI disk
Oct 20 16:53:51 matt-desktop kernel: [   27.739349] sd 2:0:0:0: Attached scsi generic sg0 type 0
Oct 20 16:53:51 matt-desktop kernel: [   27.818939] usb 5-2.1: configuration #1 chosen from 1 choice
Oct 20 16:53:51 matt-desktop kernel: [   27.827032] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2.1/5-2.1:1.0/input/input2
Oct 20 16:53:51 matt-desktop kernel: [   27.841444] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
Oct 20 16:53:51 matt-desktop kernel: [   27.850560] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2.1/5-2.1:1.1/input/input3
Oct 20 16:53:51 matt-desktop kernel: [   27.868523] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
Oct 20 16:53:51 matt-desktop kernel: [   28.025956] ata7.00: ATAPI: LITE-ON DVDRW LH-20A1H, LL0C, max UDMA/66
Oct 20 16:53:51 matt-desktop kernel: [   28.025973] ata7.00: limited to UDMA/33 due to 40-wire cable
Oct 20 16:53:51 matt-desktop kernel: [   28.037345] Attempting manual resume
Oct 20 16:53:51 matt-desktop kernel: [   28.037348] swsusp: Resume From Partition 8:3
Oct 20 16:53:51 matt-desktop kernel: [   28.037350] PM: Checking swsusp image.
Oct 20 16:53:51 matt-desktop kernel: [   28.037483] PM: Resume from disk failed.
Oct 20 16:53:51 matt-desktop kernel: [   28.068285] kjournald starting.  Commit interval 5 seconds
Oct 20 16:53:51 matt-desktop kernel: [   28.068297] EXT3-fs: mounted filesystem with ordered data mode.
Oct 20 16:53:51 matt-desktop kernel: [   28.212909] ata7.00: configured for UDMA/33
Oct 20 16:53:51 matt-desktop kernel: [   28.380923] scsi 6:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL0C PQ: 0 ANSI: 5
Oct 20 16:53:51 matt-desktop kernel: [   28.381022] scsi 6:0:0:0: Attached scsi generic sg1 type 5
Oct 20 16:53:51 matt-desktop kernel: [   33.963693] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 20 16:53:51 matt-desktop kernel: [   34.019668] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 20 16:53:51 matt-desktop kernel: [   34.071945] input: PC Speaker as /devices/platform/pcspkr/input/input4
Oct 20 16:53:51 matt-desktop kernel: [   34.118240] Linux agpgart interface v0.102
Oct 20 16:53:51 matt-desktop kernel: [   34.200612] iTCO_vendor_support: vendor-support=0
Oct 20 16:53:51 matt-desktop kernel: [   34.259992] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Oct 20 16:53:51 matt-desktop kernel: [   34.264314] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
Oct 20 16:53:51 matt-desktop kernel: [   34.264362] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 20 16:53:51 matt-desktop kernel: [   34.412178] input: Power Button (FF) as /devices/virtual/input/input5
Oct 20 16:53:51 matt-desktop kernel: [   34.439523] ACPI: Power Button (FF) [PWRF]
Oct 20 16:53:51 matt-desktop kernel: [   34.439612] input: Power Button (CM) as /devices/virtual/input/input6
Oct 20 16:53:51 matt-desktop kernel: [   34.471511] ACPI: Power Button (CM) [PWRB]
Oct 20 16:53:51 matt-desktop kernel: [   34.880091] parport_pc 00:07: reported by Plug and Play ACPI
Oct 20 16:53:51 matt-desktop kernel: [   34.880137] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Oct 20 16:53:51 matt-desktop kernel: [   35.443503] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 16:53:51 matt-desktop kernel: [   35.443516] PCI: Setting latency timer of device 0000:04:00.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   35.443542] sky2 0000:04:00.0: v1.20 addr 0xf7000000 irq 16 Yukon-EC Ultra (0xb4) rev 2
Oct 20 16:53:51 matt-desktop kernel: [   35.443920] sky2 eth0: addr 00:1a:4d:63:cd:b2
Oct 20 16:53:51 matt-desktop kernel: [   35.536452] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
Oct 20 16:53:51 matt-desktop kernel: [   35.536479] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Oct 20 16:53:51 matt-desktop kernel: [   35.688402] Driver 'sr' needs updating - please use bus_type methods
Oct 20 16:53:51 matt-desktop kernel: [   35.705018] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Oct 20 16:53:51 matt-desktop kernel: [   35.705022] Uniform CD-ROM driver Revision: 3.20
Oct 20 16:53:51 matt-desktop kernel: [   35.705074] sr 6:0:0:0: Attached scsi CD-ROM sr0
Oct 20 16:53:51 matt-desktop kernel: [   35.739995] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 20
Oct 20 16:53:51 matt-desktop kernel: [   35.749250] phy0: Selected rate control algorithm 'simple'
Oct 20 16:53:51 matt-desktop kernel: [   35.800358] Linux video capture interface: v2.00
Oct 20 16:53:51 matt-desktop kernel: [   35.838524] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
Oct 20 16:53:51 matt-desktop kernel: [   35.838694] usbcore: registered new interface driver gspca
Oct 20 16:53:51 matt-desktop kernel: [   35.838698] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Oct 20 16:53:51 matt-desktop kernel: [   35.869044] usbcore: registered new interface driver snd-usb-audio
Oct 20 16:53:51 matt-desktop kernel: [   35.916750] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
Oct 20 16:53:51 matt-desktop kernel: [   35.916792] usbcore: registered new interface driver sn9c102
Oct 20 16:53:51 matt-desktop kernel: [   36.850205] lp0: using parport0 (interrupt-driven).
Oct 20 16:53:51 matt-desktop kernel: [   36.897302] Adding 2000084k swap on /dev/sda3.  Priority:-1 extents:1 across:2000084k
Oct 20 16:53:51 matt-desktop kernel: [   37.449767] EXT3 FS on sda4, internal journal
Oct 20 16:53:51 matt-desktop kernel: [   38.414845] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 20 16:53:51 matt-desktop kernel: [   38.698414] No dock devices found.
Oct 20 16:53:51 matt-desktop NetworkManager: <info>  starting... 
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: Successfully dropped root privileges.
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: avahi-daemon 0.6.22 starting up.
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: Successfully called chroot().
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: Successfully dropped remaining capabilities.
Oct 20 16:53:51 matt-desktop avahi-daemon[5290]: chroot.c: open() failed: No such file or directory
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: Failed to open /etc/resolv.conf: Invalid argument
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: No service file found in /etc/avahi/services.
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: Network interface enumeration completed.
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 20 16:53:51 matt-desktop avahi-daemon[5289]: Server startup complete. Host name is matt-desktop.local. Local service cookie is 2536227442.
Oct 20 16:53:51 matt-desktop kernel: [   39.575516] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Oct 20 16:53:51 matt-desktop kernel: [   39.575520] apm: disabled - APM is not SMP safe.
Oct 20 16:53:51 matt-desktop kernel: [   39.719774] ppdev: user-space parallel port driver
Oct 20 16:53:52 matt-desktop kernel: [   39.791859] audit(1224518032.066:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5331 profile="/usr/sbin/cupsd" namespace="default"
Oct 20 16:53:52 matt-desktop dhcdbd: Started up.
Oct 20 16:53:53 matt-desktop kernel: [   41.284009] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
Oct 20 16:53:54 matt-desktop hcid[5574]: Bluetooth HCI daemon
Oct 20 16:53:54 matt-desktop kernel: [   42.242521] Bluetooth: Core ver 2.11
Oct 20 16:53:54 matt-desktop kernel: [   42.242628] NET: Registered protocol family 31
Oct 20 16:53:54 matt-desktop kernel: [   42.242632] Bluetooth: HCI device and connection manager initialized
Oct 20 16:53:54 matt-desktop kernel: [   42.242638] Bluetooth: HCI socket layer initialized
Oct 20 16:53:54 matt-desktop hcid[5574]: Starting SDP server
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'rt61pci'. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Deactivating device wlan0. 
Oct 20 16:53:54 matt-desktop kernel: [   42.271677] sky2 eth0: enabling interface
Oct 20 16:53:54 matt-desktop kernel: [   42.277965] Bluetooth: L2CAP ver 2.9
Oct 20 16:53:54 matt-desktop kernel: [   42.277970] Bluetooth: L2CAP socket layer initialized
Oct 20 16:53:54 matt-desktop hcid[5574]: Created local server at unix:abstract=/var/run/dbus-7ggdDFBXI5,guid=41fa301559558affe0bbf99648fca992
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Deactivating device eth0. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 20 16:53:54 matt-desktop NetworkManager: <debug> [1224518034.562983] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVDRW_LH_20A1H'). 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 20 16:53:54 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) started... 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 16:53:54 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 20 16:53:54 matt-desktop input[5595]: Bluetooth Input daemon
Oct 20 16:53:54 matt-desktop input[5595]: Registered input manager path:/org/bluez/input
Oct 20 16:53:54 matt-desktop audio[5611]: Bluetooth Audio daemon
Oct 20 16:53:54 matt-desktop NetworkManager: <debug> [1224518034.600508] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Oct 20 16:53:54 matt-desktop audio[5611]: Unix socket created: 5
Oct 20 16:53:54 matt-desktop audio[5611]: audio.conf: Key file does not have key 'Enable'
Oct 20 16:53:54 matt-desktop audio[5611]: audio.conf: Key file does not have key 'Disable'
Oct 20 16:53:54 matt-desktop kernel: [   42.344110] Bluetooth: RFCOMM socket layer initialized
Oct 20 16:53:54 matt-desktop kernel: [   42.344124] Bluetooth: RFCOMM TTY layer initialized
Oct 20 16:53:54 matt-desktop kernel: [   42.344126] Bluetooth: RFCOMM ver 1.8
Oct 20 16:53:54 matt-desktop audio[5611]: add_service_record: got record id 0x10000
Oct 20 16:53:54 matt-desktop audio[5611]: audio.conf: Key file does not have key 'Disable'
Oct 20 16:53:54 matt-desktop audio[5611]: audio.conf: Key file does not have group 'A2DP'
Oct 20 16:53:54 matt-desktop last message repeated 3 times
Oct 20 16:53:54 matt-desktop audio[5611]: SEP 0x806d790 registered: type:0 codec:0 seid:1
Oct 20 16:53:54 matt-desktop audio[5611]: add_service_record: got record id 0x10001
Oct 20 16:53:54 matt-desktop audio[5611]: add_service_record: got record id 0x10002
Oct 20 16:53:54 matt-desktop audio[5611]: add_service_record: got record id 0x10003
Oct 20 16:53:54 matt-desktop audio[5611]: Registered manager path:/org/bluez/audio
Oct 20 16:53:55 matt-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct 20 16:53:55 matt-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 20 16:53:55 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 20 16:53:55 matt-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Oct 20 16:53:55 matt-desktop NetworkManager: <info>  Deactivating device eth0. 
Oct 20 16:53:55 matt-desktop NetworkManager: <info>  Activation (eth0): cancelling... 
Oct 20 16:53:55 matt-desktop NetworkManager: <info>  Activation (eth0) cancellation handler scheduled... 
Oct 20 16:53:55 matt-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Oct 20 16:53:55 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 16:53:55 matt-desktop last message repeated 2 times
Oct 20 16:53:55 matt-desktop kernel: [   43.379248] NET: Registered protocol family 17
Oct 20 16:53:56 matt-desktop kernel: [   44.087041] [drm] Initialized drm 1.1.0 20060810
Oct 20 16:53:56 matt-desktop NetworkManager: <info>  Activation (eth0) cancellation handled. 
Oct 20 16:53:56 matt-desktop NetworkManager: <info>  Activation (eth0): cancelled. 
Oct 20 16:53:56 matt-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Oct 20 16:53:56 matt-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Oct 20 16:53:56 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 16:53:56 matt-desktop anacron[5746]: Anacron 2.3 started on 2008-10-20
Oct 20 16:53:56 matt-desktop anacron[5746]: Will run job `cron.daily' in 5 min.
Oct 20 16:53:56 matt-desktop anacron[5746]: Will run job `cron.weekly' in 10 min.
Oct 20 16:53:56 matt-desktop anacron[5746]: Will run job `cron.monthly' in 15 min.
Oct 20 16:53:56 matt-desktop anacron[5746]: Jobs will be executed sequentially
Oct 20 16:53:56 matt-desktop /usr/sbin/cron[5773]: (CRON) INFO (pidfile fd = 3)
Oct 20 16:53:56 matt-desktop /usr/sbin/cron[5774]: (CRON) STARTUP (fork ok)
Oct 20 16:53:56 matt-desktop /usr/sbin/cron[5774]: (CRON) INFO (Running @reboot jobs)
Oct 20 16:53:57 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Oct 20 16:54:01 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Oct 20 16:54:08 matt-desktop kernel: [   55.751936] NET: Registered protocol family 10
Oct 20 16:54:08 matt-desktop kernel: [   55.752171] lo: Disabled Privacy Extensions
Oct 20 16:54:08 matt-desktop kernel: [   55.752563] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 20 16:54:08 matt-desktop kernel: [   55.753016] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 20 16:54:08 matt-desktop pulseaudio[6034]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Oct 20 16:54:08 matt-desktop pulseaudio[6034]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct 20 16:54:10 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Oct 20 16:54:11 matt-desktop hcid[5574]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Oct 20 16:54:11 matt-desktop hcid[5574]: Default authorization agent (:1.20, /org/bluez/auth) registered
Oct 20 16:54:14 matt-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 20 16:54:14 matt-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 20 16:54:23 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct 20 16:54:28 matt-desktop dhclient: No DHCPOFFERS received.
Oct 20 16:54:28 matt-desktop avahi-autoipd(eth0)[6212]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 20 16:54:28 matt-desktop avahi-autoipd(eth0)[6212]: Successfully called chroot().
Oct 20 16:54:28 matt-desktop avahi-autoipd(eth0)[6212]: Successfully dropped root privileges.
Oct 20 16:54:28 matt-desktop avahi-autoipd(eth0)[6212]: Starting with address 169.254.8.140
Oct 20 16:54:33 matt-desktop avahi-autoipd(eth0)[6212]: Callout BIND, address 169.254.8.140 on interface eth0
Oct 20 16:54:33 matt-desktop avahi-daemon[5289]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.140.
Oct 20 16:54:33 matt-desktop avahi-daemon[5289]: New relevant interface eth0.IPv4 for mDNS.
Oct 20 16:54:33 matt-desktop avahi-daemon[5289]: Registering new address record for 169.254.8.140 on eth0.IPv4.
Oct 20 16:54:37 matt-desktop avahi-autoipd(eth0)[6212]: Successfully claimed IP address 169.254.8.140
Oct 20 16:54:43 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Oct 20 16:54:43 matt-desktop NetworkManager: <debug> [1224518083.549093] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'ASpunkMonkey' 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / ASpunkMonkey 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Deactivating device wlan0. 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Device wlan0 activation scheduled... 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0) started... 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'ASpunkMonkey' is encrypted, but NO valid key exists.  New key needed. 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'ASpunkMonkey'. 
Oct 20 16:54:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 16:54:58 matt-desktop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'ASpunkMonkey' received. 
Oct 20 16:54:58 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 16:54:58 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 16:54:58 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 16:54:58 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 16:54:58 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 16:54:58 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'ASpunkMonkey' is encrypted, and a key exists.  No new key needed. 
Oct 20 16:54:59 matt-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was '0' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 415370756e6b4d6f6e6b6579' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 16:55:00 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 16:55:01 matt-desktop kernel: [  109.016027] wlan0: Initial auth_alg=0
Oct 20 16:55:01 matt-desktop kernel: [  109.016035] wlan0: authenticate with AP 00:1f:9f:42:15:e5
Oct 20 16:55:01 matt-desktop kernel: [  109.018311] wlan0: RX authentication from 00:1f:9f:42:15:e5 (alg=0 transaction=2 status=0)
Oct 20 16:55:01 matt-desktop kernel: [  109.018316] wlan0: authenticated
Oct 20 16:55:01 matt-desktop kernel: [  109.018321] wlan0: associate with AP 00:1f:9f:42:15:e5
Oct 20 16:55:01 matt-desktop kernel: [  109.021523] wlan0: RX AssocResp from 00:1f:9f:42:15:e5 (capab=0x411 status=0 aid=2)
Oct 20 16:55:01 matt-desktop kernel: [  109.021528] wlan0: associated
Oct 20 16:55:01 matt-desktop kernel: [  109.024433] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 20 16:55:01 matt-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct 20 16:55:01 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'ASpunkMonkey'. 
Oct 20 16:55:01 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 20 16:55:01 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Oct 20 16:55:02 matt-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Oct 20 16:55:02 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 16:55:02 matt-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Oct 20 16:55:02 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 20 16:55:02 matt-desktop avahi-daemon[5289]: Registering new address record for fe80::21a:70ff:fe3c:8dbf on wlan0.*.
Oct 20 16:55:03 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 16:55:03 matt-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Oct 20 16:55:03 matt-desktop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:55:03 matt-desktop dhclient: DHCPOFFER of 192.168.1.67 from 192.168.1.254
Oct 20 16:55:03 matt-desktop dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 255.255.255.255 port 67
Oct 20 16:55:03 matt-desktop dhclient: DHCPACK of 192.168.1.67 from 192.168.1.254
Oct 20 16:55:03 matt-desktop avahi-daemon[5289]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 16:55:03 matt-desktop avahi-daemon[5289]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 16:55:03 matt-desktop avahi-daemon[5289]: Registering new address record for 192.168.1.67 on wlan0.IPv4.
Oct 20 16:55:03 matt-desktop dhclient: bound to 192.168.1.67 -- renewal in 38935 seconds.
Oct 20 16:55:03 matt-desktop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
Oct 20 16:55:03 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 20 16:55:03 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Oct 20 16:55:04 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Oct 20 16:55:04 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Oct 20 16:55:04 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Oct 20 16:55:04 matt-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 20 16:55:04 matt-desktop NetworkManager: <info>    address 192.168.1.67 
Oct 20 16:55:04 matt-desktop NetworkManager: <info>    netmask 255.255.255.0 
Oct 20 16:55:04 matt-desktop NetworkManager: <info>    broadcast 192.168.1.255 
Oct 20 16:55:04 matt-desktop NetworkManager: <info>    gateway 192.168.1.254 
Oct 20 16:55:04 matt-desktop NetworkManager: <info>    nameserver 192.168.1.254 
Oct 20 16:55:04 matt-desktop NetworkManager: <info>    domain name 'config' 
Oct 20 16:55:04 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Oct 20 16:55:04 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 20 16:55:04 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Oct 20 16:55:04 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 20 16:55:04 matt-desktop avahi-daemon[5289]: Withdrawing address record for 192.168.1.67 on wlan0.
Oct 20 16:55:04 matt-desktop avahi-daemon[5289]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 16:55:04 matt-desktop avahi-daemon[5289]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 20 16:55:04 matt-desktop avahi-daemon[5289]: Withdrawing address record for fe80::21a:70ff:fe3c:8dbf on wlan0.
Oct 20 16:55:04 matt-desktop avahi-daemon[5289]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 16:55:04 matt-desktop avahi-daemon[5289]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 16:55:04 matt-desktop avahi-daemon[5289]: Registering new address record for 192.168.1.67 on wlan0.IPv4.
Oct 20 16:55:05 matt-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 20 16:55:05 matt-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 20 16:55:05 matt-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Oct 20 16:55:05 matt-desktop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Oct 20 16:55:05 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 20 16:55:05 matt-desktop NetworkManager: <debug> [1224518105.509474] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ASpunkMonkey' 
Oct 20 16:55:05 matt-desktop NetworkManager: <debug> [1224518105.509667] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ASpunkMonkey' 
Oct 20 16:55:05 matt-desktop NetworkManager: <debug> [1224518105.509810] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ASpunkMonkey' 
Oct 20 16:55:05 matt-desktop NetworkManager: <debug> [1224518105.509950] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ASpunkMonkey' 
Oct 20 16:55:05 matt-desktop NetworkManager: <debug> [1224518105.510106] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ASpunkMonkey' 
Oct 20 16:55:05 matt-desktop NetworkManager: <debug> [1224518105.510246] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'ASpunkMonkey' 
Oct 20 16:55:05 matt-desktop ntpdate[6316]: step time server 91.189.94.4 offset 82816.542222 sec
Oct 21 15:55:23 matt-desktop avahi-daemon[5289]: Registering new address record for fe80::21a:70ff:fe3c:8dbf on wlan0.*.
Oct 21 15:55:32 matt-desktop kernel: [  123.376373] wlan0: no IPv6 routers present
Oct 20 23:41:05 matt-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct 20 23:41:05 matt-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Oct 20 23:41:05 matt-desktop kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Oct 20 23:41:05 matt-desktop kernel: Symbols match kernel version 2.6.24.
Oct 20 23:41:05 matt-desktop kernel: Loaded 19939 symbols from 100 modules.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] 896MB LOWMEM available.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] found SMP MP-table at 000f5360
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Zone PFN ranges:
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   DMA             0 ->     4096
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   HighMem    229376 ->   524000
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]     0:        0 ->   524000
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] On node 0 totalpages: 524000
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
Oct 20 23:41:05 matt-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] DMI 2.4 present.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6CF0 checksum 0
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: RSDP 000F6CF0, 0014 (r0 GBT   )
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: DSDT 7FEE3180, 49F4 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: HPET 7FEE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: MCFG 7FEE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: APIC 7FEE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: SSDT 7FEE7DC0, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: SSDT 7FEE8250, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519907
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Kernel command line: root=UUID=6c75aea6-38fc-4a0b-a141-d73c7506188f ro quiet splash
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Initializing CPU#0
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 20 23:41:05 matt-desktop kernel: [    0.000000] Detected 1809.029 MHz processor.
Oct 20 23:41:05 matt-desktop kernel: [   22.683545] Console: colour VGA+ 80x25
Oct 20 23:41:05 matt-desktop kernel: [   22.683549] console [tty0] enabled
Oct 20 23:41:05 matt-desktop kernel: [   22.683771] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 20 23:41:05 matt-desktop kernel: [   22.684029] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 20 23:41:05 matt-desktop kernel: [   22.772009] Memory: 2065688k/2096000k available (2177k kernel code, 29084k reserved, 1006k data, 368k init, 1178496k highmem)
Oct 20 23:41:05 matt-desktop kernel: [   22.772015] virtual kernel memory layout:
Oct 20 23:41:05 matt-desktop kernel: [   22.772016]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 20 23:41:05 matt-desktop kernel: [   22.772017]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 20 23:41:05 matt-desktop kernel: [   22.772018]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 20 23:41:05 matt-desktop kernel: [   22.772019]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 20 23:41:05 matt-desktop kernel: [   22.772020]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 20 23:41:05 matt-desktop kernel: [   22.772021]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Oct 20 23:41:05 matt-desktop kernel: [   22.772022]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Oct 20 23:41:05 matt-desktop kernel: [   22.772025] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 20 23:41:05 matt-desktop kernel: [   22.772064] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Oct 20 23:41:05 matt-desktop kernel: [   22.772200] hpet clockevent registered
Oct 20 23:41:05 matt-desktop kernel: [   22.852196] Calibrating delay using timer specific routine.. 3620.91 BogoMIPS (lpj=7241821)
Oct 20 23:41:05 matt-desktop kernel: [   22.852216] Security Framework initialized
Oct 20 23:41:05 matt-desktop kernel: [   22.852222] SELinux:  Disabled at boot.
Oct 20 23:41:05 matt-desktop kernel: [   22.852234] AppArmor: AppArmor initialized
Oct 20 23:41:05 matt-desktop kernel: [   22.852238] Failure registering capabilities with primary security module.
Oct 20 23:41:05 matt-desktop kernel: [   22.852245] Mount-cache hash table entries: 512
Oct 20 23:41:05 matt-desktop kernel: [   22.852363] Initializing cgroup subsys ns
Oct 20 23:41:05 matt-desktop kernel: [   22.852368] Initializing cgroup subsys cpuacct
Oct 20 23:41:05 matt-desktop kernel: [   22.852378] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Oct 20 23:41:05 matt-desktop kernel: [   22.852385] monitor/mwait feature present.
Oct 20 23:41:05 matt-desktop kernel: [   22.852386] using mwait in idle threads.
Oct 20 23:41:05 matt-desktop kernel: [   22.852390] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 20 23:41:05 matt-desktop kernel: [   22.852392] CPU: L2 cache: 2048K
Oct 20 23:41:05 matt-desktop kernel: [   22.852395] CPU: Physical Processor ID: 0
Oct 20 23:41:05 matt-desktop kernel: [   22.852396] CPU: Processor Core ID: 0
Oct 20 23:41:05 matt-desktop kernel: [   22.852398] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Oct 20 23:41:05 matt-desktop kernel: [   22.852406] Compat vDSO mapped to ffffe000.
Oct 20 23:41:05 matt-desktop kernel: [   22.852419] Checking 'hlt' instruction... OK.
Oct 20 23:41:05 matt-desktop kernel: [   22.868650] SMP alternatives: switching to UP code
Oct 20 23:41:05 matt-desktop kernel: [   22.870225] Early unpacking initramfs... done
Oct 20 23:41:05 matt-desktop kernel: [   23.201725] ACPI: Core revision 20070126
Oct 20 23:41:05 matt-desktop kernel: [   23.201764] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 20 23:41:05 matt-desktop kernel: [   23.325885] CPU0: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
Oct 20 23:41:05 matt-desktop kernel: [   23.325903] SMP alternatives: switching to SMP code
Oct 20 23:41:05 matt-desktop kernel: [   23.326624] Booting processor 1/1 eip 3000
Oct 20 23:41:05 matt-desktop kernel: [   23.336786] Initializing CPU#1
Oct 20 23:41:05 matt-desktop kernel: [   23.416128] Calibrating delay using timer specific routine.. 3618.01 BogoMIPS (lpj=7236030)
Oct 20 23:41:05 matt-desktop kernel: [   23.416135] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Oct 20 23:41:05 matt-desktop kernel: [   23.416139] monitor/mwait feature present.
Oct 20 23:41:05 matt-desktop kernel: [   23.416142] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 20 23:41:05 matt-desktop kernel: [   23.416144] CPU: L2 cache: 2048K
Oct 20 23:41:05 matt-desktop kernel: [   23.416146] CPU: Physical Processor ID: 0
Oct 20 23:41:05 matt-desktop kernel: [   23.416147] CPU: Processor Core ID: 1
Oct 20 23:41:05 matt-desktop kernel: [   23.416149] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Oct 20 23:41:05 matt-desktop kernel: [   23.416654] CPU1: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
Oct 20 23:41:05 matt-desktop kernel: [   23.416673] Total of 2 processors activated (7238.92 BogoMIPS).
Oct 20 23:41:05 matt-desktop kernel: [   23.416817] ENABLING IO-APIC IRQs
Oct 20 23:41:05 matt-desktop kernel: [   23.416982] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 20 23:41:05 matt-desktop kernel: [   23.564215] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 20 23:41:05 matt-desktop kernel: [   23.584228] Brought up 2 CPUs
Oct 20 23:41:05 matt-desktop kernel: [   23.584251] CPU0 attaching sched-domain:
Oct 20 23:41:05 matt-desktop kernel: [   23.584253]  domain 0: span 03
Oct 20 23:41:05 matt-desktop kernel: [   23.584255]   groups: 01 02
Oct 20 23:41:05 matt-desktop kernel: [   23.584258] CPU1 attaching sched-domain:
Oct 20 23:41:05 matt-desktop kernel: [   23.584259]  domain 0: span 03
Oct 20 23:41:05 matt-desktop kernel: [   23.584261]   groups: 02 01
Oct 20 23:41:05 matt-desktop kernel: [   23.584479] net_namespace: 64 bytes
Oct 20 23:41:05 matt-desktop kernel: [   23.584490] Booting paravirtualized kernel on bare hardware
Oct 20 23:41:05 matt-desktop kernel: [   23.584905] Time: 23:40:43  Date: 10/20/08
Oct 20 23:41:05 matt-desktop kernel: [   23.584931] NET: Registered protocol family 16
Oct 20 23:41:05 matt-desktop kernel: [   23.585113] EISA bus registered
Oct 20 23:41:05 matt-desktop kernel: [   23.585117] ACPI: bus type pci registered
Oct 20 23:41:05 matt-desktop kernel: [   23.591140] PCI: PCI BIOS revision 3.00 entry at 0xfb430, last bus=5
Oct 20 23:41:05 matt-desktop kernel: [   23.591142] PCI: Using configuration type 1
Oct 20 23:41:05 matt-desktop kernel: [   23.591166] Setting up standard PCI resources
Oct 20 23:41:05 matt-desktop kernel: [   23.591857] mtrr: your CPUs had inconsistent variable MTRR settings
Oct 20 23:41:05 matt-desktop kernel: [   23.591858] mtrr: probably your BIOS does not setup all CPUs.
Oct 20 23:41:05 matt-desktop kernel: [   23.591860] mtrr: corrected configuration.
Oct 20 23:41:05 matt-desktop kernel: [   23.593115] ACPI: EC: Look up EC in DSDT
Oct 20 23:41:05 matt-desktop kernel: [   23.597069] ACPI: Interpreter enabled
Oct 20 23:41:05 matt-desktop kernel: [   23.597075] ACPI: (supports S0 S1 S4 S5)
Oct 20 23:41:05 matt-desktop kernel: [   23.597093] ACPI: Using IOAPIC for interrupt routing
Oct 20 23:41:05 matt-desktop kernel: [   23.601486] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 20 23:41:05 matt-desktop kernel: [   23.602144] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Oct 20 23:41:05 matt-desktop kernel: [   23.602147] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Oct 20 23:41:05 matt-desktop kernel: [   23.603017] PCI: Transparent bridge - 0000:00:1e.0
Oct 20 23:41:05 matt-desktop kernel: [   23.603049] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 20 23:41:05 matt-desktop kernel: [   23.603187] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Oct 20 23:41:05 matt-desktop kernel: [   23.603258] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Oct 20 23:41:05 matt-desktop kernel: [   23.603330] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Oct 20 23:41:05 matt-desktop kernel: [   23.603399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Oct 20 23:41:05 matt-desktop kernel: [   23.613825] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 20 23:41:05 matt-desktop kernel: [   23.613920] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 23:41:05 matt-desktop kernel: [   23.614018] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Oct 20 23:41:05 matt-desktop kernel: [   23.614111] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Oct 20 23:41:05 matt-desktop kernel: [   23.614203] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 23:41:05 matt-desktop kernel: [   23.614296] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
Oct 20 23:41:05 matt-desktop kernel: [   23.614388] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Oct 20 23:41:05 matt-desktop kernel: [   23.614481] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 23:41:05 matt-desktop kernel: [   23.614606] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 20 23:41:05 matt-desktop kernel: [   23.614636] pnp: PnP ACPI init
Oct 20 23:41:05 matt-desktop kernel: [   23.614643] ACPI: bus type pnp registered
Oct 20 23:41:05 matt-desktop kernel: [   23.616770] pnpacpi: exceeded the max number of mem resources: 12
Oct 20 23:41:05 matt-desktop kernel: [   23.616910] pnp: PnP ACPI: found 12 devices
Oct 20 23:41:05 matt-desktop kernel: [   23.616912] ACPI: ACPI bus type pnp unregistered
Oct 20 23:41:05 matt-desktop kernel: [   23.616917] PnPBIOS: Disabled by ACPI PNP
Oct 20 23:41:05 matt-desktop kernel: [   23.617137] PCI: Using ACPI for IRQ routing
Oct 20 23:41:05 matt-desktop kernel: [   23.617140] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 20 23:41:05 matt-desktop kernel: [   23.684370] NET: Registered protocol family 8
Oct 20 23:41:05 matt-desktop kernel: [   23.684373] NET: Registered protocol family 20
Oct 20 23:41:05 matt-desktop kernel: [   23.684417] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 20 23:41:05 matt-desktop kernel: [   23.684423] hpet0: 3 64-bit timers, 14318180 Hz
Oct 20 23:41:05 matt-desktop kernel: [   23.685458] AppArmor: AppArmor Filesystem Enabled
Oct 20 23:41:05 matt-desktop kernel: [   23.688276] Time: tsc clocksource has been installed.
Oct 20 23:41:05 matt-desktop kernel: [   23.688291] Switched to high resolution mode on CPU 0
Oct 20 23:41:05 matt-desktop kernel: [   23.688386] Switched to high resolution mode on CPU 1
Oct 20 23:41:05 matt-desktop kernel: [   23.701328] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701332] system 00:01: ioport range 0x290-0x29f has been reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701336] system 00:01: ioport range 0x800-0x87f has been reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701339] system 00:01: ioport range 0x290-0x294 has been reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701343] system 00:01: ioport range 0x880-0x88f has been reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701356] system 00:08: ioport range 0x400-0x4bf could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701365] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701373] system 00:0a: iomem range 0xcf600-0xcffff has been reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701377] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701381] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701385] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701389] system 00:0a: iomem range 0x7fee0000-0x7fefffff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701393] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701397] system 00:0a: iomem range 0x100000-0x7fedffff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701401] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701405] system 00:0a: iomem range 0xfed10000-0xfed1dfff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701409] system 00:0a: iomem range 0xfed20000-0xfed8ffff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701413] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.701417] system 00:0a: iomem range 0xffb00000-0xffb7ffff could not be reserved
Oct 20 23:41:05 matt-desktop kernel: [   23.731874] PCI: Bridge: 0000:00:01.0
Oct 20 23:41:05 matt-desktop kernel: [   23.731877]   IO window: 8000-8fff
Oct 20 23:41:05 matt-desktop kernel: [   23.731880]   MEM window: f4000000-f5ffffff
Oct 20 23:41:05 matt-desktop kernel: [   23.731883]   PREFETCH window: e0000000-efffffff
Oct 20 23:41:05 matt-desktop kernel: [   23.731886] PCI: Bridge: 0000:00:1c.0
Oct 20 23:41:05 matt-desktop kernel: [   23.731889]   IO window: 7000-7fff
Oct 20 23:41:05 matt-desktop kernel: [   23.731893]   MEM window: disabled.
Oct 20 23:41:05 matt-desktop kernel: [   23.731896]   PREFETCH window: disabled.
Oct 20 23:41:05 matt-desktop kernel: [   23.731900] PCI: Bridge: 0000:00:1c.3
Oct 20 23:41:05 matt-desktop kernel: [   23.731902]   IO window: 9000-afff
Oct 20 23:41:05 matt-desktop kernel: [   23.731906]   MEM window: f8000000-f80fffff
Oct 20 23:41:05 matt-desktop kernel: [   23.731910]   PREFETCH window: disabled.
Oct 20 23:41:05 matt-desktop kernel: [   23.731914] PCI: Bridge: 0000:00:1c.4
Oct 20 23:41:05 matt-desktop kernel: [   23.731916]   IO window: b000-bfff
Oct 20 23:41:05 matt-desktop kernel: [   23.731921]   MEM window: f6000000-f7ffffff
Oct 20 23:41:05 matt-desktop kernel: [   23.731924]   PREFETCH window: 80000000-800fffff
Oct 20 23:41:05 matt-desktop kernel: [   23.731928] PCI: Bridge: 0000:00:1e.0
Oct 20 23:41:05 matt-desktop kernel: [   23.731929]   IO window: disabled.
Oct 20 23:41:05 matt-desktop kernel: [   23.731934]   MEM window: f8100000-f81fffff
Oct 20 23:41:05 matt-desktop kernel: [   23.731937]   PREFETCH window: disabled.
Oct 20 23:41:05 matt-desktop kernel: [   23.731951] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:41:05 matt-desktop kernel: [   23.731956] PCI: Setting latency timer of device 0000:00:01.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   23.731973] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:41:05 matt-desktop kernel: [   23.731977] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   23.731994] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:41:05 matt-desktop kernel: [   23.731999] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 20 23:41:05 matt-desktop kernel: [   23.732014] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:41:05 matt-desktop kernel: [   23.732019] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Oct 20 23:41:05 matt-desktop kernel: [   23.732028] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   23.732038] NET: Registered protocol family 2
Oct 20 23:41:05 matt-desktop kernel: [   23.769343] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 20 23:41:05 matt-desktop kernel: [   23.769602] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 20 23:41:05 matt-desktop kernel: [   23.770003] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 20 23:41:05 matt-desktop kernel: [   23.770211] TCP: Hash tables configured (established 131072 bind 65536)
Oct 20 23:41:05 matt-desktop kernel: [   23.770214] TCP reno registered
Oct 20 23:41:05 matt-desktop kernel: [   23.781434] checking if image is initramfs... it is
Oct 20 23:41:05 matt-desktop kernel: [   24.434012] Freeing initrd memory: 7702k freed
Oct 20 23:41:05 matt-desktop kernel: [   24.434766] audit: initializing netlink socket (disabled)
Oct 20 23:41:05 matt-desktop kernel: [   24.434779] audit(1224546043.416:1): initialized
Oct 20 23:41:05 matt-desktop kernel: [   24.434984] highmem bounce pool size: 64 pages
Oct 20 23:41:05 matt-desktop kernel: [   24.436895] VFS: Disk quotas dquot_6.5.1
Oct 20 23:41:05 matt-desktop kernel: [   24.436964] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 20 23:41:05 matt-desktop kernel: [   24.437094] io scheduler noop registered
Oct 20 23:41:05 matt-desktop kernel: [   24.437096] io scheduler anticipatory registered
Oct 20 23:41:05 matt-desktop kernel: [   24.437098] io scheduler deadline registered
Oct 20 23:41:05 matt-desktop kernel: [   24.437111] io scheduler cfq registered (default)
Oct 20 23:41:05 matt-desktop kernel: [   24.437216] Boot video device is 0000:01:00.0
Oct 20 23:41:05 matt-desktop kernel: [   24.437322] PCI: Setting latency timer of device 0000:00:01.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   24.437356] assign_interrupt_mode Found MSI capability
Oct 20 23:41:05 matt-desktop kernel: [   24.437384] Allocate Port Service[0000:00:01.0:pcie00]
Oct 20 23:41:05 matt-desktop kernel: [   24.437458] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   24.437496] assign_interrupt_mode Found MSI capability
Oct 20 23:41:05 matt-desktop kernel: [   24.437527] Allocate Port Service[0000:00:1c.0:pcie00]
Oct 20 23:41:05 matt-desktop kernel: [   24.437558] Allocate Port Service[0000:00:1c.0:pcie02]
Oct 20 23:41:05 matt-desktop kernel: [   24.437635] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 20 23:41:05 matt-desktop kernel: [   24.437673] assign_interrupt_mode Found MSI capability
Oct 20 23:41:05 matt-desktop kernel: [   24.437704] Allocate Port Service[0000:00:1c.3:pcie00]
Oct 20 23:41:05 matt-desktop kernel: [   24.437735] Allocate Port Service[0000:00:1c.3:pcie02]
Oct 20 23:41:05 matt-desktop kernel: [   24.437811] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Oct 20 23:41:05 matt-desktop kernel: [   24.437849] assign_interrupt_mode Found MSI capability
Oct 20 23:41:05 matt-desktop kernel: [   24.437879] Allocate Port Service[0000:00:1c.4:pcie00]
Oct 20 23:41:05 matt-desktop kernel: [   24.437911] Allocate Port Service[0000:00:1c.4:pcie02]
Oct 20 23:41:05 matt-desktop kernel: [   24.438140] isapnp: Scanning for PnP cards...
Oct 20 23:41:05 matt-desktop kernel: [   24.791349] isapnp: No Plug & Play device found
Oct 20 23:41:05 matt-desktop kernel: [   24.815310] Real Time Clock Driver v1.12ac
Oct 20 23:41:05 matt-desktop kernel: [   24.815418] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 20 23:41:05 matt-desktop kernel: [   24.815532] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 23:41:05 matt-desktop kernel: [   24.816083] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 23:41:05 matt-desktop kernel: [   24.816821] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 20 23:41:05 matt-desktop kernel: [   24.816886] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 20 23:41:05 matt-desktop kernel: [   24.817017] PNP: No PS/2 controller found. Probing ports directly.
Oct 20 23:41:05 matt-desktop kernel: [   24.817349] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 20 23:41:05 matt-desktop kernel: [   24.817354] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 20 23:41:05 matt-desktop kernel: [   24.836239] mice: PS/2 mouse device common for all mice
Oct 20 23:41:05 matt-desktop kernel: [   24.836399] EISA: Probing bus 0 at eisa.0
Oct 20 23:41:05 matt-desktop kernel: [   24.836422] Cannot allocate resource for EISA slot 7
Oct 20 23:41:05 matt-desktop kernel: [   24.836423] Cannot allocate resource for EISA slot 8
Oct 20 23:41:05 matt-desktop kernel: [   24.836425] EISA: Detected 0 cards.
Oct 20 23:41:05 matt-desktop kernel: [   24.836428] cpuidle: using governor ladder
Oct 20 23:41:05 matt-desktop kernel: [   24.836430] cpuidle: using governor menu
Oct 20 23:41:05 matt-desktop kernel: [   24.836507] NET: Registered protocol family 1
Oct 20 23:41:05 matt-desktop kernel: [   24.836532] Using IPI No-Shortcut mode
Oct 20 23:41:05 matt-desktop kernel: [   24.836557] registered taskstats version 1
Oct 20 23:41:05 matt-desktop kernel: [   24.836670]   Magic number: 12:102:707
Oct 20 23:41:05 matt-desktop kernel: [   24.836725] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 20 23:41:05 matt-desktop kernel: [   24.836726] EDD information not available.
Oct 20 23:41:05 matt-desktop kernel: [   24.836881] Freeing unused kernel memory: 368k freed
Oct 20 23:41:05 matt-desktop kernel: [   26.038117] fuse init (API version 7.9)
Oct 20 23:41:05 matt-desktop kernel: [   26.056847] ACPI: Processor [CPU0] (supports 2 throttling states)
Oct 20 23:41:05 matt-desktop kernel: [   26.056958] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
Oct 20 23:41:05 matt-desktop kernel: [   26.057098] ACPI: Processor [CPU1] (supports 2 throttling states)
Oct 20 23:41:05 matt-desktop kernel: [   26.057112] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 20 23:41:05 matt-desktop kernel: [   26.057122] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 20 23:41:05 matt-desktop kernel: [   26.180251] usbcore: registered new interface driver usbfs
Oct 20 23:41:05 matt-desktop kernel: [   26.180272] usbcore: registered new interface driver hub
Oct 20 23:41:05 matt-desktop kernel: [   26.180598] usbcore: registered new device driver usb
Oct 20 23:41:05 matt-desktop kernel: [   26.181622] USB Universal Host Controller Interface driver v3.0
Oct 20 23:41:05 matt-desktop kernel: [   26.181669] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:41:05 matt-desktop kernel: [   26.181680] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   26.181683] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Oct 20 23:41:05 matt-desktop kernel: [   26.181898] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Oct 20 23:41:05 matt-desktop kernel: [   26.181925] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c000
Oct 20 23:41:05 matt-desktop kernel: [   26.182044] usb usb1: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   26.182066] hub 1-0:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   26.182071] hub 1-0:1.0: 2 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   26.285014] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Oct 20 23:41:05 matt-desktop kernel: [   26.285027] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Oct 20 23:41:05 matt-desktop kernel: [   26.285030] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Oct 20 23:41:05 matt-desktop kernel: [   26.285053] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Oct 20 23:41:05 matt-desktop kernel: [   26.285079] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000c400
Oct 20 23:41:05 matt-desktop kernel: [   26.285197] usb usb2: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   26.285220] hub 2-0:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   26.285225] hub 2-0:1.0: 2 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   26.372445] SCSI subsystem initialized
Oct 20 23:41:05 matt-desktop kernel: [   26.389000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Oct 20 23:41:05 matt-desktop kernel: [   26.389013] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   26.389017] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 20 23:41:05 matt-desktop kernel: [   26.389041] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Oct 20 23:41:05 matt-desktop kernel: [   26.389067] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000c800
Oct 20 23:41:05 matt-desktop kernel: [   26.389170] usb usb3: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   26.389193] hub 3-0:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   26.389197] hub 3-0:1.0: 2 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   26.402613] libata version 3.00 loaded.
Oct 20 23:41:05 matt-desktop kernel: [   26.492983] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:41:05 matt-desktop kernel: [   26.492995] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Oct 20 23:41:05 matt-desktop kernel: [   26.492999] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 20 23:41:05 matt-desktop kernel: [   26.493022] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Oct 20 23:41:05 matt-desktop kernel: [   26.493049] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000cc00
Oct 20 23:41:05 matt-desktop kernel: [   26.493158] usb usb4: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   26.493181] hub 4-0:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   26.493186] hub 4-0:1.0: 2 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   26.524867] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 20 23:41:05 matt-desktop kernel: [   26.596949] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Oct 20 23:41:05 matt-desktop kernel: [   26.596961] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Oct 20 23:41:05 matt-desktop kernel: [   26.596965] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 20 23:41:05 matt-desktop kernel: [   26.596989] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Oct 20 23:41:05 matt-desktop kernel: [   26.597014] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d000
Oct 20 23:41:05 matt-desktop kernel: [   26.597122] usb usb5: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   26.597146] hub 5-0:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   26.597151] hub 5-0:1.0: 2 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   26.691008] usb 1-2: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   26.699925] ahci 0000:03:00.0: version 3.0
Oct 20 23:41:05 matt-desktop kernel: [   26.699958] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:41:05 matt-desktop kernel: [   26.931850] usb 2-1: new full speed USB device using uhci_hcd and address 2
Oct 20 23:41:05 matt-desktop kernel: [   27.099182] usb 2-1: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   27.339785] usb 5-1: new full speed USB device using uhci_hcd and address 2
Oct 20 23:41:05 matt-desktop kernel: [   27.483106] usb 5-1: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   27.486014] hub 5-1:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   27.487983] hub 5-1:1.0: 4 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   27.703737] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Oct 20 23:41:05 matt-desktop kernel: [   27.703743] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Oct 20 23:41:05 matt-desktop kernel: [   27.703751] PCI: Setting latency timer of device 0000:03:00.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   27.703912] scsi0 : ahci
Oct 20 23:41:05 matt-desktop kernel: [   27.704082] scsi1 : ahci
Oct 20 23:41:05 matt-desktop kernel: [   27.704142] ata1: SATA max UDMA/133 abar m8192@0xf8000000 port 0xf8000100 irq 17
Oct 20 23:41:05 matt-desktop kernel: [   27.704146] ata2: SATA max UDMA/133 abar m8192@0xf8000000 port 0xf8000180 irq 17
Oct 20 23:41:05 matt-desktop kernel: [   27.836714] usb 5-2: new full speed USB device using uhci_hcd and address 3
Oct 20 23:41:05 matt-desktop kernel: [   28.014074] usb 5-2: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   28.019975] hub 5-2:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   28.020945] hub 5-2:1.0: 3 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   28.023671] ata1: SATA link down (SStatus 0 SControl 300)

```

---

### Post by the_duality on 2008-10-21
Part 2:

```
Oct 20 23:41:05 matt-desktop kernel: [   28.340925] usb 5-1.4: new full speed USB device using uhci_hcd and address 4
Oct 20 23:41:05 matt-desktop kernel: [   28.344694] ata2: SATA link down (SStatus 0 SControl 300)
Oct 20 23:41:05 matt-desktop kernel: [   28.345220] ata_piix 0000:00:1f.2: version 2.12
Oct 20 23:41:05 matt-desktop kernel: [   28.345227] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Oct 20 23:41:05 matt-desktop kernel: [   28.466041] usb 5-1.4: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   28.499645] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:41:05 matt-desktop kernel: [   28.499684] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Oct 20 23:41:05 matt-desktop kernel: [   28.499740] scsi2 : ata_piix
Oct 20 23:41:05 matt-desktop kernel: [   28.499919] scsi3 : ata_piix
Oct 20 23:41:05 matt-desktop kernel: [   28.500387] ata3: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Oct 20 23:41:05 matt-desktop kernel: [   28.500390] ata4: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Oct 20 23:41:05 matt-desktop kernel: [   28.672901] usb 5-2.1: new full speed USB device using uhci_hcd and address 5
Oct 20 23:41:05 matt-desktop kernel: [   28.679797] ata3.00: HPA unlocked: 488279137 -> 488281250, native 488281250
Oct 20 23:41:05 matt-desktop kernel: [   28.679806] ata3.00: ATA-7: Maxtor 7L250S0, BANC1G10, max UDMA/133
Oct 20 23:41:05 matt-desktop kernel: [   28.679811] ata3.00: 488281250 sectors, multi 16: LBA48 NCQ (not used)
Oct 20 23:41:05 matt-desktop kernel: [   28.698075] ata3.00: configured for UDMA/133
Oct 20 23:41:05 matt-desktop kernel: [   28.814013] usb 5-2.1: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   28.827899] usbcore: registered new interface driver hiddev
Oct 20 23:41:05 matt-desktop kernel: [   28.827933] usbcore: registered new interface driver libusual
Oct 20 23:41:05 matt-desktop kernel: [   28.833082] Initializing USB Mass Storage driver...
Oct 20 23:41:05 matt-desktop kernel: [   28.842021] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input1
Oct 20 23:41:05 matt-desktop kernel: [   28.862389] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 7L250S0   BANC PQ: 0 ANSI: 5
Oct 20 23:41:05 matt-desktop kernel: [   28.862464] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Oct 20 23:41:05 matt-desktop kernel: [   28.862493] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:41:05 matt-desktop kernel: [   28.862523] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Oct 20 23:41:05 matt-desktop kernel: [   28.862564] scsi4 : ata_piix
Oct 20 23:41:05 matt-desktop kernel: [   28.862606] scsi5 : ata_piix
Oct 20 23:41:05 matt-desktop kernel: [   28.863018] ata5: SATA max UDMA/133 cmd 0xd800 ctl 0xdc00 bmdma 0xe800 irq 17
Oct 20 23:41:05 matt-desktop kernel: [   28.863021] ata6: SATA max UDMA/133 cmd 0xe000 ctl 0xe400 bmdma 0xe808 irq 17
Oct 20 23:41:05 matt-desktop kernel: [   28.871630] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1a.0-2
Oct 20 23:41:05 matt-desktop kernel: [   28.871720] scsi6 : SCSI emulation for USB Mass Storage devices
Oct 20 23:41:05 matt-desktop kernel: [   28.871808] usb-storage: device found at 2
Oct 20 23:41:05 matt-desktop kernel: [   28.871810] usb-storage: waiting for device to settle before scanning
Oct 20 23:41:05 matt-desktop kernel: [   28.874180] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2.1/5-2.1:1.0/input/input2
Oct 20 23:41:05 matt-desktop kernel: [   28.903585] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
Oct 20 23:41:05 matt-desktop kernel: [   28.909971] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2.1/5-2.1:1.1/input/input3
Oct 20 23:41:05 matt-desktop kernel: [   28.919602] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
Oct 20 23:41:05 matt-desktop kernel: [   28.919621] usbcore: registered new interface driver usbhid
Oct 20 23:41:05 matt-desktop kernel: [   28.919626] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 20 23:41:05 matt-desktop kernel: [   28.920161] usbcore: registered new interface driver usb-storage
Oct 20 23:41:05 matt-desktop kernel: [   28.920164] USB Mass Storage support registered.
Oct 20 23:41:05 matt-desktop kernel: [   29.190181] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
Oct 20 23:41:05 matt-desktop kernel: [   29.190195] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Oct 20 23:41:05 matt-desktop kernel: [   29.190199] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Oct 20 23:41:05 matt-desktop kernel: [   29.190231] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Oct 20 23:41:05 matt-desktop kernel: [   29.194139] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Oct 20 23:41:05 matt-desktop kernel: [   29.194145] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xf8205000
Oct 20 23:41:05 matt-desktop kernel: [   29.208513] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 20 23:41:05 matt-desktop kernel: [   29.208670] usb usb6: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   29.208705] hub 6-0:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   29.208712] hub 6-0:1.0: 4 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   29.311603] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Oct 20 23:41:05 matt-desktop kernel: [   29.311616] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Oct 20 23:41:05 matt-desktop kernel: [   29.311620] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 20 23:41:05 matt-desktop kernel: [   29.311651] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Oct 20 23:41:05 matt-desktop kernel: [   29.315557] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Oct 20 23:41:05 matt-desktop kernel: [   29.315561] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf8204000
Oct 20 23:41:05 matt-desktop kernel: [   29.327497] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 20 23:41:05 matt-desktop kernel: [   29.327632] usb usb7: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   29.327665] hub 7-0:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   29.327671] hub 7-0:1.0: 6 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   29.431783] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
Oct 20 23:41:05 matt-desktop kernel: [   29.431788] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:41:05 matt-desktop kernel: [   29.431821] PCI: Setting latency timer of device 0000:03:00.1 to 64
Oct 20 23:41:05 matt-desktop kernel: [   29.431835] ACPI: PCI interrupt for device 0000:03:00.1 disabled
Oct 20 23:41:05 matt-desktop kernel: [   29.436869] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:41:05 matt-desktop kernel: [   29.436903] PCI: Setting latency timer of device 0000:03:00.1 to 64
Oct 20 23:41:05 matt-desktop kernel: [   29.437291] scsi7 : pata_jmicron
Oct 20 23:41:05 matt-desktop kernel: [   29.437931] scsi8 : pata_jmicron
Oct 20 23:41:05 matt-desktop kernel: [   29.438399] ata7: PATA max UDMA/100 cmd 0x9000 ctl 0x9400 bmdma 0xa000 irq 16
Oct 20 23:41:05 matt-desktop kernel: [   29.438403] ata8: PATA max UDMA/100 cmd 0x9800 ctl 0x9c00 bmdma 0xa008 irq 16
Oct 20 23:41:05 matt-desktop kernel: [   29.439373] Driver 'sd' needs updating - please use bus_type methods
Oct 20 23:41:05 matt-desktop kernel: [   29.439451] sd 2:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Oct 20 23:41:05 matt-desktop kernel: [   29.439463] sd 2:0:0:0: [sda] Write Protect is off
Oct 20 23:41:05 matt-desktop kernel: [   29.439465] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 20 23:41:05 matt-desktop kernel: [   29.439481] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 23:41:05 matt-desktop kernel: [   29.439529] sd 2:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Oct 20 23:41:05 matt-desktop kernel: [   29.439539] sd 2:0:0:0: [sda] Write Protect is off
Oct 20 23:41:05 matt-desktop kernel: [   29.439541] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 20 23:41:05 matt-desktop kernel: [   29.439556] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 23:41:05 matt-desktop kernel: [   29.439560]  sda: sda1 sda2 sda3 sda4
Oct 20 23:41:05 matt-desktop kernel: [   29.480219] sd 2:0:0:0: [sda] Attached SCSI disk
Oct 20 23:41:05 matt-desktop kernel: [   29.484933] sd 2:0:0:0: Attached scsi generic sg0 type 0
Oct 20 23:41:05 matt-desktop kernel: [   29.735403] usb 6-3: new high speed USB device using ehci_hcd and address 3
Oct 20 23:41:05 matt-desktop kernel: [   29.758332] Attempting manual resume
Oct 20 23:41:05 matt-desktop kernel: [   29.758335] swsusp: Resume From Partition 8:3
Oct 20 23:41:05 matt-desktop kernel: [   29.758337] PM: Checking swsusp image.
Oct 20 23:41:05 matt-desktop kernel: [   29.758455] PM: Resume from disk failed.
Oct 20 23:41:05 matt-desktop kernel: [   29.770281] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 20 23:41:05 matt-desktop kernel: [   29.770284] EXT3-fs: write access will be enabled during recovery.
Oct 20 23:41:05 matt-desktop kernel: [   29.772954] ata7.00: ATAPI: LITE-ON DVDRW LH-20A1H, LL0C, max UDMA/66
Oct 20 23:41:05 matt-desktop kernel: [   29.772969] ata7.00: limited to UDMA/33 due to 40-wire cable
Oct 20 23:41:05 matt-desktop kernel: [   29.869283] usb 6-3: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   29.869496] scsi9 : SCSI emulation for USB Mass Storage devices
Oct 20 23:41:05 matt-desktop kernel: [   29.869665] usb 5-1: USB disconnect, address 2
Oct 20 23:41:05 matt-desktop kernel: [   29.869668] usb 5-1.4: USB disconnect, address 4
Oct 20 23:41:05 matt-desktop kernel: [   29.869895] usb-storage: device found at 3
Oct 20 23:41:05 matt-desktop kernel: [   29.869897] usb-storage: waiting for device to settle before scanning
Oct 20 23:41:05 matt-desktop kernel: [   29.960960] ata7.00: configured for UDMA/33
Oct 20 23:41:05 matt-desktop kernel: [   29.999439] usb 5-2: USB disconnect, address 3
Oct 20 23:41:05 matt-desktop kernel: [   29.999442] usb 5-2.1: USB disconnect, address 5
Oct 20 23:41:05 matt-desktop kernel: [   30.128055] scsi 7:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL0C PQ: 0 ANSI: 5
Oct 20 23:41:05 matt-desktop kernel: [   30.128160] scsi 7:0:0:0: Attached scsi generic sg1 type 5
Oct 20 23:41:05 matt-desktop kernel: [   30.135465] Driver 'sr' needs updating - please use bus_type methods
Oct 20 23:41:05 matt-desktop kernel: [   30.143230] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Oct 20 23:41:05 matt-desktop kernel: [   30.143235] Uniform CD-ROM driver Revision: 3.20
Oct 20 23:41:05 matt-desktop kernel: [   30.143297] sr 7:0:0:0: Attached scsi CD-ROM sr0
Oct 20 23:41:05 matt-desktop kernel: [   30.156357] usb 1-2: USB disconnect, address 2
Oct 20 23:41:05 matt-desktop kernel: [   30.419521] usb 1-2: new low speed USB device using uhci_hcd and address 3
Oct 20 23:41:05 matt-desktop kernel: [   30.586821] usb 1-2: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   30.602897] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input4
Oct 20 23:41:05 matt-desktop kernel: [   30.628413] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1a.0-2
Oct 20 23:41:05 matt-desktop kernel: [   30.628509] usb 2-1: USB disconnect, address 2
Oct 20 23:41:05 matt-desktop kernel: [   30.995553] usb 7-5: new high speed USB device using ehci_hcd and address 2
Oct 20 23:41:05 matt-desktop kernel: [   31.127742] usb 7-5: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   31.127891] hub 7-5:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   31.127988] hub 7-5:1.0: 4 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   31.671207] usb 7-5.4: new full speed USB device using ehci_hcd and address 4
Oct 20 23:41:05 matt-desktop kernel: [   31.764305] usb 7-5.4: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   32.003136] usb 5-2: new full speed USB device using uhci_hcd and address 6
Oct 20 23:41:05 matt-desktop kernel: [   32.173581] usb 5-2: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   32.178476] hub 5-2:1.0: USB hub found
Oct 20 23:41:05 matt-desktop kernel: [   32.179433] hub 5-2:1.0: 3 ports detected
Oct 20 23:41:05 matt-desktop kernel: [   32.492420] usb 5-2.1: new full speed USB device using uhci_hcd and address 7
Oct 20 23:41:05 matt-desktop kernel: [   32.629546] usb 5-2.1: configuration #1 chosen from 1 choice
Oct 20 23:41:05 matt-desktop kernel: [   32.637642] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2.1/5-2.1:1.0/input/input5
Oct 20 23:41:05 matt-desktop kernel: [   32.656014] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
Oct 20 23:41:05 matt-desktop kernel: [   32.664463] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2.1/5-2.1:1.1/input/input6
Oct 20 23:41:05 matt-desktop kernel: [   32.688131] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
Oct 20 23:41:05 matt-desktop kernel: [   33.541022] kjournald starting.  Commit interval 5 seconds
Oct 20 23:41:05 matt-desktop kernel: [   33.541035] EXT3-fs: sda4: orphan cleanup on readonly fs
Oct 20 23:41:05 matt-desktop kernel: [   33.541043] ext3_orphan_cleanup: deleting unreferenced inode 477386
Oct 20 23:41:05 matt-desktop kernel: [   33.541069] EXT3-fs: sda4: 1 orphan inode deleted
Oct 20 23:41:05 matt-desktop kernel: [   33.541071] EXT3-fs: recovery complete.
Oct 20 23:41:05 matt-desktop kernel: [   33.542485] EXT3-fs: mounted filesystem with ordered data mode.
Oct 20 23:41:05 matt-desktop kernel: [   34.866820] usb-storage: device scan complete
Oct 20 23:41:05 matt-desktop kernel: [   34.867431] scsi 9:0:0:0: Direct-Access                               0.00 PQ: 0 ANSI: 2
Oct 20 23:41:05 matt-desktop kernel: [   34.868825] sd 9:0:0:0: [sdb] 7897088 512-byte hardware sectors (4043 MB)
Oct 20 23:41:05 matt-desktop kernel: [   34.869430] sd 9:0:0:0: [sdb] Write Protect is off
Oct 20 23:41:05 matt-desktop kernel: [   34.869435] sd 9:0:0:0: [sdb] Mode Sense: 00 00 00 00
Oct 20 23:41:05 matt-desktop kernel: [   34.869438] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Oct 20 23:41:05 matt-desktop kernel: [   34.872048] sd 9:0:0:0: [sdb] 7897088 512-byte hardware sectors (4043 MB)
Oct 20 23:41:05 matt-desktop kernel: [   34.872676] sd 9:0:0:0: [sdb] Write Protect is off
Oct 20 23:41:05 matt-desktop kernel: [   34.872680] sd 9:0:0:0: [sdb] Mode Sense: 00 00 00 00
Oct 20 23:41:05 matt-desktop kernel: [   34.872683] sd 9:0:0:0: [sdb] Assuming drive cache: write through
Oct 20 23:41:05 matt-desktop kernel: [   34.872687]  sdb: unknown partition table
Oct 20 23:41:05 matt-desktop kernel: [   35.569821] sd 9:0:0:0: [sdb] Attached SCSI removable disk
Oct 20 23:41:05 matt-desktop kernel: [   35.569874] sd 9:0:0:0: Attached scsi generic sg2 type 0
Oct 20 23:41:05 matt-desktop kernel: [   40.661552] input: PC Speaker as /devices/platform/pcspkr/input/input7
Oct 20 23:41:05 matt-desktop kernel: [   40.726942] parport_pc 00:07: reported by Plug and Play ACPI
Oct 20 23:41:05 matt-desktop kernel: [   40.726989] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Oct 20 23:41:05 matt-desktop kernel: [   40.770838] iTCO_vendor_support: vendor-support=0
Oct 20 23:41:05 matt-desktop kernel: [   40.785837] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Oct 20 23:41:05 matt-desktop kernel: [   40.785915] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
Oct 20 23:41:05 matt-desktop kernel: [   40.785951] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 20 23:41:05 matt-desktop kernel: [   40.821855] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 20 23:41:05 matt-desktop kernel: [   40.861877] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 20 23:41:05 matt-desktop kernel: [   40.901826] Linux agpgart interface v0.102
Oct 20 23:41:05 matt-desktop kernel: [   41.075241] input: Power Button (FF) as /devices/virtual/input/input8
Oct 20 23:41:05 matt-desktop kernel: [   41.202791] ACPI: Power Button (FF) [PWRF]
Oct 20 23:41:05 matt-desktop kernel: [   41.202853] input: Power Button (CM) as /devices/virtual/input/input9
Oct 20 23:41:05 matt-desktop kernel: [   41.258772] ACPI: Power Button (CM) [PWRB]
Oct 20 23:41:05 matt-desktop kernel: [   41.516623] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 20
Oct 20 23:41:05 matt-desktop kernel: [   41.527792] phy0: Selected rate control algorithm 'simple'
Oct 20 23:41:05 matt-desktop kernel: [   42.088745] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:41:05 matt-desktop kernel: [   42.088757] PCI: Setting latency timer of device 0000:04:00.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   42.088785] sky2 0000:04:00.0: v1.20 addr 0xf7000000 irq 16 Yukon-EC Ultra (0xb4) rev 2
Oct 20 23:41:05 matt-desktop kernel: [   42.089812] sky2 eth0: addr 00:1a:4d:63:cd:b2
Oct 20 23:41:05 matt-desktop kernel: [   42.236274] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
Oct 20 23:41:05 matt-desktop kernel: [   42.236301] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Oct 20 23:41:05 matt-desktop kernel: [   42.355776] Linux video capture interface: v2.00
Oct 20 23:41:05 matt-desktop kernel: [   42.400946] usbcore: registered new interface driver snd-usb-audio
Oct 20 23:41:05 matt-desktop kernel: [   42.407955] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
Oct 20 23:41:05 matt-desktop kernel: [   42.412213] usbcore: registered new interface driver gspca
Oct 20 23:41:05 matt-desktop kernel: [   42.412218] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Oct 20 23:41:05 matt-desktop kernel: [   42.471044] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
Oct 20 23:41:05 matt-desktop kernel: [   42.471088] usbcore: registered new interface driver sn9c102
Oct 20 23:41:05 matt-desktop kernel: [   43.332736] lp0: using parport0 (interrupt-driven).
Oct 20 23:41:05 matt-desktop kernel: [   43.401048] Adding 2000084k swap on /dev/sda3.  Priority:-1 extents:1 across:2000084k
Oct 20 23:41:05 matt-desktop kernel: [   43.954147] EXT3 FS on sda4, internal journal
Oct 20 23:41:05 matt-desktop kernel: [   44.885257] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 20 23:41:05 matt-desktop kernel: [   45.176987] No dock devices found.
Oct 20 23:41:05 matt-desktop NetworkManager: <info>  starting... 
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: Successfully dropped root privileges.
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: avahi-daemon 0.6.22 starting up.
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: Successfully called chroot().
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: Successfully dropped remaining capabilities.
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: No service file found in /etc/avahi/services.
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: Network interface enumeration completed.
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 20 23:41:05 matt-desktop avahi-daemon[5476]: Server startup complete. Host name is matt-desktop.local. Local service cookie is 3400978361.
Oct 20 23:41:05 matt-desktop kernel: [   46.054369] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Oct 20 23:41:05 matt-desktop kernel: [   46.054374] apm: disabled - APM is not SMP safe.
Oct 20 23:41:05 matt-desktop kernel: [   46.181867] ppdev: user-space parallel port driver
Oct 20 23:41:06 matt-desktop kernel: [   46.237260] audit(1224542466.024:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5518 profile="/usr/sbin/cupsd" namespace="default"
Oct 20 23:41:06 matt-desktop dhcdbd: Started up.
Oct 20 23:41:07 matt-desktop kernel: [   47.326230] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
Oct 20 23:41:08 matt-desktop hcid[5763]: Bluetooth HCI daemon
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'rt61pci'. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Deactivating device wlan0. 
Oct 20 23:41:08 matt-desktop kernel: [   48.296540] Bluetooth: Core ver 2.11
Oct 20 23:41:08 matt-desktop kernel: [   48.296799] NET: Registered protocol family 31
Oct 20 23:41:08 matt-desktop kernel: [   48.296803] Bluetooth: HCI device and connection manager initialized
Oct 20 23:41:08 matt-desktop kernel: [   48.296807] Bluetooth: HCI socket layer initialized
Oct 20 23:41:08 matt-desktop hcid[5763]: Starting SDP server
Oct 20 23:41:08 matt-desktop kernel: [   48.315516] Bluetooth: L2CAP ver 2.9
Oct 20 23:41:08 matt-desktop kernel: [   48.315521] Bluetooth: L2CAP socket layer initialized
Oct 20 23:41:08 matt-desktop hcid[5763]: Created local server at unix:abstract=/var/run/dbus-QrN0TwThym,guid=11b87cf9d74cd97681f2017f48fd0904
Oct 20 23:41:08 matt-desktop kernel: [   48.320105] sky2 eth0: enabling interface
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Deactivating device eth0. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 20 23:41:08 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 20 23:41:08 matt-desktop input[5784]: Bluetooth Input daemon
Oct 20 23:41:08 matt-desktop input[5784]: Registered input manager path:/org/bluez/input
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) started... 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 23:41:08 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 20 23:41:08 matt-desktop audio[5788]: Bluetooth Audio daemon
Oct 20 23:41:08 matt-desktop audio[5788]: Unix socket created: 5
Oct 20 23:41:08 matt-desktop audio[5788]: audio.conf: Key file does not have key 'Enable'
Oct 20 23:41:08 matt-desktop audio[5788]: audio.conf: Key file does not have key 'Disable'
Oct 20 23:41:08 matt-desktop NetworkManager: <debug> [1224542468.165329] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Oct 20 23:41:08 matt-desktop kernel: [   48.375682] Bluetooth: RFCOMM socket layer initialized
Oct 20 23:41:08 matt-desktop kernel: [   48.375697] Bluetooth: RFCOMM TTY layer initialized
Oct 20 23:41:08 matt-desktop kernel: [   48.375699] Bluetooth: RFCOMM ver 1.8
Oct 20 23:41:08 matt-desktop audio[5788]: add_service_record: got record id 0x10000
Oct 20 23:41:08 matt-desktop audio[5788]: audio.conf: Key file does not have key 'Disable'
Oct 20 23:41:08 matt-desktop audio[5788]: audio.conf: Key file does not have group 'A2DP'
Oct 20 23:41:08 matt-desktop last message repeated 3 times
Oct 20 23:41:08 matt-desktop audio[5788]: SEP 0x806d790 registered: type:0 codec:0 seid:1
Oct 20 23:41:08 matt-desktop audio[5788]: add_service_record: got record id 0x10001
Oct 20 23:41:08 matt-desktop audio[5788]: add_service_record: got record id 0x10002
Oct 20 23:41:08 matt-desktop audio[5788]: add_service_record: got record id 0x10003
Oct 20 23:41:08 matt-desktop audio[5788]: Registered manager path:/org/bluez/audio
Oct 20 23:41:09 matt-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct 20 23:41:09 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 20 23:41:09 matt-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 20 23:41:09 matt-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Oct 20 23:41:09 matt-desktop NetworkManager: <info>  Deactivating device eth0. 
Oct 20 23:41:09 matt-desktop NetworkManager: <info>  Activation (eth0): cancelling... 
Oct 20 23:41:09 matt-desktop NetworkManager: <info>  Activation (eth0) cancellation handler scheduled... 
Oct 20 23:41:09 matt-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Oct 20 23:41:09 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 23:41:09 matt-desktop last message repeated 2 times
Oct 20 23:41:09 matt-desktop kernel: [   49.716080] NET: Registered protocol family 17
Oct 20 23:41:10 matt-desktop kernel: [   50.257224] [drm] Initialized drm 1.1.0 20060810
Oct 20 23:41:10 matt-desktop NetworkManager: <info>  Activation (eth0) cancellation handled. 
Oct 20 23:41:10 matt-desktop NetworkManager: <info>  Activation (eth0): cancelled. 
Oct 20 23:41:10 matt-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Oct 20 23:41:10 matt-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Oct 20 23:41:10 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 23:41:10 matt-desktop anacron[5958]: Anacron 2.3 started on 2008-10-20
Oct 20 23:41:10 matt-desktop anacron[5958]: Will run job `cron.daily' in 5 min.
Oct 20 23:41:10 matt-desktop anacron[5958]: Will run job `cron.weekly' in 10 min.
Oct 20 23:41:10 matt-desktop anacron[5958]: Will run job `cron.monthly' in 15 min.
Oct 20 23:41:10 matt-desktop anacron[5958]: Jobs will be executed sequentially
Oct 20 23:41:10 matt-desktop /usr/sbin/cron[5985]: (CRON) INFO (pidfile fd = 3)
Oct 20 23:41:10 matt-desktop /usr/sbin/cron[5986]: (CRON) STARTUP (fork ok)
Oct 20 23:41:10 matt-desktop /usr/sbin/cron[5986]: (CRON) INFO (Running @reboot jobs)
Oct 20 23:41:13 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Oct 20 23:41:16 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct 20 23:41:21 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Oct 20 23:41:21 matt-desktop kernel: [   61.845818] NET: Registered protocol family 10
Oct 20 23:41:21 matt-desktop kernel: [   61.846063] lo: Disabled Privacy Extensions
Oct 20 23:41:21 matt-desktop kernel: [   61.846658] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 20 23:41:21 matt-desktop kernel: [   61.846891] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 20 23:41:21 matt-desktop pulseaudio[6202]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Oct 20 23:41:21 matt-desktop pulseaudio[6202]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct 20 23:41:23 matt-desktop hcid[5763]: Default passkey agent (:1.21, /org/bluez/passkey) registered
Oct 20 23:41:23 matt-desktop hcid[5763]: Default authorization agent (:1.21, /org/bluez/auth) registered
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Oct 20 23:41:26 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Will activate connection 'wlan0/ASpunkMonkey'. 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Device wlan0 activation scheduled... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) started... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'ASpunkMonkey' is encrypted, but NO valid key exists.  New key needed. 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'ASpunkMonkey'. 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'ASpunkMonkey' received. 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 23:41:26 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'ASpunkMonkey' is encrypted, and a key exists.  No new key needed. 
Oct 20 23:41:27 matt-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop hald: mounted /dev/sdb on behalf of uid 1000
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was '0' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 415370756e6b4d6f6e6b6579' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:41:28 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 23:41:29 matt-desktop kernel: [   69.348353] wlan0: Initial auth_alg=0
Oct 20 23:41:29 matt-desktop kernel: [   69.348359] wlan0: authenticate with AP 00:1f:9f:42:15:e5
Oct 20 23:41:29 matt-desktop kernel: [   69.350142] wlan0: RX authentication from 00:1f:9f:42:15:e5 (alg=0 transaction=2 status=0)
Oct 20 23:41:29 matt-desktop kernel: [   69.350148] wlan0: authenticated
Oct 20 23:41:29 matt-desktop kernel: [   69.350153] wlan0: associate with AP 00:1f:9f:42:15:e5
Oct 20 23:41:29 matt-desktop kernel: [   69.352904] wlan0: RX AssocResp from 00:1f:9f:42:15:e5 (capab=0x411 status=0 aid=2)
Oct 20 23:41:29 matt-desktop kernel: [   69.352910] wlan0: associated
Oct 20 23:41:29 matt-desktop kernel: [   69.352916] wlan0: switched to short barker preamble (BSSID=00:1f:9f:42:15:e5)
Oct 20 23:41:29 matt-desktop kernel: [   69.354955] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 20 23:41:29 matt-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct 20 23:41:29 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'ASpunkMonkey'. 
Oct 20 23:41:29 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 20 23:41:29 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Oct 20 23:41:30 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Oct 20 23:41:30 matt-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Oct 20 23:41:30 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 20 23:41:30 matt-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Oct 20 23:41:30 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 23:41:30 matt-desktop avahi-daemon[5476]: Registering new address record for fe80::21a:70ff:fe3c:8dbf on wlan0.*.
Oct 20 23:41:31 matt-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Oct 20 23:41:31 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 23:41:34 matt-desktop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Oct 20 23:41:35 matt-desktop dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 255.255.255.255 port 67
Oct 20 23:41:35 matt-desktop dhclient: DHCPACK of 192.168.1.67 from 192.168.1.254
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: Registering new address record for 192.168.1.67 on wlan0.IPv4.
Oct 20 23:41:35 matt-desktop dhclient: bound to 192.168.1.67 -- renewal in 39715 seconds.
Oct 20 23:41:35 matt-desktop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface wlan0 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Oct 20 23:41:35 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Oct 20 23:41:35 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Oct 20 23:41:35 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Oct 20 23:41:35 matt-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>    address 192.168.1.67 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>    netmask 255.255.255.0 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>    broadcast 192.168.1.255 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>    gateway 192.168.1.254 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>    nameserver 192.168.1.254 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>    domain name 'config' 
Oct 20 23:41:35 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Oct 20 23:41:35 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Oct 20 23:41:35 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: Withdrawing address record for 192.168.1.67 on wlan0.
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: Withdrawing address record for fe80::21a:70ff:fe3c:8dbf on wlan0.
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 23:41:35 matt-desktop avahi-daemon[5476]: Registering new address record for 192.168.1.67 on wlan0.IPv4.
Oct 20 23:41:36 matt-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 20 23:41:36 matt-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 20 23:41:36 matt-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Oct 20 23:41:36 matt-desktop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Oct 20 23:41:36 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 20 23:41:36 matt-desktop ntpdate[6472]: step time server 91.189.94.4 offset 82816.228036 sec
Oct 21 22:41:53 matt-desktop avahi-daemon[5476]: Registering new address record for fe80::21a:70ff:fe3c:8dbf on wlan0.*.
Oct 21 22:42:00 matt-desktop dhclient: No DHCPOFFERS received.
Oct 21 22:42:00 matt-desktop avahi-autoipd(eth0)[6490]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 21 22:42:00 matt-desktop avahi-autoipd(eth0)[6490]: Successfully called chroot().
Oct 21 22:42:00 matt-desktop avahi-autoipd(eth0)[6490]: Successfully dropped root privileges.
Oct 21 22:42:00 matt-desktop avahi-autoipd(eth0)[6490]: Starting with address 169.254.8.140
Oct 21 22:42:02 matt-desktop kernel: [   86.911130] wlan0: no IPv6 routers present
Oct 21 22:42:05 matt-desktop avahi-autoipd(eth0)[6490]: Callout BIND, address 169.254.8.140 on interface eth0
Oct 21 22:42:05 matt-desktop avahi-daemon[5476]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.140.
Oct 21 22:42:05 matt-desktop avahi-daemon[5476]: New relevant interface eth0.IPv4 for mDNS.
Oct 21 22:42:05 matt-desktop avahi-daemon[5476]: Registering new address record for 169.254.8.140 on eth0.IPv4.
Oct 21 22:42:09 matt-desktop avahi-autoipd(eth0)[6490]: Successfully claimed IP address 169.254.8.140
Oct 20 23:46:16 matt-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct 20 23:46:16 matt-desktop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Oct 20 23:46:16 matt-desktop kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Oct 20 23:46:16 matt-desktop kernel: Symbols match kernel version 2.6.24.
Oct 20 23:46:16 matt-desktop kernel: Loaded 19939 symbols from 100 modules.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] 1150MB HIGHMEM available.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] 896MB LOWMEM available.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] found SMP MP-table at 000f5360
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Entering add_active_range(0, 0, 524000) 0 entries of 256 used
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Zone PFN ranges:
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   DMA             0 ->     4096
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   Normal       4096 ->   229376
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   HighMem    229376 ->   524000
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]     0:        0 ->   524000
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] On node 0 totalpages: 524000
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   HighMem zone: 292323 pages, LIFO batch:31
Oct 20 23:46:16 matt-desktop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] DMI 2.4 present.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6CF0 checksum 0
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: RSDP 000F6CF0, 0014 (r0 GBT   )
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: RSDT 7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: DSDT 7FEE3180, 49F4 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: HPET 7FEE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: MCFG 7FEE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: APIC 7FEE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: SSDT 7FEE7DC0, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: SSDT 7FEE8250, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519907
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Kernel command line: root=UUID=6c75aea6-38fc-4a0b-a141-d73c7506188f ro quiet splash
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Initializing CPU#0
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Oct 20 23:46:16 matt-desktop kernel: [    0.000000] Detected 1809.048 MHz processor.
Oct 20 23:46:16 matt-desktop kernel: [   21.339329] Console: colour VGA+ 80x25
Oct 20 23:46:16 matt-desktop kernel: [   21.339333] console [tty0] enabled
Oct 20 23:46:16 matt-desktop kernel: [   21.339557] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Oct 20 23:46:16 matt-desktop kernel: [   21.339815] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 20 23:46:16 matt-desktop kernel: [   21.427849] Memory: 2065688k/2096000k available (2177k kernel code, 29084k reserved, 1006k data, 368k init, 1178496k highmem)
Oct 20 23:46:16 matt-desktop kernel: [   21.427856] virtual kernel memory layout:
Oct 20 23:46:16 matt-desktop kernel: [   21.427857]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 20 23:46:16 matt-desktop kernel: [   21.427858]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 20 23:46:16 matt-desktop kernel: [   21.427859]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Oct 20 23:46:16 matt-desktop kernel: [   21.427860]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Oct 20 23:46:16 matt-desktop kernel: [   21.427861]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 20 23:46:16 matt-desktop kernel: [   21.427862]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
Oct 20 23:46:16 matt-desktop kernel: [   21.427863]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
Oct 20 23:46:16 matt-desktop kernel: [   21.427865] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 20 23:46:16 matt-desktop kernel: [   21.427904] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Oct 20 23:46:16 matt-desktop kernel: [   21.428040] hpet clockevent registered
Oct 20 23:46:16 matt-desktop kernel: [   21.508036] Calibrating delay using timer specific routine.. 3620.90 BogoMIPS (lpj=7241807)
Oct 20 23:46:16 matt-desktop kernel: [   21.508056] Security Framework initialized
Oct 20 23:46:16 matt-desktop kernel: [   21.508062] SELinux:  Disabled at boot.
Oct 20 23:46:16 matt-desktop kernel: [   21.508074] AppArmor: AppArmor initialized
Oct 20 23:46:16 matt-desktop kernel: [   21.508078] Failure registering capabilities with primary security module.
Oct 20 23:46:16 matt-desktop kernel: [   21.508085] Mount-cache hash table entries: 512
Oct 20 23:46:16 matt-desktop kernel: [   21.508203] Initializing cgroup subsys ns
Oct 20 23:46:16 matt-desktop kernel: [   21.508207] Initializing cgroup subsys cpuacct
Oct 20 23:46:16 matt-desktop kernel: [   21.508217] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Oct 20 23:46:16 matt-desktop kernel: [   21.508225] monitor/mwait feature present.
Oct 20 23:46:16 matt-desktop kernel: [   21.508226] using mwait in idle threads.
Oct 20 23:46:16 matt-desktop kernel: [   21.508230] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 20 23:46:16 matt-desktop kernel: [   21.508232] CPU: L2 cache: 2048K
Oct 20 23:46:16 matt-desktop kernel: [   21.508234] CPU: Physical Processor ID: 0
Oct 20 23:46:16 matt-desktop kernel: [   21.508236] CPU: Processor Core ID: 0
Oct 20 23:46:16 matt-desktop kernel: [   21.508238] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Oct 20 23:46:16 matt-desktop kernel: [   21.508246] Compat vDSO mapped to ffffe000.
Oct 20 23:46:16 matt-desktop kernel: [   21.508258] Checking 'hlt' instruction... OK.
Oct 20 23:46:16 matt-desktop kernel: [   21.524491] SMP alternatives: switching to UP code
Oct 20 23:46:16 matt-desktop kernel: [   21.526064] Early unpacking initramfs... done
Oct 20 23:46:16 matt-desktop kernel: [   21.856723] ACPI: Core revision 20070126
Oct 20 23:46:16 matt-desktop kernel: [   21.856761] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 20 23:46:16 matt-desktop kernel: [   21.998333] CPU0: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
Oct 20 23:46:16 matt-desktop kernel: [   21.998350] SMP alternatives: switching to SMP code
Oct 20 23:46:16 matt-desktop kernel: [   21.999070] Booting processor 1/1 eip 3000
Oct 20 23:46:16 matt-desktop kernel: [   22.009232] Initializing CPU#1
Oct 20 23:46:16 matt-desktop kernel: [   22.087966] Calibrating delay using timer specific routine.. 3618.00 BogoMIPS (lpj=7236018)
Oct 20 23:46:16 matt-desktop kernel: [   22.087972] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Oct 20 23:46:16 matt-desktop kernel: [   22.087977] monitor/mwait feature present.
Oct 20 23:46:16 matt-desktop kernel: [   22.087980] CPU: L1 I cache: 32K, L1 D cache: 32K
Oct 20 23:46:16 matt-desktop kernel: [   22.087981] CPU: L2 cache: 2048K
Oct 20 23:46:16 matt-desktop kernel: [   22.087983] CPU: Physical Processor ID: 0
Oct 20 23:46:16 matt-desktop kernel: [   22.087984] CPU: Processor Core ID: 1
Oct 20 23:46:16 matt-desktop kernel: [   22.087986] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Oct 20 23:46:16 matt-desktop kernel: [   22.088490] CPU1: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
Oct 20 23:46:16 matt-desktop kernel: [   22.088510] Total of 2 processors activated (7238.91 BogoMIPS).
Oct 20 23:46:16 matt-desktop kernel: [   22.088652] ENABLING IO-APIC IRQs
Oct 20 23:46:16 matt-desktop kernel: [   22.088818] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 20 23:46:16 matt-desktop kernel: [   22.236053] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 20 23:46:16 matt-desktop kernel: [   22.256066] Brought up 2 CPUs
Oct 20 23:46:16 matt-desktop kernel: [   22.256089] CPU0 attaching sched-domain:
Oct 20 23:46:16 matt-desktop kernel: [   22.256091]  domain 0: span 03
Oct 20 23:46:16 matt-desktop kernel: [   22.256093]   groups: 01 02
Oct 20 23:46:16 matt-desktop kernel: [   22.256096] CPU1 attaching sched-domain:
Oct 20 23:46:16 matt-desktop kernel: [   22.256097]  domain 0: span 03
Oct 20 23:46:16 matt-desktop kernel: [   22.256099]   groups: 02 01
Oct 20 23:46:16 matt-desktop kernel: [   22.256317] net_namespace: 64 bytes
Oct 20 23:46:16 matt-desktop kernel: [   22.256328] Booting paravirtualized kernel on bare hardware
Oct 20 23:46:16 matt-desktop kernel: [   22.256742] Time: 23:45:58  Date: 10/20/08
Oct 20 23:46:16 matt-desktop kernel: [   22.256768] NET: Registered protocol family 16
Oct 20 23:46:16 matt-desktop kernel: [   22.256950] EISA bus registered
Oct 20 23:46:16 matt-desktop kernel: [   22.256955] ACPI: bus type pci registered
Oct 20 23:46:16 matt-desktop kernel: [   22.262978] PCI: PCI BIOS revision 3.00 entry at 0xfb430, last bus=5
Oct 20 23:46:16 matt-desktop kernel: [   22.262980] PCI: Using configuration type 1
Oct 20 23:46:16 matt-desktop kernel: [   22.263004] Setting up standard PCI resources
Oct 20 23:46:16 matt-desktop kernel: [   22.263693] mtrr: your CPUs had inconsistent variable MTRR settings
Oct 20 23:46:16 matt-desktop kernel: [   22.263695] mtrr: probably your BIOS does not setup all CPUs.
Oct 20 23:46:16 matt-desktop kernel: [   22.263696] mtrr: corrected configuration.
Oct 20 23:46:16 matt-desktop kernel: [   22.264948] ACPI: EC: Look up EC in DSDT
Oct 20 23:46:16 matt-desktop kernel: [   22.268898] ACPI: Interpreter enabled
Oct 20 23:46:16 matt-desktop kernel: [   22.268903] ACPI: (supports S0 S1 S4 S5)
Oct 20 23:46:16 matt-desktop kernel: [   22.268921] ACPI: Using IOAPIC for interrupt routing
Oct 20 23:46:16 matt-desktop kernel: [   22.273314] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 20 23:46:16 matt-desktop kernel: [   22.273970] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Oct 20 23:46:16 matt-desktop kernel: [   22.273974] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Oct 20 23:46:16 matt-desktop kernel: [   22.274842] PCI: Transparent bridge - 0000:00:1e.0
Oct 20 23:46:16 matt-desktop kernel: [   22.274874] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Oct 20 23:46:16 matt-desktop kernel: [   22.275012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Oct 20 23:46:16 matt-desktop kernel: [   22.275083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Oct 20 23:46:16 matt-desktop kernel: [   22.275155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Oct 20 23:46:16 matt-desktop kernel: [   22.275224] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Oct 20 23:46:16 matt-desktop kernel: [   22.285646] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Oct 20 23:46:16 matt-desktop kernel: [   22.285741] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 23:46:16 matt-desktop kernel: [   22.285838] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Oct 20 23:46:16 matt-desktop kernel: [   22.285931] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Oct 20 23:46:16 matt-desktop kernel: [   22.286023] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Oct 20 23:46:16 matt-desktop kernel: [   22.286116] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
Oct 20 23:46:16 matt-desktop kernel: [   22.286208] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Oct 20 23:46:16 matt-desktop kernel: [   22.286300] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Oct 20 23:46:16 matt-desktop kernel: [   22.286426] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 20 23:46:16 matt-desktop kernel: [   22.286455] pnp: PnP ACPI init
Oct 20 23:46:16 matt-desktop kernel: [   22.286462] ACPI: bus type pnp registered
Oct 20 23:46:16 matt-desktop kernel: [   22.288556] pnpacpi: exceeded the max number of mem resources: 12
Oct 20 23:46:16 matt-desktop kernel: [   22.288694] pnp: PnP ACPI: found 12 devices
Oct 20 23:46:16 matt-desktop kernel: [   22.288696] ACPI: ACPI bus type pnp unregistered
Oct 20 23:46:16 matt-desktop kernel: [   22.288700] PnPBIOS: Disabled by ACPI PNP
Oct 20 23:46:16 matt-desktop kernel: [   22.288924] PCI: Using ACPI for IRQ routing
Oct 20 23:46:16 matt-desktop kernel: [   22.288927] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 20 23:46:16 matt-desktop kernel: [   22.348063] NET: Registered protocol family 8
Oct 20 23:46:16 matt-desktop kernel: [   22.348066] NET: Registered protocol family 20
Oct 20 23:46:16 matt-desktop kernel: [   22.348111] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 20 23:46:16 matt-desktop kernel: [   22.348117] hpet0: 3 64-bit timers, 14318180 Hz
Oct 20 23:46:16 matt-desktop kernel: [   22.349152] AppArmor: AppArmor Filesystem Enabled
Oct 20 23:46:16 matt-desktop kernel: [   22.352074] Time: tsc clocksource has been installed.
Oct 20 23:46:16 matt-desktop kernel: [   22.352089] Switched to high resolution mode on CPU 0
Oct 20 23:46:16 matt-desktop kernel: [   22.352184] Switched to high resolution mode on CPU 1
Oct 20 23:46:16 matt-desktop kernel: [   22.368128] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368132] system 00:01: ioport range 0x290-0x29f has been reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368138] system 00:01: ioport range 0x800-0x87f has been reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368141] system 00:01: ioport range 0x290-0x294 has been reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368145] system 00:01: ioport range 0x880-0x88f has been reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368158] system 00:08: ioport range 0x400-0x4bf could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368166] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368175] system 00:0a: iomem range 0xcf600-0xcffff has been reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368179] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368182] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368186] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368190] system 00:0a: iomem range 0x7fee0000-0x7fefffff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368194] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368198] system 00:0a: iomem range 0x100000-0x7fedffff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368202] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368206] system 00:0a: iomem range 0xfed10000-0xfed1dfff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368210] system 00:0a: iomem range 0xfed20000-0xfed8ffff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368214] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.368218] system 00:0a: iomem range 0xffb00000-0xffb7ffff could not be reserved
Oct 20 23:46:16 matt-desktop kernel: [   22.398681] PCI: Bridge: 0000:00:01.0
Oct 20 23:46:16 matt-desktop kernel: [   22.398683]   IO window: 8000-8fff
Oct 20 23:46:16 matt-desktop kernel: [   22.398687]   MEM window: f4000000-f5ffffff
Oct 20 23:46:16 matt-desktop kernel: [   22.398690]   PREFETCH window: e0000000-efffffff
Oct 20 23:46:16 matt-desktop kernel: [   22.398693] PCI: Bridge: 0000:00:1c.0
Oct 20 23:46:16 matt-desktop kernel: [   22.398695]   IO window: 7000-7fff
Oct 20 23:46:16 matt-desktop kernel: [   22.398699]   MEM window: disabled.
Oct 20 23:46:16 matt-desktop kernel: [   22.398702]   PREFETCH window: disabled.
Oct 20 23:46:16 matt-desktop kernel: [   22.398706] PCI: Bridge: 0000:00:1c.3
Oct 20 23:46:16 matt-desktop kernel: [   22.398709]   IO window: 9000-afff
Oct 20 23:46:16 matt-desktop kernel: [   22.398713]   MEM window: f8000000-f80fffff
Oct 20 23:46:16 matt-desktop kernel: [   22.398716]   PREFETCH window: disabled.
Oct 20 23:46:16 matt-desktop kernel: [   22.398720] PCI: Bridge: 0000:00:1c.4
Oct 20 23:46:16 matt-desktop kernel: [   22.398723]   IO window: b000-bfff
Oct 20 23:46:16 matt-desktop kernel: [   22.398727]   MEM window: f6000000-f7ffffff
Oct 20 23:46:16 matt-desktop kernel: [   22.398730]   PREFETCH window: 80000000-800fffff
Oct 20 23:46:16 matt-desktop kernel: [   22.398735] PCI: Bridge: 0000:00:1e.0
Oct 20 23:46:16 matt-desktop kernel: [   22.398736]   IO window: disabled.
Oct 20 23:46:16 matt-desktop kernel: [   22.398740]   MEM window: f8100000-f81fffff
Oct 20 23:46:16 matt-desktop kernel: [   22.398743]   PREFETCH window: disabled.
Oct 20 23:46:16 matt-desktop kernel: [   22.398757] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:46:16 matt-desktop kernel: [   22.398762] PCI: Setting latency timer of device 0000:00:01.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   22.398779] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:46:16 matt-desktop kernel: [   22.398783] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   22.398800] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:46:16 matt-desktop kernel: [   22.398804] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 20 23:46:16 matt-desktop kernel: [   22.398820] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:46:16 matt-desktop kernel: [   22.398825] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Oct 20 23:46:16 matt-desktop kernel: [   22.398834] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   22.398844] NET: Registered protocol family 2
Oct 20 23:46:16 matt-desktop kernel: [   22.436142] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 20 23:46:16 matt-desktop kernel: [   22.436399] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Oct 20 23:46:16 matt-desktop kernel: [   22.436800] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Oct 20 23:46:16 matt-desktop kernel: [   22.437010] TCP: Hash tables configured (established 131072 bind 65536)
Oct 20 23:46:16 matt-desktop kernel: [   22.437013] TCP reno registered
Oct 20 23:46:16 matt-desktop kernel: [   22.448225] checking if image is initramfs... it is
Oct 20 23:46:16 matt-desktop kernel: [   23.101266] Freeing initrd memory: 7702k freed
Oct 20 23:46:16 matt-desktop kernel: [   23.102016] audit: initializing netlink socket (disabled)
Oct 20 23:46:16 matt-desktop kernel: [   23.102028] audit(1224546358.413:1): initialized
Oct 20 23:46:16 matt-desktop kernel: [   23.102233] highmem bounce pool size: 64 pages
Oct 20 23:46:16 matt-desktop kernel: [   23.104129] VFS: Disk quotas dquot_6.5.1
Oct 20 23:46:16 matt-desktop kernel: [   23.104200] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 20 23:46:16 matt-desktop kernel: [   23.104326] io scheduler noop registered
Oct 20 23:46:16 matt-desktop kernel: [   23.104328] io scheduler anticipatory registered
Oct 20 23:46:16 matt-desktop kernel: [   23.104329] io scheduler deadline registered
Oct 20 23:46:16 matt-desktop kernel: [   23.104342] io scheduler cfq registered (default)
Oct 20 23:46:16 matt-desktop kernel: [   23.104450] Boot video device is 0000:01:00.0
Oct 20 23:46:16 matt-desktop kernel: [   23.104551] PCI: Setting latency timer of device 0000:00:01.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   23.104585] assign_interrupt_mode Found MSI capability
Oct 20 23:46:16 matt-desktop kernel: [   23.104613] Allocate Port Service[0000:00:01.0:pcie00]
Oct 20 23:46:16 matt-desktop kernel: [   23.104687] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   23.104725] assign_interrupt_mode Found MSI capability
Oct 20 23:46:16 matt-desktop kernel: [   23.104756] Allocate Port Service[0000:00:1c.0:pcie00]
Oct 20 23:46:16 matt-desktop kernel: [   23.104786] Allocate Port Service[0000:00:1c.0:pcie02]
Oct 20 23:46:16 matt-desktop kernel: [   23.104863] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Oct 20 23:46:16 matt-desktop kernel: [   23.104901] assign_interrupt_mode Found MSI capability
Oct 20 23:46:16 matt-desktop kernel: [   23.104932] Allocate Port Service[0000:00:1c.3:pcie00]
Oct 20 23:46:16 matt-desktop kernel: [   23.104964] Allocate Port Service[0000:00:1c.3:pcie02]
Oct 20 23:46:16 matt-desktop kernel: [   23.105041] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Oct 20 23:46:16 matt-desktop kernel: [   23.105079] assign_interrupt_mode Found MSI capability
Oct 20 23:46:16 matt-desktop kernel: [   23.105109] Allocate Port Service[0000:00:1c.4:pcie00]
Oct 20 23:46:16 matt-desktop kernel: [   23.105141] Allocate Port Service[0000:00:1c.4:pcie02]
Oct 20 23:46:16 matt-desktop kernel: [   23.105374] isapnp: Scanning for PnP cards...
Oct 20 23:46:16 matt-desktop kernel: [   23.458578] isapnp: No Plug & Play device found
Oct 20 23:46:16 matt-desktop kernel: [   23.482702] Real Time Clock Driver v1.12ac
Oct 20 23:46:16 matt-desktop kernel: [   23.482812] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 20 23:46:16 matt-desktop kernel: [   23.482928] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 23:46:16 matt-desktop kernel: [   23.483486] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 20 23:46:16 matt-desktop kernel: [   23.484215] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 20 23:46:16 matt-desktop kernel: [   23.484277] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 20 23:46:16 matt-desktop kernel: [   23.484410] PNP: No PS/2 controller found. Probing ports directly.
Oct 20 23:46:16 matt-desktop kernel: [   23.484731] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 20 23:46:16 matt-desktop kernel: [   23.484736] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct 20 23:46:16 matt-desktop kernel: [   23.516052] mice: PS/2 mouse device common for all mice
Oct 20 23:46:16 matt-desktop kernel: [   23.516215] EISA: Probing bus 0 at eisa.0
Oct 20 23:46:16 matt-desktop kernel: [   23.516238] Cannot allocate resource for EISA slot 7
Oct 20 23:46:16 matt-desktop kernel: [   23.516240] Cannot allocate resource for EISA slot 8
Oct 20 23:46:16 matt-desktop kernel: [   23.516242] EISA: Detected 0 cards.
Oct 20 23:46:16 matt-desktop kernel: [   23.516245] cpuidle: using governor ladder
Oct 20 23:46:16 matt-desktop kernel: [   23.516246] cpuidle: using governor menu
Oct 20 23:46:16 matt-desktop kernel: [   23.516324] NET: Registered protocol family 1
Oct 20 23:46:16 matt-desktop kernel: [   23.516350] Using IPI No-Shortcut mode
Oct 20 23:46:16 matt-desktop kernel: [   23.516375] registered taskstats version 1
Oct 20 23:46:16 matt-desktop kernel: [   23.516485]   Magic number: 12:205:808
Oct 20 23:46:16 matt-desktop kernel: [   23.516519]   hash matches device ptys2
Oct 20 23:46:16 matt-desktop kernel: [   23.516541] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 20 23:46:16 matt-desktop kernel: [   23.516543] EDD information not available.
Oct 20 23:46:16 matt-desktop kernel: [   23.516699] Freeing unused kernel memory: 368k freed
Oct 20 23:46:16 matt-desktop kernel: [   24.717540] fuse init (API version 7.9)
Oct 20 23:46:16 matt-desktop kernel: [   24.735866] ACPI: Processor [CPU0] (supports 2 throttling states)
Oct 20 23:46:16 matt-desktop kernel: [   24.735982] ACPI: SSDT 7FEE81C0, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
Oct 20 23:46:16 matt-desktop kernel: [   24.736121] ACPI: Processor [CPU1] (supports 2 throttling states)
Oct 20 23:46:16 matt-desktop kernel: [   24.736134] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 20 23:46:16 matt-desktop kernel: [   24.736145] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Oct 20 23:46:16 matt-desktop kernel: [   24.856384] usbcore: registered new interface driver usbfs
Oct 20 23:46:16 matt-desktop kernel: [   24.856406] usbcore: registered new interface driver hub
Oct 20 23:46:16 matt-desktop kernel: [   24.863776] usbcore: registered new device driver usb
Oct 20 23:46:16 matt-desktop kernel: [   24.865136] USB Universal Host Controller Interface driver v3.0
Oct 20 23:46:16 matt-desktop kernel: [   24.865182] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:46:16 matt-desktop kernel: [   24.865194] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   24.865198] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Oct 20 23:46:16 matt-desktop kernel: [   24.865410] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Oct 20 23:46:16 matt-desktop kernel: [   24.865437] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c000
Oct 20 23:46:16 matt-desktop kernel: [   24.865563] usb usb1: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   24.865587] hub 1-0:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   24.865591] hub 1-0:1.0: 2 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   24.967819] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Oct 20 23:46:16 matt-desktop kernel: [   24.967831] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Oct 20 23:46:16 matt-desktop kernel: [   24.967835] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Oct 20 23:46:16 matt-desktop kernel: [   24.967859] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Oct 20 23:46:16 matt-desktop kernel: [   24.967885] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000c400
Oct 20 23:46:16 matt-desktop kernel: [   24.967999] usb usb2: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   24.968027] hub 2-0:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   24.968032] hub 2-0:1.0: 2 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   25.071801] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Oct 20 23:46:16 matt-desktop kernel: [   25.071812] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   25.071816] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 20 23:46:16 matt-desktop kernel: [   25.071839] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Oct 20 23:46:16 matt-desktop kernel: [   25.071865] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000c800
Oct 20 23:46:16 matt-desktop kernel: [   25.071967] usb usb3: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   25.071989] hub 3-0:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   25.071993] hub 3-0:1.0: 2 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   25.086225] SCSI subsystem initialized
Oct 20 23:46:16 matt-desktop kernel: [   25.093295] libata version 3.00 loaded.
Oct 20 23:46:16 matt-desktop kernel: [   25.175813] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:46:16 matt-desktop kernel: [   25.175825] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Oct 20 23:46:16 matt-desktop kernel: [   25.175829] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 20 23:46:16 matt-desktop kernel: [   25.175852] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Oct 20 23:46:16 matt-desktop kernel: [   25.175878] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000cc00
Oct 20 23:46:16 matt-desktop kernel: [   25.175990] usb usb4: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   25.176012] hub 4-0:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   25.176017] hub 4-0:1.0: 2 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   25.207697] usb 1-2: new low speed USB device using uhci_hcd and address 2
Oct 20 23:46:16 matt-desktop kernel: [   25.279800] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
Oct 20 23:46:16 matt-desktop kernel: [   25.279812] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Oct 20 23:46:16 matt-desktop kernel: [   25.279816] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 20 23:46:16 matt-desktop kernel: [   25.279839] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Oct 20 23:46:16 matt-desktop kernel: [   25.279863] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d000
Oct 20 23:46:16 matt-desktop kernel: [   25.279970] usb usb5: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   25.279996] hub 5-0:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   25.280001] hub 5-0:1.0: 2 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   25.376521] usb 1-2: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   25.383853] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
Oct 20 23:46:16 matt-desktop kernel: [   25.383866] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Oct 20 23:46:16 matt-desktop kernel: [   25.383870] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Oct 20 23:46:16 matt-desktop kernel: [   25.383892] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Oct 20 23:46:16 matt-desktop kernel: [   25.387804] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Oct 20 23:46:16 matt-desktop kernel: [   25.387810] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xf8205000
Oct 20 23:46:16 matt-desktop kernel: [   25.403660] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 20 23:46:16 matt-desktop kernel: [   25.403775] usb usb6: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   25.403798] hub 6-0:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   25.403803] hub 6-0:1.0: 4 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   25.507739] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Oct 20 23:46:16 matt-desktop kernel: [   25.507754] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Oct 20 23:46:16 matt-desktop kernel: [   25.507757] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 20 23:46:16 matt-desktop kernel: [   25.507780] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Oct 20 23:46:16 matt-desktop kernel: [   25.511693] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Oct 20 23:46:16 matt-desktop kernel: [   25.511699] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf8204000
Oct 20 23:46:16 matt-desktop kernel: [   25.523671] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 20 23:46:16 matt-desktop kernel: [   25.523785] usb usb7: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   25.523808] hub 7-0:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   25.523814] hub 7-0:1.0: 6 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   25.627891] ahci 0000:03:00.0: version 3.0
Oct 20 23:46:16 matt-desktop kernel: [   25.627932] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:46:16 matt-desktop kernel: [   26.215589] usb 6-3: new high speed USB device using ehci_hcd and address 3
Oct 20 23:46:16 matt-desktop kernel: [   26.349432] usb 6-3: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   26.349718] usb 1-2: USB disconnect, address 2
Oct 20 23:46:16 matt-desktop kernel: [   26.349859] usbcore: registered new interface driver hiddev
Oct 20 23:46:16 matt-desktop kernel: [   26.588550] usb 1-2: new low speed USB device using uhci_hcd and address 3
Oct 20 23:46:16 matt-desktop kernel: [   26.631555] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Oct 20 23:46:16 matt-desktop kernel: [   26.631561] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Oct 20 23:46:16 matt-desktop kernel: [   26.631569] PCI: Setting latency timer of device 0000:03:00.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   26.631723] scsi0 : ahci
Oct 20 23:46:16 matt-desktop kernel: [   26.631902] scsi1 : ahci
Oct 20 23:46:16 matt-desktop kernel: [   26.631962] ata1: SATA max UDMA/133 abar m8192@0xf8000000 port 0xf8000100 irq 17
Oct 20 23:46:16 matt-desktop kernel: [   26.631966] ata2: SATA max UDMA/133 abar m8192@0xf8000000 port 0xf8000180 irq 17
Oct 20 23:46:16 matt-desktop kernel: [   26.759450] usb 1-2: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   26.951511] ata1: SATA link down (SStatus 0 SControl 300)
Oct 20 23:46:16 matt-desktop kernel: [   26.999491] usb 7-5: new high speed USB device using ehci_hcd and address 2
Oct 20 23:46:16 matt-desktop kernel: [   27.131872] usb 7-5: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   27.132039] hub 7-5:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   27.132134] hub 7-5:1.0: 4 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   27.271468] ata2: SATA link down (SStatus 0 SControl 300)
Oct 20 23:46:16 matt-desktop kernel: [   27.271995] ata_piix 0000:00:1f.2: version 2.12
Oct 20 23:46:16 matt-desktop kernel: [   27.272001] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Oct 20 23:46:16 matt-desktop kernel: [   27.427439] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:46:16 matt-desktop kernel: [   27.427477] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Oct 20 23:46:16 matt-desktop kernel: [   27.427532] scsi2 : ata_piix
Oct 20 23:46:16 matt-desktop kernel: [   27.427732] scsi3 : ata_piix
Oct 20 23:46:16 matt-desktop kernel: [   27.428206] ata3: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Oct 20 23:46:16 matt-desktop kernel: [   27.428209] ata4: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Oct 20 23:46:16 matt-desktop kernel: [   27.488535] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input1
Oct 20 23:46:16 matt-desktop kernel: [   27.511471] input,hidraw0: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:1a.0-2
Oct 20 23:46:16 matt-desktop kernel: [   27.611586] ata3.00: HPA unlocked: 488279137 -> 488281250, native 488281250
Oct 20 23:46:16 matt-desktop kernel: [   27.611595] ata3.00: ATA-7: Maxtor 7L250S0, BANC1G10, max UDMA/133
Oct 20 23:46:16 matt-desktop kernel: [   27.611600] ata3.00: 488281250 sectors, multi 16: LBA48 NCQ (not used)
Oct 20 23:46:16 matt-desktop kernel: [   27.624535] ata3.00: configured for UDMA/133
Oct 20 23:46:16 matt-desktop kernel: [   27.675478] usb 7-5.4: new full speed USB device using ehci_hcd and address 4
Oct 20 23:46:16 matt-desktop kernel: [   27.768433] usb 7-5.4: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   27.768761] usbcore: registered new interface driver usbhid
Oct 20 23:46:16 matt-desktop kernel: [   27.768765] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 20 23:46:16 matt-desktop kernel: [   27.768853] usbcore: registered new interface driver libusual
Oct 20 23:46:16 matt-desktop kernel: [   27.794171] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 7L250S0   BANC PQ: 0 ANSI: 5
Oct 20 23:46:16 matt-desktop kernel: [   27.794248] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Oct 20 23:46:16 matt-desktop kernel: [   27.794280] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 17
Oct 20 23:46:16 matt-desktop kernel: [   27.794315] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Oct 20 23:46:16 matt-desktop kernel: [   27.800082] Initializing USB Mass Storage driver...
Oct 20 23:46:16 matt-desktop kernel: [   27.800522] scsi4 : ata_piix
Oct 20 23:46:16 matt-desktop kernel: [   27.801002] scsi5 : ata_piix
Oct 20 23:46:16 matt-desktop kernel: [   27.801422] ata5: SATA max UDMA/133 cmd 0xd800 ctl 0xdc00 bmdma 0xe800 irq 17
Oct 20 23:46:16 matt-desktop kernel: [   27.801425] ata6: SATA max UDMA/133 cmd 0xe000 ctl 0xe400 bmdma 0xe808 irq 17
Oct 20 23:46:16 matt-desktop kernel: [   28.007347] usb 5-2: new full speed USB device using uhci_hcd and address 2
Oct 20 23:46:16 matt-desktop kernel: [   28.131017] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
Oct 20 23:46:16 matt-desktop kernel: [   28.131025] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:46:16 matt-desktop kernel: [   28.131058] PCI: Setting latency timer of device 0000:03:00.1 to 64
Oct 20 23:46:16 matt-desktop kernel: [   28.131072] ACPI: PCI interrupt for device 0000:03:00.1 disabled
Oct 20 23:46:16 matt-desktop kernel: [   28.133835] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:46:16 matt-desktop kernel: [   28.133864] PCI: Setting latency timer of device 0000:03:00.1 to 64
Oct 20 23:46:16 matt-desktop kernel: [   28.133912] scsi6 : pata_jmicron
Oct 20 23:46:16 matt-desktop kernel: [   28.133957] scsi7 : pata_jmicron
Oct 20 23:46:16 matt-desktop kernel: [   28.134418] ata7: PATA max UDMA/100 cmd 0x9000 ctl 0x9400 bmdma 0xa000 irq 16
Oct 20 23:46:16 matt-desktop kernel: [   28.134421] ata8: PATA max UDMA/100 cmd 0x9800 ctl 0x9c00 bmdma 0xa008 irq 16
Oct 20 23:46:16 matt-desktop kernel: [   28.138630] Driver 'sd' needs updating - please use bus_type methods
Oct 20 23:46:16 matt-desktop kernel: [   28.138702] sd 2:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Oct 20 23:46:16 matt-desktop kernel: [   28.138714] sd 2:0:0:0: [sda] Write Protect is off
Oct 20 23:46:16 matt-desktop kernel: [   28.138716] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 20 23:46:16 matt-desktop kernel: [   28.138731] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 23:46:16 matt-desktop kernel: [   28.138778] sd 2:0:0:0: [sda] 488281250 512-byte hardware sectors (250000 MB)
Oct 20 23:46:16 matt-desktop kernel: [   28.138788] sd 2:0:0:0: [sda] Write Protect is off
Oct 20 23:46:16 matt-desktop kernel: [   28.138790] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Oct 20 23:46:16 matt-desktop kernel: [   28.138806] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 20 23:46:16 matt-desktop kernel: [   28.138809]  sda: sda1 sda2 sda3 sda4
Oct 20 23:46:16 matt-desktop kernel: [   28.176987] sd 2:0:0:0: [sda] Attached SCSI disk
Oct 20 23:46:16 matt-desktop kernel: [   28.181696] usb 5-2: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   28.182109] sd 2:0:0:0: Attached scsi generic sg0 type 0
Oct 20 23:46:16 matt-desktop kernel: [   28.187608] hub 5-2:1.0: USB hub found
Oct 20 23:46:16 matt-desktop kernel: [   28.188581] hub 5-2:1.0: 3 ports detected
Oct 20 23:46:16 matt-desktop kernel: [   28.298454] scsi8 : SCSI emulation for USB Mass Storage devices
Oct 20 23:46:16 matt-desktop kernel: [   28.298998] usb-storage: device found at 3
Oct 20 23:46:16 matt-desktop kernel: [   28.299000] usb-storage: waiting for device to settle before scanning
Oct 20 23:46:16 matt-desktop kernel: [   28.467818] ata7.00: ATAPI: LITE-ON DVDRW LH-20A1H, LL0C, max UDMA/66
Oct 20 23:46:16 matt-desktop kernel: [   28.467834] ata7.00: limited to UDMA/33 due to 40-wire cable
Oct 20 23:46:16 matt-desktop kernel: [   28.504561] usb 5-2.1: new full speed USB device using uhci_hcd and address 3
Oct 20 23:46:16 matt-desktop kernel: [   28.553517] Attempting manual resume
Oct 20 23:46:16 matt-desktop kernel: [   28.553520] swsusp: Resume From Partition 8:3
Oct 20 23:46:16 matt-desktop kernel: [   28.553522] PM: Checking swsusp image.
Oct 20 23:46:16 matt-desktop kernel: [   28.553645] PM: Resume from disk failed.
Oct 20 23:46:16 matt-desktop kernel: [   28.566111] EXT3-fs: INFO: recovery required on readonly filesystem.
Oct 20 23:46:16 matt-desktop kernel: [   28.566114] EXT3-fs: write access will be enabled during recovery.
Oct 20 23:46:16 matt-desktop kernel: [   28.641678] usb 5-2.1: configuration #1 chosen from 1 choice
Oct 20 23:46:16 matt-desktop kernel: [   28.649769] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2.1/5-2.1:1.0/input/input2
Oct 20 23:46:16 matt-desktop kernel: [   28.656790] ata7.00: configured for UDMA/33
Oct 20 23:46:16 matt-desktop kernel: [   28.663257] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
Oct 20 23:46:16 matt-desktop kernel: [   28.671607] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2.1/5-2.1:1.1/input/input3
Oct 20 23:46:16 matt-desktop kernel: [   28.700388] input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:1d.2-2.1
Oct 20 23:46:16 matt-desktop kernel: [   28.705565] usbcore: registered new interface driver usb-storage
Oct 20 23:46:16 matt-desktop kernel: [   28.705571] USB Mass Storage support registered.
Oct 20 23:46:16 matt-desktop kernel: [   28.823900] scsi 6:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1H   LL0C PQ: 0 ANSI: 5
Oct 20 23:46:16 matt-desktop kernel: [   28.824009] scsi 6:0:0:0: Attached scsi generic sg1 type 5
Oct 20 23:46:16 matt-desktop kernel: [   28.831096] Driver 'sr' needs updating - please use bus_type methods
Oct 20 23:46:16 matt-desktop kernel: [   28.838770] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Oct 20 23:46:16 matt-desktop kernel: [   28.838775] Uniform CD-ROM driver Revision: 3.20
Oct 20 23:46:16 matt-desktop kernel: [   28.838842] sr 6:0:0:0: Attached scsi CD-ROM sr0
Oct 20 23:46:16 matt-desktop kernel: [   28.888953] kjournald starting.  Commit interval 5 seconds
Oct 20 23:46:16 matt-desktop kernel: [   28.888965] EXT3-fs: sda4: orphan cleanup on readonly fs
Oct 20 23:46:16 matt-desktop kernel: [   28.888974] ext3_orphan_cleanup: deleting unreferenced inode 196805
Oct 20 23:46:16 matt-desktop kernel: [   28.889017] ext3_orphan_cleanup: deleting unreferenced inode 477386
Oct 20 23:46:16 matt-desktop kernel: [   28.889029] EXT3-fs: sda4: 2 orphan inodes deleted
Oct 20 23:46:16 matt-desktop kernel: [   28.889031] EXT3-fs: recovery complete.
Oct 20 23:46:16 matt-desktop kernel: [   28.916072] EXT3-fs: mounted filesystem with ordered data mode.
Oct 20 23:46:16 matt-desktop kernel: [   33.295704] usb-storage: device scan complete
Oct 20 23:46:16 matt-desktop kernel: [   33.296431] scsi 8:0:0:0: Direct-Access                               0.00 PQ: 0 ANSI: 2
Oct 20 23:46:16 matt-desktop kernel: [   33.297688] sd 8:0:0:0: [sdb] 7897088 512-byte hardware sectors (4043 MB)
Oct 20 23:46:16 matt-desktop kernel: [   33.299430] sd 8:0:0:0: [sdb] Write Protect is off
Oct 20 23:46:16 matt-desktop kernel: [   33.299433] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
Oct 20 23:46:16 matt-desktop kernel: [   33.299435] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Oct 20 23:46:16 matt-desktop kernel: [   33.301930] sd 8:0:0:0: [sdb] 7897088 512-byte hardware sectors (4043 MB)
Oct 20 23:46:16 matt-desktop kernel: [   33.302560] sd 8:0:0:0: [sdb] Write Protect is off
Oct 20 23:46:16 matt-desktop kernel: [   33.302563] sd 8:0:0:0: [sdb] Mode Sense: 00 00 00 00
Oct 20 23:46:16 matt-desktop kernel: [   33.302565] sd 8:0:0:0: [sdb] Assuming drive cache: write through
Oct 20 23:46:16 matt-desktop kernel: [   33.302570]  sdb: unknown partition table
Oct 20 23:46:16 matt-desktop kernel: [   33.999574] sd 8:0:0:0: [sdb] Attached SCSI removable disk
Oct 20 23:46:16 matt-desktop kernel: [   33.999619] sd 8:0:0:0: Attached scsi generic sg2 type 0
Oct 20 23:46:16 matt-desktop kernel: [   35.926315] input: PC Speaker as /devices/platform/pcspkr/input/input4
Oct 20 23:46:16 matt-desktop kernel: [   36.019390] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 20 23:46:16 matt-desktop kernel: [   36.041896] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 20 23:46:16 matt-desktop kernel: [   36.155327] parport_pc 00:07: reported by Plug and Play ACPI
Oct 20 23:46:16 matt-desktop kernel: [   36.155373] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Oct 20 23:46:16 matt-desktop kernel: [   36.199289] Linux agpgart interface v0.102
Oct 20 23:46:16 matt-desktop kernel: [   36.311245] iTCO_vendor_support: vendor-support=0
Oct 20 23:46:16 matt-desktop kernel: [   36.332836] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Oct 20 23:46:16 matt-desktop kernel: [   36.332913] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0460)
Oct 20 23:46:16 matt-desktop kernel: [   36.332950] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 20 23:46:16 matt-desktop kernel: [   36.355392] input: Power Button (FF) as /devices/virtual/input/input5
Oct 20 23:46:16 matt-desktop kernel: [   36.411236] ACPI: Power Button (FF) [PWRF]
Oct 20 23:46:16 matt-desktop kernel: [   36.411295] input: Power Button (CM) as /devices/virtual/input/input6
Oct 20 23:46:16 matt-desktop kernel: [   36.475212] ACPI: Power Button (CM) [PWRB]
Oct 20 23:46:16 matt-desktop kernel: [   37.001814] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 18 (level, low) -> IRQ 20
Oct 20 23:46:16 matt-desktop kernel: [   37.039416] phy0: Selected rate control algorithm 'simple'
Oct 20 23:46:16 matt-desktop kernel: [   37.398636] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 20 23:46:16 matt-desktop kernel: [   37.398648] PCI: Setting latency timer of device 0000:04:00.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   37.398673] sky2 0000:04:00.0: v1.20 addr 0xf7000000 irq 16 Yukon-EC Ultra (0xb4) rev 2
Oct 20 23:46:16 matt-desktop kernel: [   37.399066] sky2 eth0: addr 00:1a:4d:63:cd:b2
Oct 20 23:46:16 matt-desktop kernel: [   37.606054] Linux video capture interface: v2.00
Oct 20 23:46:16 matt-desktop kernel: [   37.716978] usbcore: registered new interface driver snd-usb-audio
Oct 20 23:46:16 matt-desktop kernel: [   37.723085] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
Oct 20 23:46:16 matt-desktop kernel: [   37.727044] usbcore: registered new interface driver gspca
Oct 20 23:46:16 matt-desktop kernel: [   37.727049] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Oct 20 23:46:16 matt-desktop kernel: [   37.792665] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
Oct 20 23:46:16 matt-desktop kernel: [   37.792685] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Oct 20 23:46:16 matt-desktop kernel: [   37.808077] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47
Oct 20 23:46:16 matt-desktop kernel: [   37.808115] usbcore: registered new interface driver sn9c102
Oct 20 23:46:16 matt-desktop kernel: [   38.493433] lp0: using parport0 (interrupt-driven).
Oct 20 23:46:16 matt-desktop kernel: [   38.566769] Adding 2000084k swap on /dev/sda3.  Priority:-1 extents:1 across:2000084k
Oct 20 23:46:16 matt-desktop kernel: [   39.118021] EXT3 FS on sda4, internal journal
Oct 20 23:46:16 matt-desktop kernel: [   40.040551] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 20 23:46:16 matt-desktop kernel: [   40.331417] No dock devices found.
Oct 20 23:46:16 matt-desktop NetworkManager: <info>  starting... 
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: Successfully dropped root privileges.
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: avahi-daemon 0.6.22 starting up.
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: Successfully called chroot().
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: Successfully dropped remaining capabilities.
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: No service file found in /etc/avahi/services.
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: Network interface enumeration completed.
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: Registering HINFO record with values 'I686'/'LINUX'.
Oct 20 23:46:16 matt-desktop avahi-daemon[5397]: Server startup complete. Host name is matt-desktop.local. Local service cookie is 966434748.
Oct 20 23:46:16 matt-desktop kernel: [   41.192869] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Oct 20 23:46:16 matt-desktop kernel: [   41.192874] apm: disabled - APM is not SMP safe.
Oct 20 23:46:16 matt-desktop kernel: [   41.312158] ppdev: user-space parallel port driver
Oct 20 23:46:16 matt-desktop kernel: [   41.375840] audit(1224542776.996:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5439 profile="/usr/sbin/cupsd" namespace="default"
Oct 20 23:46:17 matt-desktop dhcdbd: Started up.
Oct 20 23:46:18 matt-desktop kernel: [   42.546810] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
Oct 20 23:46:19 matt-desktop hcid[5684]: Bluetooth HCI daemon
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'rt61pci'. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Deactivating device wlan0. 
Oct 20 23:46:19 matt-desktop kernel: [   43.513001] sky2 eth0: enabling interface
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  eth0: Device is fully-supported using driver 'sky2'. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Deactivating device eth0. 
Oct 20 23:46:19 matt-desktop kernel: [   43.527902] Bluetooth: Core ver 2.11
Oct 20 23:46:19 matt-desktop kernel: [   43.528284] NET: Registered protocol family 31
Oct 20 23:46:19 matt-desktop kernel: [   43.528290] Bluetooth: HCI device and connection manager initialized
Oct 20 23:46:19 matt-desktop kernel: [   43.528295] Bluetooth: HCI socket layer initialized
Oct 20 23:46:19 matt-desktop hcid[5684]: Starting SDP server
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct 20 23:46:19 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Will activate connection 'eth0'. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Device eth0 activation scheduled... 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) started... 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 23:46:19 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct 20 23:46:19 matt-desktop kernel: [   43.547301] Bluetooth: L2CAP ver 2.9
Oct 20 23:46:19 matt-desktop kernel: [   43.547307] Bluetooth: L2CAP socket layer initialized
Oct 20 23:46:19 matt-desktop hcid[5684]: Created local server at unix:abstract=/var/run/dbus-yMCPPpWJgu,guid=18e4f9c1ee42574f7727a61848fd0a3b
Oct 20 23:46:19 matt-desktop input[5708]: Bluetooth Input daemon
Oct 20 23:46:19 matt-desktop input[5708]: Registered input manager path:/org/bluez/input
Oct 20 23:46:19 matt-desktop audio[5728]: Bluetooth Audio daemon
Oct 20 23:46:19 matt-desktop audio[5728]: Unix socket created: 5
Oct 20 23:46:19 matt-desktop audio[5728]: audio.conf: Key file does not have key 'Enable'
Oct 20 23:46:19 matt-desktop audio[5728]: audio.conf: Key file does not have key 'Disable'
Oct 20 23:46:19 matt-desktop kernel: [   43.622944] Bluetooth: RFCOMM socket layer initialized
Oct 20 23:46:19 matt-desktop kernel: [   43.622958] Bluetooth: RFCOMM TTY layer initialized
Oct 20 23:46:19 matt-desktop kernel: [   43.622960] Bluetooth: RFCOMM ver 1.8
Oct 20 23:46:19 matt-desktop NetworkManager: <debug> [1224542779.249288] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Oct 20 23:46:19 matt-desktop audio[5728]: add_service_record: got record id 0x10000
Oct 20 23:46:19 matt-desktop audio[5728]: audio.conf: Key file does not have key 'Disable'
Oct 20 23:46:19 matt-desktop audio[5728]: audio.conf: Key file does not have group 'A2DP'
Oct 20 23:46:19 matt-desktop last message repeated 3 times
Oct 20 23:46:19 matt-desktop audio[5728]: SEP 0x806d790 registered: type:0 codec:0 seid:1
Oct 20 23:46:19 matt-desktop audio[5728]: add_service_record: got record id 0x10001
Oct 20 23:46:19 matt-desktop audio[5728]: add_service_record: got record id 0x10002
Oct 20 23:46:19 matt-desktop audio[5728]: add_service_record: got record id 0x10003
Oct 20 23:46:19 matt-desktop audio[5728]: Registered manager path:/org/bluez/audio
Oct 20 23:46:20 matt-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct 20 23:46:20 matt-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct 20 23:46:20 matt-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 20 23:46:20 matt-desktop NetworkManager: <info>  SWITCH: terminating current connection 'eth0' because it's no longer valid. 
Oct 20 23:46:20 matt-desktop NetworkManager: <info>  Deactivating device eth0. 
Oct 20 23:46:20 matt-desktop NetworkManager: <info>  Activation (eth0): cancelling... 
Oct 20 23:46:20 matt-desktop NetworkManager: <info>  Activation (eth0) cancellation handler scheduled... 
Oct 20 23:46:20 matt-desktop NetworkManager: <info>  Activation (eth0): waiting for device to cancel activation. 
Oct 20 23:46:20 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 23:46:20 matt-desktop last message repeated 2 times
Oct 20 23:46:20 matt-desktop kernel: [   44.788025] NET: Registered protocol family 17
Oct 20 23:46:21 matt-desktop kernel: [   45.445876] [drm] Initialized drm 1.1.0 20060810
Oct 20 23:46:21 matt-desktop NetworkManager: <info>  Activation (eth0) cancellation handled. 
Oct 20 23:46:21 matt-desktop NetworkManager: <info>  Activation (eth0): cancelled. 
Oct 20 23:46:21 matt-desktop NetworkManager: nm_device_is_802_3_ethernet: assertion `dev != NULL' failed
Oct 20 23:46:21 matt-desktop NetworkManager: nm_device_is_802_11_wireless: assertion `dev != NULL' failed
Oct 20 23:46:21 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 23:46:21 matt-desktop anacron[5879]: Anacron 2.3 started on 2008-10-20
Oct 20 23:46:21 matt-desktop anacron[5879]: Will run job `cron.daily' in 5 min.
Oct 20 23:46:21 matt-desktop anacron[5879]: Will run job `cron.weekly' in 10 min.
Oct 20 23:46:21 matt-desktop anacron[5879]: Will run job `cron.monthly' in 15 min.
Oct 20 23:46:21 matt-desktop anacron[5879]: Jobs will be executed sequentially
Oct 20 23:46:21 matt-desktop /usr/sbin/cron[5906]: (CRON) INFO (pidfile fd = 3)
Oct 20 23:46:21 matt-desktop /usr/sbin/cron[5907]: (CRON) STARTUP (fork ok)
Oct 20 23:46:21 matt-desktop /usr/sbin/cron[5907]: (CRON) INFO (Running @reboot jobs)
Oct 20 23:46:24 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Oct 20 23:46:32 matt-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Oct 20 23:46:32 matt-desktop kernel: [   56.589520] NET: Registered protocol family 10
Oct 20 23:46:32 matt-desktop kernel: [   56.589869] lo: Disabled Privacy Extensions
Oct 20 23:46:32 matt-desktop kernel: [   56.590746] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 20 23:46:32 matt-desktop kernel: [   56.591076] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 20 23:46:32 matt-desktop pulseaudio[6125]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Oct 20 23:46:32 matt-desktop pulseaudio[6125]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct 20 23:46:34 matt-desktop hcid[5684]: Default passkey agent (:1.21, /org/bluez/passkey) registered
Oct 20 23:46:34 matt-desktop hcid[5684]: Default authorization agent (:1.21, /org/bluez/auth) registered
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
Oct 20 23:46:37 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Will activate connection 'wlan0/ASpunkMonkey'. 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Device wlan0 activation scheduled... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) started... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'ASpunkMonkey' is encrypted, but NO valid key exists.  New key needed. 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'ASpunkMonkey'. 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'ASpunkMonkey' received. 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Oct 20 23:46:37 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless): access point 'ASpunkMonkey' is encrypted, and a key exists.  No new key needed. 
Oct 20 23:46:37 matt-desktop hald: mounted /dev/sdb on behalf of uid 1000
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was '0' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 415370756e6b4d6f6e6b6579' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 pairwise TKIP' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 group TKIP' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  SUP: response was 'OK' 
Oct 20 23:46:38 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Oct 20 23:46:39 matt-desktop kernel: [   64.106216] wlan0: Initial auth_alg=0
Oct 20 23:46:39 matt-desktop kernel: [   64.106222] wlan0: authenticate with AP 00:1f:9f:42:15:e5
Oct 20 23:46:39 matt-desktop kernel: [   64.108883] wlan0: RX authentication from 00:1f:9f:42:15:e5 (alg=0 transaction=2 status=0)
Oct 20 23:46:39 matt-desktop kernel: [   64.108887] wlan0: authenticated
Oct 20 23:46:39 matt-desktop kernel: [   64.108890] wlan0: associate with AP 00:1f:9f:42:15:e5
Oct 20 23:46:39 matt-desktop kernel: [   64.111600] wlan0: RX AssocResp from 00:1f:9f:42:15:e5 (capab=0x411 status=0 aid=2)
Oct 20 23:46:39 matt-desktop kernel: [   64.111606] wlan0: associated
Oct 20 23:46:39 matt-desktop kernel: [   64.113706] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 20 23:46:39 matt-desktop NetworkManager: <info>  Supplicant state changed: 1 
Oct 20 23:46:39 matt-desktop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'ASpunkMonkey'. 
Oct 20 23:46:39 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct 20 23:46:39 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Oct 20 23:46:40 matt-desktop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Oct 20 23:46:40 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 23:46:40 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Oct 20 23:46:40 matt-desktop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
Oct 20 23:46:41 matt-desktop avahi-daemon[5397]: Registering new address record for fe80::21a:70ff:fe3c:8dbf on wlan0.*.
Oct 20 23:46:41 matt-desktop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
Oct 20 23:46:41 matt-desktop dhclient: wmaster0: unknown hardware address type 801
Oct 20 23:46:42 matt-desktop dhclient: DHCPREQUEST of 192.168.1.67 on wlan0 to 255.255.255.255 port 67
Oct 20 23:46:42 matt-desktop dhclient: DHCPACK of 192.168.1.67 from 192.168.1.254
Oct 20 23:46:42 matt-desktop avahi-daemon[5397]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 23:46:42 matt-desktop avahi-daemon[5397]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 23:46:42 matt-desktop avahi-daemon[5397]: Registering new address record for 192.168.1.67 on wlan0.IPv4.
Oct 20 23:46:42 matt-desktop dhclient: bound to 192.168.1.67 -- renewal in 40492 seconds.
Oct 20 23:46:42 matt-desktop NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface wlan0 
Oct 20 23:46:42 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct 20 23:46:42 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Oct 20 23:46:43 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Oct 20 23:46:43 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Oct 20 23:46:43 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Oct 20 23:46:43 matt-desktop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct 20 23:46:43 matt-desktop NetworkManager: <info>    address 192.168.1.67 
Oct 20 23:46:43 matt-desktop NetworkManager: <info>    netmask 255.255.255.0 
Oct 20 23:46:43 matt-desktop NetworkManager: <info>    broadcast 192.168.1.255 
Oct 20 23:46:43 matt-desktop NetworkManager: <info>    gateway 192.168.1.254 
Oct 20 23:46:43 matt-desktop NetworkManager: <info>    nameserver 192.168.1.254 
Oct 20 23:46:43 matt-desktop NetworkManager: <info>    domain name 'config' 
Oct 20 23:46:43 matt-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Oct 20 23:46:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 20 23:46:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Oct 20 23:46:43 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Oct 20 23:46:43 matt-desktop avahi-daemon[5397]: Withdrawing address record for 192.168.1.67 on wlan0.
Oct 20 23:46:43 matt-desktop avahi-daemon[5397]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 23:46:43 matt-desktop avahi-daemon[5397]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct 20 23:46:43 matt-desktop avahi-daemon[5397]: Withdrawing address record for fe80::21a:70ff:fe3c:8dbf on wlan0.
Oct 20 23:46:43 matt-desktop avahi-daemon[5397]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.67.
Oct 20 23:46:43 matt-desktop avahi-daemon[5397]: New relevant interface wlan0.IPv4 for mDNS.
Oct 20 23:46:43 matt-desktop avahi-daemon[5397]: Registering new address record for 192.168.1.67 on wlan0.IPv4.
Oct 20 23:46:44 matt-desktop NetworkManager: <info>  Clearing nscd hosts cache. 
Oct 20 23:46:44 matt-desktop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct 20 23:46:44 matt-desktop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Oct 20 23:46:44 matt-desktop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
Oct 20 23:46:44 matt-desktop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct 20 23:46:44 matt-desktop ntpdate[6397]: step time server 91.189.94.4 offset 82817.100476 sec
Oct 21 22:47:02 matt-desktop avahi-daemon[5397]: Registering new address record for fe80::21a:70ff:fe3c:8dbf on wlan0.*.
Oct 21 22:47:04 matt-desktop dhclient: No DHCPOFFERS received.
Oct 21 22:47:04 matt-desktop avahi-autoipd(eth0)[6410]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Oct 21 22:47:04 matt-desktop avahi-autoipd(eth0)[6410]: Successfully called chroot().
Oct 21 22:47:04 matt-desktop avahi-autoipd(eth0)[6410]: Successfully dropped root privileges.
Oct 21 22:47:04 matt-desktop avahi-autoipd(eth0)[6410]: Starting with address 169.254.8.140
Oct 21 22:47:09 matt-desktop avahi-autoipd(eth0)[6410]: Callout BIND, address 169.254.8.140 on interface eth0
Oct 21 22:47:09 matt-desktop avahi-daemon[5397]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.8.140.
Oct 21 22:47:09 matt-desktop avahi-daemon[5397]: New relevant interface eth0.IPv4 for mDNS.
Oct 21 22:47:09 matt-desktop avahi-daemon[5397]: Registering new address record for 169.254.8.140 on eth0.IPv4.
Oct 21 22:47:11 matt-desktop kernel: [   78.892503] wlan0: no IPv6 routers present
Oct 21 22:47:13 matt-desktop avahi-autoipd(eth0)[6410]: Successfully claimed IP address 169.254.8.140
```

Cheers for the help :)

PS. Was going to struggle to get the entire output (terminal window was cutting off most of it) - before I realised those lecture notes on terminal commands might actually be useful! :D

---

### Post by the_duality on 2008-10-22
/bump :)

---

### Post by Titan8990 on 2008-10-22
Sorry for the delay. Lets try disabling ACPI. Is this a laptop?

Alright, here is how to disable ACPI. There is a file used by grub called menu.lst located at /boot/grub. The file looks like this:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

What we are looking to change is the Ubuntu entry that is closest to the top (if you have not done any updates you will only have two, one for recovery mode and one for standard). This should be under the "end default options" comment.

Mine looks like this:


title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

What you are wanting to do is add "acpi=off" to the end of the kernel line.

Here is an example:


title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=48ee14f2-b8e2-4627-9d67-3ced8c1b2651 ro quiet splash **acpi=off**
initrd		/boot/initrd.img-2.6.24-21-generic
quiet


The command to edit the file is:

gksu gedit /boot/grub/menu.lst

or if you prefer CLI (like myself):

sudo nano /boot/grub/menu.lst



I hope this helps. Let me know if this resolves your issue.

---

### Post by the_duality on 2008-10-22
Cheers for getting back to me :)

This is on a desktop - in which case are the instructions still valid?

Thanks again!

---

### Post by Titan8990 on 2008-10-22
Yes, it is still valid with a desktop. It would have been valid for both actually. It is better that is a desktop because ACPI helps a lot lengthen battery life on laptops. If you are interested: [http://en.wikipedia.org/wiki/Acpi](http://en.wikipedia.org/wiki/Acpi).

If you are still having an issue with your graphics driver you may want to start a new thread and mark this one as solved.

I always recommend trying envyng:

sudo apt-get install envyng-gtk 


Envyng will download, install, and configure your graphic driver for you.


Good luck.

---

### Post by the_duality on 2008-10-22
Bad news, Ubuntu will not even boot after I do that. It freezes at the boot up progress bar/splash, and if I do ctrl+alt+del, I get an error about it not being able to start the X server due to some internal error. :(

The plot thickens!

Many thanks for your help :)

---

### Post by the_duality on 2008-10-23
/bump :)

---

### Post by Titan8990 on 2008-10-23
You can remove the acpi=off line easily from the grub menu. To do so highlight over the entry that you select to log in to Ubuntu. From there hit "E" to edit. Then you will see it split in to different sections. Again, you want to change the kernel line and remove the acpi=off.


From my experience most lock ups come from incompatibilities with ACPI or APIC of your motherboard. I didn't see any indication in your syslog that APIC is causing a problem. 

What hardware is this running on?

---

### Post by the_duality on 2008-10-23
Intel Core2 Duo E4300 (1.8GHz)
2Gb RAM
Radeon 1950XT 256Mb PCI-E gfx card
Gigabyte Motherboard
Realtek HD Sound (Built into mobo)
Linksys WMP54G Wireless PCI card

I think that is everything :)

Your help is really appreciated!

---

### Post by Titan8990 on 2008-10-24
Is the Gigabyte board an Intel or Nvidia chipset?

---

