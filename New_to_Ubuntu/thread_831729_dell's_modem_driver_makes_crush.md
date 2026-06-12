---
title: "dell's modem driver makes crush"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by medya on 2008-06-17
I installed Dell's driver for HSF conexant modems , and modem works but ... it makes my ubuntu crush after a few minutes.

the crush is not like normal crush it is wierd.

first the keyboard messes up (keyboard stops working or it keeps typing a letter) then slowly I loose more control over things (then I cant do right click , then I cant click then everything stops)

what should I do ? (btw I have ubuntu 64 bit hardy heron)

---

### Post by medya on 2008-06-17
may I bump this topic ?

---

### Post by MasterSander on 2008-06-17
You can check your logs (/var/logs) for any information. (view as root)

---

### Post by Arenlor on 2008-06-17
I can't provide a solution, but the lockups are due to a kernel segfault. I had the same problem with a device I tried, turns out it's a bad USB port.

---

### Post by medya on 2008-06-18
Arenlor did you fix it ? what should I do ?

---

### Post by medya on 2008-06-18
so what should I do to this seggault ?

---

### Post by Arenlor on 2008-06-18
Try reinstalling the drivers.

---

### Post by medya on 2008-06-19
I re-installed the driver, there is no use !

---

### Post by Arenlor on 2008-06-20
What do you get in your system log for this? System > Administration > System Log > syslog

---

### Post by ModelM on 2008-06-20
Perhaps I misunderstand but I see in the thread tags that one of the tags is "64 bit". If this is correct and you are indeed running a 64 bit version of Linux, I don't think the drivers from Dell will work for you. I believe they are 32 bit only.

I'm also running the Conexant HSF modem drivers from Dell and all works fine. In fact the modem performs exceptionally well. The name of the package I downloaded from Dell is:

hsfmodem_7.68.00.09oem_i386.deb

As I've already said, I think this package is for 32 bit only.

---

### Post by Arenlor on 2008-06-21
There is not 32 bit only. All 32 bit works on 64 bit, just as all 16 works on 32 and 64, etc on down (and in the future on up).

---

### Post by medya on 2008-06-21
I have installed the 64bit version, by the way here is my sys log I marked the supsectious part in red

by the way I should mention the ubuntu crushed 5 times just at the moment which i pressed Post Reply for this post .
so I had to swtich to windows and post this post (which u are reading now) by windows.
so perhaps there is a problem with Sending data .

