---
title: "Drive recognises CDs but not DVDs"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by tyleritis on 2008-08-27
I can play CDs fine, but neither of my drives will even recognise that there is a DVD in the drive, I just get:

"Unable to mount media. There is probably no media in the drive."

I have the libdvd stuff and w32codecs already. What do I do?

---

### Post by oliviacond on 2008-08-27
can ur cd drive support dvd? izit dvd-rom/dvd-writer?
the hardware must support reading dvd.

---

### Post by Kevbert on 2008-08-27
What's the make and model of the drives ?
Are the drives SATA ?  I've had a similar problem, but PATA/IDE drives work fine.  Have a look at the /var/log/dmesg file and see if you get any errors.  The drive may be marked as a scsi drive (and not sata or pata!)

---

### Post by tyleritis on 2008-09-01
Yes, I have two drives that should play DVDs. I was having trouble with the older one last year when I was running windows so I bought the new one.

The new one that I'm trying to use is LITE-ON DVDRW SOHW- 1633S
The older one is IDE5216CO

Here's what the /var/log/dmesg file says:

[    0.000000] Linux version 2.6.22-15-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Wed Aug 20 18:39:13 UTC 2008 (Ubuntu 2.6.22-15.58-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f56c0
[    0.000000] Entering add_active_range(0, 0, 122864) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   122864
[    0.000000]   HighMem    122864 ->   122864
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   122864
[    0.000000] On node 0 totalpages: 122864
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 927 pages used for memmap
[    0.000000]   Normal zone: 117841 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7170 checksum 0
[    0.000000] ACPI: RSDP 000F7170, 0014 (r0 KM400A)
[    0.000000] ACPI: RSDT 1DFF3000, 002C (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1DFF3040, 0074 (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1DFF30C0, 4168 (r1 KM400A AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1DFF0000, 0040
[    0.000000] ACPI: APIC 1DFF7240, 005A (r1 KM400A AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
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
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] Built 1 zonelists.  Total pages: 121905
[    0.000000] Kernel command line: root=UUID=3010b4c3-6787-46ca-99cc-acc8c155e39f ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1792.406 MHz processor.
[   14.386886] Console: colour VGA+ 80x25
[   14.387388] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.387755] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.405476] Memory: 475660k/491456k available (2016k kernel code, 15236k reserved, 919k data, 364k init, 0k highmem)
[   14.405489] virtual kernel memory layout:
[   14.405490]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.405492]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.405493]     vmalloc : 0xde800000 - 0xff7fe000   ( 527 MB)
[   14.405495]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[   14.405496]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.405498]       .data : 0xc02f8086 - 0xc03dde84   ( 919 kB)
[   14.405499]       .text : 0xc0100000 - 0xc02f8086   (2016 kB)
[   14.405503] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.405558] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   14.485541] Calibrating delay using timer specific routine.. 3588.17 BogoMIPS (lpj=7176354)
[   14.485584] Security Framework v1.0.0 initialized
[   14.485594] SELinux:  Disabled at boot.
[   14.485615] Mount-cache hash table entries: 512
[   14.485801] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   14.485814] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   14.485817] CPU: L2 Cache: 256K (64 bytes/line)
[   14.485821] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   14.485835] Compat vDSO mapped to ffffe000.
[   14.485852] Checking 'hlt' instruction... OK.
[   14.501711] SMP alternatives: switching to UP code
[   14.502047] Freeing SMP alternatives: 11k freed
[   14.502503] Early unpacking initramfs... done
[   14.862453] ACPI: Core revision 20070126
[   14.862583] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.877022] CPU0: AMD Athlon(tm) XP 2200+ stepping 01
[   14.877053] Total of 1 processors activated (3588.17 BogoMIPS).
[   14.877812] ENABLING IO-APIC IRQs
[   14.878120] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.025376] Brought up 1 CPUs
[   15.025609] Booting paravirtualized kernel on bare hardware
[   15.025709] Time:  6:37:35  Date: 08/01/108
[   15.025751] NET: Registered protocol family 16
[   15.025895] EISA bus registered
[   15.025912] ACPI: bus type pci registered
[   15.033687] PCI: PCI BIOS revision 2.10 entry at 0xfb9d0, last bus=1
[   15.033690] PCI: Using configuration type 1
[   15.033693] Setting up standard PCI resources
[   15.044051] ACPI: EC: Look up EC in DSDT
[   15.048318] ACPI: Interpreter enabled
[   15.048328] ACPI: (supports S0 S1 S3 S4 S5)
[   15.048352] ACPI: Using IOAPIC for interrupt routing
[   15.054735] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.054746] PCI: Probing PCI hardware (bus 00)
[   15.055190] PCI quirk: region 0400-047f claimed by vt8235 PM
[   15.055195] PCI quirk: region 5000-500f claimed by vt8235 SMB
[   15.055471] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.076282] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[   15.076441] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[   15.076597] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 *12)
[   15.076752] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 6 7 10 11 12)
[   15.076885] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.077013] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.077140] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.077276] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   15.077448] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[   15.077617] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[   15.077805] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[   15.077972] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[   15.078073] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.078088] pnp: PnP ACPI init
[   15.078102] ACPI: bus type pnp registered
[   15.081652] pnp: PnP ACPI: found 14 devices
[   15.081655] ACPI: ACPI bus type pnp unregistered
[   15.081660] PnPBIOS: Disabled by ACPI PNP
[   15.081740] PCI: Using ACPI for IRQ routing
[   15.081744] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.106441] NET: Registered protocol family 8
[   15.106444] NET: Registered protocol family 20
[   15.106543] pnp: 00:00: iomem range 0xd0000-0xd3fff has been reserved
[   15.106548] pnp: 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   15.106551] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   15.106554] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   15.106562] pnp: 00:02: ioport range 0x400-0x47f has been reserved
[   15.106565] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[   15.109234] Time: tsc clocksource has been installed.
[   15.136942] PCI: Bridge: 0000:00:01.0
[   15.136944]   IO window: disabled.
[   15.136950]   MEM window: dc000000-ddffffff
[   15.136954]   PREFETCH window: d8000000-dbffffff
[   15.136973] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.136988] NET: Registered protocol family 2
[   15.173281] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   15.173363] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   15.173756] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   15.174044] TCP: Hash tables configured (established 16384 bind 16384)
[   15.174047] TCP reno registered
[   15.185397] checking if image is initramfs... it is
[   15.636983] Switched to high resolution mode on CPU 0
[   15.861925] Freeing initrd memory: 7116k freed
[   15.862507] audit: initializing netlink socket (disabled)
[   15.862526] audit(1220251055.092:1): initialized
[   15.864727] VFS: Disk quotas dquot_6.5.1
[   15.864818] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.864953] io scheduler noop registered
[   15.864956] io scheduler anticipatory registered
[   15.864959] io scheduler deadline registered
[   15.864975] io scheduler cfq registered (default)
[   15.864992] PCI: VIA PCI bridge detected. Disabling DAC.
[   15.865055] Boot video device is 0000:01:00.0
[   15.865272] isapnp: Scanning for PnP cards...
[   16.218992] isapnp: No Plug & Play device found
[   16.259150] Real Time Clock Driver v1.12ac
[   16.259278] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.259391] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.260738] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.261840] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.262131] input: Macintosh mouse button emulation as /class/input/input0
[   16.262229] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   16.262232] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   16.512513] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.512747] mice: PS/2 mouse device common for all mice
[   16.512913] EISA: Probing bus 0 at eisa.0
[   16.512940] Cannot allocate resource for EISA slot 5
[   16.512954] EISA: Detected 0 cards.
[   16.513093] TCP cubic registered
[   16.513104] NET: Registered protocol family 1
[   16.513130] Using IPI No-Shortcut mode
[   16.513342]   Magic number: 8:307:619
[   16.513453]   hash matches device ptye9
[   16.513473]   hash matches device ptybc
[   16.514210] Freeing unused kernel memory: 364k freed
[   16.556496] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.763123] AppArmor: AppArmor initialized<5>audit(1220251057.092:2):  type=1505 info="AppArmor initialized" pid=1189
[   17.773784] fuse init (API version 7.8)
[   17.779884] Failure registering capabilities with primary security module.
[   17.800683] ACPI: Fan [FAN] (on)
[   17.806550] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   17.808471] ACPI: Thermal Zone [THRM] (18 C)
[   18.517810] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 16
[   18.568806] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[de014000-de0147ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   18.593755] usbcore: registered new interface driver usbfs
[   18.593795] usbcore: registered new interface driver hub
[   18.593827] usbcore: registered new device driver usb
[   18.594937] USB Universal Host Controller Interface driver v3.0
[   18.595434] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[   18.595438] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   18.595450] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   18.595465] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   18.595734] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   18.595771] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000d400
[   18.595962] usb usb1: configuration #1 chosen from 1 choice
[   18.595997] hub 1-0:1.0: USB hub found
[   18.596011] hub 1-0:1.0: 2 ports detected
[   18.697335] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.697345] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.699390] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   18.699411] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   18.699443] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   18.699471] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d800
[   18.699607] usb usb2: configuration #1 chosen from 1 choice
[   18.699648] hub 2-0:1.0: USB hub found
[   18.699660] hub 2-0:1.0: 2 ports detected
[   18.724767] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   18.803297] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   18.803317] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   18.803353] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   18.803381] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000dc00
[   18.803541] usb usb3: configuration #1 chosen from 1 choice
[   18.803576] hub 3-0:1.0: USB hub found
[   18.803589] hub 3-0:1.0: 2 ports detected
[   18.826861] Floppy drive(s): fd0 is 1.44M
[   18.881170] FDC 0 is a post-1991 82077
[   18.908902] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   18.908927] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   18.908988] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   18.909052] ehci_hcd 0000:00:10.3: irq 17, io mem 0xde015000
[   18.939051] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   18.939079] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.939259] usb usb4: configuration #1 chosen from 1 choice
[   18.939299] hub 4-0:1.0: USB hub found
[   18.939315] hub 4-0:1.0: 6 ports detected
[   19.043468] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   19.043866] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[   19.043869] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   19.043882] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 18
[   19.043897] VP_IDE: chipset revision 6
[   19.043900] VP_IDE: not 100% native mode: will probe irqs later
[   19.043913] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   19.043923]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[   19.043938]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[   19.043949] Probing IDE interface ide0...
[    4.560000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.564000] Time: acpi_pm clocksource has been installed.
[    4.944000] hda: ST340014A, ATA DISK drive
[    5.224000] hdb: ST3200822A, ATA DISK drive
[    5.280000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    5.288000] Probing IDE interface ide1...
[    5.328000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0001080010008fda]
[    5.552000] usb 4-5: new high speed USB device using ehci_hcd and address 3
[    5.820000] usb 4-5: configuration #1 chosen from 1 choice
[    6.060000] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    6.152000] hdc: LITE-ON DVDRW SOHW-1633S, ATAPI CD/DVD-ROM drive
[    6.232000] usb 1-1: configuration #1 chosen from 1 choice
[    6.260000] usbcore: registered new interface driver hiddev
[    6.276000] input: A4Tech USB Optical Mouse as /class/input/input2
[    6.276000] input: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:10.0-1
[    6.276000] usbcore: registered new interface driver usbhid
[    6.276000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    6.936000] hdd: IDE5216CO, ATAPI CD/DVD-ROM drive
[    6.992000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.000000] SCSI subsystem initialized
[    7.008000] libata version 2.21 loaded.
[    7.012000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    7.012000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    7.012000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
[    7.012000] eth0: VIA Rhine II at 0x1ec00, 00:0e:a6:6c:93:72, IRQ 19.
[    7.012000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[    7.024000] hda: max request size: 512KiB
[    7.044000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[    7.048000] hda: cache flushes supported
[    7.048000]  hda: hda1 hda2 < hda5 >
[    7.076000] hdb: max request size: 512KiB
[    7.080000] hdb: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[    7.080000] hdb: cache flushes supported
[    7.080000]  hdb: hdb1 hdb2 < hdb5 >
[    7.120000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.120000] Uniform CD-ROM driver Revision: 3.20
[    7.148000] hdd: ATAPI 40X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.576000] Attempting manual resume
[    7.576000] swsusp: Resume From Partition 3:5
[    7.576000] PM: Checking swsusp image.
[    7.576000] PM: Resume from disk failed.
[    7.624000] kjournald starting.  Commit interval 5 seconds
[    7.624000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.856000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.924000] agpgart: Detected VIA KM400/KM400A chipset
[   21.968000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.980000] agpgart: AGP aperture is 128M @ 0xd0000000
[   21.980000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.640000] irda_init()
[   22.640000] NET: Registered protocol family 23
[   23.232000] input: PC Speaker as /class/input/input3
[   23.256000] parport_pc 00:0a: reported by Plug and Play ACPI
[   23.256000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   23.344000] ieee80211_init: failed to initialize WME (err=-17)
[   23.476000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   23.476000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   23.476000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   23.476000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   23.476000] wmaster0: Selected rate control algorithm 'simple'
[   23.556000] usbcore: registered new interface driver rt73usb
[   24.064000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   24.064000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   24.064000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   24.064000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   24.576000] codec_read: codec 0 is not valid [0xfe0000]
[   24.584000] codec_read: codec 0 is not valid [0xfe0000]
[   24.588000] codec_read: codec 0 is not valid [0xfe0000]
[   24.596000] codec_read: codec 0 is not valid [0xfe0000]
[   25.108000] lp0: using parport0 (interrupt-driven).
[   25.216000] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
[   25.500000] EXT3 FS on hda1, internal journal

---

### Post by Notgone on 2008-09-19
I'm having the same issue with my LITE-ON DVDRW SOHW- 1633S. Is there a utility somewhere that can detect/configure IDE optical drives?

---

