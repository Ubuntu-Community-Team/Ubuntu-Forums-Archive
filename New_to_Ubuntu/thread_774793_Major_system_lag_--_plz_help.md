---
title: "Major system lag -- plz help"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Bodsda on 2008-04-29
Hey guys. Whenever a program uses the internet my cpu spikes to 40%-60%-100% -- ive run top while an internet page is loading youtube and i see mozilla causing it however if i do anything in apt this also causes the spikes so im finding it difficult to determine what is causing it. I used to run Gutsy which was fine except no wifi i was wired in, then i ran Hardy Beta 5 which was brilliant, wifi and no lag, then when i upgraded this started happening, so i did a clean install of Hardy and am still having problems. 

Heres a few screens of top while youtube is loading a video.
(The lag is also present when loading a simple site like photobucket or ubuntu com docs)

dmesg
```
[    0.000000] Linux version 2.6.24-16-386 (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 Thu Apr 10 12:50:06 UTC 2008 (Ubuntu 2.6.24-16.30-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3d40
[    0.000000] Entering add_active_range(0, 0, 393200) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   393200
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   393200
[    0.000000] On node 0 totalpages: 393200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1279 pages used for memmap
[    0.000000]   HighMem zone: 162545 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F57A0 checksum 0
[    0.000000] ACPI: RSDP 000F57A0, 0014 (r0 VIAK8M)
[    0.000000] ACPI: RSDT 5FFF3000, 002C (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 5FFF3040, 0074 (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 5FFF30C0, 5308 (r1 VIAK8M AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 5FFF0000, 0040
[    0.000000] ACPI: APIC 5FFF8400, 005A (r1 VIAK8M AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390129
[    0.000000] Kernel command line: root=UUID=730bfc3b-4524-4026-9487-af8de4dfa648 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 999.990 MHz processor.
[   15.951318] Console: colour VGA+ 80x25
[   15.951323] console [tty0] enabled
[   15.951916] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.952907] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.035991] Memory: 1546520k/1572800k available (2067k kernel code, 25036k reserved, 968k data, 360k init, 655296k highmem)
[   16.036005] virtual kernel memory layout:
[   16.036007]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
[   16.036009]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.036011]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.036013]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.036015]       .init : 0xc03fa000 - 0xc0454000   ( 360 kB)
[   16.036018]       .data : 0xc0304fb4 - 0xc03f73a4   ( 968 kB)
[   16.036020]       .text : 0xc0100000 - 0xc0304fb4   (2067 kB)
[   16.036025] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.036088] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.116116] Calibrating delay using timer specific routine.. 2002.53 BogoMIPS (lpj=4005077)
[   16.116150] Security Framework initialized
[   16.116159] SELinux:  Disabled at boot.
[   16.116176] AppArmor: AppArmor initialized
[   16.116182] Failure registering capabilities with primary security module.
[   16.116192] Mount-cache hash table entries: 512
[   16.116330] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[   16.116342] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   16.116347] CPU: L2 Cache: 128K (64 bytes/line)
[   16.116351] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[   16.116364] Compat vDSO mapped to ffffe000.
[   16.116376] CPU: AMD Sempron(tm) Processor 3000+ stepping 02
[   16.116384] Checking 'hlt' instruction... OK.
[   16.134090] Freeing SMP alternatives: 0k freed
[   16.134264] Early unpacking initramfs... done
[   16.760373] ACPI: Core revision 20070126
[   16.760468] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.784531] ENABLING IO-APIC IRQs
[   16.784853] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   16.932259] net_namespace: 64 bytes
[   16.932267] Booting paravirtualized kernel on bare hardware
[   16.933047] Time: 22:04:24  Date: 04/29/08
[   16.933084] NET: Registered protocol family 16
[   16.933326] EISA bus registered
[   16.933363] ACPI: bus type pci registered
[   16.939330] PCI: PCI BIOS revision 2.10 entry at 0xfb820, last bus=1
[   16.939334] PCI: Using configuration type 1
[   16.939337] Setting up standard PCI resources
[   16.944300] ACPI: EC: Look up EC in DSDT
[   16.952480] ACPI: Interpreter enabled
[   16.952487] ACPI: (supports S0 S3 S4 S5)
[   16.952510] ACPI: Using IOAPIC for interrupt routing
[   16.962356] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.963492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   17.056492] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[   17.056750] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[   17.057005] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[   17.057235] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   17.057463] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   17.057676] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   17.057889] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   17.058101] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   17.058364] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[   17.058609] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[   17.058854] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[   17.059137] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[   17.059302] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.059342] pnp: PnP ACPI init
[   17.059355] ACPI: bus type pnp registered
[   17.065694] pnp: PnP ACPI: found 12 devices
[   17.065699] ACPI: ACPI bus type pnp unregistered
[   17.065705] PnPBIOS: Disabled by ACPI PNP
[   17.065982] PCI: Using ACPI for IRQ routing
[   17.065987] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.112083] NET: Registered protocol family 8
[   17.112086] NET: Registered protocol family 20
[   17.112168] AppArmor: AppArmor Filesystem Enabled
[   17.116075] Time: tsc clocksource has been installed.
[   17.124130] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[   17.124135] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[   17.124140] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   17.124145] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   17.124150] system 00:00: iomem range 0x5fff0000-0x5fffffff could not be reserved
[   17.124156] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   17.124161] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   17.124166] system 00:00: iomem range 0x100000-0x5ffeffff could not be reserved
[   17.124171] system 00:00: iomem range 0x0-0x0 could not be reserved
[   17.124176] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   17.124181] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   17.124186] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[   17.124197] system 00:02: ioport range 0x4000-0x407f has been reserved
[   17.124202] system 00:02: ioport range 0x5000-0x500f has been reserved
[   17.124212] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   17.124217] system 00:03: ioport range 0x290-0x29f has been reserved
[   17.124222] system 00:03: ioport range 0x800-0x805 has been reserved
[   17.154765] PCI: Bridge: 0000:00:01.0
[   17.154769]   IO window: disabled.
[   17.154775]   MEM window: e8000000-eaffffff
[   17.154780]   PREFETCH window: d0000000-dfffffff
[   17.154799] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.154816] NET: Registered protocol family 2
[   17.192156] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.192588] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   17.193978] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   17.194327] TCP: Hash tables configured (established 131072 bind 65536)
[   17.194331] TCP reno registered
[   17.204258] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   17.791237]  it is
[   18.424465] Freeing initrd memory: 8118k freed
[   18.425214] audit: initializing netlink socket (disabled)
[   18.425230] audit(1209506664.264:1): initialized
[   18.425412] highmem bounce pool size: 64 pages
[   18.427801] VFS: Disk quotas dquot_6.5.1
[   18.427841] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.428038] io scheduler noop registered
[   18.428042] io scheduler anticipatory registered
[   18.428045] io scheduler deadline registered
[   18.428061] io scheduler cfq registered (default)
[   18.428077] PCI: VIA PCI bridge detected. Disabling DAC.
[   18.428157] Boot video device is 0000:01:00.0
[   18.428475] isapnp: Scanning for PnP cards...
[   18.782712] isapnp: No Plug & Play device found
[   18.826581] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.826706] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.826894] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.827590] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.827989] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   18.829046] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.829144] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.829319] PNP: No PS/2 controller found. Probing ports directly.
[   18.829755] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.829762] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.840026] mice: PS/2 mouse device common for all mice
[   18.840179] EISA: Probing bus 0 at eisa.0
[   18.840201] Cannot allocate resource for EISA slot 4
[   18.840204] Cannot allocate resource for EISA slot 5
[   18.840220] EISA: Detected 0 cards.
[   18.840224] cpuidle: using governor ladder
[   18.840410] NET: Registered protocol family 1
[   18.840446] Using IPI Shortcut mode
[   18.840480] registered taskstats version 1
[   18.840629]   Magic number: 4:16:99
[   18.840798] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.840801] EDD information not available.
[   18.841166] Freeing unused kernel memory: 360k freed
[   20.298115] fuse init (API version 7.9)
[   20.411977] ACPI: Thermal Zone [THRM] (49 C)
[   21.616514] SCSI subsystem initialized
[   21.711385] usbcore: registered new interface driver usbfs
[   21.711415] usbcore: registered new interface driver hub
[   21.751783] usbcore: registered new device driver usb
[   21.753384] USB Universal Host Controller Interface driver v3.0
[   21.753777] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   21.753786] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16
[   21.753801] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   21.754098] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   21.754135] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000d000
[   21.754319] usb usb1: configuration #1 chosen from 1 choice
[   21.754353] hub 1-0:1.0: USB hub found
[   21.754362] hub 1-0:1.0: 2 ports detected
[   21.779730] libata version 3.00 loaded.
[   21.798244] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   21.798253] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   21.855877] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16
[   21.855894] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   21.855926] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   21.855952] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000d400
[   21.856103] usb usb2: configuration #1 chosen from 1 choice
[   21.856135] hub 2-0:1.0: USB hub found
[   21.856143] hub 2-0:1.0: 2 ports detected
[   21.959869] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16
[   21.959886] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   21.959918] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   21.959945] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000d800
[   21.960095] usb usb3: configuration #1 chosen from 1 choice
[   21.960128] hub 3-0:1.0: USB hub found
[   21.960135] hub 3-0:1.0: 2 ports detected
[   22.063870] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16
[   22.063887] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   22.063920] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   22.063947] uhci_hcd 0000:00:10.3: irq 16, io base 0x0000dc00
[   22.064104] usb usb4: configuration #1 chosen from 1 choice
[   22.064136] hub 4-0:1.0: USB hub found
[   22.064144] hub 4-0:1.0: 2 ports detected
[   22.095728] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   22.095852] Floppy drive(s): fd0 is 1.44M
[   22.115575] FDC 0 is a post-1991 82077
[   22.167969] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 16
[   22.167988] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   22.168039] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   22.168089] ehci_hcd 0000:00:10.4: irq 16, io mem 0xeb000000
[   22.223707] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.223860] usb usb5: configuration #1 chosen from 1 choice
[   22.223894] hub 5-0:1.0: USB hub found
[   22.223903] hub 5-0:1.0: 8 ports detected
[   22.328290] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   22.328301] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   22.328369] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[   22.328398] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   22.328431] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   22.332885] pata_via 0000:00:0f.1: version 0.3.3
[   22.332915] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   22.340634] scsi0 : pata_via
[   22.342082] scsi1 : pata_via
[   22.343831] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xcc00 irq 14
[   22.343836] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xcc08 irq 15
[   22.529429] ata1.01: ATA-6: Maxtor 4D040H2, DAH017K0, max UDMA/100
[   22.529436] ata1.01: 80043264 sectors, multi 16: LBA 
[   22.544174] ata1.01: configured for UDMA/100
[   22.619704] usb 1-1: device not accepting address 2, error -71
[   22.880077] ata2.00: ATAPI: DVDRW DRW-6S160P, PSG6, max UDMA/66
[   22.880099] ata2.00: limited to UDMA/33 due to 40-wire cable
[   23.067940] ata2.00: configured for UDMA/33
[   23.068079] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 4D040H2   DAH0 PQ: 0 ANSI: 5
[   23.069030] scsi 1:0:0:0: CD-ROM            DVDRW    DRW-6S160P       PSG6 PQ: 0 ANSI: 5
[   23.071402] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   23.071413] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
[   23.075706] eth0: VIA Rhine II at 0xeb001000, 00:16:ec:17:3f:c5, IRQ 18.
[   23.076418] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   23.081667] sata_via 0000:00:0f.0: version 2.3
[   23.081689] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 17
[   23.081740] sata_via 0000:00:0f.0: routed to hard irq line 11
[   23.083375] scsi2 : sata_via
[   23.084931] scsi3 : sata_via
[   23.085001] ata3: SATA max UDMA/133 cmd 0xb400 ctl 0xb800 bmdma 0xc400 irq 17
[   23.085006] ata4: SATA max UDMA/133 cmd 0xbc00 ctl 0xc000 bmdma 0xc408 irq 17
[   23.287635] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.311759] Driver 'sd' needs updating - please use bus_type methods
[   23.311857] sd 0:0:1:0: [sda] 80043264 512-byte hardware sectors (40982 MB)
[   23.311874] sd 0:0:1:0: [sda] Write Protect is off
[   23.311879] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   23.311900] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.311959] sd 0:0:1:0: [sda] 80043264 512-byte hardware sectors (40982 MB)
[   23.311972] sd 0:0:1:0: [sda] Write Protect is off
[   23.311976] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   23.311996] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.312003]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   23.320869]  sda1
[   23.320955] sd 0:0:1:0: [sda] Attached SCSI disk
[   23.333483] sd 0:0:1:0: Attached scsi generic sg0 type 0
[   23.333561] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   23.337872] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   23.337880] Uniform CD-ROM driver Revision: 3.20
[   23.337950] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.452000] ata3.00: ATA-7: SAMSUNG HD080HJ, WT100-41, max UDMA7
[   23.452008] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.484064] ata3.00: configured for UDMA/133
[   23.687590] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   23.698388] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD080HJ  WT10 PQ: 0 ANSI: 5
[   23.698941] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   23.698960] sd 2:0:0:0: [sdb] Write Protect is off
[   23.698965] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   23.698988] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.699053] sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   23.699067] sd 2:0:0:0: [sdb] Write Protect is off
[   23.699071] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   23.699092] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.699098]  sdb: sdb1 sdb2 sdb3 sdb4
[   23.725572] sd 2:0:0:0: [sdb] Attached SCSI disk
[   23.725625] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   23.811605] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   23.944974] usb 5-1: configuration #1 chosen from 1 choice
[   23.945407] hub 5-1:1.0: USB hub found
[   23.946483] hub 5-1:1.0: 4 ports detected
[   24.064934] Attempting manual resume
[   24.064939] swsusp: Resume From Partition 8:17
[   24.064942] PM: Checking swsusp image.
[   24.065180] PM: Resume from disk failed.
[   24.120928] kjournald starting.  Commit interval 5 seconds
[   24.120947] EXT3-fs: mounted filesystem with ordered data mode.
[   24.475544] usb 5-4: new high speed USB device using ehci_hcd and address 4
[   24.779646] usb 5-4: configuration #1 chosen from 1 choice
[   24.979831] usb 5-1.3: new low speed USB device using ehci_hcd and address 5
[   25.051816] usb 5-1.3: device descriptor read/64, error -32
[   25.227789] usb 5-1.3: device descriptor read/64, error -32
[   25.403765] usb 5-1.3: new low speed USB device using ehci_hcd and address 6
[   25.475752] usb 5-1.3: device descriptor read/64, error -32
[   25.651730] usb 5-1.3: device descriptor read/64, error -32
[   25.827702] usb 5-1.3: new low speed USB device using ehci_hcd and address 7
[   26.235425] usb 5-1.3: device not accepting address 7, error -32
[   26.307633] usb 5-1.3: new low speed USB device using ehci_hcd and address 8
[   26.715396] usb 5-1.3: device not accepting address 8, error -32
[   26.915671] usb 5-1.4: new high speed USB device using ehci_hcd and address 9
[   27.008410] usb 5-1.4: configuration #1 chosen from 1 choice
[   27.247357] usb 1-2: new low speed USB device using uhci_hcd and address 4
[   27.432819] usb 1-2: configuration #1 chosen from 1 choice
[   30.527196] Linux agpgart interface v0.102
[   30.555255] agpgart: Detected AGP bridge 0
[   30.635249] agpgart: AGP aperture is 128M @ 0xe0000000
[   30.857066] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.879568] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.807218] input: Power Button (FF) as /devices/virtual/input/input1
[   31.819056] ACPI: Power Button (FF) [PWRF]
[   31.819234] input: Power Button (CM) as /devices/virtual/input/input2
[   31.835070] ACPI: Power Button (CM) [PWRB]
[   33.935364] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   33.935376] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 19
[   33.935519] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   34.913094] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 20
[   34.913125] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   35.487169] Real Time Clock Driver v1.12ac
[   35.915300] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   36.465175] usbcore: registered new interface driver hiddev
[   36.483113] input: G-Tech CHINA    USB Wireless Mouse & KeyBoard V1.01   as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input4
[   36.494851] input,hidraw0: USB HID v1.00 Keyboard [G-Tech CHINA    USB Wireless Mouse & KeyBoard V1.01  ] on usb-0000:00:10.0-2
[   36.535306] input: G-Tech CHINA    USB Wireless Mouse & KeyBoard V1.01   as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.1/input/input5
[   36.558860] input,hidraw1: USB HID v1.00 Mouse [G-Tech CHINA    USB Wireless Mouse & KeyBoard V1.01  ] on usb-0000:00:10.0-2
[   36.558886] usbcore: registered new interface driver usbhid
[   36.558893] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   37.069465] parport_pc 00:0b: reported by Plug and Play ACPI
[   37.069537] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   37.698358] usbcore: registered new interface driver libusual
[   37.718163] Initializing USB Mass Storage driver...
[   37.960846] phy0: Selected rate control algorithm 'simple'
[   38.141770] usbcore: registered new interface driver rt73usb
[   38.166400] scsi4 : SCSI emulation for USB Mass Storage devices
[   38.166936] usbcore: registered new interface driver usb-storage
[   38.166945] USB Mass Storage support registered.
[   38.167117] usbcore: registered new interface driver rt2500usb
[   38.167758] usb-storage: device found at 9
[   38.167764] usb-storage: waiting for device to settle before scanning
[   42.035784] lp0: using parport0 (interrupt-driven).
[   42.129167] Adding 2955952k swap on /dev/sdb1.  Priority:-1 extents:1 across:2955952k
[   42.731071] EXT3 FS on sdb3, internal journal
[   43.166424] usb-storage: device scan complete
[   43.166920] scsi 4:0:0:0: Direct-Access     ClvrStuf USB Flash Drive  6.50 PQ: 0 ANSI: 0 CCS
[   43.167407] scsi 4:0:0:1: CD-ROM            ClvrStuf USB Flash Drive  6.50 PQ: 0 ANSI: 0
[   43.178092] sd 4:0:0:0: [sdc] 1962399 512-byte hardware sectors (1005 MB)
[   43.178834] sd 4:0:0:0: [sdc] Write Protect is off
[   43.178840] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[   43.178845] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   43.180912] sd 4:0:0:0: [sdc] 1962399 512-byte hardware sectors (1005 MB)
[   43.181526] sd 4:0:0:0: [sdc] Write Protect is off
[   43.181532] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[   43.181536] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[   43.181543]  sdc: sdc1
[   43.185828] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   43.185893] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   43.193245] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[   43.193329] sr 4:0:0:1: Attached scsi CD-ROM sr1
[   43.193387] sr 4:0:0:1: Attached scsi generic sg4 type 5
[   43.561075] kjournald starting.  Commit interval 5 seconds
[   43.566389] EXT3 FS on sdb2, internal journal
[   43.566397] EXT3-fs: mounted filesystem with ordered data mode.
[   43.581215] kjournald starting.  Commit interval 5 seconds
[   43.582452] EXT3 FS on sdb4, internal journal
[   43.582463] EXT3-fs: mounted filesystem with ordered data mode.
[   44.299750] ip_tables: (C) 2000-2006 Netfilter Core Team
[   44.912561] No dock devices found.
[   45.504629] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[   45.504672] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   45.504677] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   25.240902] Marking TSC unstable due to: cpufreq changes.
[   25.241679] Time: acpi_pm clocksource has been installed.
[   25.384933] Clocksource tsc unstable (delta = 114230688 ns)
[   26.053066] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   26.053071] apm: overridden by ACPI.
[   26.191079] ppdev: user-space parallel port driver
[   26.263016] audit(1209503093.636:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4886 profile="/usr/sbin/cupsd" namespace="default"
[   27.744311] eth0: link down
[   27.810508] Bluetooth: Core ver 2.11
[   27.812557] NET: Registered protocol family 31
[   27.812561] Bluetooth: HCI device and connection manager initialized
[   27.812565] Bluetooth: HCI socket layer initialized
[   27.834366] Bluetooth: L2CAP ver 2.9
[   27.834372] Bluetooth: L2CAP socket layer initialized
[   27.895459] Bluetooth: RFCOMM socket layer initialized
[   27.896019] Bluetooth: RFCOMM TTY layer initialized
[   27.896023] Bluetooth: RFCOMM ver 1.8
[   67.052037] NET: Registered protocol family 10
[   67.053196] lo: Disabled Privacy Extensions
[   67.054558] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.056102] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.679503] UDF-fs: No VRS found
[   44.694314] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.698968] ISOFS: changing to secondary root
[  196.719227] eth0: link down
[  196.720042] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  196.829637] eth0: link down
[  196.830461] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  109.892702] wlan0: Initial auth_alg=0
[  109.892710] wlan0: authenticate with AP 00:1d:68:4e:e4:c3
[  109.898335] wlan0: RX authentication from 00:1d:68:4e:e4:c3 (alg=0 transaction=2 status=0)
[  109.898340] wlan0: authenticated
[  109.898343] wlan0: associate with AP 00:1d:68:4e:e4:c3
[  109.903672] wlan0: RX AssocResp from 00:1d:68:4e:e4:c3 (capab=0x11 status=0 aid=2)
[  109.903677] wlan0: associated
[  109.903682] wlan0: CTS protection enabled (BSSID=00:1d:68:4e:e4:c3)
[  109.903721] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  109.903725] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  109.903727] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  109.903730] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  109.905433] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  110.133695] NET: Registered protocol family 17
[  116.778241] eth0: link down
[  116.778698] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  117.005219] wlan0: no IPv6 routers present

```

lspci
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7300 GT (rev a2)

```

lsusb
```
Bus 005 Device 009: ID 08ec:0020 M-Systems Flash Disk Pioneers 
Bus 005 Device 004: ID 050d:705a Belkin Components 
Bus 005 Device 002: ID 05e3:0606 Genesys Logic, Inc. D-Link DUB-H4 USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0425:0101 Motorola Semiconductors HK, Ltd G-Tech Wireless Mouse & Keyboard
Bus 001 Device 001: ID 0000:0000  

```

iwconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:ec:17:3f:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110900 (108.3 KB)  TX bytes:110900 (108.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:bf:59:b7  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:febf:59b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23667669 (22.5 MB)  TX bytes:1333494 (1.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-BF-59-B7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

If you need any more information plz ask,.,. this is really frustrating.
Thankyou in advanced

---

