---
title: "USB stick and card reader stopped working"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by MarkX on 2008-06-10
Can't read USB card reader or memory sticks any more. Previously they automounted without problems and now there is nothing, not even a message on insertion.

This is the output of "dmsg" before and after inserting the SD card into the slot:
[B]
BEFORE[/B]

[   24.809826] usb 3-3: new high speed USB device using ehci_hcd and address 5
[   25.217206] usb 3-3: device not accepting address 5, error -32
[   35.566092] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.685817] Linux agpgart interface v0.102
[   35.729947] agpgart: Detected SiS chipset - id:1857
[   35.736029] agpgart: AGP aperture is 64M @ 0xd0000000
[   35.813724] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.873636] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   36.025443] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   36.385147] input: Power Button (FF) as /devices/virtual/input/input3
[   36.404697] ACPI: Power Button (FF) [PWRF]
[   36.404916] input: Power Button (CM) as /devices/virtual/input/input4
[   36.417726] ACPI: Power Button (CM) [PWRB]
[   37.833844] nvidia: module license 'NVIDIA' taints kernel.
[   39.039435] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   39.067451] parport_pc 00:0a: reported by Plug and Play ACPI
[   39.067563] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   39.487282] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 20
[   39.807674] intel8x0_measure_ac97_clock: measured 55612 usecs
[   39.807682] intel8x0: clocking to 48000
[   39.808574] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   39.809258] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   42.233184] lp0: using parport0 (interrupt-driven).
[   42.322572] Adding 875500k swap on /dev/sda5.  Priority:-1 extents:1 across:875500k
[   42.910296] EXT3 FS on sda1, internal journal
[   44.548064] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.287792] No dock devices found.
[   46.806322] apm: BIOS not found.
[   46.979262] ppdev: user-space parallel port driver
[   47.199034] audit(1213132221.115:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4726 profile="/usr/sbin/cupsd" namespace="default"
[   49.174038] Bluetooth: Core ver 2.11
[   49.175207] NET: Registered protocol family 31
[   49.175216] Bluetooth: HCI device and connection manager initialized
[   49.175222] Bluetooth: HCI socket layer initialized
[   49.218541] Bluetooth: L2CAP ver 2.9
[   49.218549] Bluetooth: L2CAP socket layer initialized
[   49.297665] usb 3-3: new high speed USB device using ehci_hcd and address 6
[   49.305637] Bluetooth: RFCOMM socket layer initialized
[   49.306025] Bluetooth: RFCOMM TTY layer initialized
[   49.306029] Bluetooth: RFCOMM ver 1.8
[   49.409521] usb 3-3: device descriptor read/64, error -32
[   49.626023] usb 3-3: device descriptor read/64, error -32
[   49.840855] usb 3-3: new high speed USB device using ehci_hcd and address 7
[   49.952654] usb 3-3: device descriptor read/64, error -32
[   50.172336] usb 3-3: device descriptor read/64, error -32
[   50.388034] usb 3-3: new high speed USB device using ehci_hcd and address 8
[   50.795422] usb 3-3: device not accepting address 8, error -32
[   50.917253] usb 3-3: new high speed USB device using ehci_hcd and address 9
[   50.928282] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   50.928703] agpgart: Device is in legacy mode, falling back to 2.x
[   50.928893] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   50.929116] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   51.008130] eth0: Media Link On 100mbps full-duplex 
[   51.365093] usb 3-3: device not accepting address 9, error -32
[   52.342153] NET: Registered protocol family 17
[   58.152177] NET: Registered protocol family 10
[   58.152476] lo: Disabled Privacy Extensions
[   68.941327] eth0: no IPv6 routers present
[  355.449435] usb 3-2: new high speed USB device using ehci_hcd and address 10
[  355.561326] usb 3-2: device descriptor read/64, error -32
[  355.777112] usb 3-2: device descriptor read/64, error -32
[  355.992922] usb 3-2: new high speed USB device using ehci_hcd and address 11
[  356.104793] usb 3-2: device descriptor read/64, error -32
[  356.320581] usb 3-2: device descriptor read/64, error -32
[  356.536371] usb 3-2: new high speed USB device using ehci_hcd and address 12
[  356.943972] usb 3-2: device not accepting address 12, error -32
[  357.055875] usb 3-2: new high speed USB device using ehci_hcd and address 13
[  357.463467] usb 3-2: device not accepting address 13, error -32