```
Jun 22 15:20:25 Potter64buntu syslogd 1.5.0#1ubuntu1: restart.
Jun 22 15:20:25 Potter64buntu kernel: Inspecting /boot/System.map-2.6.24-16-generic
Jun 

22 15:20:25 Potter64buntu kernel: Loaded 28313 symbols from /boot/System.map-2.6.24-16-generic.
Jun 22 15:20:25 Potter64buntu kernel: Symbols match kernel 

version 2.6.24.
Jun 22 15:20:25 Potter64buntu kernel: Loaded 26244 symbols from 93 modules.
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Linux version 

2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Jun 22 

15:20:25 Potter64buntu kernel: [    0.000000] Command line: root=UUID=f3afdcdd-5a53-41ee-967b-c34e7e03e262 ro quiet splash
Jun 22 15:20:25 Potter64buntu 

kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 

(usable)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 22 15:20:25 Potter64buntu kernel: 

[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 

000000007fee0000 (usable)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jun 22 15:20:25 

Potter64buntu kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]  BIOS-

e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 

(reserved)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jun 22 15:20:25 Potter64buntu 

kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Entering 

add_active_range(0, 256, 524000) 1 entries of 3200 used
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] end_pfn_map = 1048576
Jun 22 15:20:25 

Potter64buntu kernel: [    0.000000] DMI 2.4 present.
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6990 checksum 

0
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: RSDP 000F6990, 0014 (r0 GBT   )
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: RSDT 

7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 

42302E31 GBTU  1010101)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: DSDT 7FEE3180, 3955 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
Jun 22 

15:20:25 Potter64buntu kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: HPET 7FEE6C40, 0038 (r1 GBT 

   GBTUACPI 42302E31 GBTU       98)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: MCFG 7FEE6CC0, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: APIC 7FEE6B40, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 22 15:20:25 Potter64buntu 

kernel: [    0.000000] ACPI: SSDT 7FEE6D40, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: SSDT 

7FEE71D0, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] No NUMA configuration found
Jun 22 15:20:25 

Potter64buntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007fee0000
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Entering 

add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 

3200 used
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
Jun 22 15:20:25 Potter64buntu kernel: [   

 0.000000] Zone PFN ranges:
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]   DMA             0 ->     4096
Jun 22 15:20:25 Potter64buntu kernel: [    

0.000000]   DMA32        4096 ->  1048576
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]   Normal    1048576 ->  1048576
Jun 22 15:20:25 Potter64buntu 

kernel: [    0.000000] Movable zone start PFN for each node
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun 22 

15:20:25 Potter64buntu kernel: [    0.000000]     0:        0 ->      159
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]     0:      256 ->   524000
Jun 

22 15:20:25 Potter64buntu kernel: [    0.000000] On node 0 totalpages: 523903
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]   DMA zone: 56 pages used 

for memmap
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]   DMA zone: 1208 pages reserved
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]   DMA 

zone: 2735 pages, LIFO batch:0
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]   DMA32 zone: 7108 pages used for memmap
Jun 22 15:20:25 Potter64buntu 

kernel: [    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: PM-

Timer IO Port: 0x408
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 22 15:20:25 Potter64buntu kernel: [    

0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jun 22 15:20:25 

Potter64buntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Processor #1
Jun 

22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] 

ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jun 

22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: 

LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jun 22 

15:20:25 Potter64buntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] 

IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl 

dfl)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 22 15:20:25 Potter64buntu kernel: [   

 0.000000] ACPI: IRQ0 used by override.
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 22 15:20:25 Potter64buntu kernel: 

[    0.000000] ACPI: IRQ9 used by override.
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Setting APIC routing to flat
Jun 22 15:20:25 Potter64buntu 

kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration 

information
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 22 15:20:25 

Potter64buntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jun 22 15:20:25 Potter64buntu kernel: [    

0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Allocating PCI 

resources starting at 80000000 (gap: 7ff00000:70100000)
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jun 22 

15:20:25 Potter64buntu kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Built 1 

zonelists in Node order, mobility grouping on.  Total pages: 515531
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] Policy zone: DMA32
Jun 22 15:20:25 

Potter64buntu kernel: [    0.000000] Kernel command line: root=UUID=f3afdcdd-5a53-41ee-967b-c34e7e03e262 ro quiet splash
Jun 22 15:20:25 Potter64buntu kernel: 

[    0.000000] Initializing CPU#0
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jun 22 15:20:25 

Potter64buntu kernel: [    0.000000] hpet clockevent registered
Jun 22 15:20:25 Potter64buntu kernel: [    0.000000] TSC calibrated against HPET
Jun 22 

15:20:25 Potter64buntu kernel: [   32.704668] time.c: Detected 2666.664 MHz processor.
Jun 22 15:20:25 Potter64buntu kernel: [   32.705756] Console: colour 

VGA+ 80x25
Jun 22 15:20:25 Potter64buntu kernel: [   32.705759] console [tty0] enabled
Jun 22 15:20:25 Potter64buntu kernel: [   32.705771] Checking 

aperture...
Jun 22 15:20:25 Potter64buntu kernel: [   32.705777] Calgary: detecting Calgary via BIOS EBDA area
Jun 22 15:20:25 Potter64buntu kernel: [   

32.705779] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun 22 15:20:25 Potter64buntu kernel: [   32.720275] Memory: 2053636k/2096000k 

available (2466k kernel code, 41976k reserved, 1309k data, 316k init)
Jun 22 15:20:25 Potter64buntu kernel: [   32.720301] SLUB: Genslabs=12, HWalign=64, 

Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Jun 22 15:20:25 Potter64buntu kernel: [   32.798658] Calibrating delay using timer specific routine.. 5336.63 

BogoMIPS (lpj=10673263)
Jun 22 15:20:25 Potter64buntu kernel: [   32.798681] Security Framework initialized
Jun 22 15:20:25 Potter64buntu kernel: [   

32.798686] SELinux:  Disabled at boot.
Jun 22 15:20:25 Potter64buntu kernel: [   32.798695] AppArmor: AppArmor initialized
Jun 22 15:20:25 Potter64buntu 

kernel: [   32.798697] Failure registering capabilities with primary security module.
Jun 22 15:20:25 Potter64buntu kernel: [   32.798840] Dentry cache hash 

table entries: 262144 (order: 9, 2097152 bytes)
Jun 22 15:20:25 Potter64buntu kernel: [   32.799782] Inode-cache hash table entries: 131072 (order: 8, 1048576 

bytes)
Jun 22 15:20:25 Potter64buntu kernel: [   32.800217] Mount-cache hash table entries: 256
Jun 22 15:20:25 Potter64buntu kernel: [   32.800307] CPU: L1 I 

cache: 32K, L1 D cache: 32K
Jun 22 15:20:25 Potter64buntu kernel: [   32.800308] CPU: L2 cache: 6144K
Jun 22 15:20:25 Potter64buntu kernel: [   32.800310] CPU 

0/0 -> Node 0
Jun 22 15:20:25 Potter64buntu kernel: [   32.800311] using mwait in idle threads.
Jun 22 15:20:25 Potter64buntu kernel: [   32.800312] CPU: 

Physical Processor ID: 0
Jun 22 15:20:25 Potter64buntu kernel: [   32.800313] CPU: Processor Core ID: 0
Jun 22 15:20:25 Potter64buntu kernel: [   32.800318] 

CPU0: Thermal monitoring enabled (TM2)
Jun 22 15:20:25 Potter64buntu kernel: [   32.800328] SMP alternatives: switching to UP code
Jun 22 15:20:25 

Potter64buntu kernel: [   32.800977] Early unpacking initramfs... done
Jun 22 15:20:25 Potter64buntu kernel: [   33.076287] ACPI: Core revision 20070126
Jun 22 

15:20:25 Potter64buntu kernel: [   33.076313] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 22 15:20:25 Potter64buntu kernel: [  

 33.118951] Using local APIC timer interrupts.
Jun 22 15:20:25 Potter64buntu kernel: [   33.156456] APIC timer calibration result 20833309
Jun 22 15:20:25 

Potter64buntu kernel: [   33.156457] Detected 20.833 MHz APIC timer.
Jun 22 15:20:25 Potter64buntu kernel: [   33.156510] SMP alternatives: switching to SMP 

code
Jun 22 15:20:25 Potter64buntu kernel: [   33.157091] Booting processor 1/2 APIC 0x1
Jun 22 15:20:25 Potter64buntu kernel: [   33.167713] Initializing 

CPU#1
Jun 22 15:20:25 Potter64buntu kernel: [   33.244459] Calibrating delay using timer specific routine.. 5333.35 BogoMIPS (lpj=10666712)
Jun 22 15:20:25 

Potter64buntu kernel: [   33.244465] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 22 15:20:25 Potter64buntu kernel: [   33.244466] CPU: L2 cache: 6144K
Jun 22 

15:20:25 Potter64buntu kernel: [   33.244467] CPU 1/1 -> Node 0
Jun 22 15:20:25 Potter64buntu kernel: [   33.244468] CPU: Physical Processor ID: 0
Jun 22 

15:20:25 Potter64buntu kernel: [   33.244469] CPU: Processor Core ID: 1
Jun 22 15:20:25 Potter64buntu kernel: [   33.244473] CPU1: Thermal monitoring enabled 

(TM2)
Jun 22 15:20:25 Potter64buntu kernel: [   33.245156] Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz stepping 06
Jun 22 15:20:25 Potter64buntu kernel: [  

 33.245187] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 22 15:20:25 Potter64buntu kernel: [   33.265205] Brought up 2 CPUs
Jun 22 15:20:25 

Potter64buntu kernel: [   33.265264] CPU0 attaching sched-domain:
Jun 22 15:20:25 Potter64buntu kernel: [   33.265265]  domain 0: span 03
Jun 22 15:20:25 

Potter64buntu kernel: [   33.265266]   groups: 01 02
Jun 22 15:20:25 Potter64buntu kernel: [   33.265268]   domain 1: span 03
Jun 22 15:20:25 Potter64buntu 

kernel: [   33.265269]    groups: 03
Jun 22 15:20:25 Potter64buntu kernel: [   33.265270] CPU1 attaching sched-domain:
Jun 22 15:20:25 Potter64buntu kernel: [  

 33.265271]  domain 0: span 03
Jun 22 15:20:25 Potter64buntu kernel: [   33.265272]   groups: 02 01
Jun 22 15:20:25 Potter64buntu kernel: [   33.265273]   

domain 1: span 03
Jun 22 15:20:25 Potter64buntu kernel: [   33.265274]    groups: 03
Jun 22 15:20:25 Potter64buntu kernel: [   33.265428] net_namespace: 120 

bytes
Jun 22 15:20:25 Potter64buntu kernel: [   33.265689] Time: 15:19:55  Date: 06/22/08
Jun 22 15:20:25 Potter64buntu kernel: [   33.265707] NET: Registered 

protocol family 16
Jun 22 15:20:25 Potter64buntu kernel: [   33.265831] ACPI: bus type pci registered
Jun 22 15:20:25 Potter64buntu kernel: [   33.265883] PCI: 

Using configuration type 1
Jun 22 15:20:25 Potter64buntu kernel: [   33.266639] ACPI: EC: Look up EC in DSDT
Jun 22 15:20:25 Potter64buntu kernel: [   

33.269588] ACPI: Interpreter enabled
Jun 22 15:20:25 Potter64buntu kernel: [   33.269592] ACPI: (supports S0 S3 S4 S5)
Jun 22 15:20:25 Potter64buntu kernel: [  

 33.269602] ACPI: Using IOAPIC for interrupt routing
Jun 22 15:20:25 Potter64buntu kernel: [   33.272526] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 22 

15:20:25 Potter64buntu kernel: [   33.272899] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Jun 22 15:20:25 Potter64buntu kernel: [   33.272902] 

PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Jun 22 15:20:25 Potter64buntu kernel: [   33.273329] PCI: Transparent bridge - 0000:00:1e.0
Jun 22 15:20:25 

Potter64buntu kernel: [   33.273348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 22 15:20:25 Potter64buntu kernel: [   33.273431] ACPI: PCI 

Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Jun 22 15:20:25 Potter64buntu kernel: [   33.273479] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Jun 22 15:20:25 Potter64buntu kernel: [   33.273525] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jun 22 15:20:25 Potter64buntu kernel: [   

33.279630] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 22 15:20:25 Potter64buntu kernel: [   33.279689] ACPI: PCI Interrupt Link 

[LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 22 15:20:25 Potter64buntu kernel: [   33.279748] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 

10 11 12 14 15)
Jun 22 15:20:25 Potter64buntu kernel: [   33.279805] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 22 15:20:25 

Potter64buntu kernel: [   33.279863] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 22 15:20:25 Potter64buntu kernel: [   

33.279921] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 22 15:20:25 Potter64buntu kernel: [   33.279978] ACPI: PCI 

Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 22 15:20:25 Potter64buntu kernel: [   33.280036] ACPI: PCI Interrupt Link [LNK1] 

(IRQs *3 4 5 6 7 9 10 11 12 14 15)
Jun 22 15:20:25 Potter64buntu kernel: [   33.280113] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 22 15:20:25 

Potter64buntu kernel: [   33.280132] pnp: PnP ACPI init
Jun 22 15:20:25 Potter64buntu kernel: [   33.280136] ACPI: bus type pnp registered
Jun 22 15:20:25 

Potter64buntu kernel: [   33.281678] pnpacpi: exceeded the max number of mem resources: 12
Jun 22 15:20:25 Potter64buntu kernel: [   33.281764] pnp: PnP ACPI: 

found 15 devices
Jun 22 15:20:25 Potter64buntu kernel: [   33.281766] ACPI: ACPI bus type pnp unregistered
Jun 22 15:20:25 Potter64buntu kernel: [   33.281920] 

PCI: Using ACPI for IRQ routing
Jun 22 15:20:25 Potter64buntu kernel: [   33.281921] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a 

report
Jun 22 15:20:25 Potter64buntu kernel: [   33.292506] NET: Registered protocol family 8
Jun 22 15:20:25 Potter64buntu kernel: [   33.292508] NET: 

Registered protocol family 20
Jun 22 15:20:25 Potter64buntu kernel: [   33.292535] PCI-GART: No AMD northbridge found.
Jun 22 15:20:25 Potter64buntu kernel: [  

 33.292538] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 22 15:20:25 Potter64buntu kernel: [   33.292541] hpet0: 3 64-bit timers, 14318180 Hz
Jun 22 15:20:25 

Potter64buntu kernel: [   33.293566] AppArmor: AppArmor Filesystem Enabled
Jun 22 15:20:25 Potter64buntu kernel: [   33.296462] Time: tsc clocksource has been 

installed.
Jun 22 15:20:25 Potter64buntu kernel: [   33.296468] Switched to high resolution mode on CPU 0
Jun 22 15:20:25 Potter64buntu kernel: [   33.297202] 

Switched to high resolution mode on CPU 1
Jun 22 15:20:25 Potter64buntu kernel: [   33.304460] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jun 22 

15:20:25 Potter64buntu kernel: [   33.304462] system 00:01: ioport range 0x290-0x29f has been reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304464] 

system 00:01: ioport range 0x800-0x87f has been reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304466] system 00:01: ioport range 0x290-0x294 has been 

reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304468] system 00:01: ioport range 0x880-0x88f has been reserved
Jun 22 15:20:25 Potter64buntu kernel: [  

 33.304476] system 00:0b: ioport range 0x400-0x4bf could not be reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304480] system 00:0c: iomem range 

0xf0000000-0xf3ffffff could not be reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304484] system 00:0d: iomem range 0xcd200-0xcffff has been reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304487] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
Jun 22 15:20:25 Potter64buntu kernel: [   

33.304489] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304491] system 00:0d: iomem range 

0xfc000-0xfffff could not be reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304493] system 00:0d: iomem range 0x7fee0000-0x7fefffff could not be 

reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304495] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Jun 22 15:20:25 Potter64buntu kernel: 

[   33.304498] system 00:0d: iomem range 0x100000-0x7fedffff could not be reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304500] system 00:0d: iomem 

range 0xfec00000-0xfec00fff has been reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304502] system 00:0d: iomem range 0xfed13000-0xfed1dfff has been 

reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304504] system 00:0d: iomem range 0xfed20000-0xfed8ffff has been reserved
Jun 22 15:20:25 Potter64buntu 

kernel: [   33.304506] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304509] system 

00:0d: iomem range 0xffb00000-0xffb7ffff has been reserved
Jun 22 15:20:25 Potter64buntu kernel: [   33.304772] PCI: Bridge: 0000:00:01.0
Jun 22 15:20:25 

Potter64buntu kernel: [   33.304773]   IO window: b000-bfff
Jun 22 15:20:25 Potter64buntu kernel: [   33.304775]   MEM window: f4000000-f7ffffff
Jun 22 

15:20:25 Potter64buntu kernel: [   33.304777]   PREFETCH window: e0000000-efffffff
Jun 22 15:20:25 Potter64buntu kernel: [   33.304779] PCI: Bridge: 

0000:00:1c.0
Jun 22 15:20:25 Potter64buntu kernel: [   33.304780]   IO window: a000-afff
Jun 22 15:20:25 Potter64buntu kernel: [   33.304783]   MEM window: 

disabled.
Jun 22 15:20:25 Potter64buntu kernel: [   33.304785]   PREFETCH window: disabled.
Jun 22 15:20:25 Potter64buntu kernel: [   33.304788] PCI: Bridge: 

0000:00:1c.3
Jun 22 15:20:25 Potter64buntu kernel: [   33.304789]   IO window: c000-cfff
Jun 22 15:20:25 Potter64buntu kernel: [   33.304792]   MEM window: 

f8000000-f9ffffff
Jun 22 15:20:25 Potter64buntu kernel: [   33.304794]   PREFETCH window: 80000000-800fffff
Jun 22 15:20:25 Potter64buntu kernel: [   

33.304797] PCI: Bridge: 0000:00:1e.0
Jun 22 15:20:25 Potter64buntu kernel: [   33.304799]   IO window: d000-dfff
Jun 22 15:20:25 Potter64buntu kernel: [   

33.304801]   MEM window: fa000000-fa0fffff
Jun 22 15:20:25 Potter64buntu kernel: [   33.304803]   PREFETCH window: disabled.
Jun 22 15:20:25 Potter64buntu 

kernel: [   33.304812] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 22 15:20:25 Potter64buntu kernel: [   33.304815] PCI: Setting 

latency timer of device 0000:00:01.0 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   33.304826] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> 

IRQ 16
Jun 22 15:20:25 Potter64buntu kernel: [   33.304829] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   

33.304840] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:20:25 Potter64buntu kernel: [   33.304843] PCI: Setting latency 

timer of device 0000:00:1c.3 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   33.304849] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jun 22 15:20:25 

Potter64buntu kernel: [   33.304855] NET: Registered protocol family 2
Jun 22 15:20:25 Potter64buntu kernel: [   33.340513] IP route cache hash table entries: 

65536 (order: 7, 524288 bytes)
Jun 22 15:20:25 Potter64buntu kernel: [   33.340933] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jun 

22 15:20:25 Potter64buntu kernel: [   33.341846] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 22 15:20:25 Potter64buntu kernel: [   

33.342105] TCP: Hash tables configured (established 262144 bind 65536)
Jun 22 15:20:25 Potter64buntu kernel: [   33.342106] TCP reno registered
Jun 22 15:20:25 

Potter64buntu kernel: [   33.352552] checking if image is initramfs... it is
Jun 22 15:20:25 Potter64buntu kernel: [   33.895153] Freeing initrd memory: 8209k 

freed
Jun 22 15:20:25 Potter64buntu kernel: [   33.897642] audit: initializing netlink socket (disabled)
Jun 22 15:20:25 Potter64buntu kernel: [   33.897657] 

audit(1214147995.148:1): initialized
Jun 22 15:20:25 Potter64buntu kernel: [   33.898998] VFS: Disk quotas dquot_6.5.1
Jun 22 15:20:25 Potter64buntu kernel: [  

 33.899041] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 22 15:20:25 Potter64buntu kernel: [   33.899116] io scheduler noop registered
Jun 22 

15:20:25 Potter64buntu kernel: [   33.899117] io scheduler anticipatory registered
Jun 22 15:20:25 Potter64buntu kernel: [   33.899118] io scheduler deadline 

registered
Jun 22 15:20:25 Potter64buntu kernel: [   33.899182] io scheduler cfq registered (default)
Jun 22 15:20:25 Potter64buntu kernel: [   33.901894] Boot 

video device is 0000:01:00.0
Jun 22 15:20:25 Potter64buntu kernel: [   33.902000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Jun 22 15:20:25 

Potter64buntu kernel: [   33.902020] assign_interrupt_mode Found MSI capability
Jun 22 15:20:25 Potter64buntu kernel: [   33.902037] Allocate Port Service

[0000:00:01.0:pcie00]
Jun 22 15:20:25 Potter64buntu kernel: [   33.902083] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Jun 22 15:20:25 

Potter64buntu kernel: [   33.902109] assign_interrupt_mode Found MSI capability
Jun 22 15:20:25 Potter64buntu kernel: [   33.902129] Allocate Port Service

[0000:00:1c.0:pcie00]
Jun 22 15:20:25 Potter64buntu kernel: [   33.902149] Allocate Port Service[0000:00:1c.0:pcie02]
Jun 22 15:20:25 Potter64buntu kernel: [   

33.902199] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   33.902225] assign_interrupt_mode Found MSI 

capability
Jun 22 15:20:25 Potter64buntu kernel: [   33.902245] Allocate Port Service[0000:00:1c.3:pcie00]
Jun 22 15:20:25 Potter64buntu kernel: [   33.902266] 

Allocate Port Service[0000:00:1c.3:pcie02]
Jun 22 15:20:25 Potter64buntu kernel: [   33.917611] Real Time Clock Driver v1.12ac
Jun 22 15:20:25 Potter64buntu 

kernel: [   33.917713] hpet_resources: 0xfed00000 is busy
Jun 22 15:20:25 Potter64buntu kernel: [   33.917735] Linux agpgart interface v0.102
Jun 22 15:20:25 

Potter64buntu kernel: [   33.917736] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 22 15:20:25 Potter64buntu kernel: [   

33.917827] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 22 15:20:25 Potter64buntu kernel: [   33.918158] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 

16550A
Jun 22 15:20:25 Potter64buntu kernel: [   33.918617] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 22 15:20:25 

Potter64buntu kernel: [   33.918655] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 22 15:20:25 Potter64buntu kernel: [   

33.918713] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 22 15:20:25 Potter64buntu kernel: [   33.918994] serio: i8042 KBD port 

at 0x60,0x64 irq 1
Jun 22 15:20:25 Potter64buntu kernel: [   33.918997] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 22 15:20:25 Potter64buntu kernel: [   

33.936973] mice: PS/2 mouse device common for all mice
Jun 22 15:20:25 Potter64buntu kernel: [   33.937002] cpuidle: using governor ladder
Jun 22 15:20:25 

Potter64buntu kernel: [   33.937004] cpuidle: using governor menu
Jun 22 15:20:25 Potter64buntu kernel: [   33.937092] NET: Registered protocol family 1
Jun 22 

15:20:25 Potter64buntu kernel: [   33.937123] registered taskstats version 1
Jun 22 15:20:25 Potter64buntu kernel: [   33.937184]   Magic number: 12:514:336
Jun 22 15:20:25 Potter64buntu kernel: [   33.937187]   hash matches device ttyzb
Jun 22 15:20:25 Potter64buntu kernel: [   33.937202]   hash matches device 

tty57
Jun 22 15:20:25 Potter64buntu kernel: [   33.937213] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jun 22 15:20:25 

Potter64buntu kernel: [   33.937214] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 22 15:20:25 Potter64buntu kernel: [   33.937216] EDD information 

not available.
Jun 22 15:20:25 Potter64buntu kernel: [   33.937221] Freeing unused kernel memory: 316k freed
Jun 22 15:20:25 Potter64buntu kernel: [   

33.966832] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 22 15:20:25 Potter64buntu kernel: [   35.058447] fuse init 

(API version 7.9)
Jun 22 15:20:25 Potter64buntu kernel: [   35.071421] ACPI: Processor [CPU0] (supports 8 throttling states)
Jun 22 15:20:25 Potter64buntu 

kernel: [   35.071495] ACPI: SSDT 7FEE7140, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
Jun 22 15:20:25 Potter64buntu kernel: [   35.071577] ACPI: 

Processor [CPU1] (supports 8 throttling states)
Jun 22 15:20:25 Potter64buntu kernel: [   35.071587] ACPI Exception (processor_core-0816): AE_NOT_FOUND, 

Processor Device is not present [20070126]
Jun 22 15:20:25 Potter64buntu kernel: [   35.071594] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor 

Device is not present [20070126]
Jun 22 15:20:25 Potter64buntu kernel: [   35.241355] usbcore: registered new interface driver usbfs
Jun 22 15:20:25 

Potter64buntu kernel: [   35.241369] usbcore: registered new interface driver hub
Jun 22 15:20:25 Potter64buntu kernel: [   35.246674] r8169 Gigabit Ethernet 

driver 2.2LK loaded
Jun 22 15:20:25 Potter64buntu kernel: [   35.246691] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:20:25 

Potter64buntu kernel: [   35.246704] PCI: Setting latency timer of device 0000:03:00.0 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   35.246896] eth0: 

RTL8168b/8111b at 0xffffc200008ae000, 00:1d:7d:c7:b8:fa, XID 38000000 IRQ 508
Jun 22 15:20:25 Potter64buntu kernel: [   35.247972] usbcore: registered new 

device driver usb
Jun 22 15:20:25 Potter64buntu kernel: [   35.253109] USB Universal Host Controller Interface driver v3.0
Jun 22 15:20:25 Potter64buntu 

kernel: [   35.253139] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
Jun 22 15:20:25 Potter64buntu kernel: [   35.253145] PCI: Setting 

latency timer of device 0000:00:1d.0 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   35.253147] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 22 15:20:25 

Potter64buntu kernel: [   35.253321] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jun 22 15:20:25 Potter64buntu kernel: [   35.253343] 

uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
Jun 22 15:20:25 Potter64buntu kernel: [   35.253420] usb usb1: configuration #1 chosen from 1 choice
Jun 22 

15:20:25 Potter64buntu kernel: [   35.253435] hub 1-0:1.0: USB hub found
Jun 22 15:20:25 Potter64buntu kernel: [   35.253438] hub 1-0:1.0: 2 ports detected
Jun 

22 15:20:25 Potter64buntu kernel: [   35.303787] SCSI subsystem initialized
Jun 22 15:20:25 Potter64buntu kernel: [   35.313143] libata version 3.00 loaded.
Jun 22 15:20:25 Potter64buntu kernel: [   35.356404] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:20:25 Potter64buntu 

kernel: [   35.356412] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   35.356415] uhci_hcd 0000:00:1d.1: 

UHCI Host Controller
Jun 22 15:20:25 Potter64buntu kernel: [   35.356431] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jun 22 15:20:25 

Potter64buntu kernel: [   35.356452] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e000
Jun 22 15:20:25 Potter64buntu kernel: [   35.356514] usb usb2: 

configuration #1 chosen from 1 choice
Jun 22 15:20:25 Potter64buntu kernel: [   35.356527] hub 2-0:1.0: USB hub found
Jun 22 15:20:25 Potter64buntu kernel: [   

35.356530] hub 2-0:1.0: 2 ports detected
Jun 22 15:20:25 Potter64buntu kernel: [   35.460389] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> 

IRQ 18
Jun 22 15:20:25 Potter64buntu kernel: [   35.460395] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   

35.460397] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 22 15:20:25 Potter64buntu kernel: [   35.460410] uhci_hcd 0000:00:1d.2: new USB bus registered, 

assigned bus number 3
Jun 22 15:20:25 Potter64buntu kernel: [   35.460431] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e100
Jun 22 15:20:25 Potter64buntu 

kernel: [   35.460491] usb usb3: configuration #1 chosen from 1 choice
Jun 22 15:20:25 Potter64buntu kernel: [   35.460504] hub 3-0:1.0: USB hub found
Jun 22 

15:20:25 Potter64buntu kernel: [   35.460507] hub 3-0:1.0: 2 ports detected
Jun 22 15:20:25 Potter64buntu kernel: [   35.564385] ACPI: PCI Interrupt 

0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
Jun 22 15:20:25 Potter64buntu kernel: [   35.564392] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   35.564395] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jun 22 15:20:25 Potter64buntu kernel: [   35.564410] uhci_hcd 

0000:00:1d.3: new USB bus registered, assigned bus number 4
Jun 22 15:20:25 Potter64buntu kernel: [   35.564431] uhci_hcd 0000:00:1d.3: irq 16, io base 

0x0000e200
Jun 22 15:20:25 Potter64buntu kernel: [   35.564498] usb usb4: configuration #1 chosen from 1 choice
Jun 22 15:20:25 Potter64buntu kernel: [   

35.564511] hub 4-0:1.0: USB hub found
Jun 22 15:20:25 Potter64buntu kernel: [   35.564514] hub 4-0:1.0: 2 ports detected
Jun 22 15:20:25 Potter64buntu kernel: 

[   35.668484] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
Jun 22 15:20:25 Potter64buntu kernel: [   35.669800] PCI: Setting latency 

timer of device 0000:00:1d.7 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   35.669804] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 22 15:20:25 

Potter64buntu kernel: [   35.669839] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jun 22 15:20:25 Potter64buntu kernel: [   35.673740] 

PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Jun 22 15:20:25 Potter64buntu kernel: [   35.673744] ehci_hcd 0000:00:1d.7: irq 23, io mem 

0xfa104000
Jun 22 15:20:25 Potter64buntu kernel: [   35.700848] usb 2-2: new low speed USB device using uhci_hcd and address 2
Jun 22 15:20:25 Potter64buntu 

kernel: [   35.712836] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 22 15:20:25 Potter64buntu kernel: [   35.712924] usb usb5: 

configuration #1 chosen from 1 choice
Jun 22 15:20:25 Potter64buntu kernel: [   35.712945] hub 5-0:1.0: USB hub found
Jun 22 15:20:25 Potter64buntu kernel: [   

35.712949] hub 5-0:1.0: 8 ports detected
Jun 22 15:20:25 Potter64buntu kernel: [   35.818530] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> 

IRQ 19
Jun 22 15:20:25 Potter64buntu kernel: [   35.818550] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   

35.818556] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Jun 22 15:20:25 Potter64buntu kernel: [   35.820147] ata_piix 0000:00:1f.2: version 2.12
Jun 22 

15:20:25 Potter64buntu kernel: [   35.820150] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Jun 22 15:20:25 Potter64buntu kernel: [   35.820158] ACPI: PCI 

Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:20:25 Potter64buntu kernel: [   35.820172] PCI: Setting latency timer of device 

0000:00:1f.2 to 64
Jun 22 15:20:25 Potter64buntu kernel: [   35.820441] scsi0 : ata_piix
Jun 22 15:20:25 Potter64buntu kernel: [   35.820823] scsi1 : ata_piix
Jun 22 15:20:25 Potter64buntu kernel: [   35.821193] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jun 22 15:20:25 Potter64buntu kernel: [   

35.821195] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jun 22 15:20:25 Potter64buntu kernel: [   36.180943] ata1.00: HPA unlocked: 

625140335 -> 625142448, native 625142448
Jun 22 15:20:25 Potter64buntu kernel: [   36.180946] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
Jun 22 15:20:25 

Potter64buntu kernel: [   36.180948] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 22 15:20:25 Potter64buntu kernel: [   36.225230] 

ata1.00: configured for UDMA/133
Jun 22 15:20:25 Potter64buntu kernel: [   36.553041] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB05, max UDMA/33
Jun 22 

15:20:25 Potter64buntu kernel: [   36.560274] usb 2-2: new low speed USB device using uhci_hcd and address 3
Jun 22 15:20:25 Potter64buntu kernel: [   

36.560546] ata2.01: HPA unlocked: 321670847 -> 321672960, native 321672960
Jun 22 15:20:25 Potter64buntu kernel: [   36.560548] ata2.01: ATA-7: 

HDT722516DLAT80, V43OA96A, max UDMA/133
Jun 22 15:20:25 Potter64buntu kernel: [   36.560550] ata2.01: 321672960 sectors, multi 16: LBA48 
Jun 22 15:20:25 

Potter64buntu kernel: [   36.732976] ata2.00: configured for UDMA/33
Jun 22 15:20:25 Potter64buntu kernel: [   36.735531] usb 2-2: configuration #1 chosen 

from 1 choice
Jun 22 15:20:25 Potter64buntu kernel: [   36.749141] ata2.01: configured for UDMA/100
Jun 22 15:20:25 Potter64buntu kernel: [   36.749201] scsi 

0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
Jun 22 15:20:25 Potter64buntu kernel: [   36.749774] scsi 1:0:0:0: CD-ROM            

TSSTcorp CD/DVDW SH-S182M SB05 PQ: 0 ANSI: 5
Jun 22 15:20:25 Potter64buntu kernel: [   36.749832] scsi 1:0:1:0: Direct-Access     ATA      HDT722516DLAT80  

V43O PQ: 0 ANSI: 5
Jun 22 15:20:25 Potter64buntu kernel: [   36.753637] Driver 'sd' needs updating - please use bus_type methods
Jun 22 15:20:25 Potter64buntu 

kernel: [   36.753668] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Jun 22 15:20:25 Potter64buntu kernel: [   36.753675] sd 0:0:0:0: 

[sda] Write Protect is off
Jun 22 15:20:25 Potter64buntu kernel: [   36.753677] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 22 15:20:25 Potter64buntu kernel: 

[   36.753686] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 22 15:20:25 Potter64buntu kernel: [   36.753717] sd 

0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Jun 22 15:20:25 Potter64buntu kernel: [   36.753723] sd 0:0:0:0: [sda] Write Protect is off
Jun 

22 15:20:25 Potter64buntu kernel: [   36.753725] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 22 15:20:25 Potter64buntu kernel: [   36.753734] sd 0:0:0:0: 

[sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 22 15:20:25 Potter64buntu kernel: [   36.753737]  sda:<4>Driver 'sr' needs 

updating - please use bus_type methods
Jun 22 15:20:25 Potter64buntu kernel: [   36.772991]  sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
Jun 22 15:20:25 

Potter64buntu kernel: [   36.803014] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 22 15:20:25 Potter64buntu kernel: [   36.803046] sd 1:0:1:0: [sdb] 321672960 

512-byte hardware sectors (164697 MB)
Jun 22 15:20:25 Potter64buntu kernel: [   36.803053] sd 1:0:1:0: [sdb] Write Protect is off
Jun 22 15:20:25 Potter64buntu 

kernel: [   36.803054] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jun 22 15:20:25 Potter64buntu kernel: [   36.803064] sd 1:0:1:0: [sdb] Write cache: enabled, 

read cache: enabled, doesn't support DPO or FUA
Jun 22 15:20:25 Potter64buntu kernel: [   36.803086] sd 1:0:1:0: [sdb] 321672960 512-byte hardware sectors 

(164697 MB)
Jun 22 15:20:25 Potter64buntu kernel: [   36.803092] sd 1:0:1:0: [sdb] Write Protect is off
Jun 22 15:20:25 Potter64buntu kernel: [   36.803093] sd 

1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jun 22 15:20:25 Potter64buntu kernel: [   36.803103] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, 

doesn't support DPO or FUA
Jun 22 15:20:25 Potter64buntu kernel: [   36.803105]  sdb: sdb1 sdb2 < sdb5sr0: scsi3-mmc drive: 94x/94x writer dvd-ram cd/rw 

xa/form2 cdda tray
Jun 22 15:20:25 Potter64buntu kernel: [   36.831352] Uniform CD-ROM driver Revision: 3.20
Jun 22 15:20:25 Potter64buntu kernel: [   

36.831380] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 22 15:20:25 Potter64buntu kernel: [   36.846573]  sdb6 sdb7 >
Jun 22 15:20:25 Potter64buntu kernel: [   

36.853051] sd 1:0:1:0: [sdb] Attached SCSI disk
Jun 22 15:20:25 Potter64buntu kernel: [   36.855470] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 22 

15:20:25 Potter64buntu kernel: [   36.855481] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jun 22 15:20:25 Potter64buntu kernel: [   36.855492] sd 1:0:1:0: 

Attached scsi generic sg2 type 0
Jun 22 15:20:25 Potter64buntu kernel: [   36.976254] usb 4-2: new full speed USB device using uhci_hcd and address 2
Jun 22 

15:20:25 Potter64buntu kernel: [   37.152533] usb 4-2: configuration #1 chosen from 1 choice
Jun 22 15:20:25 Potter64buntu kernel: [   37.155650] usbcore: 

registered new interface driver hiddev
Jun 22 15:20:25 Potter64buntu kernel: [   37.169616] input: Formosa21 USB IR Receiver as 

/devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2
Jun 22 15:20:25 Potter64buntu kernel: [   37.196267] input,hidraw0: USB HID v1.10 Keyboard 

[Formosa21 USB IR Receiver] on usb-0000:00:1d.1-2
Jun 22 15:20:25 Potter64buntu kernel: [   37.196279] usbcore: registered new interface driver usbhid
Jun 22 

15:20:25 Potter64buntu kernel: [   37.196280] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jun 22 15:20:25 Potter64buntu 

kernel: [   37.230411] Attempting manual resume
Jun 22 15:20:25 Potter64buntu kernel: [   37.230413] swsusp: Resume From Partition 8:7
Jun 22 15:20:25 

Potter64buntu kernel: [   37.230414] PM: Checking swsusp image.
Jun 22 15:20:25 Potter64buntu kernel: [   37.230538] PM: Resume from disk failed.
Jun 22 

15:20:25 Potter64buntu kernel: [   37.256337] EXT3-fs: INFO: recovery required on readonly filesystem.
Jun 22 15:20:25 Potter64buntu kernel: [   37.256339] 

EXT3-fs: write access will be enabled during recovery.
Jun 22 15:20:25 Potter64buntu kernel: [   39.096982] kjournald starting.  Commit interval 5 seconds
Jun 

22 15:20:25 Potter64buntu kernel: [   39.096988] EXT3-fs: sda5: orphan cleanup on readonly fs
Jun 22 15:20:25 Potter64buntu kernel: [   39.096993] 

ext3_orphan_cleanup: deleting unreferenced inode 589869
Jun 22 15:20:25 Potter64buntu kernel: [   39.097018] ext3_orphan_cleanup: deleting unreferenced inode 

862209
Jun 22 15:20:25 Potter64buntu kernel: [   39.097030] ext3_orphan_cleanup: deleting unreferenced inode 862208
Jun 22 15:20:25 Potter64buntu kernel: [   

39.097036] ext3_orphan_cleanup: deleting unreferenced inode 589845
Jun 22 15:20:25 Potter64buntu kernel: [   39.097040] EXT3-fs: sda5: 4 orphan inodes deleted
Jun 22 15:20:25 Potter64buntu kernel: [   39.097042] EXT3-fs: recovery complete.
Jun 22 15:20:25 Potter64buntu kernel: [   39.135435] EXT3-fs: mounted 

filesystem with ordered data mode.
Jun 22 15:20:25 Potter64buntu kernel: [   46.672091] input: PC Speaker as /devices/platform/pcspkr/input/input3
Jun 22 

15:20:25 Potter64buntu kernel: [   46.765652] iTCO_vendor_support: vendor-support=0
Jun 22 15:20:25 Potter64buntu kernel: [   46.793424] iTCO_wdt: Intel TCO 

WatchDog Timer Driver v1.02 (26-Jul-2007)
Jun 22 15:20:25 Potter64buntu kernel: [   46.948208] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 22 15:20:25 

Potter64buntu kernel: [   46.964312] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 22 15:20:25 Potter64buntu kernel: [   46.992346] input: 

Power Button (FF) as /devices/virtual/input/input4
Jun 22 15:20:25 Potter64buntu kernel: [   47.056181] ACPI: Power Button (FF) [PWRF]
Jun 22 15:20:25 

Potter64buntu kernel: [   47.056217] input: Power Button (CM) as /devices/virtual/input/input5
Jun 22 15:20:25 Potter64buntu kernel: [   47.120185] ACPI: 

Power Button (CM) [PWRB]
Jun 22 15:20:25 Potter64buntu kernel: [   47.472994] input: ImExPS/2 Generic Explorer Mouse as 

/devices/platform/i8042/serio1/input/input6
Jun 22 15:20:25 Potter64buntu kernel: [   47.523246] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, 

TCOBASE=0x0460)
Jun 22 15:20:25 Potter64buntu kernel: [   47.523269] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun 22 15:20:25 Potter64buntu kernel: 

[   47.523293] parport_pc 00:08: reported by Plug and Play ACPI
Jun 22 15:20:25 Potter64buntu kernel: [   47.523336] parport0: PC-style at 0x378, irq 7 

[PCSPP,TRISTATE]
Jun 22 15:20:25 Potter64buntu kernel: [   47.551610] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
Jun 

22 15:20:25 Potter64buntu kernel: [   47.552903] flexcop-pci: will use the HW PID filter.
Jun 22 15:20:25 Potter64buntu kernel: [   47.552907] flexcop-pci: 

card revision 2
Jun 22 15:20:25 Potter64buntu kernel: [   47.552913] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:20:25 

Potter64buntu kernel: [   47.567797] DVB: registering new adapter (FlexCop Digital TV device)
Jun 22 15:20:25 Potter64buntu kernel: [   47.569392] b2c2-

flexcop: MAC address = 00:08:c9:a1:0f:18
Jun 22 15:20:25 Potter64buntu kernel: [   47.647491] Bluetooth: Core ver 2.11
Jun 22 15:20:25 Potter64buntu kernel: [  

 47.648763] NET: Registered protocol family 31
Jun 22 15:20:25 Potter64buntu kernel: [   47.648764] Bluetooth: HCI device and connection manager initialized
Jun 22 15:20:25 Potter64buntu kernel: [   47.648766] Bluetooth: HCI socket layer initialized
Jun 22 15:20:25 Potter64buntu kernel: [   47.712150] hsfengine: 

module license 'see LICENSE file distributed with driver' taints kernel.
Jun 22 15:20:25 Potter64buntu kernel: [   47.787016] intel_rng: FWH not detected
Jun 

22 15:20:25 Potter64buntu kernel: [   47.862188] Bluetooth: HCI USB driver ver 2.9
Jun 22 15:20:25 Potter64buntu kernel: [   47.864055] usbcore: registered 

new interface driver hci_usb
Jun 22 15:20:25 Potter64buntu kernel: [   47.914854] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:20:25 Potter64buntu kernel: [  

 48.115908] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:20:25 Potter64buntu kernel: [   48.139203] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:20:25 

Potter64buntu kernel: [   48.139205] mt352_read_register: readreg error (reg=127, ret==-121)
Jun 22 15:20:25 Potter64buntu kernel: [   48.152533] b2c2-

flexcop: i2c master_xfer failed
Jun 22 15:20:25 Potter64buntu kernel: [   48.152535] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -121)
Jun 22 

15:20:25 Potter64buntu kernel: [   48.152537] Unknown/Unsupported NXT chip: 00 00 00 00 00
Jun 22 15:20:25 Potter64buntu kernel: [   48.171729] b2c2-flexcop: 

i2c master_xfer failed
Jun 22 15:20:25 Potter64buntu kernel: [   48.171730] lgdt330x: i2c_read_demod_bytes: addr 0x59 select 0x02 error (ret == -121)
Jun 22 

15:20:25 Potter64buntu kernel: [   48.195528] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:20:25 Potter64buntu kernel: [   48.210241] b2c2-flexcop: i2c 

master_xfer failed
Jun 22 15:20:25 Potter64buntu kernel: [   48.210243] stv0297_readreg: readreg error (reg == 0x80, ret == -121)
Jun 22 15:20:25 Potter64buntu 

kernel: [   48.223433] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:20:25 Potter64buntu kernel: [   48.223435] mt312_read: ret == -121
Jun 22 15:20:25 

Potter64buntu kernel: [   48.223447] b2c2-flexcop: no frontend driver found for this B2C2/FlexCop adapter
Jun 22 15:20:25 Potter64buntu kernel: [   48.224806] 

ACPI: PCI interrupt for device 0000:04:01.0 disabled
Jun 22 15:20:25 Potter64buntu kernel: [   48.224997] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 

(level, low) -> IRQ 16
Jun 22 15:20:25 Potter64buntu kernel: [   48.226234] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Jun 22 15:20:25 

Potter64buntu kernel: [   48.289440] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 18 (level, low) -> IRQ 18
Jun 22 15:20:25 Potter64buntu kernel: [   49.021241] 

ttySHSF0 at I/O 0xd100 (irq = 18) is a Conexant HSF softmodem (PCI-14f1:2f30-14f1:20d5)
Jun 22 15:20:25 Potter64buntu kernel: [   49.224545] lp0: using 

parport0 (interrupt-driven).
Jun 22 15:20:25 Potter64buntu kernel: [   49.279512] Adding 979924k swap on /dev/sda7.  Priority:-1 extents:1 across:979924k
Jun 

22 15:20:25 Potter64buntu kernel: [   49.804319] EXT3 FS on sda5, internal journal
Jun 22 15:20:25 Potter64buntu kernel: [   53.816749] kjournald starting.  

Commit interval 5 seconds
Jun 22 15:20:25 Potter64buntu kernel: [   53.816986] EXT3 FS on sda6, internal journal
Jun 22 15:20:25 Potter64buntu kernel: [   

53.816989] EXT3-fs: mounted filesystem with ordered data mode.
Jun 22 15:20:25 Potter64buntu kernel: [   53.834780] kjournald starting.  Commit interval 5 

seconds
Jun 22 15:20:25 Potter64buntu kernel: [   53.835053] EXT3 FS on sda8, internal journal
Jun 22 15:20:25 Potter64buntu kernel: [   53.835056] EXT3-fs: 

mounted filesystem with ordered data mode.
Jun 22 15:20:25 Potter64buntu kernel: [   54.030517] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 22 15:20:25 

Potter64buntu kernel: [   63.128188] No dock devices found.
Jun 22 15:20:25 Potter64buntu NetworkManager: <info>  starting... 
Jun 22 15:20:25 Potter64buntu 

avahi-daemon[8578]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jun 22 15:20:25 Potter64buntu avahi-daemon[8578]: Successfully dropped root 

privileges.
Jun 22 15:20:25 Potter64buntu avahi-daemon[8578]: avahi-daemon 0.6.22 starting up.
Jun 22 15:20:25 Potter64buntu avahi-daemon[8578]: Successfully 

called chroot().
Jun 22 15:20:25 Potter64buntu avahi-daemon[8578]: Successfully dropped remaining capabilities.
Jun 22 15:20:25 Potter64buntu avahi-daemon

[8578]: No service file found in /etc/avahi/services.
Jun 22 15:20:25 Potter64buntu avahi-daemon[8578]: Network interface enumeration completed.
Jun 22 

15:20:25 Potter64buntu avahi-daemon[8578]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 22 15:20:25 Potter64buntu avahi-daemon[8578]: Server 

startup complete. Host name is Potter64buntu.local. Local service cookie is 3480980385.
Jun 22 15:20:25 Potter64buntu kernel: [   63.769840] ppdev: user-space 

parallel port driver
Jun 22 15:20:25 Potter64buntu kernel: [   63.863685] audit(1214131825.682:2): type=1503 operation="inode_permission" requested_mask="a::" 

denied_mask="a::" name="/dev/tty" pid=8611 profile="/usr/sbin/cupsd" namespace="default"
Jun 22 15:20:25 Potter64buntu dhcdbd: Started up.
Jun 22 15:20:28 

Potter64buntu kernel: [   66.723367] r8169: eth0: link down
Jun 22 15:20:28 Potter64buntu NetworkManager: <info>  eth0: Device is fully-supported using driver 

'r8169'. 
Jun 22 15:20:28 Potter64buntu NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Jun 22 15:20:28 Potter64buntu 

NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 22 15:20:28 Potter64buntu NetworkManager: <info>  Now managing 

wired Ethernet (802.3) device 'eth0'. 
Jun 22 15:20:28 Potter64buntu NetworkManager: <info>  Deactivating device eth0. 
Jun 22 15:20:28 Potter64buntu 

NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jun 22 15:20:28 Potter64buntu hcid[8838]: Bluetooth HCI daemon
Jun 22 

15:20:28 Potter64buntu hcid[8838]: HCI dev 0 registered
Jun 22 15:20:28 Potter64buntu hcid[8838]: Starting SDP server
Jun 22 15:20:28 Potter64buntu kernel: [   

66.792487] Bluetooth: L2CAP ver 2.9
Jun 22 15:20:28 Potter64buntu hcid[8838]: Created local server at unix:abstract=/var/run/dbus-

28YJUudUQV,guid=25db359d10b9e38b94ca6e65485e2e74
Jun 22 15:20:28 Potter64buntu kernel: [   66.792491] Bluetooth: L2CAP socket layer initialized
Jun 22 15:20:28 

Potter64buntu audio[8859]: Bluetooth Audio daemon
Jun 22 15:20:28 Potter64buntu audio[8859]: Unix socket created: 5
Jun 22 15:20:28 Potter64buntu audio[8859]: 

audio.conf: Key file does not have key 'Enable'
Jun 22 15:20:28 Potter64buntu audio[8859]: audio.conf: Key file does not have key 'Disable'
Jun 22 15:20:28 

Potter64buntu hcid[8838]: HCI dev 0 up
Jun 22 15:20:28 Potter64buntu hcid[8838]: Device hci0 has been added
Jun 22 15:20:28 Potter64buntu hcid[8838]: Starting 

security manager 0
Jun 22 15:20:28 Potter64buntu kernel: [   66.854017] Bluetooth: RFCOMM socket layer initialized
Jun 22 15:20:28 Potter64buntu kernel: [   

66.854025] Bluetooth: RFCOMM TTY layer initialized
Jun 22 15:20:28 Potter64buntu kernel: [   66.854026] Bluetooth: RFCOMM ver 1.8
Jun 22 15:20:28 Potter64buntu 

input[8860]: Bluetooth Input daemon
Jun 22 15:20:28 Potter64buntu input[8860]: Registered input manager path:/org/bluez/input
Jun 22 15:20:28 Potter64buntu 

hcid[8838]: Device hci0 has been activated
Jun 22 15:20:28 Potter64buntu audio[8859]: add_service_record: got record id 0x10000
Jun 22 15:20:28 Potter64buntu 

audio[8859]: audio.conf: Key file does not have key 'Disable'
Jun 22 15:20:28 Potter64buntu audio[8859]: audio.conf: Key file does not have group 'A2DP'
Jun 22 

15:20:28 Potter64buntu last message repeated 3 times
Jun 22 15:20:28 Potter64buntu audio[8859]: SEP 0x62d3b0 registered: type:0 codec:0 seid:1
Jun 22 15:20:28 

Potter64buntu audio[8859]: add_service_record: got record id 0x10001
Jun 22 15:20:28 Potter64buntu audio[8859]: add_service_record: got record id 0x10002
Jun 

22 15:20:28 Potter64buntu audio[8859]: add_service_record: got record id 0x10003
Jun 22 15:20:28 Potter64buntu audio[8859]: Registered manager 

path:/org/bluez/audio
Jun 22 15:20:30 Potter64buntu anacron[8940]: Anacron 2.3 started on 2008-06-22
Jun 22 15:20:30 Potter64buntu anacron[8940]: Will run job 

`cron.daily' in 5 min.
Jun 22 15:20:30 Potter64buntu anacron[8940]: Will run job `cron.weekly' in 10 min.
Jun 22 15:20:30 Potter64buntu anacron[8940]: Jobs 

will be executed sequentially
Jun 22 15:20:30 Potter64buntu /usr/sbin/cron[8969]: (CRON) INFO (pidfile fd = 3)
Jun 22 15:20:30 Potter64buntu /usr/sbin/cron

[8970]: (CRON) STARTUP (fork ok)
Jun 22 15:20:30 Potter64buntu /usr/sbin/cron[8970]: (CRON) INFO (Running @reboot jobs)
Jun 22 15:25:30 Potter64buntu anacron

[8940]: Job `cron.daily' started
Jun 22 15:25:30 Potter64buntu anacron[9069]: Updated timestamp for job `cron.daily' to 2008-06-22
Jun 22 15:28:03 

Potter64buntu kernel: [  521.912647] NET: Registered protocol family 10
Jun 22 15:28:03 Potter64buntu kernel: [  521.912823] lo: Disabled Privacy Extensions
Jun 22 15:28:03 Potter64buntu kernel: [  521.913079] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 22 15:28:05 Potter64buntu hcid[8838]: Default passkey 

agent (:1.19, /org/bluez/passkey) registered
Jun 22 15:28:05 Potter64buntu hcid[8838]: Default authorization agent (:1.19, /org/bluez/auth) registered
Jun 22 

15:28:07 Potter64buntu NetworkManager: <info>  Updating allowed wireless network lists. 
Jun 22 15:28:07 Potter64buntu NetworkManager: <WARN>  

nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun 22 15:28:08 

Potter64buntu kernel: [  526.942627] cdrom: sr0: mrw address space DMA selected
Jun 22 15:28:08 Potter64buntu kernel: [  527.067233] cdrom: sr0: mrw address 

space DMA selected
Jun 22 15:28:12 Potter64buntu kernel: [  531.128975] UDF-fs: No VRS found
Jun 22 15:28:13 Potter64buntu kernel: [  531.176091] ISO 9660 

Extensions: Microsoft Joliet Level 3
Jun 22 15:28:13 Potter64buntu kernel: [  531.176747] ISOFS: changing to secondary root
Jun 22 15:28:20 Potter64buntu 

kernel: [  538.243045] usb 5-3: new high speed USB device using ehci_hcd and address 4
Jun 22 15:28:20 Potter64buntu kernel: [  538.377808] usb 5-3: 

configuration #1 chosen from 1 choice
Jun 22 15:28:20 Potter64buntu NetworkManager: <debug> [1214132300.229295] nm_hal_device_added(): New device added (hal 

udi is '/org/freedesktop/Hal/devices/usb_device_951_1605_5B7B19900669'). 
Jun 22 15:28:20 Potter64buntu kernel: [  538.436339] usbcore: registered new 

interface driver libusual
Jun 22 15:28:20 Potter64buntu NetworkManager: <debug> [1214132300.297132] nm_hal_device_added(): New device added (hal udi is 

'/org/freedesktop/Hal/devices/usb_device_951_1605_5B7B19900669_if0'). 
Jun 22 15:28:20 Potter64buntu kernel: [  538.460524] Initializing USB Mass Storage 

driver...
Jun 22 15:28:20 Potter64buntu kernel: [  538.461176] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 22 15:28:20 Potter64buntu kernel: [  

538.461728] usbcore: registered new interface driver usb-storage
Jun 22 15:28:20 Potter64buntu kernel: [  538.461730] USB Mass Storage support registered.
Jun 

22 15:28:20 Potter64buntu kernel: [  538.461905] usb-storage: device found at 4
Jun 22 15:28:20 Potter64buntu kernel: [  538.461906] usb-storage: waiting for 

device to settle before scanning
Jun 22 15:28:25 Potter64buntu kernel: [  543.458873] usb-storage: device scan complete
Jun 22 15:28:25 Potter64buntu kernel: [ 

 543.459633] scsi 2:0:0:0: Direct-Access     Kingston DataTravelerMini PMAP PQ: 0 ANSI: 0 CCS
Jun 22 15:28:25 Potter64buntu NetworkManager: <debug> 

[1214132305.356974] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_951_1605_5B7B19900669_if0_scsi_host'). 
Jun 

22 15:28:25 Potter64buntu NetworkManager: <debug> [1214132305.358187] nm_hal_device_added(): New device added (hal udi is 

'/org/freedesktop/Hal/devices/usb_device_951_1605_5B7B19900669_if0_scsi_host_scsi_device_lun0'). 
Jun 22 15:28:27 Potter64buntu kernel: [  545.192362] sd 

2:0:0:0: [sdc] 4030464 512-byte hardware sectors (2064 MB)
Jun 22 15:28:27 Potter64buntu kernel: [  545.192987] sd 2:0:0:0: [sdc] Write Protect is off
Jun 22 

15:28:27 Potter64buntu kernel: [  545.192989] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
Jun 22 15:28:27 Potter64buntu kernel: [  545.192991] sd 2:0:0:0: [sdc] 

Assuming drive cache: write through
Jun 22 15:28:27 Potter64buntu kernel: [  545.196233] sd 2:0:0:0: [sdc] 4030464 512-byte hardware sectors (2064 MB)
Jun 22 

15:28:27 Potter64buntu kernel: [  545.196859] sd 2:0:0:0: [sdc] Write Protect is off
Jun 22 15:28:27 Potter64buntu kernel: [  545.196862] sd 2:0:0:0: [sdc] 

Mode Sense: 23 00 00 00
Jun 22 15:28:27 Potter64buntu kernel: [  545.196863] sd 2:0:0:0: [sdc] Assuming drive cache: write through
Jun 22 15:28:27 

Potter64buntu kernel: [  545.196866]  sdc: sdc1
Jun 22 15:28:27 Potter64buntu kernel: [  545.198285] sd 2:0:0:0: [sdc] Attached SCSI removable disk
Jun 22 

15:28:27 Potter64buntu kernel: [  545.198316] sd 2:0:0:0: Attached scsi generic sg3 type 0
Jun 22 15:28:27 Potter64buntu NetworkManager: <debug> 

[1214132307.051779] nm_hal_device_added(): New device added (hal udi is 

'/org/freedesktop/Hal/devices/usb_device_951_1605_5B7B19900669_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
Jun 22 15:28:27 Potter64buntu NetworkManager: 

<debug> [1214132307.360617] nm_hal_device_added(): New device added (hal udi is 

'/org/freedesktop/Hal/devices/storage_serial_Kingston_DataTravelerMini_5B7B19900669_0_0'). 
Jun 22 15:28:27 Potter64buntu NetworkManager: <debug> 

[1214132307.399348] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_68AB_FB60'). 
Jun 22 15:28:29 Potter64buntu 

hald: mounted /dev/sdc1 on behalf of uid 1000
Jun 22 15:32:26 Potter64buntu kernel: [  784.631319] PPP generic driver version 2.4.2
Jun 22 15:32:26 

Potter64buntu pppd[9467]: pppd 2.4.4 started by potter, uid 1000
Jun 22 15:32:26 Potter64buntu pppd[9467]: Using interface ppp0
Jun 22 15:32:26 Potter64buntu 

pppd[9467]: Connect: ppp0 <--> /dev/ttySHSF0
Jun 22 15:32:28 Potter64buntu pppd[9467]: PAP authentication succeeded
Jun 22 15:32:28 Potter64buntu kernel: [  

786.717334] PPP BSD Compression module registered
Jun 22 15:32:28 Potter64buntu kernel: [  786.759597] PPP Deflate Compression module registered
Jun 22 

15:32:29 Potter64buntu pppd[9467]: Cannot determine ethernet address for proxy ARP
Jun 22 15:32:29 Potter64buntu pppd[9467]: local  IP address 84.241.17.169
Jun 22 15:32:29 Potter64buntu pppd[9467]: remote IP address 85.15.0.134
Jun 22 15:32:29 Potter64buntu pppd[9467]: primary   DNS address 85.15.1.12
Jun 22 

15:32:29 Potter64buntu pppd[9467]: secondary DNS address 85.15.1.10
Jun 22 15:32:31 Potter64buntu pppd[9467]: CCP terminated by peer
Jun 22 15:32:31 

Potter64buntu pppd[9467]: Compression disabled by peer.
[COLOR="Red"]Jun 22 15:36:10 Potter64buntu kernel: [ 1008.321540] general protection fault: 0000 [1] 

SMP [/COLOR]


Jun 22 15:37:41 Potter64buntu syslogd 1.5.0#1ubuntu1: restart.
Jun 22 15:37:41 Potter64buntu kernel: Inspecting /boot/System.map-2.6.24-16-generic
Jun 22 15:37:41 Potter64buntu kernel: Loaded 28313 symbols from /boot/System.map-2.6.24-16-generic.
Jun 22 15:37:41 Potter64buntu kernel: Symbols match kernel 

version 2.6.24.
Jun 22 15:37:41 Potter64buntu kernel: Loaded 26836 symbols from 95 modules.
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Linux version 

2.6.24-16-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 12:47:45 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
Jun 22 

15:37:41 Potter64buntu kernel: [    0.000000] Command line: root=UUID=f3afdcdd-5a53-41ee-967b-c34e7e03e262 ro quiet splash
Jun 22 15:37:41 Potter64buntu 

kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 

(usable)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 22 15:37:41 Potter64buntu kernel: 

[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 

000000007fee0000 (usable)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
Jun 22 15:37:41 

Potter64buntu kernel: [    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]  BIOS-

e820: 000000007fef0000 - 000000007ff00000 (reserved)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 

(reserved)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Jun 22 15:37:41 Potter64buntu 

kernel: [    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Entering 

add_active_range(0, 256, 524000) 1 entries of 3200 used
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] end_pfn_map = 1048576
Jun 22 15:37:41 

Potter64buntu kernel: [    0.000000] DMI 2.4 present.
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6990 checksum 

0
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: RSDP 000F6990, 0014 (r0 GBT   )
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: RSDT 

7FEE3040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 GBT    GBTUACPI 

42302E31 GBTU  1010101)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: DSDT 7FEE3180, 3955 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
Jun 22 

15:37:41 Potter64buntu kernel: [    0.000000] ACPI: FACS 7FEE0000, 0040
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: HPET 7FEE6C40, 0038 (r1 GBT 

   GBTUACPI 42302E31 GBTU       98)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: MCFG 7FEE6CC0, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: APIC 7FEE6B40, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
Jun 22 15:37:41 Potter64buntu 

kernel: [    0.000000] ACPI: SSDT 7FEE6D40, 015C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: SSDT 

7FEE71D0, 0275 (r1  PmRef    CpuPm     3000 INTL 20040311)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] No NUMA configuration found
Jun 22 15:37:41 

Potter64buntu kernel: [    0.000000] Faking a node at 0000000000000000-000000007fee0000
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Entering 

add_active_range(0, 0, 159) 0 entries of 3200 used
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Entering add_active_range(0, 256, 524000) 1 entries of 

3200 used
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007fee0000
Jun 22 15:37:41 Potter64buntu kernel: [   

 0.000000] Zone PFN ranges:
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]   DMA             0 ->     4096
Jun 22 15:37:41 Potter64buntu kernel: [    

0.000000]   DMA32        4096 ->  1048576
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]   Normal    1048576 ->  1048576
Jun 22 15:37:41 Potter64buntu 

kernel: [    0.000000] Movable zone start PFN for each node
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] early_node_map[2] active PFN ranges
Jun 22 

15:37:41 Potter64buntu kernel: [    0.000000]     0:        0 ->      159
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]     0:      256 ->   524000
Jun 

22 15:37:41 Potter64buntu kernel: [    0.000000] On node 0 totalpages: 523903
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]   DMA zone: 56 pages used 

for memmap
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]   DMA zone: 1208 pages reserved
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]   DMA 

zone: 2735 pages, LIFO batch:0
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]   DMA32 zone: 7108 pages used for memmap
Jun 22 15:37:41 Potter64buntu 

kernel: [    0.000000]   DMA32 zone: 512796 pages, LIFO batch:31
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]   Normal zone: 0 pages used for memmap
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: PM-

Timer IO Port: 0x408
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 22 15:37:41 Potter64buntu kernel: [    

0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Processor #0 (Bootup-CPU)
Jun 22 15:37:41 

Potter64buntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Processor #1
Jun 

22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] 

ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Jun 

22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: 

LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
Jun 22 

15:37:41 Potter64buntu kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] 

IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl 

dfl)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 22 15:37:41 Potter64buntu kernel: [   

 0.000000] ACPI: IRQ0 used by override.
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 22 15:37:41 Potter64buntu kernel: 

[    0.000000] ACPI: IRQ9 used by override.
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Setting APIC routing to flat
Jun 22 15:37:41 Potter64buntu 

kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration 

information
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 22 15:37:41 

Potter64buntu kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jun 22 15:37:41 Potter64buntu kernel: [    

0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Allocating PCI 

resources starting at 80000000 (gap: 7ff00000:70100000)
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Jun 22 

15:37:41 Potter64buntu kernel: [    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Built 1 

zonelists in Node order, mobility grouping on.  Total pages: 515531
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] Policy zone: DMA32
Jun 22 15:37:41 

Potter64buntu kernel: [    0.000000] Kernel command line: root=UUID=f3afdcdd-5a53-41ee-967b-c34e7e03e262 ro quiet splash
Jun 22 15:37:41 Potter64buntu kernel: 

[    0.000000] Initializing CPU#0
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jun 22 15:37:41 

Potter64buntu kernel: [    0.000000] hpet clockevent registered
Jun 22 15:37:41 Potter64buntu kernel: [    0.000000] TSC calibrated against HPET
Jun 22 

15:37:41 Potter64buntu kernel: [   35.079129] time.c: Detected 2666.669 MHz processor.
Jun 22 15:37:41 Potter64buntu kernel: [   35.080214] Console: colour 

VGA+ 80x25
Jun 22 15:37:41 Potter64buntu kernel: [   35.080216] console [tty0] enabled
Jun 22 15:37:41 Potter64buntu kernel: [   35.080229] Checking 

aperture...
Jun 22 15:37:41 Potter64buntu kernel: [   35.080235] Calgary: detecting Calgary via BIOS EBDA area
Jun 22 15:37:41 Potter64buntu kernel: [   

35.080236] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun 22 15:37:41 Potter64buntu kernel: [   35.094704] Memory: 2053636k/2096000k 

available (2466k kernel code, 41976k reserved, 1309k data, 316k init)
Jun 22 15:37:41 Potter64buntu kernel: [   35.094730] SLUB: Genslabs=12, HWalign=64, 

Order=0-1, MinObjects=4, CPUs=4, Nodes=1
Jun 22 15:37:41 Potter64buntu kernel: [   35.172875] Calibrating delay using timer specific routine.. 5336.62 

BogoMIPS (lpj=10673243)
Jun 22 15:37:41 Potter64buntu kernel: [   35.172899] Security Framework initialized
Jun 22 15:37:41 Potter64buntu kernel: [   

35.172903] SELinux:  Disabled at boot.
Jun 22 15:37:41 Potter64buntu kernel: [   35.172912] AppArmor: AppArmor initialized
Jun 22 15:37:41 Potter64buntu 

kernel: [   35.172915] Failure registering capabilities with primary security module.
Jun 22 15:37:41 Potter64buntu kernel: [   35.173057] Dentry cache hash 

table entries: 262144 (order: 9, 2097152 bytes)
Jun 22 15:37:41 Potter64buntu kernel: [   35.173994] Inode-cache hash table entries: 131072 (order: 8, 1048576 

bytes)
Jun 22 15:37:41 Potter64buntu kernel: [   35.174421] Mount-cache hash table entries: 256
Jun 22 15:37:41 Potter64buntu kernel: [   35.174510] CPU: L1 I 

cache: 32K, L1 D cache: 32K
Jun 22 15:37:41 Potter64buntu kernel: [   35.174512] CPU: L2 cache: 6144K
Jun 22 15:37:41 Potter64buntu kernel: [   35.174514] CPU 

0/0 -> Node 0
Jun 22 15:37:41 Potter64buntu kernel: [   35.174515] using mwait in idle threads.
Jun 22 15:37:41 Potter64buntu kernel: [   35.174516] CPU: 

Physical Processor ID: 0
Jun 22 15:37:41 Potter64buntu kernel: [   35.174517] CPU: Processor Core ID: 0
Jun 22 15:37:41 Potter64buntu kernel: [   35.174521] 

CPU0: Thermal monitoring enabled (TM2)
Jun 22 15:37:41 Potter64buntu kernel: [   35.174531] SMP alternatives: switching to UP code
Jun 22 15:37:41 

Potter64buntu kernel: [   35.175179] Early unpacking initramfs... done
Jun 22 15:37:41 Potter64buntu kernel: [   35.449779] ACPI: Core revision 20070126
Jun 22 

15:37:41 Potter64buntu kernel: [   35.449805] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 22 15:37:41 Potter64buntu kernel: [  

 35.492407] Using local APIC timer interrupts.
Jun 22 15:37:41 Potter64buntu kernel: [   35.529814] APIC timer calibration result 20833348
Jun 22 15:37:41 

Potter64buntu kernel: [   35.529815] Detected 20.833 MHz APIC timer.
Jun 22 15:37:41 Potter64buntu kernel: [   35.529869] SMP alternatives: switching to SMP 

code
Jun 22 15:37:41 Potter64buntu kernel: [   35.530448] Booting processor 1/2 APIC 0x1
Jun 22 15:37:41 Potter64buntu kernel: [   35.541042] Initializing 

CPU#1
Jun 22 15:37:41 Potter64buntu kernel: [   35.617589] Calibrating delay using timer specific routine.. 5333.36 BogoMIPS (lpj=10666720)
Jun 22 15:37:41 

Potter64buntu kernel: [   35.617594] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 22 15:37:41 Potter64buntu kernel: [   35.617595] CPU: L2 cache: 6144K
Jun 22 

15:37:41 Potter64buntu kernel: [   35.617596] CPU 1/1 -> Node 0
Jun 22 15:37:41 Potter64buntu kernel: [   35.617598] CPU: Physical Processor ID: 0
Jun 22 

15:37:41 Potter64buntu kernel: [   35.617598] CPU: Processor Core ID: 1
Jun 22 15:37:41 Potter64buntu kernel: [   35.617603] CPU1: Thermal monitoring enabled 

(TM2)
Jun 22 15:37:41 Potter64buntu kernel: [   35.618285] Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz stepping 06
Jun 22 15:37:41 Potter64buntu kernel: [  

 35.618315] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 22 15:37:41 Potter64buntu kernel: [   35.638281] Brought up 2 CPUs
Jun 22 15:37:41 

Potter64buntu kernel: [   35.638339] CPU0 attaching sched-domain:
Jun 22 15:37:41 Potter64buntu kernel: [   35.638340]  domain 0: span 03
Jun 22 15:37:41 

Potter64buntu kernel: [   35.638341]   groups: 01 02
Jun 22 15:37:41 Potter64buntu kernel: [   35.638343]   domain 1: span 03
Jun 22 15:37:41 Potter64buntu 

kernel: [   35.638344]    groups: 03
Jun 22 15:37:41 Potter64buntu kernel: [   35.638345] CPU1 attaching sched-domain:
Jun 22 15:37:41 Potter64buntu kernel: [  

 35.638346]  domain 0: span 03
Jun 22 15:37:41 Potter64buntu kernel: [   35.638347]   groups: 02 01
Jun 22 15:37:41 Potter64buntu kernel: [   35.638349]   

domain 1: span 03
Jun 22 15:37:41 Potter64buntu kernel: [   35.638350]    groups: 03
Jun 22 15:37:41 Potter64buntu kernel: [   35.638503] net_namespace: 120 

bytes
Jun 22 15:37:41 Potter64buntu kernel: [   35.638763] Time: 15:37:13  Date: 06/22/08
Jun 22 15:37:41 Potter64buntu kernel: [   35.638780] NET: Registered 

protocol family 16
Jun 22 15:37:41 Potter64buntu kernel: [   35.638905] ACPI: bus type pci registered
Jun 22 15:37:41 Potter64buntu kernel: [   35.638957] PCI: 

Using configuration type 1
Jun 22 15:37:41 Potter64buntu kernel: [   35.639711] ACPI: EC: Look up EC in DSDT
Jun 22 15:37:41 Potter64buntu kernel: [   

35.642649] ACPI: Interpreter enabled
Jun 22 15:37:41 Potter64buntu kernel: [   35.642653] ACPI: (supports S0 S3 S4 S5)
Jun 22 15:37:41 Potter64buntu kernel: [  

 35.642664] ACPI: Using IOAPIC for interrupt routing
Jun 22 15:37:41 Potter64buntu kernel: [   35.645579] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 22 

15:37:41 Potter64buntu kernel: [   35.645952] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
Jun 22 15:37:41 Potter64buntu kernel: [   35.645954] 

PCI quirk: region 0480-04bf claimed by ICH6 GPIO
Jun 22 15:37:41 Potter64buntu kernel: [   35.646380] PCI: Transparent bridge - 0000:00:1e.0
Jun 22 15:37:41 

Potter64buntu kernel: [   35.646399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 22 15:37:41 Potter64buntu kernel: [   35.646482] ACPI: PCI 

Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Jun 22 15:37:41 Potter64buntu kernel: [   35.646530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Jun 22 15:37:41 Potter64buntu kernel: [   35.646576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Jun 22 15:37:41 Potter64buntu kernel: [   

35.652664] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 22 15:37:41 Potter64buntu kernel: [   35.652723] ACPI: PCI Interrupt Link 

[LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 22 15:37:41 Potter64buntu kernel: [   35.652781] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 

10 11 12 14 15)
Jun 22 15:37:41 Potter64buntu kernel: [   35.652838] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 22 15:37:41 

Potter64buntu kernel: [   35.652896] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 22 15:37:41 Potter64buntu kernel: [   

35.652953] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 22 15:37:41 Potter64buntu kernel: [   35.653011] ACPI: PCI 

Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Jun 22 15:37:41 Potter64buntu kernel: [   35.653069] ACPI: PCI Interrupt Link [LNK1] 

(IRQs *3 4 5 6 7 9 10 11 12 14 15)
Jun 22 15:37:41 Potter64buntu kernel: [   35.653145] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 22 15:37:41 

Potter64buntu kernel: [   35.653163] pnp: PnP ACPI init
Jun 22 15:37:41 Potter64buntu kernel: [   35.653168] ACPI: bus type pnp registered
Jun 22 15:37:41 

Potter64buntu kernel: [   35.654706] pnpacpi: exceeded the max number of mem resources: 12
Jun 22 15:37:41 Potter64buntu kernel: [   35.654792] pnp: PnP ACPI: 

found 15 devices
Jun 22 15:37:41 Potter64buntu kernel: [   35.654793] ACPI: ACPI bus type pnp unregistered
Jun 22 15:37:41 Potter64buntu kernel: [   35.654946] 

PCI: Using ACPI for IRQ routing
Jun 22 15:37:41 Potter64buntu kernel: [   35.654948] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a 

report
Jun 22 15:37:41 Potter64buntu kernel: [   35.665510] NET: Registered protocol family 8
Jun 22 15:37:41 Potter64buntu kernel: [   35.665512] NET: 

Registered protocol family 20
Jun 22 15:37:41 Potter64buntu kernel: [   35.665538] PCI-GART: No AMD northbridge found.
Jun 22 15:37:41 Potter64buntu kernel: [  

 35.665542] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 22 15:37:41 Potter64buntu kernel: [   35.665545] hpet0: 3 64-bit timers, 14318180 Hz
Jun 22 15:37:41 

Potter64buntu kernel: [   35.666568] AppArmor: AppArmor Filesystem Enabled
Jun 22 15:37:41 Potter64buntu kernel: [   35.669455] Time: tsc clocksource has been 

installed.
Jun 22 15:37:41 Potter64buntu kernel: [   35.669462] Switched to high resolution mode on CPU 0
Jun 22 15:37:41 Potter64buntu kernel: [   35.670194] 

Switched to high resolution mode on CPU 1
Jun 22 15:37:41 Potter64buntu kernel: [   35.677433] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jun 22 

15:37:41 Potter64buntu kernel: [   35.677435] system 00:01: ioport range 0x290-0x29f has been reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677437] 

system 00:01: ioport range 0x800-0x87f has been reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677439] system 00:01: ioport range 0x290-0x294 has been 

reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677441] system 00:01: ioport range 0x880-0x88f has been reserved
Jun 22 15:37:41 Potter64buntu kernel: [  

 35.677448] system 00:0b: ioport range 0x400-0x4bf could not be reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677453] system 00:0c: iomem range 

0xf0000000-0xf3ffffff could not be reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677457] system 00:0d: iomem range 0xcd200-0xcffff has been reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677459] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
Jun 22 15:37:41 Potter64buntu kernel: [   

35.677461] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677464] system 00:0d: iomem range 

0xfc000-0xfffff could not be reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677466] system 00:0d: iomem range 0x7fee0000-0x7fefffff could not be 

reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677468] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Jun 22 15:37:41 Potter64buntu kernel: 

[   35.677470] system 00:0d: iomem range 0x100000-0x7fedffff could not be reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677472] system 00:0d: iomem 

range 0xfec00000-0xfec00fff has been reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677475] system 00:0d: iomem range 0xfed13000-0xfed1dfff has been 

reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677477] system 00:0d: iomem range 0xfed20000-0xfed8ffff has been reserved
Jun 22 15:37:41 Potter64buntu 

kernel: [   35.677479] system 00:0d: iomem range 0xfee00000-0xfee00fff could not be reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677481] system 

00:0d: iomem range 0xffb00000-0xffb7ffff has been reserved
Jun 22 15:37:41 Potter64buntu kernel: [   35.677744] PCI: Bridge: 0000:00:01.0
Jun 22 15:37:41 

Potter64buntu kernel: [   35.677745]   IO window: b000-bfff
Jun 22 15:37:41 Potter64buntu kernel: [   35.677747]   MEM window: f4000000-f7ffffff
Jun 22 

15:37:41 Potter64buntu kernel: [   35.677749]   PREFETCH window: e0000000-efffffff
Jun 22 15:37:41 Potter64buntu kernel: [   35.677751] PCI: Bridge: 

0000:00:1c.0
Jun 22 15:37:41 Potter64buntu kernel: [   35.677753]   IO window: a000-afff
Jun 22 15:37:41 Potter64buntu kernel: [   35.677755]   MEM window: 

disabled.
Jun 22 15:37:41 Potter64buntu kernel: [   35.677757]   PREFETCH window: disabled.
Jun 22 15:37:41 Potter64buntu kernel: [   35.677760] PCI: Bridge: 

0000:00:1c.3
Jun 22 15:37:41 Potter64buntu kernel: [   35.677761]   IO window: c000-cfff
Jun 22 15:37:41 Potter64buntu kernel: [   35.677764]   MEM window: 

f8000000-f9ffffff
Jun 22 15:37:41 Potter64buntu kernel: [   35.677766]   PREFETCH window: 80000000-800fffff
Jun 22 15:37:41 Potter64buntu kernel: [   

35.677769] PCI: Bridge: 0000:00:1e.0
Jun 22 15:37:41 Potter64buntu kernel: [   35.677771]   IO window: d000-dfff
Jun 22 15:37:41 Potter64buntu kernel: [   

35.677773]   MEM window: fa000000-fa0fffff
Jun 22 15:37:41 Potter64buntu kernel: [   35.677775]   PREFETCH window: disabled.
Jun 22 15:37:41 Potter64buntu 

kernel: [   35.677784] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 22 15:37:41 Potter64buntu kernel: [   35.677787] PCI: Setting 

latency timer of device 0000:00:01.0 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   35.677798] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> 

IRQ 16
Jun 22 15:37:41 Potter64buntu kernel: [   35.677801] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   

35.677812] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:37:41 Potter64buntu kernel: [   35.677815] PCI: Setting latency 

timer of device 0000:00:1c.3 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   35.677821] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jun 22 15:37:41 

Potter64buntu kernel: [   35.677827] NET: Registered protocol family 2
Jun 22 15:37:41 Potter64buntu kernel: [   35.713392] IP route cache hash table entries: 

65536 (order: 7, 524288 bytes)
Jun 22 15:37:41 Potter64buntu kernel: [   35.713812] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Jun 

22 15:37:41 Potter64buntu kernel: [   35.714727] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 22 15:37:41 Potter64buntu kernel: [   

35.714981] TCP: Hash tables configured (established 262144 bind 65536)
Jun 22 15:37:41 Potter64buntu kernel: [   35.714983] TCP reno registered
Jun 22 15:37:41 

Potter64buntu kernel: [   35.725400] checking if image is initramfs... it is
Jun 22 15:37:41 Potter64buntu kernel: [   36.266571] Freeing initrd memory: 8209k 

freed
Jun 22 15:37:41 Potter64buntu kernel: [   36.269058] audit: initializing netlink socket (disabled)
Jun 22 15:37:41 Potter64buntu kernel: [   36.269074] 

audit(1214149033.148:1): initialized
Jun 22 15:37:41 Potter64buntu kernel: [   36.270410] VFS: Disk quotas dquot_6.5.1
Jun 22 15:37:41 Potter64buntu kernel: [  

 36.270452] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 22 15:37:41 Potter64buntu kernel: [   36.270527] io scheduler noop registered
Jun 22 

15:37:41 Potter64buntu kernel: [   36.270529] io scheduler anticipatory registered
Jun 22 15:37:41 Potter64buntu kernel: [   36.270530] io scheduler deadline 

registered
Jun 22 15:37:41 Potter64buntu kernel: [   36.270594] io scheduler cfq registered (default)
Jun 22 15:37:41 Potter64buntu kernel: [   36.273299] Boot 

video device is 0000:01:00.0
Jun 22 15:37:41 Potter64buntu kernel: [   36.273404] PCI: Setting latency timer of device 0000:00:01.0 to 64
Jun 22 15:37:41 

Potter64buntu kernel: [   36.273423] assign_interrupt_mode Found MSI capability
Jun 22 15:37:41 Potter64buntu kernel: [   36.273440] Allocate Port Service

[0000:00:01.0:pcie00]
Jun 22 15:37:41 Potter64buntu kernel: [   36.273486] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Jun 22 15:37:41 

Potter64buntu kernel: [   36.273511] assign_interrupt_mode Found MSI capability
Jun 22 15:37:41 Potter64buntu kernel: [   36.273532] Allocate Port Service

[0000:00:1c.0:pcie00]
Jun 22 15:37:41 Potter64buntu kernel: [   36.273551] Allocate Port Service[0000:00:1c.0:pcie02]
Jun 22 15:37:41 Potter64buntu kernel: [   

36.273602] PCI: Setting latency timer of device 0000:00:1c.3 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   36.273627] assign_interrupt_mode Found MSI 

capability
Jun 22 15:37:41 Potter64buntu kernel: [   36.273648] Allocate Port Service[0000:00:1c.3:pcie00]
Jun 22 15:37:41 Potter64buntu kernel: [   36.273669] 

Allocate Port Service[0000:00:1c.3:pcie02]
Jun 22 15:37:41 Potter64buntu kernel: [   36.289000] Real Time Clock Driver v1.12ac
Jun 22 15:37:41 Potter64buntu 

kernel: [   36.289101] hpet_resources: 0xfed00000 is busy
Jun 22 15:37:41 Potter64buntu kernel: [   36.289122] Linux agpgart interface v0.102
Jun 22 15:37:41 

Potter64buntu kernel: [   36.289124] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 22 15:37:41 Potter64buntu kernel: [   

36.289215] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 22 15:37:41 Potter64buntu kernel: [   36.289544] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 

16550A
Jun 22 15:37:41 Potter64buntu kernel: [   36.290001] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 22 15:37:41 

Potter64buntu kernel: [   36.290039] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 22 15:37:41 Potter64buntu kernel: [   

36.290097] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 22 15:37:41 Potter64buntu kernel: [   36.290381] serio: i8042 KBD port 

at 0x60,0x64 irq 1
Jun 22 15:37:41 Potter64buntu kernel: [   36.290385] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 22 15:37:41 Potter64buntu kernel: [   

36.299977] mice: PS/2 mouse device common for all mice
Jun 22 15:37:41 Potter64buntu kernel: [   36.299999] cpuidle: using governor ladder
Jun 22 15:37:41 

Potter64buntu kernel: [   36.300000] cpuidle: using governor menu
Jun 22 15:37:41 Potter64buntu kernel: [   36.300088] NET: Registered protocol family 1
Jun 22 

15:37:41 Potter64buntu kernel: [   36.300119] registered taskstats version 1
Jun 22 15:37:41 Potter64buntu kernel: [   36.300178]   Magic number: 12:823:639
Jun 22 15:37:41 Potter64buntu kernel: [   36.300203] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jun 22 15:37:41 

Potter64buntu kernel: [   36.300205] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 22 15:37:41 Potter64buntu kernel: [   36.300206] EDD information 

not available.
Jun 22 15:37:41 Potter64buntu kernel: [   36.300210] Freeing unused kernel memory: 316k freed
Jun 22 15:37:41 Potter64buntu kernel: [   

36.329716] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 22 15:37:41 Potter64buntu kernel: [   37.417714] fuse init 

(API version 7.9)
Jun 22 15:37:41 Potter64buntu kernel: [   37.428082] ACPI: Processor [CPU0] (supports 8 throttling states)
Jun 22 15:37:41 Potter64buntu 

kernel: [   37.428161] ACPI: SSDT 7FEE7140, 0087 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
Jun 22 15:37:41 Potter64buntu kernel: [   37.428241] ACPI: 

Processor [CPU1] (supports 8 throttling states)
Jun 22 15:37:41 Potter64buntu kernel: [   37.428249] ACPI Exception (processor_core-0816): AE_NOT_FOUND, 

Processor Device is not present [20070126]
Jun 22 15:37:41 Potter64buntu kernel: [   37.428256] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor 

Device is not present [20070126]
Jun 22 15:37:41 Potter64buntu kernel: [   37.533151] usbcore: registered new interface driver usbfs
Jun 22 15:37:41 

Potter64buntu kernel: [   37.533164] usbcore: registered new interface driver hub
Jun 22 15:37:41 Potter64buntu kernel: [   37.538510] usbcore: registered new 

device driver usb
Jun 22 15:37:41 Potter64buntu kernel: [   37.547683] USB Universal Host Controller Interface driver v3.0
Jun 22 15:37:41 Potter64buntu 

kernel: [   37.547719] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
Jun 22 15:37:41 Potter64buntu kernel: [   37.547727] PCI: Setting 

latency timer of device 0000:00:1d.0 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   37.547729] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 22 15:37:41 

Potter64buntu kernel: [   37.547873] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Jun 22 15:37:41 Potter64buntu kernel: [   37.547894] 

uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
Jun 22 15:37:41 Potter64buntu kernel: [   37.547962] usb usb1: configuration #1 chosen from 1 choice
Jun 22 

15:37:41 Potter64buntu kernel: [   37.547974] hub 1-0:1.0: USB hub found
Jun 22 15:37:41 Potter64buntu kernel: [   37.547977] hub 1-0:1.0: 2 ports detected
Jun 

22 15:37:41 Potter64buntu kernel: [   37.620290] SCSI subsystem initialized
Jun 22 15:37:41 Potter64buntu kernel: [   37.642699] libata version 3.00 loaded.
Jun 22 15:37:41 Potter64buntu kernel: [   37.648234] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:37:41 Potter64buntu 

kernel: [   37.648242] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   37.648244] uhci_hcd 0000:00:1d.1: 

UHCI Host Controller
Jun 22 15:37:41 Potter64buntu kernel: [   37.648257] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Jun 22 15:37:41 

Potter64buntu kernel: [   37.648279] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e000
Jun 22 15:37:41 Potter64buntu kernel: [   37.648340] usb usb2: 

configuration #1 chosen from 1 choice
Jun 22 15:37:41 Potter64buntu kernel: [   37.648354] hub 2-0:1.0: USB hub found
Jun 22 15:37:41 Potter64buntu kernel: [   

37.648357] hub 2-0:1.0: 2 ports detected
Jun 22 15:37:41 Potter64buntu kernel: [   37.751966] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> 

IRQ 18
Jun 22 15:37:41 Potter64buntu kernel: [   37.751974] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   

37.751977] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 22 15:37:41 Potter64buntu kernel: [   37.751992] uhci_hcd 0000:00:1d.2: new USB bus registered, 

assigned bus number 3
Jun 22 15:37:41 Potter64buntu kernel: [   37.752016] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e100
Jun 22 15:37:41 Potter64buntu 

kernel: [   37.752082] usb usb3: configuration #1 chosen from 1 choice
Jun 22 15:37:41 Potter64buntu kernel: [   37.752096] hub 3-0:1.0: USB hub found
Jun 22 

15:37:41 Potter64buntu kernel: [   37.752099] hub 3-0:1.0: 2 ports detected
Jun 22 15:37:41 Potter64buntu kernel: [   37.855686] ACPI: PCI Interrupt 

0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
Jun 22 15:37:41 Potter64buntu kernel: [   37.855693] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   37.855696] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jun 22 15:37:41 Potter64buntu kernel: [   37.855710] uhci_hcd 

0000:00:1d.3: new USB bus registered, assigned bus number 4
Jun 22 15:37:41 Potter64buntu kernel: [   37.855731] uhci_hcd 0000:00:1d.3: irq 16, io base 

0x0000e200
Jun 22 15:37:41 Potter64buntu kernel: [   37.855792] usb usb4: configuration #1 chosen from 1 choice
Jun 22 15:37:41 Potter64buntu kernel: [   

37.855807] hub 4-0:1.0: USB hub found
Jun 22 15:37:41 Potter64buntu kernel: [   37.855810] hub 4-0:1.0: 2 ports detected
Jun 22 15:37:41 Potter64buntu kernel: 

[   37.959479] r8169 Gigabit Ethernet driver 2.2LK loaded
Jun 22 15:37:41 Potter64buntu kernel: [   37.959494] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 

(level, low) -> IRQ 19
Jun 22 15:37:41 Potter64buntu kernel: [   37.959506] PCI: Setting latency timer of device 0000:03:00.0 to 64
Jun 22 15:37:41 

Potter64buntu kernel: [   37.959702] eth0: RTL8168b/8111b at 0xffffc200008ae000, 00:1d:7d:c7:b8:fa, XID 38000000 IRQ 508
Jun 22 15:37:41 Potter64buntu kernel: 

[   37.960848] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
Jun 22 15:37:41 Potter64buntu kernel: [   37.962091] PCI: Setting latency 

timer of device 0000:00:1d.7 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   37.962095] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 22 15:37:41 

Potter64buntu kernel: [   37.962131] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Jun 22 15:37:41 Potter64buntu kernel: [   37.966634] 

PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Jun 22 15:37:41 Potter64buntu kernel: [   37.966638] ehci_hcd 0000:00:1d.7: irq 23, io mem 

0xfa104000
Jun 22 15:37:41 Potter64buntu kernel: [   37.991280] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jun 22 15:37:41 Potter64buntu 

kernel: [   38.003231] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 22 15:37:41 Potter64buntu kernel: [   38.003312] usb usb5: 

configuration #1 chosen from 1 choice
Jun 22 15:37:41 Potter64buntu kernel: [   38.003331] hub 5-0:1.0: USB hub found
Jun 22 15:37:41 Potter64buntu kernel: [   

38.003340] hub 5-0:1.0: 8 ports detected
Jun 22 15:37:41 Potter64buntu kernel: [   38.108519] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> 

IRQ 19
Jun 22 15:37:41 Potter64buntu kernel: [   38.108539] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   

38.108545] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Jun 22 15:37:41 Potter64buntu kernel: [   38.110135] ata_piix 0000:00:1f.2: version 2.12
Jun 22 

15:37:41 Potter64buntu kernel: [   38.110138] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
Jun 22 15:37:41 Potter64buntu kernel: [   38.110147] ACPI: PCI 

Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:37:41 Potter64buntu kernel: [   38.110160] PCI: Setting latency timer of device 

0000:00:1f.2 to 64
Jun 22 15:37:41 Potter64buntu kernel: [   38.110432] scsi0 : ata_piix
Jun 22 15:37:41 Potter64buntu kernel: [   38.110816] scsi1 : ata_piix
Jun 22 15:37:41 Potter64buntu kernel: [   38.111189] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Jun 22 15:37:41 Potter64buntu kernel: [   

38.111191] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Jun 22 15:37:41 Potter64buntu kernel: [   38.514033] ata1.00: HPA unlocked: 

625140335 -> 625142448, native 625142448
Jun 22 15:37:41 Potter64buntu kernel: [   38.514036] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
Jun 22 15:37:41 

Potter64buntu kernel: [   38.514038] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Jun 22 15:37:41 Potter64buntu kernel: [   38.553764] usb 5-

3: new high speed USB device using ehci_hcd and address 2
Jun 22 15:37:41 Potter64buntu kernel: [   38.565897] ata1.00: configured for UDMA/133
Jun 22 15:37:41 

Potter64buntu kernel: [   38.613600] Clocksource tsc unstable (delta = 68989515 ns)
Jun 22 15:37:41 Potter64buntu kernel: [   38.618341] Time: hpet 

clocksource has been installed.
Jun 22 15:37:41 Potter64buntu kernel: [   38.699122] usb 5-3: configuration #1 chosen from 1 choice
Jun 22 15:37:41 

Potter64buntu kernel: [   38.937105] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB05, max UDMA/33
Jun 22 15:37:41 Potter64buntu kernel: [   38.946930] ata2.01: 

HPA unlocked: 321670847 -> 321672960, native 321672960
Jun 22 15:37:41 Potter64buntu kernel: [   38.946932] ata2.01: ATA-7: HDT722516DLAT80, V43OA96A, max 

UDMA/133
Jun 22 15:37:41 Potter64buntu kernel: [   38.946934] ata2.01: 321672960 sectors, multi 16: LBA48 
Jun 22 15:37:41 Potter64buntu kernel: [   39.120874] 

ata2.00: configured for UDMA/33
Jun 22 15:37:41 Potter64buntu kernel: [   39.136995] ata2.01: configured for UDMA/100
Jun 22 15:37:41 Potter64buntu kernel: [   

39.137080] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
Jun 22 15:37:41 Potter64buntu kernel: [   39.137629] scsi 1:0:0:0: CD

-ROM            TSSTcorp CD/DVDW SH-S182M SB05 PQ: 0 ANSI: 5
Jun 22 15:37:41 Potter64buntu kernel: [   39.137703] scsi 1:0:1:0: Direct-Access     ATA      

HDT722516DLAT80  V43O PQ: 0 ANSI: 5
Jun 22 15:37:41 Potter64buntu kernel: [   39.141255] Driver 'sd' needs updating - please use bus_type methods
Jun 22 

15:37:41 Potter64buntu kernel: [   39.141294] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Jun 22 15:37:41 Potter64buntu kernel: [   

39.141301] sd 0:0:0:0: [sda] Write Protect is off
Jun 22 15:37:41 Potter64buntu kernel: [   39.141302] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 22 

15:37:41 Potter64buntu kernel: [   39.141312] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 22 15:37:41 

Potter64buntu kernel: [   39.141339] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Jun 22 15:37:41 Potter64buntu kernel: [   39.141345] sd 

0:0:0:0: [sda] Write Protect is off
Jun 22 15:37:41 Potter64buntu kernel: [   39.141346] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jun 22 15:37:41 

Potter64buntu kernel: [   39.141356] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 22 15:37:41 Potter64buntu 

kernel: [   39.141358]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jun 22 15:37:41 Potter64buntu kernel: [   39.157112] usbcore: 

registered new interface driver libusual
Jun 22 15:37:41 Potter64buntu kernel: [   39.159053] Initializing USB Mass Storage driver...
Jun 22 15:37:41 

Potter64buntu kernel: [   39.159413]  sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
Jun 22 15:37:41 Potter64buntu kernel: [   39.189360] sd 0:0:0:0: [sda] Attached 

SCSI disk
Jun 22 15:37:41 Potter64buntu kernel: [   39.195743] sd 1:0:1:0: [sdb] 321672960 512-byte hardware sectors (164697 MB)
Jun 22 15:37:41 Potter64buntu 

kernel: [   39.195746] sr0: scsi3-mmc drive: 94x/94x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 22 15:37:41 Potter64buntu kernel: [   39.195748] Uniform CD-

ROM driver Revision: 3.20
Jun 22 15:37:41 Potter64buntu kernel: [   39.195758] sd 1:0:1:0: [sdb] Write Protect is off
Jun 22 15:37:41 Potter64buntu kernel: [   

39.195760] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jun 22 15:37:41 Potter64buntu kernel: [   39.195773] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: 

enabled, doesn't support DPO or FUA
Jun 22 15:37:41 Potter64buntu kernel: [   39.195789] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jun 22 15:37:41 Potter64buntu 

kernel: [   39.195809] sd 1:0:1:0: [sdb] 321672960 512-byte hardware sectors (164697 MB)
Jun 22 15:37:41 Potter64buntu kernel: [   39.195817] sd 1:0:1:0: 

[sdb] Write Protect is off
Jun 22 15:37:41 Potter64buntu kernel: [   39.195819] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
Jun 22 15:37:41 Potter64buntu kernel: 

[   39.195832] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 22 15:37:41 Potter64buntu kernel: [   39.195840]  

sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 >
Jun 22 15:37:41 Potter64buntu kernel: [   39.234555] sd 1:0:1:0: [sdb] Attached SCSI disk
Jun 22 15:37:41 Potter64buntu 

kernel: [   39.237015] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 22 15:37:41 Potter64buntu kernel: [   39.237025] sr 1:0:0:0: Attached scsi generic sg1 

type 5
Jun 22 15:37:41 Potter64buntu kernel: [   39.237034] sd 1:0:1:0: Attached scsi generic sg2 type 0
Jun 22 15:37:41 Potter64buntu kernel: [   39.396426] 

usb 2-2: new low speed USB device using uhci_hcd and address 3
Jun 22 15:37:41 Potter64buntu kernel: [   39.552821] Attempting manual resume
Jun 22 15:37:41 

Potter64buntu kernel: [   39.552823] swsusp: Resume From Partition 8:7
Jun 22 15:37:41 Potter64buntu kernel: [   39.552824] PM: Checking swsusp image.
Jun 22 

15:37:41 Potter64buntu kernel: [   39.552957] PM: Resume from disk failed.
Jun 22 15:37:41 Potter64buntu kernel: [   39.559834] EXT3-fs: INFO: recovery 

required on readonly filesystem.
Jun 22 15:37:41 Potter64buntu kernel: [   39.559836] EXT3-fs: write access will be enabled during recovery.
Jun 22 15:37:41 

Potter64buntu kernel: [   39.571127] usb 2-2: configuration #1 chosen from 1 choice
Jun 22 15:37:41 Potter64buntu kernel: [   39.810821] usb 4-2: new full 

speed USB device using uhci_hcd and address 2
Jun 22 15:37:41 Potter64buntu kernel: [   39.986085] usb 4-2: configuration #1 chosen from 1 choice
Jun 22 

15:37:41 Potter64buntu kernel: [   39.989239] scsi2 : SCSI emulation for USB Mass Storage devices
Jun 22 15:37:41 Potter64buntu kernel: [   39.989283] 

usbcore: registered new interface driver usb-storage
Jun 22 15:37:41 Potter64buntu kernel: [   39.989285] USB Mass Storage support registered.
Jun 22 15:37:41 

Potter64buntu kernel: [   39.989365] usbcore: registered new interface driver hiddev
Jun 22 15:37:41 Potter64buntu kernel: [   39.989381] usb-storage: device 

found at 2
Jun 22 15:37:41 Potter64buntu kernel: [   39.989382] usb-storage: waiting for device to settle before scanning
Jun 22 15:37:41 Potter64buntu kernel: 

[   40.003065] input: Formosa21 USB IR Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input2
Jun 22 15:37:41 Potter64buntu kernel: [   

40.026270] input,hidraw0: USB HID v1.10 Keyboard [Formosa21 USB IR Receiver] on usb-0000:00:1d.1-2
Jun 22 15:37:41 Potter64buntu kernel: [   40.026279] 

usbcore: registered new interface driver usbhid
Jun 22 15:37:41 Potter64buntu kernel: [   40.026282] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: 

v2.6:USB HID core driver
Jun 22 15:37:41 Potter64buntu kernel: [   40.238353] kjournald starting.  Commit interval 5 seconds
Jun 22 15:37:41 Potter64buntu 

kernel: [   40.238364] EXT3-fs: sda5: orphan cleanup on readonly fs
Jun 22 15:37:41 Potter64buntu kernel: [   40.238369] ext3_orphan_cleanup: deleting 

unreferenced inode 862181
Jun 22 15:37:41 Potter64buntu kernel: [   40.238394] ext3_orphan_cleanup: deleting unreferenced inode 862180
Jun 22 15:37:41 

Potter64buntu kernel: [   40.238400] ext3_orphan_cleanup: deleting unreferenced inode 589844
Jun 22 15:37:41 Potter64buntu kernel: [   40.238406] 

ext3_orphan_cleanup: deleting unreferenced inode 589831
Jun 22 15:37:41 Potter64buntu kernel: [   40.238415] EXT3-fs: sda5: 4 orphan inodes deleted
Jun 22 

15:37:41 Potter64buntu kernel: [   40.238416] EXT3-fs: recovery complete.
Jun 22 15:37:41 Potter64buntu kernel: [   40.252636] EXT3-fs: mounted filesystem 

with ordered data mode.
Jun 22 15:37:41 Potter64buntu kernel: [   44.973667] usb-storage: device scan complete
Jun 22 15:37:41 Potter64buntu kernel: [   

44.974162] scsi 2:0:0:0: Direct-Access     Kingston DataTravelerMini PMAP PQ: 0 ANSI: 0 CCS
Jun 22 15:37:41 Potter64buntu kernel: [   44.975273] sd 2:0:0:0: 

[sdc] 4030464 512-byte hardware sectors (2064 MB)
Jun 22 15:37:41 Potter64buntu kernel: [   44.975897] sd 2:0:0:0: [sdc] Write Protect is off
Jun 22 15:37:41 

Potter64buntu kernel: [   44.975899] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
Jun 22 15:37:41 Potter64buntu kernel: [   44.975901] sd 2:0:0:0: [sdc] Assuming 

drive cache: write through
Jun 22 15:37:41 Potter64buntu kernel: [   44.978514] sd 2:0:0:0: [sdc] 4030464 512-byte hardware sectors (2064 MB)
Jun 22 15:37:41 

Potter64buntu kernel: [   44.979138] sd 2:0:0:0: [sdc] Write Protect is off
Jun 22 15:37:41 Potter64buntu kernel: [   44.979140] sd 2:0:0:0: [sdc] Mode Sense: 

23 00 00 00
Jun 22 15:37:41 Potter64buntu kernel: [   44.979141] sd 2:0:0:0: [sdc] Assuming drive cache: write through
Jun 22 15:37:41 Potter64buntu kernel: [  

 44.979144]  sdc: sdc1
Jun 22 15:37:41 Potter64buntu kernel: [   44.980674] sd 2:0:0:0: [sdc] Attached SCSI removable disk
Jun 22 15:37:41 Potter64buntu 

kernel: [   44.980697] sd 2:0:0:0: Attached scsi generic sg3 type 0
Jun 22 15:37:41 Potter64buntu kernel: [   47.604230] input: PC Speaker as 

/devices/platform/pcspkr/input/input3
Jun 22 15:37:41 Potter64buntu kernel: [   47.959001] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 22 15:37:41 

Potter64buntu kernel: [   47.992025] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 22 15:37:41 Potter64buntu kernel: [   48.038262] 

iTCO_vendor_support: vendor-support=0
Jun 22 15:37:41 Potter64buntu kernel: [   48.107331] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jun 22 

15:37:41 Potter64buntu kernel: [   48.122791] input: Power Button (FF) as /devices/virtual/input/input4
Jun 22 15:37:41 Potter64buntu kernel: [   48.186016] 

ACPI: Power Button (FF) [PWRF]
Jun 22 15:37:41 Potter64buntu kernel: [   48.186052] input: Power Button (CM) as /devices/virtual/input/input5
Jun 22 15:37:41 

Potter64buntu kernel: [   48.250789] ACPI: Power Button (CM) [PWRB]
Jun 22 15:37:41 Potter64buntu kernel: [   48.310948] b2c2-flexcop: B2C2 FlexcopII/II

(b)/III digital TV receiver chip loaded successfully
Jun 22 15:37:41 Potter64buntu kernel: [   48.329477] flexcop-pci: will use the HW PID filter.
Jun 22 

15:37:41 Potter64buntu kernel: [   48.329481] flexcop-pci: card revision 2
Jun 22 15:37:41 Potter64buntu kernel: [   48.329488] ACPI: PCI Interrupt 

0000:04:01.0[A] -> GSI 19 (level, low) -> IRQ 19
Jun 22 15:37:41 Potter64buntu kernel: [   48.352713] DVB: registering new adapter (FlexCop Digital TV device)
Jun 22 15:37:41 Potter64buntu kernel: [   48.354342] b2c2-flexcop: MAC address = 00:08:c9:a1:0f:18
Jun 22 15:37:41 Potter64buntu kernel: [   48.464408] 

hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
Jun 22 15:37:41 Potter64buntu kernel: [   48.495408] input: ImExPS/2 

Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input6
Jun 22 15:37:41 Potter64buntu kernel: [   48.555689] parport_pc 00:08: reported by Plug 

and Play ACPI
Jun 22 15:37:41 Potter64buntu kernel: [   48.555725] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
Jun 22 15:37:41 

Potter64buntu kernel: [   48.555747] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jun 22 15:37:41 Potter64buntu kernel: [   48.555761] iTCO_wdt: 

initialized. heartbeat=30 sec (nowayout=0)
Jun 22 15:37:41 Potter64buntu kernel: [   48.927709] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:37:41 

Potter64buntu kernel: [   49.061445] intel_rng: FWH not detected
Jun 22 15:37:41 Potter64buntu kernel: [   49.065385] Bluetooth: Core ver 2.11
Jun 22 15:37:41 

Potter64buntu kernel: [   49.065518] NET: Registered protocol family 31
Jun 22 15:37:41 Potter64buntu kernel: [   49.065520] Bluetooth: HCI device and 

connection manager initialized
Jun 22 15:37:41 Potter64buntu kernel: [   49.065522] Bluetooth: HCI socket layer initialized
Jun 22 15:37:41 Potter64buntu 

kernel: [   49.092147] Bluetooth: HCI USB driver ver 2.9
Jun 22 15:37:41 Potter64buntu kernel: [   49.094188] usbcore: registered new interface driver hci_usb
Jun 22 15:37:41 Potter64buntu kernel: [   49.136998] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:37:41 Potter64buntu kernel: [   49.213575] b2c2-flexcop: 

i2c master_xfer failed
Jun 22 15:37:41 Potter64buntu kernel: [   49.213579] mt352_read_register: readreg error (reg=127, ret==-121)
Jun 22 15:37:41 

Potter64buntu kernel: [   49.269581] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:37:41 Potter64buntu kernel: [   49.269585] nxt200x: nxt200x_readbytes: i2c 

read error (addr 0x0a, err == -121)
Jun 22 15:37:41 Potter64buntu kernel: [   49.269586] Unknown/Unsupported NXT chip: 00 00 00 00 00
Jun 22 15:37:41 

Potter64buntu kernel: [   49.292967] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:37:41 Potter64buntu kernel: [   49.292970] lgdt330x: i2c_read_demod_bytes: 

addr 0x59 select 0x02 error (ret == -121)
Jun 22 15:37:41 Potter64buntu kernel: [   49.310334] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:37:41 

Potter64buntu kernel: [   49.329383] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:37:41 Potter64buntu kernel: [   49.329386] stv0297_readreg: readreg error 

(reg == 0x80, ret == -121)
Jun 22 15:37:41 Potter64buntu kernel: [   49.353625] b2c2-flexcop: i2c master_xfer failed
Jun 22 15:37:41 Potter64buntu kernel: [   

49.353628] mt312_read: ret == -121
Jun 22 15:37:41 Potter64buntu kernel: [   49.353639] b2c2-flexcop: no frontend driver found for this B2C2/FlexCop adapter
Jun 22 15:37:41 Potter64buntu kernel: [   49.354993] ACPI: PCI interrupt for device 0000:04:01.0 disabled
Jun 22 15:37:41 Potter64buntu kernel: [   49.355121] 

ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 18 (level, low) -> IRQ 18
Jun 22 15:37:41 Potter64buntu kernel: [   49.355360] ACPI: PCI Interrupt 0000:00:1b.0[A] 

-> GSI 16 (level, low) -> IRQ 16
Jun 22 15:37:41 Potter64buntu kernel: [   49.356594] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Jun 22 15:37:41 

Potter64buntu kernel: [   50.112886] ttySHSF0 at I/O 0xd100 (irq = 18) is a Conexant HSF softmodem (PCI-14f1:2f30-14f1:20d5)
Jun 22 15:37:41 Potter64buntu 

kernel: [   50.458744] lp0: using parport0 (interrupt-driven).
Jun 22 15:37:41 Potter64buntu kernel: [   50.513570] Adding 979924k swap on /dev/sda7.  

Priority:-1 extents:1 across:979924k
Jun 22 15:37:41 Potter64buntu kernel: [   51.035265] EXT3 FS on sda5, internal journal
Jun 22 15:37:41 Potter64buntu 

kernel: [   54.357770] kjournald starting.  Commit interval 5 seconds
Jun 22 15:37:41 Potter64buntu kernel: [   54.357970] EXT3 FS on sda6, internal journal
Jun 22 15:37:41 Potter64buntu kernel: [   54.357973] EXT3-fs: mounted filesystem with ordered data mode.
Jun 22 15:37:41 Potter64buntu kernel: [   54.382579] 

kjournald starting.  Commit interval 5 seconds
Jun 22 15:37:41 Potter64buntu kernel: [   54.382814] EXT3 FS on sda8, internal journal
Jun 22 15:37:41 

Potter64buntu kernel: [   54.382817] EXT3-fs: mounted filesystem with ordered data mode.
Jun 22 15:37:41 Potter64buntu kernel: [   54.570986] ip_tables: (C) 

2000-2006 Netfilter Core Team
Jun 22 15:37:41 Potter64buntu kernel: [   63.404601] No dock devices found.
Jun 22 15:37:41 Potter64buntu NetworkManager: <info>  

starting... 
Jun 22 15:37:41 Potter64buntu avahi-daemon[8618]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Jun 22 15:37:41 Potter64buntu avahi-

daemon[8618]: Successfully dropped root privileges.
Jun 22 15:37:41 Potter64buntu avahi-daemon[8618]: avahi-daemon 0.6.22 starting up.
Jun 22 15:37:41 

Potter64buntu avahi-daemon[8618]: Successfully called chroot().
Jun 22 15:37:41 Potter64buntu avahi-daemon[8618]: Successfully dropped remaining capabilities.
Jun 22 15:37:41 Potter64buntu avahi-daemon[8618]: No service file found in /etc/avahi/services.
Jun 22 15:37:41 Potter64buntu avahi-daemon[8618]: Network 

interface enumeration completed.
Jun 22 15:37:41 Potter64buntu avahi-daemon[8618]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 22 15:37:41 

Potter64buntu avahi-daemon[8618]: Server startup complete. Host name is Potter64buntu.local. Local service cookie is 3843590225.
Jun 22 15:37:41 Potter64buntu 

kernel: [   64.027890] ppdev: user-space parallel port driver
Jun 22 15:37:41 Potter64buntu kernel: [   64.121047] audit(1214132861.739:2): type=1503 

operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8651 profile="/usr/sbin/cupsd" namespace="default"
Jun 22 15:37:41 

Potter64buntu dhcdbd: Started up.
Jun 22 15:37:44 Potter64buntu kernel: [   67.019967] r8169: eth0: link down
Jun 22 15:37:44 Potter64buntu NetworkManager: 

<info>  eth0: Device is fully-supported using driver 'r8169'. 
Jun 22 15:37:44 Potter64buntu NetworkManager: <info>  nm_device_init(): waiting for device's 

worker thread to start 
Jun 22 15:37:44 Potter64buntu NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Jun 22 15:37:44 

Potter64buntu NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Jun 22 15:37:44 Potter64buntu NetworkManager: <info>  Deactivating 

device eth0. 
Jun 22 15:37:44 Potter64buntu NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Jun 22 15:37:44 

Potter64buntu hcid[8884]: Bluetooth HCI daemon
Jun 22 15:37:44 Potter64buntu hcid[8884]: HCI dev 0 registered
Jun 22 15:37:44 Potter64buntu hcid[8884]: 

Starting SDP server
Jun 22 15:37:44 Potter64buntu kernel: [   67.075457] Bluetooth: L2CAP ver 2.9
Jun 22 15:37:44 Potter64buntu hcid[8884]: Created local 

server at unix:abstract=/var/run/dbus-7Z9m5ccl1K,guid=ade6caa18404a00a92fc1377485e3280
Jun 22 15:37:44 Potter64buntu kernel: [   67.075460] Bluetooth: L2CAP 

socket layer initialized
Jun 22 15:37:44 Potter64buntu audio[8903]: Bluetooth Audio daemon
Jun 22 15:37:44 Potter64buntu audio[8903]: Unix socket created: 5
Jun 

22 15:37:44 Potter64buntu audio[8903]: audio.conf: Key file does not have key 'Enable'
Jun 22 15:37:44 Potter64buntu audio[8903]: audio.conf: Key file does 

not have key 'Disable'
Jun 22 15:37:44 Potter64buntu hcid[8884]: HCI dev 0 up
Jun 22 15:37:44 Potter64buntu hcid[8884]: Device hci0 has been added
Jun 22 

15:37:44 Potter64buntu hcid[8884]: Starting security manager 0
Jun 22 15:37:44 Potter64buntu kernel: [   67.129100] Bluetooth: RFCOMM socket layer initialized
Jun 22 15:37:44 Potter64buntu kernel: [   67.129109] Bluetooth: RFCOMM TTY layer initialized
Jun 22 15:37:44 Potter64buntu kernel: [   67.129111] Bluetooth: 

RFCOMM ver 1.8
Jun 22 15:37:44 Potter64buntu input[8904]: Bluetooth Input daemon
Jun 22 15:37:44 Potter64buntu input[8904]: Registered input manager 

path:/org/bluez/input
Jun 22 15:37:44 Potter64buntu hcid[8884]: Device hci0 has been activated
Jun 22 15:37:44 Potter64buntu audio[8903]: add_service_record: 

got record id 0x10000
Jun 22 15:37:44 Potter64buntu audio[8903]: audio.conf: Key file does not have key 'Disable'
Jun 22 15:37:44 Potter64buntu audio[8903]: 

audio.conf: Key file does not have group 'A2DP'
Jun 22 15:37:44 Potter64buntu last message repeated 3 times
Jun 22 15:37:44 Potter64buntu audio[8903]: SEP 

0x62d3b0 registered: type:0 codec:0 seid:1
Jun 22 15:37:44 Potter64buntu audio[8903]: add_service_record: got record id 0x10001
Jun 22 15:37:44 Potter64buntu 

audio[8903]: add_service_record: got record id 0x10002
Jun 22 15:37:44 Potter64buntu audio[8903]: add_service_record: got record id 0x10003
Jun 22 15:37:44 

Potter64buntu audio[8903]: Registered manager path:/org/bluez/audio
Jun 22 15:37:46 Potter64buntu anacron[8984]: Anacron 2.3 started on 2008-06-22
Jun 22 

15:37:46 Potter64buntu anacron[8984]: Will run job `cron.weekly' in 10 min.
Jun 22 15:37:46 Potter64buntu anacron[8984]: Jobs will be executed sequentially
Jun 

