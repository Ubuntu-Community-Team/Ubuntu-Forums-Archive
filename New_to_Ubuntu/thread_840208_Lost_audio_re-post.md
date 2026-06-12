---
title: "Lost audio re-post"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by nnjond on 2008-06-25
Hi, can anyone help me? Something went wrong with this thread and I couldn't carry on with it. So I'm starting again.

My scrn froze while multitasking and had to reboot. Now I have no audio and get this message:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."



nick@nick-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter




nick@nick-desktop:~$ dmesg
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000005dee0000 (usable)
[ 0.000000] BIOS-e820: 000000005dee0000 - 000000005dee3000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000005dee3000 - 000000005def0000 (ACPI data)
[ 0.000000] BIOS-e820: 000000005def0000 - 000000005df00000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[ 0.000000] 606MB HIGHMEM available.
[ 0.000000] 896MB LOWMEM available.
[ 0.000000] found SMP MP-table at 000f3d10
[ 0.000000] Entering add_active_range(0, 0, 384736) 0 entries of 256 used
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0 -> 4096
[ 0.000000] Normal 4096 -> 229376
[ 0.000000] HighMem 229376 -> 384736
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[1] active PFN ranges
[ 0.000000] 0: 0 -> 384736
[ 0.000000] On node 0 totalpages: 384736
[ 0.000000] DMA zone: 32 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 4064 pages, LIFO batch:0
[ 0.000000] Normal zone: 1760 pages used for memmap
[ 0.000000] Normal zone: 223520 pages, LIFO batch:31
[ 0.000000] HighMem zone: 1213 pages used for memmap
[ 0.000000] HighMem zone: 154147 pages, LIFO batch:31
[ 0.000000] Movable zone: 0 pages used for memmap
[ 0.000000] DMI 2.2 present.
[ 0.000000] ACPI: RSDP signature @ 0xC00F7DA0 checksum 0
[ 0.000000] ACPI: RSDP 000F7DA0, 0014 (r0 AWARD )
[ 0.000000] ACPI: RSDT 5DEE3040, 002C (r1 AWARD AWRDACPI 42302E31 AWRD 0)
[ 0.000000] ACPI: FACP 5DEE30C0, 0074 (r1 AWARD AWRDACPI 42302E31 AWRD 0)
[ 0.000000] ACPI: DSDT 5DEE3180, 3BD1 (r1 AWARD AWRDACPI 1000 MSFT 100000E)
[ 0.000000] ACPI: FACS 5DEE0000, 0040
[ 0.000000] ACPI: APIC 5DEE6DC0, 005A (r1 AWARD AWRDACPI 42302E31 AWRD 0)
[ 0.000000] ACPI: PM-Timer IO Port: 0x1008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] Processor #0 15:12 APIC version 16
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] Allocating PCI resources starting at 60000000 (gap: 5df00000:a0d00000)
[ 0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[ 0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[ 0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 381731
[ 0.000000] Kernel command line: root=UUID=d2cde2b7-321f-4db5-888a-eaf52aa5f66d ro quiet splash
[ 0.000000] mapped APIC to ffffb000 (fee00000)
[ 0.000000] mapped IOAPIC to ffffa000 (fec00000)
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] Detected 1599.565 MHz processor.
[ 17.728314] Console: colour VGA+ 80x25
[ 17.728318] console [tty0] enabled
[ 17.728786] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 17.729654] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 17.792297] Memory: 1513420k/1538944k available (2177k kernel code, 24300k reserved, 1006k data, 368k init, 621440k highmem)
[ 17.792306] virtual kernel memory layout:
[ 17.792307] fixmap : 0xfff4b000 - 0xfffff000 ( 720 kB)
[ 17.792308] pkmap : 0xff800000 - 0xffc00000 (4096 kB)
[ 17.792310] vmalloc : 0xf8800000 - 0xff7fe000 ( 111 MB)
[ 17.792311] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
[ 17.792313] .init : 0xc0421000 - 0xc047d000 ( 368 kB)
[ 17.792314] .data : 0xc0320434 - 0xc041bdc4 (1006 kB)
[ 17.792315] .text : 0xc0100000 - 0xc0320434 (2177 kB)
[ 17.792319] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 17.792362] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[ 17.872364] Calibrating delay using timer specific routine.. 3200.96 BogoMIPS (lpj=6401926)
[ 17.872394] Security Framework initialized
[ 17.872402] SELinux: Disabled at boot.
[ 17.872420] AppArmor: AppArmor initialized
[ 17.872425] Failure registering capabilities with primary security module.
[ 17.872434] Mount-cache hash table entries: 512
[ 17.872564] Initializing cgroup subsys ns
[ 17.872568] Initializing cgroup subsys cpuacct
[ 17.872579] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[ 17.872589] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 17.872592] CPU: L2 Cache: 256K (64 bytes/line)
[ 17.872595] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001 00000000
[ 17.872607] Compat vDSO mapped to ffffe000.
[ 17.872619] Checking 'hlt' instruction... OK.
[ 17.888676] SMP alternatives: switching to UP code
[ 17.889922] Freeing SMP alternatives: 11k freed
[ 17.890054] Early unpacking initramfs... done
[ 18.271879] ACPI: Core revision 20070126
[ 18.271938] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[ 18.274312] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
[ 18.274332] Total of 1 processors activated (3200.96 BogoMIPS).
[ 18.274427] ENABLING IO-APIC IRQs
[ 18.274587] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 18.420297] Brought up 1 CPUs
[ 18.420319] CPU0 attaching sched-domain:
[ 18.420322] domain 0: span 01
[ 18.420324] groups: 01
[ 18.420500] net_namespace: 64 bytes
[ 18.420505] Booting paravirtualized kernel on bare hardware
[ 18.420994] Time: 16:15:46 Date: 06/24/08
[ 18.421018] NET: Registered protocol family 16
[ 18.421202] EISA bus registered
[ 18.421223] ACPI: bus type pci registered
[ 18.442522] PCI: PCI BIOS revision 2.10 entry at 0xfa6b0, last bus=1
[ 18.442525] PCI: Using configuration type 1
[ 18.442529] Setting up standard PCI resources
[ 18.444403] ACPI: EC: Look up EC in DSDT
[ 18.447795] ACPI: Interpreter enabled
[ 18.447798] ACPI: (supports S0 S3 S4 S5)
[ 18.447811] ACPI: Using IOAPIC for interrupt routing
[ 18.452340] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 18.452869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 18.476079] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[ 18.476181] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[ 18.476285] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[ 18.476384] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[ 18.476483] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[ 18.476581] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[ 18.476683] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[ 18.476785] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[ 18.476902] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 18.476932] pnp: PnP ACPI init
[ 18.476939] ACPI: bus type pnp registered
[ 18.477155] pnpacpi: exceeded the max number of mem resources: 12
[ 18.479697] pnp: PnP ACPI: found 12 devices
[ 18.479700] ACPI: ACPI bus type pnp unregistered
[ 18.479704] PnPBIOS: Disabled by ACPI PNP
[ 18.479920] PCI: Using ACPI for IRQ routing
[ 18.479923] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
[ 18.492273] NET: Registered protocol family 8
[ 18.492275] NET: Registered protocol family 20
[ 18.492342] AppArmor: AppArmor Filesystem Enabled
[ 18.496233] Time: tsc clocksource has been installed.
[ 18.504269] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[ 18.504273] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[ 18.504276] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[ 18.504279] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[ 18.504283] system 00:00: iomem range 0x5df00000-0x5dffffff has been reserved
[ 18.504286] system 00:00: iomem range 0x5dee0000-0x5defffff could not be reserved
[ 18.504290] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[ 18.504293] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[ 18.504296] system 00:00: iomem range 0x100000-0x5dedffff could not be reserved
[ 18.504300] system 00:00: iomem range 0x5e000000-0x5fffffff has been reserved
[ 18.504303] system 00:00: iomem range 0xffee0000-0xffefffff has been reserved
[ 18.504306] system 00:00: iomem range 0xfffe0000-0xfffeffff has been reserved
[ 18.504314] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[ 18.504317] system 00:02: ioport range 0x800-0x805 has been reserved
[ 18.504320] system 00:02: ioport range 0x290-0x297 has been reserved
[ 18.534706] PCI: Bridge: 0000:00:01.0
[ 18.534709] IO window: d000-dfff
[ 18.534713] MEM window: e8000000-e80fffff
[ 18.534717] PREFETCH window: e0000000-e7ffffff
[ 18.534736] NET: Registered protocol family 2
[ 18.572298] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 18.572625] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 18.573790] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 18.574391] TCP: Hash tables configured (established 131072 bind 65536)
[ 18.574395] TCP reno registered
[ 18.584360] checking if image is initramfs... it is
[ 19.036116] Switched to high resolution mode on CPU 0
[ 19.320175] Freeing initrd memory: 7318k freed
[ 19.320780] audit: initializing netlink socket (disabled)
[ 19.320794] audit(1214324146.424:1): initialized
[ 19.320949] highmem bounce pool size: 64 pages
[ 19.322729] VFS: Disk quotas dquot_6.5.1
[ 19.322805] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 19.322947] io scheduler noop registered
[ 19.322949] io scheduler anticipatory registered
[ 19.322951] io scheduler deadline registered
[ 19.322962] io scheduler cfq registered (default)
[ 19.379952] Boot video device is 0000:01:00.0
[ 19.380202] isapnp: Scanning for PnP cards...
[ 19.733575] isapnp: No Plug & Play device found
[ 19.761701] Real Time Clock Driver v1.12ac
[ 19.761797] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 19.761910] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 19.762040] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 19.762551] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 19.762818] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[ 19.763545] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 19.763611] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 19.763702] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[ 19.763705] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[ 19.763795] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 19.771956] mice: PS/2 mouse device common for all mice
[ 19.772071] EISA: Probing bus 0 at eisa.0
[ 19.772078] Cannot allocate resource for EISA slot 1
[ 19.772088] Cannot allocate resource for EISA slot 4
[ 19.772104] EISA: Detected 0 cards.
[ 19.772107] cpuidle: using governor ladder
[ 19.772109] cpuidle: using governor menu
[ 19.772201] NET: Registered protocol family 1
[ 19.772229] Using IPI No-Shortcut mode
[ 19.772265] registered taskstats version 1
[ 19.772355] Magic number: 12:220:288
[ 19.772383] hash matches device ttyz2
[ 19.772485] hash matches device tty21
[ 19.772513] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 19.772515] EDD information not available.
[ 19.772781] Freeing unused kernel memory: 368k freed
[ 19.799852] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[ 21.059220] fuse init (API version 7.9)
[ 21.078032] ACPI: Fan [FAN] (on)
[ 21.086326] ACPI: Thermal Zone [THRM] (40 C)
[ 21.759411] SCSI subsystem initialized
[ 21.843160] libata version 3.00 loaded.
[ 21.851872] usbcore: registered new interface driver usbfs
[ 21.851895] usbcore: registered new interface driver hub
[ 21.879183] usbcore: registered new device driver usb
[ 21.891155] sis900.c: v1.08.10 Apr. 2 2006
[ 21.891216] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
[ 21.892388] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[ 21.901952] 0000:00:04.0: Using transceiver found at address 1 as default
[ 21.904234] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 16, 00:15:58:3e:c9:c5
[ 21.924102] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 21.924147] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[ 21.924160] ohci_hcd 0000:00:03.0: OHCI Host Controller
[ 21.924394] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[ 21.924411] ohci_hcd 0000:00:03.0: irq 17, io mem 0xe8124000
[ 21.981236] usb usb1: configuration #1 chosen from 1 choice
[ 21.981262] hub 1-0:1.0: USB hub found
[ 21.981271] hub 1-0:1.0: 3 ports detected
[ 22.078760] FDC 0 is a post-1991 82077
[ 22.083191] ACPI: PCI Interrupt 0000:00:03.1[b] -> GSI 21 (level, low) -> IRQ 18
[ 22.083206] ohci_hcd 0000:00:03.1: OHCI Host Controller
[ 22.083229] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[ 22.083244] ohci_hcd 0000:00:03.1: irq 18, io mem 0xe8120000
[ 22.141187] usb usb2: configuration #1 chosen from 1 choice
[ 22.141216] hub 2-0:1.0: USB hub found
[ 22.141225] hub 2-0:1.0: 3 ports detected
[ 22.243113] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 19
[ 22.243127] ohci_hcd 0000:00:03.2: OHCI Host Controller
[ 22.243151] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[ 22.243167] ohci_hcd 0000:00:03.2: irq 19, io mem 0xe8121000
[ 22.301139] usb usb3: configuration #1 chosen from 1 choice
[ 22.301165] hub 3-0:1.0: USB hub found
[ 22.301173] hub 3-0:1.0: 2 ports detected
[ 22.403170] pata_sis 0000:00:02.5: version 0.5.2
[ 22.405176] scsi0 : pata_sis
[ 22.406243] scsi1 : pata_sis
[ 22.406840] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4000 irq 14
[ 22.406843] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4008 irq 15
[ 22.706874] usb 3-1: new low speed USB device using ohci_hcd and address 2
[ 22.751079] ata1.00: ATAPI: TSSTcorpCD/DVDW SH-S162L, TS01, max UDMA/33
[ 22.920895] usb 3-1: configuration #1 chosen from 1 choice
[ 22.942228] usbcore: registered new interface driver hiddev
[ 22.947028] ata1.00: configured for UDMA/33
[ 22.948983] input: A4Tech USB Optical Mouse as /devices/pci0000:00/0000:00:03.2/usb3/3-1/3-1:1.0/input/input2
[ 22.962811] input,hidraw0: USB HID v1.00 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:03.2-1
[ 22.962828] usbcore: registered new interface driver usbhid
[ 22.962832] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 23.208465] ata2.00: ATA-7: ST3160812A, 3.AAD, max UDMA/100
[ 23.208470] ata2.00: 312581808 sectors, multi 16: LBA48 
[ 23.233583] ata2.01: ATA-8: WDC WD2500AAJB-00WGA0, 00.02C01, max UDMA/100
[ 23.233587] ata2.01: 488397168 sectors, multi 16: LBA48 
[ 23.275016] ata2.00: configured for UDMA/100
[ 23.291496] ata2.01: configured for UDMA/100
[ 23.292405] scsi 0:0:0:0: CD-ROM TSSTcorp CD/DVDW SH-S162L TS01 PQ: 0 ANSI: 5
[ 23.292861] scsi 1:0:0:0: Direct-Access ATA ST3160812A 3.AA PQ: 0 ANSI: 5
[ 23.293209] scsi 1:0:1:0: Direct-Access ATA WDC WD2500AAJB-0 00.0 PQ: 0 ANSI: 5
[ 23.294781] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 20
[ 23.294794] ehci_hcd 0000:00:03.3: EHCI Host Controller
[ 23.294827] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[ 23.294867] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[ 23.294878] ehci_hcd 0000:00:03.3: irq 20, io mem 0xe8122000
[ 23.294970] usb 3-1: USB disconnect, address 2
[ 23.306664] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 23.306789] usb usb4: configuration #1 chosen from 1 choice
[ 23.306814] hub 4-0:1.0: USB hub found
[ 23.306821] hub 4-0:1.0: 8 ports detected
[ 23.411029] sata_sis 0000:00:05.0: version 1.0
[ 23.411056] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 21
[ 23.411062] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[ 23.412155] scsi2 : sata_sis
[ 23.413031] scsi3 : sata_sis
[ 23.413086] ata3: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xed00 irq 21
[ 23.413092] ata4: SATA max UDMA/133 cmd 0xeb00 ctl 0xec00 bmdma 0xed08 irq 21
[ 23.722525] ata3: SATA link down (SStatus 0 SControl 3F0)
[ 23.926455] usb 3-1: new low speed USB device using ohci_hcd and address 3
[ 24.042426] ata4: SATA link down (SStatus 0 SControl 3F0)
[ 24.073608] Driver 'sd' needs updating - please use bus_type methods
[ 24.075311] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 24.075325] sd 1:0:0:0: [sda] Write Protect is off
[ 24.075328] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 24.075345] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 24.075394] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 24.075403] sd 1:0:0:0: [sda] Write Protect is off
[ 24.075405] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 24.075420] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 24.075424] sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 24.085753] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[ 24.085759] Uniform CD-ROM driver Revision: 3.20
[ 24.085811] sr 0:0:0:0: Attached scsi CD-ROM sr0
[ 24.096629] sda1 sda2 < sda5 > sda3
[ 24.122114] sd 1:0:0:0: [sda] Attached SCSI disk
[ 24.122923] sd 1:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 24.122936] sd 1:0:1:0: [sdb] Write Protect is off
[ 24.122939] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 24.122956] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 24.123002] sd 1:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 24.123012] sd 1:0:1:0: [sdb] Write Protect is off
[ 24.123014] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 24.123030] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 24.123034] sdb: sdb1
[ 24.125421] sd 1:0:1:0: [sdb] Attached SCSI disk
[ 24.137899] sr 0:0:0:0: Attached scsi generic sg0 type 5
[ 24.137921] sd 1:0:0:0: Attached scsi generic sg1 type 0
[ 24.137939] sd 1:0:1:0: Attached scsi generic sg2 type 0
[ 24.149424] usb 3-1: configuration #1 chosen from 1 choice
[ 24.160508] input: A4Tech USB Optical Mouse as /devices/pci0000:00/0000:00:03.2/usb3/3-1/3-1:1.0/input/input3
[ 24.174436] input,hidraw0: USB HID v1.00 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:03.2-1
[ 24.512050] Attempting manual resume
[ 24.512054] swsusp: Resume From Partition 8:5
[ 24.512057] PM: Checking swsusp image.
[ 24.512235] PM: Resume from disk failed.
[ 24.557687] kjournald starting. Commit interval 5 seconds
[ 24.557702] EXT3-fs: mounted filesystem with ordered data mode.
[ 32.596236] input: PC Speaker as /devices/platform/pcspkr/input/input4
[ 32.778069] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 32.819650] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 32.887536] Linux agpgart interface v0.102
[ 32.941548] agpgart: Detected SiS chipset - id:1888
[ 32.941932] agpgart: AGP aperture is 4M @ 0xd8000000
[ 33.141753] parport_pc 00:0a: reported by Plug and Play ACPI
[ 33.141797] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[ 33.267848] input: Power Button (FF) as /devices/virtual/input/input5
[ 33.281480] ACPI: Power Button (FF) [PWRF]
[ 33.281590] input: Power Button (CM) as /devices/virtual/input/input6
[ 33.299385] ACPI: Power Button (CM) [PWRB]
[ 37.274244] lp0: using parport0 (interrupt-driven).
[ 37.349529] Adding 4457996k swap on /dev/sda5. Priority:-1 extents:1 across:4457996k
[ 37.928121] EXT3 FS on sda1, internal journal
[ 39.146046] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 39.663201] No dock devices found.
[ 40.091103] powernow-k8: Power state transitions not supported
[ 40.130086] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[ 40.928451] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[ 40.928457] apm: overridden by ACPI.
[ 41.046396] ppdev: user-space parallel port driver
[ 41.162667] audit(1214324168.996:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4713 profile="/usr/sbin/cupsd" namespace="default"
[ 42.189943] Bluetooth: Core ver 2.11
[ 42.190634] NET: Registered protocol family 31
[ 42.190640] Bluetooth: HCI device and connection manager initialized
[ 42.190644] Bluetooth: HCI socket layer initialized
[ 42.212487] Bluetooth: L2CAP ver 2.9
[ 42.212493] Bluetooth: L2CAP socket layer initialized
[ 42.283935] Bluetooth: RFCOMM socket layer initialized
[ 42.283954] Bluetooth: RFCOMM TTY layer initialized
[ 42.283956] Bluetooth: RFCOMM ver 1.8
[ 44.044786] eth0: Media Link On 100mbps full-duplex 
[ 46.319970] NET: Registered protocol family 17
[ 49.803268] NET: Registered protocol family 10
[ 49.803835] lo: Disabled Privacy Extensions
[ 59.915323] eth0: no IPv6 routers present
nick@nick-desktop:~$


Re: Lost audio 


Looks like Ubuntu is recognizing your sound card ok, that is good. Let's check if you are a member of the audio group. Run...

$ groups

and see if "audio" is one of the groups you belong to.

nick@nick-desktop:~$ groups

nick adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin

nick@nick-desktop:~$

---

