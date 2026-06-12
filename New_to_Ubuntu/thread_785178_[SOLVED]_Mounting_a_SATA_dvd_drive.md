---
title: "[SOLVED] Mounting a SATA dvd drive?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by joemacnz on 2008-05-07
G'day, I am trying to install a SATA DVD drive on my system but it doesn't seem to find it. 

I tried  "sudo mount /dev/sda1 /mnt/cdrom", nothing happened.

I am not sure how to proceed.

Can anyone help?

---

### Post by joemacnz on 2008-05-07
dmesg outputs the following but it means little to me.

[    0.000000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 262064) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262064
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262064
[    0.000000] On node 0 totalpages: 262064
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32433 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FAC60 checksum 0
[    0.000000] ACPI: RSDP 000FAC60, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FFB0000, 0030 (r1 A M I  OEMRSDT  10000505 MSFT       97)
[    0.000000] ACPI: FACP 3FFB0200, 0084 (r2 A M I  OEMFACP  10000505 MSFT       97)
[    0.000000] ACPI: DSDT 3FFB03F0, 46B2 (r1  A0347 A0347001        1 INTL  2002026)
[    0.000000] ACPI: FACS 3FFBE000, 0040
[    0.000000] ACPI: APIC 3FFB0390, 005C (r1 A M I  OEMAPIC  10000505 MSFT       97)
[    0.000000] ACPI: OEMB 3FFBE040, 0046 (r1 A M I  AMI_OEM  10000505 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:15 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260017
[    0.000000] Kernel command line: root=UUID=8a48e06f-755d-423c-b1a4-4bdc2e14cc12 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2200.113 MHz processor.
[   27.913194] Console: colour VGA+ 80x25
[   27.913197] console [tty0] enabled
[   27.913496] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.913836] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.930551] Memory: 1026612k/1048256k available (2067k kernel code, 20908k reserved, 968k data, 360k init, 130752k highmem)
[   27.930558] virtual kernel memory layout:
[   27.930559]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
[   27.930560]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.930561]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.930562]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.930563]       .init : 0xc03fa000 - 0xc0454000   ( 360 kB)
[   27.930564]       .data : 0xc0304fb4 - 0xc03f73a4   ( 968 kB)
[   27.930565]       .text : 0xc0100000 - 0xc0304fb4   (2067 kB)
[   27.930567] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.930603] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   28.010555] Calibrating delay using timer specific routine.. 4402.97 BogoMIPS (lpj=8805941)
[   28.010575] Security Framework initialized
[   28.010580] SELinux:  Disabled at boot.
[   28.010590] AppArmor: AppArmor initialized
[   28.010593] Failure registering capabilities with primary security module.
[   28.010598] Mount-cache hash table entries: 512
[   28.010682] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[   28.010689] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.010691] CPU: L2 Cache: 512K (64 bytes/line)
[   28.010693] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[   28.010700] Compat vDSO mapped to ffffe000.
[   28.010707] CPU: AMD Athlon(tm) 64 Processor 3500+ stepping 02
[   28.010711] Checking 'hlt' instruction... OK.
[   28.027532] Freeing SMP alternatives: 0k freed
[   28.027619] Early unpacking initramfs... done
[   28.322480] ACPI: Core revision 20070126
[   28.322524] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.324323] ENABLING IO-APIC IRQs
[   28.324491] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   28.470248] net_namespace: 64 bytes
[   28.470253] Booting paravirtualized kernel on bare hardware
[   28.470648] Time:  8:22:09  Date: 05/07/08
[   28.470664] NET: Registered protocol family 16
[   28.470778] EISA bus registered
[   28.470807] ACPI: bus type pci registered
[   28.471481] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   28.471482] PCI: Using configuration type 1
[   28.471484] Setting up standard PCI resources
[   28.477505] ACPI: EC: Look up EC in DSDT
[   28.480474] ACPI: Interpreter enabled
[   28.480476] ACPI: (supports S0 S1 S3 S4 S5)
[   28.480487] ACPI: Using IOAPIC for interrupt routing
[   28.486471] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.487581] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.487694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   28.487759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   28.487823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7.P7P9._PRT]
[   28.487886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7.P7P8._PRT]
[   28.500312] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   28.500399] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   28.500485] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   28.500573] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   28.500658] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   28.500743] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   28.500828] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   28.500913] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   28.500990] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  D7, should be CA [20070126]
[   28.500995] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.501013] pnp: PnP ACPI init
[   28.501019] ACPI: bus type pnp registered
[   28.504075] pnp: PnP ACPI: found 15 devices
[   28.504077] ACPI: ACPI bus type pnp unregistered
[   28.504080] PnPBIOS: Disabled by ACPI PNP
[   28.504212] PCI: Using ACPI for IRQ routing
[   28.504215] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.522137] NET: Registered protocol family 8
[   28.522139] NET: Registered protocol family 20
[   28.522180] AppArmor: AppArmor Filesystem Enabled
[   28.526113] Time: tsc clocksource has been installed.
[   28.534130] system 00:07: ioport range 0x290-0x297 has been reserved
[   28.534134] system 00:08: ioport range 0x3e0-0x3e7 has been reserved
[   28.534137] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   28.534139] system 00:08: ioport range 0x800-0x87f has been reserved
[   28.534141] system 00:08: ioport range 0x400-0x41f has been reserved
[   28.534144] system 00:08: iomem range 0xff780000-0xffffffff could not be reserved
[   28.534146] system 00:08: iomem range 0xf0000000-0xf7ffffff has been reserved
[   28.534150] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   28.534153] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[   28.534158] system 00:0d: iomem range 0xe0000000-0xefffffff could not be reserved
[   28.534162] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   28.534164] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   28.534167] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   28.534169] system 00:0e: iomem range 0x100000-0x3fffffff could not be reserved
[   28.534171] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   28.564406] PCI: Bridge: 0000:00:01.0
[   28.564407]   IO window: disabled.
[   28.564411]   MEM window: fca00000-feafffff
[   28.564414]   PREFETCH window: 9ff00000-bfefffff
[   28.564417] PCI: Bridge: 0000:02:00.0
[   28.564418]   IO window: disabled.
[   28.564421]   MEM window: disabled.
[   28.564424]   PREFETCH window: disabled.
[   28.564427] PCI: Bridge: 0000:02:00.1
[   28.564428]   IO window: disabled.
[   28.564430]   MEM window: disabled.
[   28.564433]   PREFETCH window: disabled.
[   28.564436] PCI: Bridge: 0000:00:13.0
[   28.564437]   IO window: disabled.
[   28.564440]   MEM window: disabled.
[   28.564442]   PREFETCH window: disabled.
[   28.564457] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   28.564463] PCI: Setting latency timer of device 0000:00:13.0 to 64
[   28.564473] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   28.564484] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   28.564491] NET: Registered protocol family 2
[   28.602090] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.602319] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   28.602980] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   28.603147] TCP: Hash tables configured (established 131072 bind 65536)
[   28.603149] TCP reno registered
[   28.614136] checking if image is initramfs... it is
[   29.065640] Switched to high resolution mode on CPU 0
[   29.189724] Freeing initrd memory: 8089k freed
[   29.190104] audit: initializing netlink socket (disabled)
[   29.190114] audit(1210148529.156:1): initialized
[   29.190205] highmem bounce pool size: 64 pages
[   29.191326] VFS: Disk quotas dquot_6.5.1
[   29.191344] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.191429] io scheduler noop registered
[   29.191431] io scheduler anticipatory registered
[   29.191432] io scheduler deadline registered
[   29.191439] io scheduler cfq registered (default)
[   29.191448] PCI: VIA PCI bridge detected. Disabling DAC.
[   29.191508] Boot video device is 0000:01:00.0
[   29.191591] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   29.191615] assign_interrupt_mode Found MSI capability
[   29.191647] Allocate Port Service[0000:02:00.0:pcie00]
[   29.191699] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   29.191722] assign_interrupt_mode Found MSI capability
[   29.191750] Allocate Port Service[0000:02:00.1:pcie00]
[   29.191889] isapnp: Scanning for PnP cards...
[   29.545463] isapnp: No Plug & Play device found
[   29.563810] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   29.563910] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.564392] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   29.564837] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   29.564881] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   29.564940] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   29.565496] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.565499] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.577091] mice: PS/2 mouse device common for all mice
[   29.577159] EISA: Probing bus 0 at eisa.0
[   29.577193] EISA: Detected 0 cards.
[   29.577195] cpuidle: using governor ladder
[   29.577287] NET: Registered protocol family 1
[   29.577305] Using IPI Shortcut mode
[   29.577325] registered taskstats version 1
[   29.577407]   Magic number: 8:188:371
[   29.577546] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   29.577547] EDD information not available.
[   29.577727] Freeing unused kernel memory: 360k freed
[   29.609041] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   30.783402] fuse init (API version 7.9)
[   30.803274] ACPI: Processor [CPU1] (supports 16 throttling states)
[   30.819507] device-mapper: uevent: version 1.0.3
[   30.819538] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   30.835169] md: linear personality registered for level -1
[   30.839760] md: multipath personality registered for level -4
[   30.844139] md: raid0 personality registered for level 0
[   30.849078] md: raid1 personality registered for level 1
[   30.853460] xor: automatically using best checksumming function: pIII_sse
[   30.871781]    pIII_sse  :  6938.000 MB/sec
[   30.871783] xor: using function: pIII_sse (6938.000 MB/sec)
[   30.872895] async_tx: api initialized (async)
[   30.939728] raid6: int32x1    827 MB/s
[   31.007700] raid6: int32x2    873 MB/s
[   31.075606] raid6: int32x4    833 MB/s
[   31.143517] raid6: int32x8    608 MB/s
[   31.211460] raid6: mmxx1     1766 MB/s
[   31.279390] raid6: mmxx2     3288 MB/s
[   31.347338] raid6: sse1x1    1635 MB/s
[   31.415266] raid6: sse1x2    2675 MB/s
[   31.483197] raid6: sse2x1    2737 MB/s
[   31.551119] raid6: sse2x2    3582 MB/s
[   31.551121] raid6: using algorithm sse2x2 (3582 MB/s)
[   31.551123] md: raid6 personality registered for level 6
[   31.551124] md: raid5 personality registered for level 5
[   31.551126] md: raid4 personality registered for level 4
[   31.578997] md: raid10 personality registered for level 10
[   32.130739] SCSI subsystem initialized
[   32.174560] libata version 3.00 loaded.
[   32.177859] ahci 0000:00:0f.0: version 3.0
[   32.177881] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 16
[   32.177918] ahci 0000:00:0f.0: controller can't do NCQ, turning off CAP_NCQ
[   32.177920] ahci 0000:00:0f.0: controller can't do PMP, turning off CAP_PMP
[   32.186560] usbcore: registered new interface driver usbfs
[   32.186579] usbcore: registered new interface driver hub
[   32.194539] usbcore: registered new device driver usb
[   32.195341] USB Universal Host Controller Interface driver v3.0
[   32.234719] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   32.394940] Floppy drive(s): fd0 is 1.44M
[   32.414184] FDC 0 is a post-1991 82077
[   33.177539] ahci 0000:00:0f.0: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   33.177543] ahci 0000:00:0f.0: flags: 64bit pm led clo pio slum part 
[   33.177838] scsi0 : ahci
[   33.178050] scsi1 : ahci
[   33.178147] scsi2 : ahci
[   33.178240] scsi3 : ahci
[   33.178651] ata1: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 221
[   33.178654] ata2: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 221
[   33.178657] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 221
[   33.178659] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 221
[   33.653064] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.809976] APIC error on CPU0: 00(08)
[   63.779434] ata1.00: qc timeout (cmd 0xa1)
[   63.779441] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   63.779443] ata1: failed to recover some devices, retrying in 5 secs
[   69.262045] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   69.418974] APIC error on CPU0: 08(08)
[   99.388432] ata1.00: qc timeout (cmd 0xa1)
[   99.388438] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   99.388441] ata1: failed to recover some devices, retrying in 5 secs
[  104.871037] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  105.027958] APIC error on CPU0: 08(08)
[  134.997416] ata1.00: qc timeout (cmd 0xa1)
[  134.997423] ata1.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[  134.997425] ata1: failed to recover some devices, retrying in 5 secs
[  140.480027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  140.791719] ata2: SATA link down (SStatus 0 SControl 300)
[  141.103412] ata3: SATA link down (SStatus 0 SControl 300)
[  141.415105] ata4: SATA link down (SStatus 0 SControl 300)
[  141.418399] pata_via 0000:00:0f.1: version 0.3.3
[  141.419253] scsi4 : pata_via
[  141.419803] scsi5 : pata_via
[  141.420592] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[  141.420595] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[  141.627623] ata5.00: ATA-7: ST3160811AS, 3.AAE, max UDMA/133
[  141.627626] ata5.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[  141.627636] ata5.00: limited to UDMA/33 due to 40-wire cable
[  141.694185] ata5.00: configured for UDMA/33
[  141.858070] scsi 4:0:0:0: Direct-Access     ATA      ST3160811AS      3.AA PQ: 0 ANSI: 5
[  141.858413] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 17
[  141.858421] uhci_hcd 0000:00:10.0: UHCI Host Controller
[  141.858643] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[  141.858671] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000dc00
[  141.859427] usb usb1: configuration #1 chosen from 1 choice
[  141.859445] hub 1-0:1.0: USB hub found
[  141.859449] hub 1-0:1.0: 2 ports detected
[  141.864502] Driver 'sd' needs updating - please use bus_type methods
[  141.864566] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  141.864575] sd 4:0:0:0: [sda] Write Protect is off
[  141.864577] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  141.864589] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  141.864619] sd 4:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[  141.864625] sd 4:0:0:0: [sda] Write Protect is off
[  141.864627] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  141.864636] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  141.864639]  sda: sda1 sda2 < sda5 >
[  141.908634] sd 4:0:0:0: [sda] Attached SCSI disk
[  141.912262] sd 4:0:0:0: Attached scsi generic sg0 type 0
[  141.962652] ACPI: PCI Interrupt 0000:00:10.1[C] -> GSI 22 (level, low) -> IRQ 18
[  141.962661] uhci_hcd 0000:00:10.1: UHCI Host Controller
[  141.962678] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[  141.962700] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000d880
[  141.962777] usb usb2: configuration #1 chosen from 1 choice
[  141.962793] hub 2-0:1.0: USB hub found
[  141.962796] hub 2-0:1.0: 2 ports detected
[  142.066615] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 16
[  142.066625] uhci_hcd 0000:00:10.2: UHCI Host Controller
[  142.066641] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[  142.066665] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000d800
[  142.066740] usb usb3: configuration #1 chosen from 1 choice
[  142.066758] hub 3-0:1.0: USB hub found
[  142.066761] hub 3-0:1.0: 2 ports detected
[  142.170463] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 19
[  142.170472] uhci_hcd 0000:00:10.3: UHCI Host Controller
[  142.170489] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[  142.170511] uhci_hcd 0000:00:10.3: irq 19, io base 0x0000d480
[  142.170591] usb usb4: configuration #1 chosen from 1 choice
[  142.170607] hub 4-0:1.0: USB hub found
[  142.170611] hub 4-0:1.0: 2 ports detected
[  142.228189] EXT3-fs: INFO: recovery required on readonly filesystem.
[  142.228192] EXT3-fs: write access will be enabled during recovery.
[  142.274414] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 22 (level, low) -> IRQ 18
[  142.274424] ehci_hcd 0000:00:10.4: EHCI Host Controller
[  142.274444] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[  142.274473] ehci_hcd 0000:00:10.4: debug port 1
[  142.274479] ehci_hcd 0000:00:10.4: irq 18, io mem 0xfebff800
[  142.330230] usb 1-2: new full speed USB device using uhci_hcd and address 2
[  142.342193] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[  142.342284] usb usb5: configuration #1 chosen from 1 choice
[  142.342301] hub 5-0:1.0: USB hub found
[  142.342306] hub 5-0:1.0: 8 ports detected
[  142.446260] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 19
[  142.446444] eth0: VIA Rhine II at 0xfebff400, 00:15:f2:2e:ab:50, IRQ 19.
[  142.447152] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[  142.482278] kjournald starting.  Commit interval 5 seconds
[  142.482290] EXT3-fs: sda1: orphan cleanup on readonly fs
[  142.505359] ext3_orphan_cleanup: deleting unreferenced inode 7667746
[  142.550348] ext3_orphan_cleanup: deleting unreferenced inode 7914380
[  142.559765] ext3_orphan_cleanup: deleting unreferenced inode 7914377
[  142.565359] ext3_orphan_cleanup: deleting unreferenced inode 7914551
[  142.568547] ext3_orphan_cleanup: deleting unreferenced inode 7914510
[  142.589293] ext3_orphan_cleanup: deleting unreferenced inode 7324776
[  142.602804] ext3_orphan_cleanup: deleting unreferenced inode 7324864
[  142.614646] ext3_orphan_cleanup: deleting unreferenced inode 7634960
[  142.616810] ext3_orphan_cleanup: deleting unreferenced inode 7634959
[  142.622187] ext3_orphan_cleanup: deleting unreferenced inode 7667938
[  142.647922] ext3_orphan_cleanup: deleting unreferenced inode 2082578
[  142.647949] ext3_orphan_cleanup: deleting unreferenced inode 10502162
[  142.647955] EXT3-fs: sda1: 12 orphan inodes deleted
[  142.647956] EXT3-fs: recovery complete.
[  142.794037] EXT3-fs: mounted filesystem with ordered data mode.
[  144.012552] usb 1-2: new full speed USB device using uhci_hcd and address 3
[  144.200240] usb 1-2: configuration #1 chosen from 1 choice
[  144.452125] usb 3-2: new low speed USB device using uhci_hcd and address 2
[  144.618380] usb 3-2: configuration #1 chosen from 1 choice
[  144.859719] usb 4-2: new low speed USB device using uhci_hcd and address 2
[  145.049916] usb 4-2: configuration #1 chosen from 1 choice
[  155.797917] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  155.801872] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  155.844785] Linux agpgart interface v0.102
[  155.849956] agpgart: Detected AGP bridge 0
[  155.857539] Real Time Clock Driver v1.12ac
[  155.857584] agpgart: AGP aperture is 256M @ 0xd0000000
[  155.927243] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  156.448785] input: Power Button (FF) as /devices/virtual/input/input3
[  156.464322] ACPI: Power Button (FF) [PWRF]
[  156.464427] input: Sleep Button (CM) as /devices/virtual/input/input4
[  156.476301] ACPI: Sleep Button (CM) [SLPB]
[  156.476367] input: Power Button (CM) as /devices/virtual/input/input5
[  156.496280] ACPI: Power Button (CM) [PWRB]
[  157.001252] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 16 (level, low) -> IRQ 20
[  157.204673] parport_pc 00:06: reported by Plug and Play ACPI
[  157.204786] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[  157.974320] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[  158.010969] nvidia: module license 'NVIDIA' taints kernel.
[  158.695829] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0802
[  158.695844] usbcore: registered new interface driver usblp
[  158.713281] usbcore: registered new interface driver hiddev
[  158.730489] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:10.2/usb3/3-2/3-2:1.0/input/input7
[  158.746115] input,hidraw0: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:10.2-2
[  158.759709] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[  158.759895] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[  168.765774] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed
[  168.765781] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: timeout initializing reports
[  168.765838] input: Logitech Logitech Extreme 3D as /devices/pci0000:00/0000:00:10.3/usb4/4-2/4-2:1.0/input/input8
[  168.776225] input,hidraw1: USB HID v1.10 Joystick [Logitech Logitech Extreme 3D] on usb-0000:00:10.3-2
[  168.776239] usbcore: registered new interface driver usbhid
[  168.776242] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  169.121075] lp0: using parport0 (interrupt-driven).
[  169.824387] EXT3 FS on sda1, internal journal
[  171.090044] ip_tables: (C) 2000-2006 Netfilter Core Team
[  171.136736] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  171.453080] PPP generic driver version 2.4.2
[  171.473360] NET: Registered protocol family 17
[  171.505118] NET: Registered protocol family 10
[  171.505269] lo: Disabled Privacy Extensions
[  172.810271] No dock devices found.
[  173.228725] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[  173.233011] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[  176.822372] ppdev: user-space parallel port driver
[  176.918851] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  176.919251] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  176.919625] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  177.581018] audit(1210148678.567:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=8399 profile="/usr/sbin/cupsd" namespace="default"
[  177.761472] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  177.761476] apm: overridden by ACPI.
[  181.843404] eth0: no IPv6 routers present
[  207.630017] eth0: no IPv6 routers present
[  219.964505] process `skype' is using obsolete setsockopt SO_BSDCOMPAT

---

### Post by joemacnz on 2008-05-14
Please  anyone? My cdrom folder in ./ is empty, I don't know if this is significant

---

### Post by joemacnz on 2008-05-19
Ok, solved like this:

> **bonestonne said:**
> gosh i'd love it if i had bookmarked the page, the solution was posted here somewhere else. lucky for you, i have a habit of writing down millions of notecards with the solutions to this. would printing pages help?

here you go:

when you boot up and you're in Grub, highlight the main Hardy install (with a fresh install its the top one (the other two are a recovery and a memtest).

Press "e" when you highlight the entry on the list.

you'll get to another screen which has a list of 4 entries.
one looks sort of like this:
```
Kernel /boot/vmlinuz-2.6.24-16-generic root=BLAHBLAH
```
(BLAHBLAH is a lot of random stuff, don't worry about what it says exactly)

highlight that line (down arrow to highlight it).

Press "e" again.

you'll now get to a point where you're editing it.

you will see:
```
<b-09f2-4836-93ad-e5a70566438d ro quiet splash
```

now you're in a place where you're editing this. these chages are not permanent at this screen.

at the end, change "ro quiet splash" to "all_generic_ide"

exactly like that, underscores included, but not in quotes.

it should say:
```
<b-09f2-4836-93ad-e5a70566438d all_generic_ide
```
when you're done.

now, press "b". if you hit escape, you'll lose the changes.

you wont see the fancy Ubuntu splash screen, just lots of text. soon it'll get you to the login screen.

now, you need to make the change permanent.

open up terminal (Applications>Accessories>Terminal)

type: "gksu gedit /boot/grub/menu.lst"

this is your grub boot list and menu. you don't want to make a point of playing with this unless you're sure you know what you're doing.

In this file, you will find the same line you just edited:
```
<b-09f2-4836-93ad-e5a70566438d ro quiet splash
```

change that exactly as you did to:
```
<b-09f2-4836-93ad-e5a70566438d all_generic_ide
```

click the save button.

you have fixed your install.

this worked for me, and i wish i was able to find the original poster.

i hope you're able to follow easily, that's exactly how the original instructions had said it.

---

### Post by cim on 2008-05-23
Thanks for this, this helped me!

---

