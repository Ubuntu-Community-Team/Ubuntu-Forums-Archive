---
title: "CMOS Date/Time Not Set"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by s.fox on 2008-08-11
Hi everyone,

For the last 3 or 4 days every time i boot up my PC i keep getting the message "CMOS Date/Time Not Set".  I have been into the BIOS and reset the date/time.  I have saved my changes.  The system then boots up like normal.
I then have finished with the PC and turn it off.  Next day when i boot up it says "CMOS Date/Time Not Set".  I feel like i am going in circles. 

Can somebody please help me?  If any more information is needed please let me know.

Thank you for any help.

---

### Post by ajgreeny on 2008-08-11
I imagine the little cmos battery on the motherboard has run out of power and needs replacing.  Have a look at your system documentation to see what you need, or take the machine to a friendly computer shop, who will probably change it for you for a small cost.

---

### Post by bobnutfield on 2008-08-11
This most likely correct, and if your motherboard is like about 75% of those in use it is a 2032 Lithium battery.  Very easy to replace yourself, but usually there is two of them stacked on top of each other.  On most motherboards, they are very accessible on the top of the motherboard.

---

### Post by s.fox on 2008-10-14
Right,  sorry for replying to this thread a little late but I am still having the same troubles.

I have replaced the battery on the motherboard but nothing appears to have changed.  The system is still forgetting the date and time.

I have noticed some error messages when I boot up and shut down.  Its going far to fast for me to read but I believe they are error messages because they weren't always there.   Also i catch a brief glance at the word "Unexpected" before it swiftly boots up/ shuts down.

I think this error is related to my woes but I can't actually read it.  Are these kind of errors stored in a log or similar?  Can I run some kind of system diagnostic and fix whatever is causing this problem?

Any advice would be most welcomed.

-Ash R

---

### Post by bobnutfield on 2008-10-14
You can try:

> cat /var/log/messages

and

> dmesg

These are going to be very long listings and will take a while to go through.  But this is where you are most likely to find the error messages you are getting.

---

### Post by SuperSonic4 on 2008-10-14
Sometimes you have to completely clear the CMOS before replacing the battery (ie remove old battery and put the jumper cap on the other pins). Leave for a minute, move the jumper cap back and put the new battery in.

---

### Post by s.fox on 2008-10-14
dmesg gave me lots of lines that all looked pretty much like this

```
[ 1729.854188] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: unexpected response fd

```