22 15:37:46 Potter64buntu /usr/sbin/cron[9013]: (CRON) INFO (pidfile fd = 3)
Jun 22 15:37:46 Potter64buntu /usr/sbin/cron[9014]: (CRON) STARTUP (fork ok)
Jun 

22 15:37:46 Potter64buntu /usr/sbin/cron[9014]: (CRON) INFO (Running @reboot jobs)
Jun 22 15:38:03 Potter64buntu kernel: [   86.051422] NET: Registered 

protocol family 10
Jun 22 15:38:03 Potter64buntu kernel: [   86.051598] lo: Disabled Privacy Extensions
Jun 22 15:38:03 Potter64buntu kernel: [   86.051858] 

ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 22 15:38:05 Potter64buntu hcid[8884]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Jun 22 

15:38:05 Potter64buntu hcid[8884]: Default authorization agent (:1.20, /org/bluez/auth) registered
Jun 22 15:38:07 Potter64buntu NetworkManager: <info>  

Updating allowed wireless network lists. 
Jun 22 15:38:07 Potter64buntu NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: 

org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Jun 22 15:38:08 Potter64buntu kernel: [   90.948865] cdrom: sr0: mrw 

address space DMA selected
Jun 22 15:38:08 Potter64buntu hald: mounted /dev/sdc1 on behalf of uid 1000
Jun 22 15:38:08 Potter64buntu kernel: [   91.115933] 

