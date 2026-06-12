---
title: "i915 driver: graphics error"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by melrokz on 2008-12-02
When loading Ubuntu, sometimes all i get is a black screen (not the terminal). At times, the login screen comes, at times it does not. When the login screen comes, I pressed Ctrl-alt-F1, did a dmesg > boot.messages and found that the last item is a load of the i915 driver.Now,Ctrl-alt-F1 does not work, same case with graphics. What could be the problem?
My video card is Intel 845GL.
Attached is a copy of my dmesg o/p.
```

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f7f0000 (usable)
[    0.000000]  BIOS-e820: 000000002f7f0000 - 000000002f7f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002f7f3000 - 000000002f800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5350
[    0.000000] Entering add_active_range(0, 0, 194544) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   194544
[    0.000000]   HighMem    194544 ->   194544
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   194544
[    0.000000] On node 0 totalpages: 194544
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1487 pages used for memmap
[    0.000000]   Normal zone: 188961 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6CD0 checksum 0
[    0.000000] ACPI: RSDP 000F6CD0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 2F7F3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 2F7F3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 2F7F30C0, 3C4A (r1 INTELR AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 2F7F0000, 0040
[    0.000000] ACPI: APIC 2F7F6D40, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 2f800000:cf400000)
[    0.000000] Built 1 zonelists.  Total pages: 193025
[    0.000000] Kernel command line: root=UUID=4aefe214-dda3-436d-94d9-389bb5f47ad5 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2394.131 MHz processor.
[   11.053139] Console: colour VGA+ 80x25
[   11.054219] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.055132] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.073446] Memory: 759436k/778176k available (2015k kernel code, 18044k reserved, 916k data, 364k init, 0k highmem)
[   11.073458] virtual kernel memory layout:
[   11.073460]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   11.073461]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.073463]     vmalloc : 0xf0000000 - 0xff7fe000   ( 247 MB)
[   11.073464]     lowmem  : 0xc0000000 - 0xef7f0000   ( 759 MB)
[   11.073465]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   11.073467]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   11.073468]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   11.073472] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.073521] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   11.153414] Calibrating delay using timer specific routine.. 4792.42 BogoMIPS (lpj=9584845)
[   11.153446] Security Framework v1.0.0 initialized
[   11.153452] SELinux:  Disabled at boot.
[   11.153470] Mount-cache hash table entries: 512
[   11.153632] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000
[   11.153644] monitor/mwait feature present.
[   11.153646] using mwait in idle threads.
[   11.153655] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   11.153659] CPU: L2 cache: 1024K
[   11.153662] CPU: Hyper-Threading is disabled
[   11.153665] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000
[   11.153678] Compat vDSO mapped to ffffe000.
[   11.153698] Checking 'hlt' instruction... OK.
[   11.169502] SMP alternatives: switching to UP code
[   11.169695] Freeing SMP alternatives: 11k freed
[   11.170030] Early unpacking initramfs... done
[   11.537178] ACPI: Core revision 20070126
[   11.537253] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.552046] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 03
[   11.552093] Total of 1 processors activated (4792.42 BogoMIPS).
[   11.552232] ENABLING IO-APIC IRQs
[   11.552425] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.696574] Brought up 1 CPUs
[   11.696719] Booting paravirtualized kernel on bare hardware
[   11.696799] Time:  0:27:27  Date: 09/19/108
[   11.696828] NET: Registered protocol family 16
[   11.696947] EISA bus registered
[   11.696963] ACPI: bus type pci registered
[   11.725512] PCI: PCI BIOS revision 2.10 entry at 0xfb4c0, last bus=1
[   11.725515] PCI: Using configuration type 1
[   11.725518] Setting up standard PCI resources
[   11.737429] ACPI: EC: Look up EC in DSDT
[   11.741851] ACPI: Interpreter enabled
[   11.741855] ACPI: (supports S0 S1 S4 S5)
[   11.741884] ACPI: Using IOAPIC for interrupt routing
[   11.747494] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.747503] PCI: Probing PCI hardware (bus 00)
[   11.747973] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   11.747975] * this clock source is slow. If you are sure your timer does not have
[   11.747977] * this bug, please use "acpi_pm_good" to disable the workaround
[   11.748028] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   11.748032] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   11.748343] PCI: Transparent bridge - 0000:00:1e.0
[   11.748372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.748624] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   11.755082] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   11.755218] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   11.755351] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   11.755482] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   11.755615] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   11.755750] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   11.755882] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   11.756016] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   11.756133] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.756146] pnp: PnP ACPI init
[   11.756162] ACPI: bus type pnp registered
[   11.759615] pnp: PnP ACPI: found 14 devices
[   11.759619] ACPI: ACPI bus type pnp unregistered
[   11.759625] PnPBIOS: Disabled by ACPI PNP
[   11.759689] PCI: Using ACPI for IRQ routing
[   11.759693] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.769825] NET: Registered protocol family 8
[   11.769828] NET: Registered protocol family 20
[   11.769915] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
[   11.772405] Time: tsc clocksource has been installed.
[   11.800269] PCI: Bridge: 0000:00:1e.0
[   11.800274]   IO window: c000-cfff
[   11.800280]   MEM window: e0000000-e1ffffff
[   11.800286]   PREFETCH window: 30000000-300fffff
[   11.800302] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   11.800314] NET: Registered protocol family 2
[   11.836352] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.836560] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   11.838687] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.839613] TCP: Hash tables configured (established 131072 bind 65536)
[   11.839617] TCP reno registered
[   11.848552] checking if image is initramfs... it is
[   12.299551] Switched to high resolution mode on CPU 0
[   12.571344] Freeing initrd memory: 7289k freed
[   12.572028] audit: initializing netlink socket (disabled)
[   12.572055] audit(1224376047.088:1): initialized
[   12.574661] VFS: Disk quotas dquot_6.5.1
[   12.574726] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.574861] io scheduler noop registered
[   12.574865] io scheduler anticipatory registered
[   12.574867] io scheduler deadline registered
[   12.574886] io scheduler cfq registered (default)
[   12.574910] Boot video device is 0000:00:02.0
[   12.575193] isapnp: Scanning for PnP cards...
[   12.928951] isapnp: No Plug & Play device found
[   12.960624] Real Time Clock Driver v1.12ac
[   12.960754] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.960858] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.961748] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   12.962762] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.963068] input: Macintosh mouse button emulation as /class/input/input0
[   12.963180] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.966321] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.966331] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.966608] mice: PS/2 mouse device common for all mice
[   12.966753] EISA: Probing bus 0 at eisa.0
[   12.966796] EISA: Detected 0 cards.
[   12.966918] TCP cubic registered
[   12.966933] NET: Registered protocol family 1
[   12.966963] Using IPI No-Shortcut mode
[   12.967147]   Magic number: 12:374:456
[   12.967342]   hash matches device urandom
[   12.967875] Freeing unused kernel memory: 364k freed
[   13.006370] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.210630] AppArmor: AppArmor initialized<5>audit(1224376048.588:2):  type=1505 info="AppArmor initialized" pid=1180
[   14.221431] fuse init (API version 7.8)
[   14.228740] Failure registering capabilities with primary security module.
[   14.241649] ACPI: Fan [FAN] (on)
[   14.248487] ACPI: Processor [CPU0] (supports 2 throttling states)
[   14.250307] ACPI: Thermal Zone [THRM] (44 C)
[   14.866958] usbcore: registered new interface driver usbfs
[   14.866992] usbcore: registered new interface driver hub
[   14.867021] usbcore: registered new device driver usb
[   14.868109] USB Universal Host Controller Interface driver v3.0
[   14.868215] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.868231] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   14.868236] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   14.868487] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   14.868517] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000d800
[   14.868667] usb usb1: configuration #1 chosen from 1 choice
[   14.868702] hub 1-0:1.0: USB hub found
[   14.868712] hub 1-0:1.0: 2 ports detected
[   14.951361] SCSI subsystem initialized
[   14.958943] libata version 2.21 loaded.
[   14.971103] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   14.971119] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   14.971124] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   14.971156] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   14.971189] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   14.971320] usb usb2: configuration #1 chosen from 1 choice
[   14.971356] hub 2-0:1.0: USB hub found
[   14.971366] hub 2-0:1.0: 2 ports detected
[   14.999717] sis900.c: v1.08.10 Apr. 2 2006
[   15.074940] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.074958] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   15.074963] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   15.075004] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   15.075038] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   15.075170] usb usb3: configuration #1 chosen from 1 choice
[   15.075206] hub 3-0:1.0: USB hub found
[   15.075215] hub 3-0:1.0: 2 ports detected
[   15.142790] FDC 0 is a post-1991 82077
[   15.183115] ata_piix 0000:00:1f.1: version 2.11
[   15.183143] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   15.183210] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   15.183330] scsi0 : ata_piix
[   15.183391] scsi1 : ata_piix
[   15.183536] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   15.183541] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   15.346560] ata1.00: ATA-7: SAMSUNG SV0411N, UA100-11, max UDMA/100
[   15.346566] ata1.00: 78242976 sectors, multi 16: LBA48 
[   15.354537] ata1.00: configured for UDMA/100
[   15.673881] ata2.00: ATAPI: SAMSUNG CDRW/DVD SM-352N, TA01, max UDMA/33
[   15.845585] ata2.00: configured for UDMA/33
[   15.845749] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SV0411N  UA10 PQ: 0 ANSI: 5
[   15.846648] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SM-352N TA01 PQ: 0 ANSI: 5
[   15.847127] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   15.847144] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   15.847149] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   15.847319] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   15.847366] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   15.847380] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xe2080000
[   15.851266] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.851648] usb usb4: configuration #1 chosen from 1 choice
[   15.851823] hub 4-0:1.0: USB hub found
[   15.851832] hub 4-0:1.0: 6 ports detected
[   15.870830] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   15.870858] sd 0:0:0:0: [sda] Write Protect is off
[   15.870862] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.870887] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.870971] sd 0:0:0:0: [sda] 78242976 512-byte hardware sectors (40060 MB)
[   15.870985] sd 0:0:0:0: [sda] Write Protect is off
[   15.870989] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.871012] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   15.871018]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10<6>ACPI: PCI Interrupt 0000:01:06.0[A] -> GSI 21 (level, low) -> IRQ 20
[   15.955184] 0000:01:06.0: SiS 900 Internal MII PHY transceiver found at address 1.
[   15.968283] 0000:01:06.0: Using transceiver found at address 1 as default
[   15.969867] eth0: SiS 900 PCI Fast Ethernet at 0xc000, IRQ 20, 00:0d:87:d3:34:6c.
[   15.971504]  sda11 >
[   15.972995] sd 0:0:0:0: [sda] Attached SCSI disk
[   15.978219] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   15.978249] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   15.991964] sr0: scsi3-mmc drive: 1x/52x writer cd/rw xa/form2 cdda tray
[   15.991972] Uniform CD-ROM driver Revision: 3.20
[   15.992050] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   16.700422] Attempting manual resume
[   16.700428] swsusp: Resume From Partition 8:6
[   16.700430] PM: Checking swsusp image.
[   16.700667] PM: Resume from disk failed.
[   23.552043] eth0: Media Link Off
[   24.670309] NET: Registered protocol family 10
[   24.670414] lo: Disabled Privacy Extensions
[   24.670487] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.283655] Linux agpgart interface v0.102 (c) Dave Jones
[   25.302288] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   25.668160] agpgart: Detected an Intel 830M Chipset.
[   25.668543] agpgart: Detected 8060K stolen memory.
[   25.682865] agpgart: AGP aperture is 128M @ 0xd8000000
[   26.053841] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.060453] iTCO_vendor_support: vendor-support=0
[   26.094266] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   26.094361] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   26.094416] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   26.161964] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.169361] intel_rng: FWH not detected
[   26.435518] input: PC Speaker as /class/input/input2
[   26.981910] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   26.981934] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   27.172200] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   27.174842] parport_pc 00:08: reported by Plug and Play ACPI
[   27.174943] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   27.301605] intel8x0_measure_ac97_clock: measured 55624 usecs
[   27.301611] intel8x0: clocking to 48000
[   28.234544] lp0: using parport0 (interrupt-driven).
[   28.293185] Adding 329292k swap on /dev/sda6.  Priority:-1 extents:1 across:329292k
[   34.140476] No dock devices found.
[   34.225034] input: Power Button (FF) as /class/input/input4
[   34.230433] ACPI: Power Button (FF) [PWRF]
[   34.276052] input: Power Button (CM) as /class/input/input5
[   34.281394] ACPI: Power Button (CM) [PWRB]
[   34.327437] input: Sleep Button (CM) as /class/input/input6
[   34.332808] ACPI: Sleep Button (CM) [SLPB]
[   36.380493] ppdev: user-space parallel port driver
[   36.699543] audit(1224356272.133:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4681 profile="/usr/sbin/cupsd"
[   36.978199] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   36.978206] apm: overridden by ACPI.
[   41.884132] dazuko: failed to register
[   42.111804] Failure registering capabilities with primary security module.
[   42.301853] Bluetooth: Core ver 2.11
[   42.302010] NET: Registered protocol family 31
[   42.302013] Bluetooth: HCI device and connection manager initialized
[   42.302018] Bluetooth: HCI socket layer initialized
[   42.318911] Bluetooth: L2CAP ver 2.8
[   42.318917] Bluetooth: L2CAP socket layer initialized
[   42.426250] Bluetooth: RFCOMM socket layer initialized
[   42.426378] Bluetooth: RFCOMM TTY layer initialized
[   42.426382] Bluetooth: RFCOMM ver 1.8
[   44.653175] [drm] Initialized drm 1.1.0 20060810
[   44.696649] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.699804] [drm] Initialized i915 1.6.0 20060119 on minor 0
```

---