cat /var/log/messages  gave me quite a bit of output,  but unfortunately it doesn't make much sense to me :(
```
cat /var/log/messages 
Oct 14 16:28:03 ashley-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct 14 16:33:21 ashley-desktop kernel: [ 1902.763851] usb 5-3.2.2: reset high speed USB device using ehci_hcd and address 7
Oct 14 17:02:28 ashley-desktop -- MARK --
Oct 14 17:03:33 ashley-desktop kernel: [ 3709.253231] ip6_tables: (C) 2000-2006 Netfilter Core Team
Oct 14 17:03:35 ashley-desktop exiting on signal 15
Oct 14 17:04:38 ashley-desktop syslogd 1.5.0#1ubuntu1: restart.
Oct 14 17:04:38 ashley-desktop kernel: Inspecting /boot/System.map-2.6.24-21-generic
Oct 14 17:04:38 ashley-desktop kernel: Loaded 27890 symbols from /boot/System.map-2.6.24-21-generic.
Oct 14 17:04:38 ashley-desktop kernel: Symbols match kernel version 2.6.24.
Oct 14 17:04:38 ashley-desktop kernel: Loaded 18093 symbols from 97 modules.
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Linux version 2.6.24-21-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Aug 25 17:32:09 UTC 2008 (Ubuntu 2.6.24-21.42-generic)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffb0000 (usable)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]  BIOS-e820: 000000001ffb0000 - 000000001ffc0000 (ACPI data)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]  BIOS-e820: 000000001ffc0000 - 000000001fff0000 (ACPI NVS)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]  BIOS-e820: 000000001fff0000 - 0000000020000000 (reserved)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffba0000 - 0000000100000000 (reserved)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] 0MB HIGHMEM available.
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] 511MB LOWMEM available.
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] found SMP MP-table at 000ff780
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Zone PFN ranges:
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]   DMA             0 ->     4096
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]   Normal       4096 ->   130992
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]   HighMem    130992 ->   130992
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Movable zone start PFN for each node
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] early_node_map[1] active PFN ranges
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000]     0:        0 ->   130992
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] DMI 2.3 present.
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FAD90 checksum 0
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: RSDP 000FAD90, 0014 (r0 ACPIAM)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: RSDT 1FFB0000, 0030 (r1 A M I  OEMRSDT   6000524 MSFT       97)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: FACP 1FFB0200, 0081 (r2 A M I  OEMFACP   6000524 MSFT       97)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: DSDT 1FFB03F0, 36BD (r1  AH002 AH002001        1 INTL  2002026)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: FACS 1FFC0000, 0040
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: APIC 1FFB0390, 005C (r1 A M I  OEMAPIC   6000524 MSFT       97)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: OEMB 1FFC0040, 003F (r1 A M I  OEMBIOS   6000524 MSFT       97)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Processor #0 15:2 APIC version 20
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Processor #1 15:2 APIC version 20
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfba0000)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e8000
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e8000 - 0000000000100000
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129969
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Kernel command line: root=UUID=fe21436d-be08-401e-86a4-79ab629a4a04 ro quiet splash
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Initializing CPU#0
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Oct 14 17:04:38 ashley-desktop kernel: [    0.000000] Detected 3200.092 MHz processor.
Oct 14 17:04:38 ashley-desktop kernel: [   26.178271] Console: colour VGA+ 80x25
Oct 14 17:04:38 ashley-desktop kernel: [   26.178275] console [tty0] enabled
Oct 14 17:04:38 ashley-desktop kernel: [   26.178629] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Oct 14 17:04:38 ashley-desktop kernel: [   26.178930] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189000] Memory: 507396k/523968k available (2177k kernel code, 15988k reserved, 1006k data, 368k init, 0k highmem)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189008] virtual kernel memory layout:
Oct 14 17:04:38 ashley-desktop kernel: [   26.189009]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189010]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189011]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189012]     lowmem  : 0xc0000000 - 0xdffb0000   ( 511 MB)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189013]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189014]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189015]       .text : 0xc0100000 - 0xc0320514   (2177 kB)
Oct 14 17:04:38 ashley-desktop kernel: [   26.189018] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Oct 14 17:04:38 ashley-desktop kernel: [   26.189055] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Oct 14 17:04:38 ashley-desktop kernel: [   26.268830] Calibrating delay using timer specific routine.. 6405.18 BogoMIPS (lpj=12810362)
Oct 14 17:04:38 ashley-desktop kernel: [   26.268855] Security Framework initialized
Oct 14 17:04:38 ashley-desktop kernel: [   26.268862] SELinux:  Disabled at boot.
Oct 14 17:04:38 ashley-desktop kernel: [   26.268876] AppArmor: AppArmor initialized
Oct 14 17:04:38 ashley-desktop kernel: [   26.268880] Failure registering capabilities with primary security module.
Oct 14 17:04:38 ashley-desktop kernel: [   26.268889] Mount-cache hash table entries: 512
Oct 14 17:04:38 ashley-desktop kernel: [   26.269019] Initializing cgroup subsys ns
Oct 14 17:04:38 ashley-desktop kernel: [   26.269023] Initializing cgroup subsys cpuacct
Oct 14 17:04:38 ashley-desktop kernel: [   26.269047] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 14 17:04:38 ashley-desktop kernel: [   26.269050] CPU: L2 cache: 512K
Oct 14 17:04:38 ashley-desktop kernel: [   26.269052] CPU: Physical Processor ID: 0
Oct 14 17:04:38 ashley-desktop kernel: [   26.269066] Compat vDSO mapped to ffffe000.
Oct 14 17:04:38 ashley-desktop kernel: [   26.269079] Checking 'hlt' instruction... OK.
Oct 14 17:04:38 ashley-desktop kernel: [   26.285155] SMP alternatives: switching to UP code
Oct 14 17:04:38 ashley-desktop kernel: [   26.286745] Early unpacking initramfs... done
Oct 14 17:04:38 ashley-desktop kernel: [   26.551901] ACPI: Core revision 20070126
Oct 14 17:04:38 ashley-desktop kernel: [   26.551969] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 14 17:04:38 ashley-desktop kernel: [   26.553435] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 09
Oct 14 17:04:38 ashley-desktop kernel: [   26.553455] SMP alternatives: switching to SMP code
Oct 14 17:04:38 ashley-desktop kernel: [   26.554172] Booting processor 1/1 eip 3000
Oct 14 17:04:38 ashley-desktop kernel: [   26.564366] Initializing CPU#1
Oct 14 17:04:38 ashley-desktop kernel: [   26.643674] Calibrating delay using timer specific routine.. 6400.42 BogoMIPS (lpj=12800844)
Oct 14 17:04:38 ashley-desktop kernel: [   26.643694] CPU: Trace cache: 12K uops, L1 D cache: 8K
Oct 14 17:04:38 ashley-desktop kernel: [   26.643696] CPU: L2 cache: 512K
Oct 14 17:04:38 ashley-desktop kernel: [   26.643698] CPU: Physical Processor ID: 0
Oct 14 17:04:38 ashley-desktop kernel: [   26.643960] CPU1: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 09
Oct 14 17:04:38 ashley-desktop kernel: [   26.644000] Total of 2 processors activated (12805.60 BogoMIPS).
Oct 14 17:04:38 ashley-desktop kernel: [   26.644130] ENABLING IO-APIC IRQs
Oct 14 17:04:38 ashley-desktop kernel: [   26.644305] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 14 17:04:38 ashley-desktop kernel: [   26.791386] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Oct 14 17:04:38 ashley-desktop kernel: [   26.811342] Brought up 2 CPUs
Oct 14 17:04:38 ashley-desktop kernel: [   26.811703] net_namespace: 64 bytes
Oct 14 17:04:38 ashley-desktop kernel: [   26.811714] Booting paravirtualized kernel on bare hardware
Oct 14 17:04:38 ashley-desktop kernel: [   26.812220] Time: 16:04:10  Date: 10/14/08
Oct 14 17:04:38 ashley-desktop kernel: [   26.812258] NET: Registered protocol family 16
Oct 14 17:04:38 ashley-desktop kernel: [   26.812529] EISA bus registered
Oct 14 17:04:38 ashley-desktop kernel: [   26.812535] ACPI: bus type pci registered
Oct 14 17:04:38 ashley-desktop kernel: [   26.812726] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
Oct 14 17:04:38 ashley-desktop kernel: [   26.812728] PCI: Using configuration type 1
Oct 14 17:04:38 ashley-desktop kernel: [   26.812742] Setting up standard PCI resources
Oct 14 17:04:38 ashley-desktop kernel: [   26.830795] ACPI: Interpreter enabled
Oct 14 17:04:38 ashley-desktop kernel: [   26.830799] ACPI: (supports S0 S1 S3 S4 S5)
Oct 14 17:04:38 ashley-desktop kernel: [   26.830815] ACPI: Using IOAPIC for interrupt routing
Oct 14 17:04:38 ashley-desktop kernel: [   26.836230] ACPI: PCI Root Bridge [PCI0] (0000:00)
Oct 14 17:04:38 ashley-desktop kernel: [   26.836709] PCI: Enabled i801 SMBus device
Oct 14 17:04:38 ashley-desktop kernel: [   26.836715] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Oct 14 17:04:38 ashley-desktop kernel: [   26.836719] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
Oct 14 17:04:38 ashley-desktop kernel: [   26.837154] PCI: Transparent bridge - 0000:00:1e.0
Oct 14 17:04:38 ashley-desktop kernel: [   26.842343] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Oct 14 17:04:38 ashley-desktop kernel: [   26.842429] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Oct 14 17:04:38 ashley-desktop kernel: [   26.842513] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Oct 14 17:04:38 ashley-desktop kernel: [   26.842596] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Oct 14 17:04:38 ashley-desktop kernel: [   26.842678] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct 14 17:04:38 ashley-desktop kernel: [   26.842762] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Oct 14 17:04:38 ashley-desktop kernel: [   26.842847] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 14 17:04:38 ashley-desktop kernel: [   26.842930] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Oct 14 17:04:38 ashley-desktop kernel: [   26.843075] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  2C, should be 23 [20070126]
Oct 14 17:04:38 ashley-desktop kernel: [   26.843084] Linux Plug and Play Support v0.97 (c) Adam Belay
Oct 14 17:04:38 ashley-desktop kernel: [   26.843126] pnp: PnP ACPI init
Oct 14 17:04:38 ashley-desktop kernel: [   26.843135] ACPI: bus type pnp registered
Oct 14 17:04:38 ashley-desktop kernel: [   26.845952] pnp: PnP ACPI: found 12 devices
Oct 14 17:04:38 ashley-desktop kernel: [   26.845956] ACPI: ACPI bus type pnp unregistered
Oct 14 17:04:38 ashley-desktop kernel: [   26.845961] PnPBIOS: Disabled by ACPI PNP
Oct 14 17:04:38 ashley-desktop kernel: [   26.846303] PCI: Using ACPI for IRQ routing
Oct 14 17:04:38 ashley-desktop kernel: [   26.846307] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Oct 14 17:04:38 ashley-desktop kernel: [   26.871001] NET: Registered protocol family 8
Oct 14 17:04:38 ashley-desktop kernel: [   26.871004] NET: Registered protocol family 20
Oct 14 17:04:38 ashley-desktop kernel: [   26.871132] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Oct 14 17:04:38 ashley-desktop kernel: [   26.871137] hpet0: 3 64-bit timers, 14318180 Hz
Oct 14 17:04:38 ashley-desktop kernel: [   26.872183] AppArmor: AppArmor Filesystem Enabled
Oct 14 17:04:38 ashley-desktop kernel: [   26.874978] Time: tsc clocksource has been installed.
Oct 14 17:04:38 ashley-desktop kernel: [   26.890984] system 00:06: ioport range 0x680-0x6ff has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.890987] system 00:06: ioport range 0x290-0x297 has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.890995] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.890998] system 00:07: ioport range 0x800-0x87f has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891000] system 00:07: ioport range 0x400-0x41f has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891002] system 00:07: ioport range 0x480-0x4bf has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891006] system 00:07: iomem range 0xfed20000-0xfed8ffff has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891009] system 00:07: iomem range 0xffb00000-0xffbfffff could not be reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891016] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891018] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891028] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891030] system 00:0b: iomem range 0xc0000-0xdffff could not be reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891033] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891035] system 00:0b: iomem range 0x100000-0x1ffeffff could not be reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.891038] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
Oct 14 17:04:38 ashley-desktop kernel: [   26.921490] PCI: Bridge: 0000:00:01.0
Oct 14 17:04:38 ashley-desktop kernel: [   26.921494]   IO window: c000-cfff
Oct 14 17:04:38 ashley-desktop kernel: [   26.921499]   MEM window: ff800000-ff8fffff
Oct 14 17:04:38 ashley-desktop kernel: [   26.921502]   PREFETCH window: d7f00000-f7efffff
Oct 14 17:04:38 ashley-desktop kernel: [   26.921507] PCI: Bridge: 0000:00:1e.0
Oct 14 17:04:38 ashley-desktop kernel: [   26.921509]   IO window: d000-dfff
Oct 14 17:04:38 ashley-desktop kernel: [   26.921514]   MEM window: ff900000-ff9fffff
Oct 14 17:04:38 ashley-desktop kernel: [   26.921518]   PREFETCH window: disabled.
Oct 14 17:04:38 ashley-desktop kernel: [   26.921548] NET: Registered protocol family 2
Oct 14 17:04:38 ashley-desktop kernel: [   26.962799] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Oct 14 17:04:38 ashley-desktop kernel: [   26.963045] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Oct 14 17:04:38 ashley-desktop kernel: [   26.963139] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Oct 14 17:04:38 ashley-desktop kernel: [   26.963236] TCP: Hash tables configured (established 16384 bind 16384)
Oct 14 17:04:38 ashley-desktop kernel: [   26.963239] TCP reno registered
Oct 14 17:04:38 ashley-desktop kernel: [   26.974837] checking if image is initramfs... it is
Oct 14 17:04:38 ashley-desktop kernel: [   27.500826] Freeing initrd memory: 7314k freed
Oct 14 17:04:38 ashley-desktop kernel: [   27.501602] audit: initializing netlink socket (disabled)
Oct 14 17:04:38 ashley-desktop kernel: [   27.501622] audit(1224000251.196:1): initialized
Oct 14 17:04:38 ashley-desktop kernel: [   27.504218] VFS: Disk quotas dquot_6.5.1
Oct 14 17:04:38 ashley-desktop kernel: [   27.504322] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Oct 14 17:04:38 ashley-desktop kernel: [   27.504492] io scheduler noop registered
Oct 14 17:04:38 ashley-desktop kernel: [   27.504494] io scheduler anticipatory registered
Oct 14 17:04:38 ashley-desktop kernel: [   27.504496] io scheduler deadline registered
Oct 14 17:04:38 ashley-desktop kernel: [   27.504508] io scheduler cfq registered (default)
Oct 14 17:04:38 ashley-desktop kernel: [   27.504962] isapnp: Scanning for PnP cards...
Oct 14 17:04:38 ashley-desktop kernel: [   27.857712] isapnp: No Plug & Play device found
Oct 14 17:04:38 ashley-desktop kernel: [   27.894035] Real Time Clock Driver v1.12ac
Oct 14 17:04:38 ashley-desktop kernel: [   27.894161] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Oct 14 17:04:38 ashley-desktop kernel: [   27.894292] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 14 17:04:38 ashley-desktop kernel: [   27.895190] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Oct 14 17:04:38 ashley-desktop kernel: [   27.896183] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Oct 14 17:04:38 ashley-desktop kernel: [   27.896265] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Oct 14 17:04:38 ashley-desktop kernel: [   27.896393] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Oct 14 17:04:38 ashley-desktop kernel: [   27.896396] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Oct 14 17:04:38 ashley-desktop kernel: [   27.896778] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct 14 17:04:38 ashley-desktop kernel: [   27.915805] mice: PS/2 mouse device common for all mice
Oct 14 17:04:38 ashley-desktop kernel: [   27.915966] EISA: Probing bus 0 at eisa.0
Oct 14 17:04:38 ashley-desktop kernel: [   27.916003] EISA: Detected 0 cards.
Oct 14 17:04:38 ashley-desktop kernel: [   27.916008] cpuidle: using governor ladder
Oct 14 17:04:38 ashley-desktop kernel: [   27.916009] cpuidle: using governor menu
Oct 14 17:04:38 ashley-desktop kernel: [   27.916117] NET: Registered protocol family 1
Oct 14 17:04:38 ashley-desktop kernel: [   27.916152] Using IPI No-Shortcut mode
Oct 14 17:04:38 ashley-desktop kernel: [   27.916193] registered taskstats version 1
Oct 14 17:04:38 ashley-desktop kernel: [   27.916295]   Magic number: 12:286:85
Oct 14 17:04:38 ashley-desktop kernel: [   27.916430] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Oct 14 17:04:38 ashley-desktop kernel: [   27.916431] EDD information not available.
Oct 14 17:04:38 ashley-desktop kernel: [   27.916901] Freeing unused kernel memory: 368k freed
Oct 14 17:04:38 ashley-desktop kernel: [   27.951620] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Oct 14 17:04:38 ashley-desktop kernel: [   29.162653] fuse init (API version 7.9)
Oct 14 17:04:38 ashley-desktop kernel: [   29.370060] usbcore: registered new interface driver usbfs
Oct 14 17:04:38 ashley-desktop kernel: [   29.370097] usbcore: registered new interface driver hub
Oct 14 17:04:38 ashley-desktop kernel: [   29.375203] usbcore: registered new device driver usb
Oct 14 17:04:38 ashley-desktop kernel: [   29.399094] USB Universal Host Controller Interface driver v3.0
Oct 14 17:04:38 ashley-desktop kernel: [   29.399245] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 14 17:04:38 ashley-desktop kernel: [   29.399272] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Oct 14 17:04:38 ashley-desktop kernel: [   29.399694] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Oct 14 17:04:38 ashley-desktop kernel: [   29.399729] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eec0
Oct 14 17:04:38 ashley-desktop kernel: [   29.399935] usb usb1: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   29.399976] hub 1-0:1.0: USB hub found
Oct 14 17:04:38 ashley-desktop kernel: [   29.399986] hub 1-0:1.0: 2 ports detected
Oct 14 17:04:38 ashley-desktop kernel: [   29.439805] SCSI subsystem initialized
Oct 14 17:04:38 ashley-desktop kernel: [   29.506823] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Oct 14 17:04:38 ashley-desktop kernel: [   29.506846] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Oct 14 17:04:38 ashley-desktop kernel: [   29.506882] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Oct 14 17:04:38 ashley-desktop kernel: [   29.506914] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ef00
Oct 14 17:04:38 ashley-desktop kernel: [   29.507094] usb usb2: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   29.507130] hub 2-0:1.0: USB hub found
Oct 14 17:04:38 ashley-desktop kernel: [   29.507140] hub 2-0:1.0: 2 ports detected
Oct 14 17:04:38 ashley-desktop kernel: [   29.610514] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Oct 14 17:04:38 ashley-desktop kernel: [   29.610537] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Oct 14 17:04:38 ashley-desktop kernel: [   29.610571] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Oct 14 17:04:38 ashley-desktop kernel: [   29.610601] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ef20
Oct 14 17:04:38 ashley-desktop kernel: [   29.610770] usb usb3: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   29.610806] hub 3-0:1.0: USB hub found
Oct 14 17:04:38 ashley-desktop kernel: [   29.610815] hub 3-0:1.0: 2 ports detected
Oct 14 17:04:38 ashley-desktop kernel: [   29.714157] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
Oct 14 17:04:38 ashley-desktop kernel: [   29.714181] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Oct 14 17:04:38 ashley-desktop kernel: [   29.714217] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Oct 14 17:04:38 ashley-desktop kernel: [   29.714244] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ef40
Oct 14 17:04:38 ashley-desktop kernel: [   29.714416] usb usb4: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   29.714452] hub 4-0:1.0: USB hub found
Oct 14 17:04:38 ashley-desktop kernel: [   29.714461] hub 4-0:1.0: 2 ports detected
Oct 14 17:04:38 ashley-desktop kernel: [   29.746105] usb 1-1: new full speed USB device using uhci_hcd and address 2
Oct 14 17:04:38 ashley-desktop kernel: [   29.792761] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Oct 14 17:04:38 ashley-desktop kernel: [   29.817896] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Oct 14 17:04:38 ashley-desktop kernel: [   29.817925] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Oct 14 17:04:38 ashley-desktop kernel: [   29.817965] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Oct 14 17:04:38 ashley-desktop kernel: [   29.821874] ehci_hcd 0000:00:1d.7: debug port 1
Oct 14 17:04:38 ashley-desktop kernel: [   29.821897] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffaffc00
Oct 14 17:04:38 ashley-desktop kernel: [   29.828177] Floppy drive(s): fd0 is 1.44M
Oct 14 17:04:38 ashley-desktop kernel: [   29.866252] FDC 0 is a post-1991 82077
Oct 14 17:04:38 ashley-desktop kernel: [   29.893512] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Oct 14 17:04:38 ashley-desktop kernel: [   29.893720] usb usb5: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   29.893757] hub 5-0:1.0: USB hub found
Oct 14 17:04:38 ashley-desktop kernel: [   29.893768] hub 5-0:1.0: 8 ports detected
Oct 14 17:04:38 ashley-desktop kernel: [   29.997395] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Oct 14 17:04:38 ashley-desktop kernel: [   29.997405] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Oct 14 17:04:38 ashley-desktop kernel: [   29.997477] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Oct 14 17:04:38 ashley-desktop kernel: [   30.003409] 8139too Fast Ethernet driver 0.9.28
Oct 14 17:04:38 ashley-desktop kernel: [   30.003525] ACPI: PCI Interrupt 0000:02:05.0[A] -> GSI 22 (level, low) -> IRQ 20
Oct 14 17:04:38 ashley-desktop kernel: [   30.004321] eth0: RealTek RTL8139 at 0xd800, 00:11:2f:ae:f9:e8, IRQ 20
Oct 14 17:04:38 ashley-desktop kernel: [   30.008358] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Oct 14 17:04:38 ashley-desktop kernel: [   30.008600] scsi0 : ata_piix
Oct 14 17:04:38 ashley-desktop kernel: [   30.008723] scsi1 : ata_piix
Oct 14 17:04:38 ashley-desktop kernel: [   30.010631] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Oct 14 17:04:38 ashley-desktop kernel: [   30.010639] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Oct 14 17:04:38 ashley-desktop kernel: [   30.524027] ata1.00: ATA-6: ST360020A, 3.34, max UDMA/100
Oct 14 17:04:38 ashley-desktop kernel: [   30.524039] ata1.00: 117231408 sectors, multi 16: LBA 
Oct 14 17:04:38 ashley-desktop kernel: [   30.524077] ata1.01: ATAPI: LITE-ON DVDRW SHW-1635S, YS0J, max UDMA/66
Oct 14 17:04:38 ashley-desktop kernel: [   30.536784] ata1.00: configured for UDMA/100
Oct 14 17:04:38 ashley-desktop kernel: [   30.723024] ata1.01: configured for UDMA/66
Oct 14 17:04:38 ashley-desktop kernel: [   30.878543] scsi 0:0:0:0: Direct-Access     ATA      ST360020A        3.34 PQ: 0 ANSI: 5
Oct 14 17:04:38 ashley-desktop kernel: [   30.879500] scsi 0:0:1:0: CD-ROM            LITE-ON  DVDRW SHW-1635S  YS0J PQ: 0 ANSI: 5
Oct 14 17:04:38 ashley-desktop kernel: [   30.888471] Driver 'sd' needs updating - please use bus_type methods
Oct 14 17:04:38 ashley-desktop kernel: [   30.888622] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
Oct 14 17:04:38 ashley-desktop kernel: [   30.888648] sd 0:0:0:0: [sda] Write Protect is off
Oct 14 17:04:38 ashley-desktop kernel: [   30.888686] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 17:04:38 ashley-desktop kernel: [   30.888806] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
Oct 14 17:04:38 ashley-desktop kernel: [   30.888826] sd 0:0:0:0: [sda] Write Protect is off
Oct 14 17:04:38 ashley-desktop kernel: [   30.888869] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 17:04:38 ashley-desktop kernel: [   30.888878]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Oct 14 17:04:38 ashley-desktop kernel: [   30.913801]  sda1 sda2 < sda5 >
Oct 14 17:04:38 ashley-desktop kernel: [   30.945487] sd 0:0:0:0: [sda] Attached SCSI disk
Oct 14 17:04:38 ashley-desktop kernel: [   30.949689] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
Oct 14 17:04:38 ashley-desktop kernel: [   30.949697] Uniform CD-ROM driver Revision: 3.20
Oct 14 17:04:38 ashley-desktop kernel: [   30.952178] sd 0:0:0:0: Attached scsi generic sg0 type 0
Oct 14 17:04:38 ashley-desktop kernel: [   30.952213] sr 0:0:1:0: Attached scsi generic sg1 type 5
Oct 14 17:04:38 ashley-desktop kernel: [   30.970079] usb 5-1: new high speed USB device using ehci_hcd and address 2
Oct 14 17:04:38 ashley-desktop kernel: [   31.240539] usb 5-1: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   31.440463] Attempting manual resume
Oct 14 17:04:38 ashley-desktop kernel: [   31.497390] kjournald starting.  Commit interval 5 seconds
Oct 14 17:04:38 ashley-desktop kernel: [   31.497411] EXT3-fs: mounted filesystem with ordered data mode.
Oct 14 17:04:38 ashley-desktop kernel: [   31.715695] usb 5-3: new high speed USB device using ehci_hcd and address 4
Oct 14 17:04:38 ashley-desktop kernel: [   31.849072] usb 5-3: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   31.849347] hub 5-3:1.0: USB hub found
Oct 14 17:04:38 ashley-desktop kernel: [   31.849574] hub 5-3:1.0: 4 ports detected
Oct 14 17:04:38 ashley-desktop kernel: [   32.373630] usb 1-2: new full speed USB device using uhci_hcd and address 4
Oct 14 17:04:38 ashley-desktop kernel: [   32.536058] usb 1-2: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   32.748787] usb 5-3.2: new high speed USB device using ehci_hcd and address 6
Oct 14 17:04:38 ashley-desktop kernel: [   32.842582] usb 5-3.2: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   32.842861] hub 5-3.2:1.0: USB hub found
Oct 14 17:04:38 ashley-desktop kernel: [   32.843211] hub 5-3.2:1.0: 4 ports detected
Oct 14 17:04:38 ashley-desktop kernel: [   33.187023] usb 2-2: new low speed USB device using uhci_hcd and address 2
Oct 14 17:04:38 ashley-desktop kernel: [   33.365653] usb 2-2: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   33.570065] usb 5-3.2.1: new high speed USB device using ehci_hcd and address 7
Oct 14 17:04:38 ashley-desktop kernel: [   33.667353] usb 5-3.2.1: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   33.865139] usb 5-3.2.2: new high speed USB device using ehci_hcd and address 8
Oct 14 17:04:38 ashley-desktop kernel: [   33.958949] usb 5-3.2.2: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   34.156226] usb 5-3.2.3: new high speed USB device using ehci_hcd and address 9
Oct 14 17:04:38 ashley-desktop kernel: [   34.250034] usb 5-3.2.3: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   34.447312] usb 5-3.2.4: new low speed USB device using ehci_hcd and address 10
Oct 14 17:04:38 ashley-desktop kernel: [   34.547230] usb 5-3.2.4: configuration #1 chosen from 1 choice
Oct 14 17:04:38 ashley-desktop kernel: [   44.603152] input: PC Speaker as /devices/platform/pcspkr/input/input2
Oct 14 17:04:38 ashley-desktop kernel: [   45.397554] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Oct 14 17:04:38 ashley-desktop kernel: [   45.421565] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Oct 14 17:04:38 ashley-desktop kernel: [   45.527280] Linux agpgart interface v0.102
Oct 14 17:04:38 ashley-desktop kernel: [   45.729858] agpgart: Detected an Intel 865 Chipset.
Oct 14 17:04:38 ashley-desktop kernel: [   45.733490] agpgart: AGP aperture is 64M @ 0xf8000000
Oct 14 17:04:38 ashley-desktop kernel: [   45.768908] input: Power Button (FF) as /devices/virtual/input/input3
Oct 14 17:04:38 ashley-desktop kernel: [   45.788604] iTCO_vendor_support: vendor-support=0
Oct 14 17:04:38 ashley-desktop kernel: [   45.810236] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Oct 14 17:04:38 ashley-desktop kernel: [   45.810402] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
Oct 14 17:04:38 ashley-desktop kernel: [   45.810450] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Oct 14 17:04:38 ashley-desktop kernel: [   45.831160] ACPI: Power Button (FF) [PWRF]
Oct 14 17:04:38 ashley-desktop kernel: [   45.831491] input: Power Button (CM) as /devices/virtual/input/input4
Oct 14 17:04:38 ashley-desktop kernel: [   45.879171] ACPI: Power Button (CM) [PWRB]
Oct 14 17:04:38 ashley-desktop kernel: [   47.053991] usbcore: registered new interface driver snd-usb-audio
Oct 14 17:04:38 ashley-desktop kernel: [   47.054742] input: Yealink usb-p1k as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.3/input/input5
Oct 14 17:04:38 ashley-desktop kernel: [   47.151267] usbcore: registered new interface driver yealink
Oct 14 17:04:38 ashley-desktop kernel: [   47.151285] /build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: Yealink phone driver:yld-20051230
Oct 14 17:04:38 ashley-desktop kernel: [   47.281942] usbcore: registered new interface driver hiddev
Oct 14 17:04:38 ashley-desktop kernel: [   47.295685] input: Kensington      Kensington USB/PS2 Orbit as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2:1.0/input/input6
Oct 14 17:04:38 ashley-desktop kernel: [   47.334382] input,hidraw0: USB HID v1.10 Mouse [Kensington      Kensington USB/PS2 Orbit] on usb-0000:00:1d.1-2
Oct 14 17:04:38 ashley-desktop kernel: [   47.336894] input: ruwido austria GmbH ruwido austria GmbH USB Infrared Keyboard V2.01 as /devices/pci0000:00/0000:00:1d.7/usb5/5-3/5-3.2/5-3.2.4/5-3.2.4:1.0/input/input7
Oct 14 17:04:38 ashley-desktop kernel: [   47.382234] input,hidraw1: USB HID v1.10 Keyboard [ruwido austria GmbH ruwido austria GmbH USB Infrared Keyboard V2.01] on usb-0000:00:1d.7-3.2.4
Oct 14 17:04:38 ashley-desktop kernel: [   47.385424] input: ruwido austria GmbH ruwido austria GmbH USB Infrared Keyboard V2.01 as /devices/pci0000:00/0000:00:1d.7/usb5/5-3/5-3.2/5-3.2.4/5-3.2.4:1.1/input/input8
Oct 14 17:04:38 ashley-desktop kernel: [   47.394745] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
Oct 14 17:04:38 ashley-desktop kernel: [   47.414173] input,hidraw2: USB HID v1.10 Mouse [ruwido austria GmbH ruwido austria GmbH USB Infrared Keyboard V2.01] on usb-0000:00:1d.7-3.2.4
Oct 14 17:04:38 ashley-desktop kernel: [   47.414257] usbcore: registered new interface driver usbhid
Oct 14 17:04:38 ashley-desktop kernel: [   47.414274] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Oct 14 17:04:38 ashley-desktop kernel: [   47.468018] usbcore: registered new interface driver libusual
Oct 14 17:04:38 ashley-desktop kernel: [   47.567950] Initializing USB Mass Storage driver...
Oct 14 17:04:38 ashley-desktop kernel: [   47.570160] scsi2 : SCSI emulation for USB Mass Storage devices
Oct 14 17:04:38 ashley-desktop kernel: [   47.570476] scsi3 : SCSI emulation for USB Mass Storage devices
Oct 14 17:04:38 ashley-desktop kernel: [   47.570698] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 14 17:04:38 ashley-desktop kernel: [   47.570843] usbcore: registered new interface driver usb-storage
Oct 14 17:04:38 ashley-desktop kernel: [   47.570849] USB Mass Storage support registered.
Oct 14 17:04:38 ashley-desktop kernel: [   47.817788] intel8x0_measure_ac97_clock: measured 55899 usecs
Oct 14 17:04:38 ashley-desktop kernel: [   47.817794] intel8x0: clocking to 48000
Oct 14 17:04:38 ashley-desktop kernel: [   48.061212] usbcore: registered new interface driver rt73usb
Oct 14 17:04:38 ashley-desktop kernel: [   49.059250] udev: renamed network interface wlan0 to wlan1
Oct 14 17:04:38 ashley-desktop kernel: [   49.296848] lp: driver loaded but no devices found
Oct 14 17:04:38 ashley-desktop kernel: [   49.470340] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Oct 14 17:04:38 ashley-desktop kernel: [   50.046562] EXT3 FS on sda1, internal journal
Oct 14 17:04:38 ashley-desktop kernel: [   51.345664] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct 14 17:04:38 ashley-desktop kernel: [   51.541705] prism2usb_init: prism2_usb.o: 0.2.8 Loaded
Oct 14 17:04:38 ashley-desktop kernel: [   51.541714] prism2usb_init: dev_info is: prism2_usb
Oct 14 17:04:38 ashley-desktop kernel: [   51.541794] usbcore: registered new interface driver prism2_usb
Oct 14 17:04:38 ashley-desktop kernel: [   52.554706] scsi 3:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
Oct 14 17:04:38 ashley-desktop kernel: [   52.554822] scsi 2:0:0:0: Direct-Access     Freecom  DataBar USB2.0   1100 PQ: 0 ANSI: 0 CCS
Oct 14 17:04:38 ashley-desktop kernel: [   52.555319] scsi 3:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.555815] scsi 3:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.556311] scsi 3:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.556577] scsi 4:0:0:0: Direct-Access     ST380215 A                0000 PQ: 0 ANSI: 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.558483] sd 4:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
Oct 14 17:04:39 ashley-desktop kernel: [   52.562774] sd 4:0:0:0: [sdb] Write Protect is off
Oct 14 17:04:39 ashley-desktop kernel: [   52.563900] sd 4:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
Oct 14 17:04:39 ashley-desktop kernel: [   52.564770] sd 4:0:0:0: [sdb] Write Protect is off
Oct 14 17:04:39 ashley-desktop kernel: [   52.564784]  sdb:<3>/build/buildd/linux-2.6.24/drivers/input/misc/yealink.c: unexpected response fd
Oct 14 17:04:39 ashley-desktop kernel: [   52.571192]  sdb1
Oct 14 17:04:39 ashley-desktop kernel: [   52.571343] sd 4:0:0:0: [sdb] Attached SCSI disk
Oct 14 17:04:39 ashley-desktop kernel: [   52.571427] sd 4:0:0:0: Attached scsi generic sg2 type 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.572740] sd 3:0:0:0: [sdc] Attached SCSI removable disk
Oct 14 17:04:39 ashley-desktop kernel: [   52.572810] sd 3:0:0:0: Attached scsi generic sg3 type 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.574003] sd 3:0:0:1: [sdd] Attached SCSI removable disk
Oct 14 17:04:39 ashley-desktop kernel: [   52.574069] sd 3:0:0:1: Attached scsi generic sg4 type 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.575349] sd 3:0:0:2: [sde] Attached SCSI removable disk
Oct 14 17:04:39 ashley-desktop kernel: [   52.575413] sd 3:0:0:2: Attached scsi generic sg5 type 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.576615] sd 3:0:0:3: [sdf] Attached SCSI removable disk
Oct 14 17:04:39 ashley-desktop kernel: [   52.576678] sd 3:0:0:3: Attached scsi generic sg6 type 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.577774] sd 2:0:0:0: [sdg] 15663104 512-byte hardware sectors (8020 MB)
Oct 14 17:04:39 ashley-desktop kernel: [   52.578507] sd 2:0:0:0: [sdg] Write Protect is off
Oct 14 17:04:39 ashley-desktop kernel: [   52.581257] sd 2:0:0:0: [sdg] 15663104 512-byte hardware sectors (8020 MB)
Oct 14 17:04:39 ashley-desktop kernel: [   52.582021] sd 2:0:0:0: [sdg] Write Protect is off
Oct 14 17:04:39 ashley-desktop kernel: [   52.582039]  sdg: sdg1
Oct 14 17:04:39 ashley-desktop kernel: [   52.582877] sd 2:0:0:0: [sdg] Attached SCSI removable disk
Oct 14 17:04:39 ashley-desktop kernel: [   52.582941] sd 2:0:0:0: Attached scsi generic sg7 type 0
Oct 14 17:04:39 ashley-desktop kernel: [   52.982334] NET: Registered protocol family 17
Oct 14 17:04:39 ashley-desktop kernel: [   53.928801] No dock devices found.
Oct 14 17:04:39 ashley-desktop kernel: [   55.887924] ppdev: user-space parallel port driver

Oct 14 17:04:40 ashley-desktop kernel: [   56.166981] audit(1224000280.065:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5173 profile="/usr/sbin/cupsd" namespace="default"
Oct 14 17:04:40 ashley-desktop kernel: [   56.262660] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct 14 17:04:40 ashley-desktop kernel: [   56.262670] apm: disabled - APM is not SMP safe.
Oct 14 17:04:41 ashley-desktop dhcdbd: Started up.
Oct 14 17:04:47 ashley-desktop kernel: [   63.437121] eth0: link down
Oct 14 17:04:47 ashley-desktop kernel: [   63.691263] Bluetooth: Core ver 2.11
Oct 14 17:04:47 ashley-desktop kernel: [   63.691698] NET: Registered protocol family 31
Oct 14 17:04:47 ashley-desktop kernel: [   63.691705] Bluetooth: HCI device and connection manager initialized
Oct 14 17:04:47 ashley-desktop kernel: [   63.691712] Bluetooth: HCI socket layer initialized
Oct 14 17:04:47 ashley-desktop kernel: [   63.759943] Bluetooth: L2CAP ver 2.9
Oct 14 17:04:47 ashley-desktop kernel: [   63.759950] Bluetooth: L2CAP socket layer initialized
Oct 14 17:04:47 ashley-desktop kernel: [   63.952512] Bluetooth: RFCOMM socket layer initialized
Oct 14 17:04:47 ashley-desktop kernel: [   63.952538] Bluetooth: RFCOMM TTY layer initialized
Oct 14 17:04:47 ashley-desktop kernel: [   63.952542] Bluetooth: RFCOMM ver 1.8
Oct 14 17:04:50 ashley-desktop kernel: [   66.139317] [drm] Initialized drm 1.1.0 20060810
Oct 14 17:04:50 ashley-desktop kernel: [   66.151466] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Oct 14 17:04:50 ashley-desktop kernel: [   66.151837] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Oct 14 17:04:51 ashley-desktop kernel: [   67.732419] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
Oct 14 17:04:51 ashley-desktop kernel: [   67.732453] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Oct 14 17:04:51 ashley-desktop kernel: [   67.732493] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Oct 14 17:04:52 ashley-desktop kernel: [   68.141077] [drm] Setting GART location based on new memory map
Oct 14 17:04:52 ashley-desktop kernel: [   68.141091] [drm] Loading R200 Microcode
Oct 14 17:04:52 ashley-desktop kernel: [   68.141136] [drm] writeback test succeeded in 1 usecs
Oct 14 17:06:31 ashley-desktop kernel: [  167.617533] NET: Registered protocol family 10
Oct 14 17:06:31 ashley-desktop kernel: [  167.618162] lo: Disabled Privacy Extensions
Oct 14 17:06:31 ashley-desktop kernel: [  167.619030] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 14 17:06:31 ashley-desktop kernel: [  167.619920] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Oct 14 17:06:32 ashley-desktop pulseaudio[5921]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 8000 Hz.
Oct 14 17:06:32 ashley-desktop pulseaudio[5921]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct 14 17:06:32 ashley-desktop pulseaudio[5921]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 8000 Hz.
Oct 14 17:06:32 ashley-desktop pulseaudio[5921]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Oct 14 17:06:46 ashley-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.reason
Oct 14 17:06:51 ashley-desktop kernel: [  187.202036] UDF-fs: Partition marked readonly; forcing readonly mount
Oct 14 17:06:51 ashley-desktop kernel: [  187.283815] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'LOADED', timestamp 2004/04/13 04:40 (103c)
Oct 14 17:06:56 ashley-desktop kernel: [  192.094293] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Oct 14 17:07:03 ashley-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.domain_name
Oct 14 17:07:03 ashley-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.nis_domain
Oct 14 17:07:03 ashley-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.nis_servers
Oct 14 17:07:03 ashley-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.interface_mtu
Oct 14 17:17:11 ashley-desktop kernel: [  804.807770] usb 5-3.2.2: reset high speed USB device using ehci_hcd and address 8
Oct 14 17:19:43 ashley-desktop kernel: [  956.332529] usb 5-3.2.2: reset high speed USB device using ehci_hcd and address 8

```

Thanks for all the help with this one,  much appreciated

-Ash R

---

### Post by bobnutfield on 2008-10-14
I took a look at your messages and do not see anything affecting your time settings.  You might try making sure the time is set correctly in your BIOS, then set the system time.  Take a look a this thread from LQ about setting your system time:

> [http://www.linuxquestions.org/questions/ubuntu-63/setting-system-date-and-time-affecting-the-clock-and-date-on-bios-586087/](http://www.linuxquestions.org/questions/ubuntu-63/setting-system-date-and-time-affecting-the-clock-and-date-on-bios-586087/)

---

### Post by bruce2000 on 2008-10-14
Hi Ash R

If it's the CMOS battery causing the problem, you could try leaving your PC on 24 hours to make sure the battery is fully charged. I'm not saying this is the cause, but it may be worth a try.

---

### Post by LowSky on 2008-10-14
Removal the Cmos Battery often require a person to reset the clock from BIOS. At boot up just hit F2 or F+whatever or maybe Delete (its up to the motherboard manufactures)
set the date and time and dont forget to save. Leave the computer on for a 24 hour cycle to recharge the CMOS battery and then do a shutdown-startup cycle to check

---