cdrom: sr0: mrw address space DMA selected
Jun 22 15:38:08 Potter64buntu kernel: [   91.187602] UDF-fs: No VRS found
Jun 22 15:38:08 Potter64buntu kernel: [   

91.237777] ISO 9660 Extensions: Microsoft Joliet Level 3
Jun 22 15:38:08 Potter64buntu kernel: [   91.238462] ISOFS: changing to secondary root
Jun 22 15:39:23 

Potter64buntu kernel: [  165.809861] PPP generic driver version 2.4.2
Jun 22 15:39:23 Potter64buntu pppd[9417]: pppd 2.4.4 started by potter, uid 1000
Jun 22 

15:39:23 Potter64buntu pppd[9417]: Using interface ppp0
Jun 22 15:39:23 Potter64buntu pppd[9417]: Connect: ppp0 <--> /dev/ttySHSF0
Jun 22 15:39:25 

Potter64buntu pppd[9417]: PAP authentication succeeded
Jun 22 15:39:25 Potter64buntu kernel: [  167.831031] PPP BSD Compression module registered
Jun 22 

15:39:25 Potter64buntu kernel: [  167.873800] PPP Deflate Compression module registered
Jun 22 15:39:26 Potter64buntu pppd[9417]: Cannot determine ethernet 