--------------------------------------------------------------------------
**AFTER:**


[username (I edited this!)-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fbc70
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAA60 checksum 0
[    0.000000] ACPI: RSDP 000FAA60, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 AMIINT SiS740XX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 1FFF0030, 0081 (r1 AMIINT SiS740XX       11 MSFT  100000B)
[    0.000000] ACPI: DSDT 1FFF0120, 3300 (r1    SiS      746      100 INTL  2002024)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: APIC 1FFF00C0, 005A (r1 AMIINT SiS740XX     1000 MSFT  100000B)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:6 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=61fcbfeb-d9d7-4ec8-bf5e-50e907368b6d ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1670.829 MHz processor.
[   17.319343] Console: colour VGA+ 80x25
[   17.319348] console [tty0] enabled
[   17.319855] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.320257] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.340649] Memory: 507652k/524224k available (2176k kernel code, 15960k reserved, 1006k data, 368k init, 0k highmem)
[   17.340660] virtual kernel memory layout:
[   17.340661]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   17.340663]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.340664]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   17.340666]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   17.340667]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   17.340669]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[   17.340670]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[   17.340674] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.340735] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   17.420647] Calibrating delay using timer specific routine.. 3343.82 BogoMIPS (lpj=6687654)
[   17.420691] Security Framework initialized
[   17.420702] SELinux:  Disabled at boot.
[   17.420728] AppArmor: AppArmor initialized
[   17.420735] Failure registering capabilities with primary security module.
[   17.420749] Mount-cache hash table entries: 512
[   17.420935] Initializing cgroup subsys ns
[   17.420942] Initializing cgroup subsys cpuacct
[   17.420957] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   17.420969] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   17.420972] CPU: L2 Cache: 256K (64 bytes/line)
[   17.420976] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000
[   17.420991] Compat vDSO mapped to ffffe000.
[   17.421009] Checking 'hlt' instruction... OK.
[   17.436949] SMP alternatives: switching to UP code
[   17.438429] Freeing SMP alternatives: 11k freed
[   17.438628] Early unpacking initramfs... done
[   17.844360] ACPI: Core revision 20070126
[   17.844486] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   17.846247] CPU0: AMD Athlon(tm) XP 2000+ stepping 02
[   17.846277] Total of 1 processors activated (3343.82 BogoMIPS).
[   17.846406] ENABLING IO-APIC IRQs
[   17.846593] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.991951] Brought up 1 CPUs
[   17.991992] CPU0 attaching sched-domain:
[   17.991996]  domain 0: span 01
[   17.991998]   groups: 01
[   17.992305] net_namespace: 64 bytes
[   17.992316] Booting paravirtualized kernel on bare hardware
[   17.992883] Time: 21:09:51  Date: 06/10/08
[   17.992936] NET: Registered protocol family 16
[   17.993244] EISA bus registered
[   17.993271] ACPI: bus type pci registered
[   17.994830] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[   17.994834] PCI: Using configuration type 1
[   17.994836] Setting up standard PCI resources
[   17.997268] ACPI: EC: Look up EC in DSDT
[   18.000732] ACPI: Interpreter enabled
[   18.000736] ACPI: (supports S0 S1 S4 S5)
[   18.000752] ACPI: Using IOAPIC for interrupt routing
[   18.005614] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.005842] Enabling SiS 96x SMBus.
[   18.006460] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.016696] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   18.016803] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.016906] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   18.017013] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   18.017113] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   18.017216] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   18.017321] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.017422] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   18.017545] ACPI: Power Resource [URP1] (off)
[   18.017576] ACPI: Power Resource [URP2] (off)
[   18.017605] ACPI: Power Resource [FDDP] (off)
[   18.017634] ACPI: Power Resource [LPTP] (off)
[   18.017698] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.017745] pnp: PnP ACPI init
[   18.017757] ACPI: bus type pnp registered
[   18.020519] pnp: PnP ACPI: found 12 devices
[   18.020523] ACPI: ACPI bus type pnp unregistered
[   18.020529] PnPBIOS: Disabled by ACPI PNP
[   18.020897] PCI: Using ACPI for IRQ routing
[   18.020901] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.035838] NET: Registered protocol family 8
[   18.035841] NET: Registered protocol family 20
[   18.035961] AppArmor: AppArmor Filesystem Enabled
[   18.039805] Time: tsc clocksource has been installed.
[   18.047851] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   18.047855] system 00:01: ioport range 0x295-0x296 has been reserved
[   18.047859] system 00:01: ioport range 0x800-0x87f has been reserved
[   18.047862] system 00:01: ioport range 0x880-0x8ff has been reserved
[   18.047865] system 00:01: ioport range 0xc00-0xc1f has been reserved
[   18.047870] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   18.078462] PCI: Bridge: 0000:00:01.0
[   18.078464]   IO window: disabled.
[   18.078472]   MEM window: cdd00000-cfefffff
[   18.078477]   PREFETCH window: bda00000-cdbfffff
[   18.078508] NET: Registered protocol family 2
[   18.115840] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.116147] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   18.116446] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   18.116755] TCP: Hash tables configured (established 16384 bind 16384)
[   18.116758] TCP reno registered
[   18.127916] checking if image is initramfs... it is
[   18.579088] Switched to high resolution mode on CPU 0
[   18.886600] Freeing initrd memory: 7323k freed
[   18.887675] audit: initializing netlink socket (disabled)
[   18.887700] audit(1213132192.444:1): initialized
[   18.890469] VFS: Disk quotas dquot_6.5.1
[   18.890611] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.890827] io scheduler noop registered
[   18.890830] io scheduler anticipatory registered
[   18.890832] io scheduler deadline registered
[   18.890846] io scheduler cfq registered (default)
[   18.890906] Boot video device is 0000:01:00.0
[   18.891322] isapnp: Scanning for PnP cards...
[   19.244527] isapnp: No Plug & Play device found
[   19.284203] Real Time Clock Driver v1.12ac
[   19.284351] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.284513] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.285448] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.286658] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.286757] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.286912] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   19.287246] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.287253] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.290338] mice: PS/2 mouse device common for all mice
[   19.290526] EISA: Probing bus 0 at eisa.0
[   19.290566] EISA: Detected 0 cards.
[   19.290571] cpuidle: using governor ladder
[   19.290574] cpuidle: using governor menu
[   19.290789] NET: Registered protocol family 1
[   19.290835] Using IPI No-Shortcut mode
[   19.290896] registered taskstats version 1
[   19.291006]   Magic number: 12:594:196
[   19.291104]   hash matches device ttys8
[   19.291126]   hash matches device ttypb
[   19.291314] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.291316] EDD information not available.
[   19.292003] Freeing unused kernel memory: 368k freed
[   19.317994] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.598318] fuse init (API version 7.9)
[   21.411220] SCSI subsystem initialized
[   21.502714] libata version 3.00 loaded.
[   21.505800] usbcore: registered new interface driver usbfs
[   21.505841] usbcore: registered new interface driver hub
[   21.525429] usbcore: registered new device driver usb
[   21.531709] sis900.c: v1.08.10 Apr. 2 2006
[   21.531830] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
[   21.532909] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   21.543700] 0000:00:04.0: Using transceiver found at address 1 as default
[   21.547433] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 16, 00:0b:6a:c2:b6:65
[   21.549516] pata_sis 0000:00:02.5: version 0.5.2
[   21.554753] scsi0 : pata_sis
[   21.566761] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.574622] scsi1 : pata_sis
[   21.575464] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   21.575468] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   21.698229] FDC 0 is a post-1991 82077
[   21.747402] ata1.00: ATA-6: Maxtor 2B020H1, WAH21PB0, max UDMA/100
[   21.747410] ata1.00: 40020624 sectors, multi 16: LBA 
[   21.747703] ata1.01: ATA-5: ST310212A, 3.02, max UDMA/66
[   21.747706] ata1.01: 20005650 sectors, multi 32: LBA 
[   21.762881] ata1.00: configured for UDMA/100
[   21.778832] ata1.01: configured for UDMA/66
[   22.114100] ata2.00: ATAPI: _NEC CD-RW/DVD-ROM CB-1100B, NS00, max UDMA/33
[   22.301871] ata2.00: configured for UDMA/33
[   22.302089] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 2B020H1   WAH2 PQ: 0 ANSI: 5
[   22.302230] scsi 0:0:1:0: Direct-Access     ATA      ST310212A        3.02 PQ: 0 ANSI: 5
[   22.302849] scsi 1:0:0:0: CD-ROM            _NEC     CDRW/DVD CB1100B NS00 PQ: 0 ANSI: 5
[   22.305680] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[   22.305703] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   22.306167] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   22.306200] ohci_hcd 0000:00:03.0: irq 17, io mem 0xcfffd000
[   22.363661] usb usb1: configuration #1 chosen from 1 choice
[   22.363700] hub 1-0:1.0: USB hub found
[   22.363714] hub 1-0:1.0: 3 ports detected
[   22.465989] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
[   22.466016] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   22.466056] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   22.466082] ohci_hcd 0000:00:03.1: irq 18, io mem 0xcfffe000
[   22.523429] usb usb2: configuration #1 chosen from 1 choice
[   22.523469] hub 2-0:1.0: USB hub found
[   22.523483] hub 2-0:1.0: 3 ports detected
[   22.626227] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 19
[   22.626255] ehci_hcd 0000:00:03.2: EHCI Host Controller
[   22.626305] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   22.626359] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[   22.626382] ehci_hcd 0000:00:03.2: irq 19, io mem 0xcffff000
[   22.768828] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   22.780799] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.780987] usb usb3: configuration #1 chosen from 1 choice
[   22.781024] hub 3-0:1.0: USB hub found
[   22.781034] hub 3-0:1.0: 6 ports detected
[   22.907893] Driver 'sd' needs updating - please use bus_type methods
[   22.908057] sd 0:0:0:0: [sda] 40020624 512-byte hardware sectors (20491 MB)
[   22.908080] sd 0:0:0:0: [sda] Write Protect is off
[   22.908083] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.908109] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.908181] sd 0:0:0:0: [sda] 40020624 512-byte hardware sectors (20491 MB)
[   22.908194] sd 0:0:0:0: [sda] Write Protect is off
[   22.908197] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.908218] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.908224]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.925710]  sda1 sda2 < sda5 >
[   22.954403] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.954525] sd 0:0:1:0: [sdb] 20005650 512-byte hardware sectors (10243 MB)
[   22.954547] sd 0:0:1:0: [sdb] Write Protect is off
[   22.954550] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   22.954575] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.954637] sd 0:0:1:0: [sdb] 20005650 512-byte hardware sectors (10243 MB)
[   22.954650] sd 0:0:1:0: [sdb] Write Protect is off
[   22.954654] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   22.954676] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.954682]  sdb: sdb1
[   22.974672] sd 0:0:1:0: [sdb] Attached SCSI disk
[   22.989787] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.989818] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   22.989843] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   22.990463] sr0: scsi3-mmc drive: 8x/52x writer cd/rw xa/form2 cdda tray
[   22.990471] Uniform CD-ROM driver Revision: 3.20
[   22.990541] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.204197] usb 3-3: new high speed USB device using ehci_hcd and address 2
[   23.316027] usb 3-3: device descriptor read/64, error -32
[   23.486434] Attempting manual resume
[   23.486441] swsusp: Resume From Partition 8:5
[   23.486443] PM: Checking swsusp image.
[   23.486882] PM: Resume from disk failed.
[   23.531710] usb 3-3: device descriptor read/64, error -32
[   23.533645] kjournald starting.  Commit interval 5 seconds
[   23.533667] EXT3-fs: mounted filesystem with ordered data mode.
[   23.747399] usb 3-3: new high speed USB device using ehci_hcd and address 3
[   23.859222] usb 3-3: device descriptor read/64, error -32
[   24.074911] usb 3-3: device descriptor read/64, error -32
[   24.290581] usb 3-3: new high speed USB device using ehci_hcd and address 4
[   24.698010] usb 3-3: device not accepting address 4, error -32
[   24.809826] usb 3-3: new high speed USB device using ehci_hcd and address 5
[   25.217206] usb 3-3: device not accepting address 5, error -32
[   35.566092] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.685817] Linux agpgart interface v0.102
[   35.729947] agpgart: Detected SiS chipset - id:1857
[   35.736029] agpgart: AGP aperture is 64M @ 0xd0000000
[   35.813724] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.873636] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   36.025443] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   36.385147] input: Power Button (FF) as /devices/virtual/input/input3
[   36.404697] ACPI: Power Button (FF) [PWRF]
[   36.404916] input: Power Button (CM) as /devices/virtual/input/input4
[   36.417726] ACPI: Power Button (CM) [PWRB]
[   37.833844] nvidia: module license 'NVIDIA' taints kernel.
[   39.039435] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   39.067451] parport_pc 00:0a: reported by Plug and Play ACPI
[   39.067563] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   39.487282] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 20
[   39.807674] intel8x0_measure_ac97_clock: measured 55612 usecs
[   39.807682] intel8x0: clocking to 48000
[   39.808574] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   39.809258] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   42.233184] lp0: using parport0 (interrupt-driven).
[   42.322572] Adding 875500k swap on /dev/sda5.  Priority:-1 extents:1 across:875500k
[   42.910296] EXT3 FS on sda1, internal journal
[   44.548064] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.287792] No dock devices found.
[   46.806322] apm: BIOS not found.
[   46.979262] ppdev: user-space parallel port driver
[   47.199034] audit(1213132221.115:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4726 profile="/usr/sbin/cupsd" namespace="default"
[   49.174038] Bluetooth: Core ver 2.11
[   49.175207] NET: Registered protocol family 31
[   49.175216] Bluetooth: HCI device and connection manager initialized
[   49.175222] Bluetooth: HCI socket layer initialized
[   49.218541] Bluetooth: L2CAP ver 2.9
[   49.218549] Bluetooth: L2CAP socket layer initialized
[   49.297665] usb 3-3: new high speed USB device using ehci_hcd and address 6
[   49.305637] Bluetooth: RFCOMM socket layer initialized
[   49.306025] Bluetooth: RFCOMM TTY layer initialized
[   49.306029] Bluetooth: RFCOMM ver 1.8
[   49.409521] usb 3-3: device descriptor read/64, error -32
[   49.626023] usb 3-3: device descriptor read/64, error -32
[   49.840855] usb 3-3: new high speed USB device using ehci_hcd and address 7
[   49.952654] usb 3-3: device descriptor read/64, error -32
[   50.172336] usb 3-3: device descriptor read/64, error -32
[   50.388034] usb 3-3: new high speed USB device using ehci_hcd and address 8
[   50.795422] usb 3-3: device not accepting address 8, error -32
[   50.917253] usb 3-3: new high speed USB device using ehci_hcd and address 9
[   50.928282] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   50.928703] agpgart: Device is in legacy mode, falling back to 2.x
[   50.928893] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   50.929116] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   51.008130] eth0: Media Link On 100mbps full-duplex 
[   51.365093] usb 3-3: device not accepting address 9, error -32
[   52.342153] NET: Registered protocol family 17
[   58.152177] NET: Registered protocol family 10
[   58.152476] lo: Disabled Privacy Extensions
[   68.941327] eth0: no IPv6 routers present
[  355.449435] usb 3-2: new high speed USB device using ehci_hcd and address 10
[  355.561326] usb 3-2: device descriptor read/64, error -32
[  355.777112] usb 3-2: device descriptor read/64, error -32
[  355.992922] usb 3-2: new high speed USB device using ehci_hcd and address 11
[  356.104793] usb 3-2: device descriptor read/64, error -32
[  356.320581] usb 3-2: device descriptor read/64, error -32
[  356.536371] usb 3-2: new high speed USB device using ehci_hcd and address 12
[  356.943972] usb 3-2: device not accepting address 12, error -32
[  357.055875] usb 3-2: new high speed USB device using ehci_hcd and address 13
[  357.463467] usb 3-2: device not accepting address 13, error -32

---