address for proxy ARP
Jun 22 15:39:26 Potter64buntu pppd[9417]: local  IP address 84.241.17.169
Jun 22 15:39:26 Potter64buntu pppd[9417]: remote IP address 

85.15.0.134
Jun 22 15:39:26 Potter64buntu pppd[9417]: primary   DNS address 85.15.1.12
Jun 22 15:39:26 Potter64buntu pppd[9417]: secondary DNS address 

85.15.1.10
Jun 22 15:39:26 Potter64buntu pppd[9417]: CCP terminated by peer
Jun 22 15:39:26 Potter64buntu pppd[9417]: Compression disabled by peer.


```
the red part says :
Jun 22 15:36:10 Potter64buntu kernel: [ 1008.321540] general protection fault: 0000 [1] SMP

---

### Post by Arenlor on 2008-06-21
It would seem you aren't actually using the Dell driver, PPP generic driver version 2.4.2 gets loaded.
Also, for some reason compression gets disabled, do you know if that's your ISP doing it, if so why?

---

### Post by medya on 2008-06-22
I am connecting using Gnome-ppp and without the Dell Driver, it wouldnt even Recoginze my modem , so I am certain that it is using the driver.

and I dont know if my isp is disabling compression .

---

### Post by Arenlor on 2008-06-22
That may be what it is, it may expect compression.

---

### Post by medya on 2008-06-23
how about that Error in the syslog ? 
**general protection fault: 0000 [1] SMP**
I searched in forums, much guys who also have 64 bit cpu, get that error, some say you have to recomplie your kernel ,
how can I do that , [without downloading anything big] ?

---

### Post by medya on 2008-07-01
:( what can I do ?

---

