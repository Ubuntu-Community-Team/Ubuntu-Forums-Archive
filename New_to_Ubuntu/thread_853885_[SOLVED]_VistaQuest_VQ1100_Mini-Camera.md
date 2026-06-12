---
title: "[SOLVED] VistaQuest VQ1100 Mini-Camera"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-07-09
I own a VistaQuest VQ1100 Mini-Camera with 1.3 Mega pixels.  I am trying to find a way to run it on Ubuntu so I don't need windows like I do now.  I only use windows for my camera and scanner and it seems like a waste to run windows for these two things.  My scanner is in SANE, but the driver does not work correctly.  Any information you could give would be appreciated.

---

### Post by ChameleonDave on 2008-07-09
What do you actually want to do with your camera?  Access its files?  Utilise it as a webcam?

---

### Post by alienexplorers on 2008-07-09
I am just trying to find a program in ubuntu that would let me download the photo's from the camera.  I can not use a smartcard or any other type of memory card since the camera is not able to use them.  I now have to have windows running with acdsee8 running to get the photo's.

---

### Post by cariboo on 2008-07-09
What is the output of dmesg when you plug your camera in?

---

### Post by alienexplorers on 2008-07-09
dmesg gives me the following output:

```
terminator@terminator-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000017ff0000 - 0000000017ff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017ff3000 - 0000000018000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 383MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98288) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98288
[    0.000000]   HighMem     98288 ->    98288
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98288
[    0.000000] On node 0 totalpages: 98288
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 735 pages used for memmap
[    0.000000]   Normal zone: 93457 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI not present or invalid.
[    0.000000] ACPI: RSDP signature @ 0xC00F6AA0 checksum 0
[    0.000000] ACPI: RSDP 000F6AA0, 0014 (r0 VIAVP3)
[    0.000000] ACPI: RSDT 17FF3000, 0028 (r1 AWARD  AWRDACPI 30302E31 AWRD        0)
[    0.000000] ACPI: FACP 17FF3040, 0074 (r1 AWARD  AWRDACPI 30302E31 AWRD        0)
[    0.000000] ACPI: DSDT 17FF30C0, 2205 (r1 AWARD  AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 17FF0000, 0040
[    0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI
[    0.000000] ACPI: acpi=force override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7ff0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 97521
[    0.000000] Kernel command line: root=UUID=2eed7dda-3209-456c-8867-a36d3716088c ro acpi=force combined_mode=libata
[    0.000000] No local APIC present or hardware disabled
[    0.000000] mapped APIC to ffffb000 (0130c000)
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 451.071 MHz processor.
[   30.924746] Console: colour VGA+ 80x25
[   30.924767] console [tty0] enabled
[   30.929298] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.931354] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.989181] Memory: 376964k/393152k available (2177k kernel code, 15576k reserved, 1006k data, 368k init, 0k highmem)
[   30.989323] virtual kernel memory layout:
[   30.989328]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   30.989335]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.989342]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[   30.989349]     lowmem  : 0xc0000000 - 0xd7ff0000   ( 383 MB)
[   30.989355]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   30.989362]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   30.989369]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   30.989924] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.990231] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   31.070376] Calibrating delay using timer specific routine.. 904.22 BogoMIPS (lpj=1808444)
[   31.070658] Security Framework initialized
[   31.070755] SELinux:  Disabled at boot.
[   31.070910] AppArmor: AppArmor initialized
[   31.070994] Failure registering capabilities with primary security module.
[   31.071108] Mount-cache hash table entries: 512
[   31.071832] Initializing cgroup subsys ns
[   31.071922] Initializing cgroup subsys cpuacct
[   31.072030] CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000 00000000
[   31.072085] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)
[   31.072171] CPU: L2 Cache: 256K (32 bytes/line)
[   31.072250] CPU: After all inits, caps: 0080213f 808029bf 00000000 00000002 00000000 00000000 00000000 00000000
[   31.072317] Compat vDSO mapped to ffffe000.
[   31.072417] Checking 'hlt' instruction... OK.
[   31.086531] SMP alternatives: switching to UP code
[   31.090061] Freeing SMP alternatives: 11k freed
[   31.090733] Early unpacking initramfs... done
[   32.782472] ACPI: Core revision 20070126
[   32.782864] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.786707] ACPI: setting ELCR to 0200 (from 0e20)
[   32.787815] CPU0: AMD-K6(tm) 3D+ Processor stepping 01
[   32.787988] SMP motherboard not detected.
[   32.788064] Local APIC not detected. Using dummy APIC emulation.
[   32.788409] Brought up 1 CPUs
[   32.788588] CPU0 attaching sched-domain:
[   32.788602]  domain 0: span 01
[   32.788612]   groups: 01
[   32.789669] net_namespace: 64 bytes
[   32.789759] Booting paravirtualized kernel on bare hardware
[   32.792017] Time:  2:41:44  Date: 07/10/08
[   32.792243] NET: Registered protocol family 16
[   32.793411] EISA bus registered
[   32.793519] ACPI: bus type pci registered
[   32.825672] PCI: PCI BIOS revision 2.10 entry at 0xfb490, last bus=1
[   32.825754] PCI: Using configuration type 1
[   32.825831] Setting up standard PCI resources
[   32.839041] ACPI: EC: Look up EC in DSDT
[   32.846405] ACPI: Interpreter enabled
[   32.846491] ACPI: (supports S0 S1 S5)
[   32.846735] ACPI: Using PIC for interrupt routing
[   32.858960] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   32.859597] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   32.859682] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   32.860604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   32.867240] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   32.868584] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   32.869821] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.871242] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   32.872588] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.872847] pnp: PnP ACPI init
[   32.872946] ACPI: bus type pnp registered
[   32.880575] pnp: PnP ACPI: found 10 devices
[   32.880658] ACPI: ACPI bus type pnp unregistered
[   32.880735] PnPBIOS: Disabled by ACPI PNP
[   32.881961] PCI: Using ACPI for IRQ routing
[   32.882043] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.910194] NET: Registered protocol family 8
[   32.910272] NET: Registered protocol family 20
[   32.910694] AppArmor: AppArmor Filesystem Enabled
[   32.914150] Time: tsc clocksource has been installed.
[   32.922342] system 00:00: iomem range 0xcf800-0xcffff has been reserved
[   32.922430] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   32.922515] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   32.922601] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   32.922688] system 00:00: iomem range 0x17ff0000-0x17ffffff could not be reserved
[   32.922790] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   32.922890] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   32.922975] system 00:00: iomem range 0x100000-0x17feffff could not be reserved
[   32.923093] system 00:02: ioport range 0x3f0-0x3f1 has been reserved
[   32.923176] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   32.955406] PCI: Bridge: 0000:00:01.0
[   32.955489]   IO window: disabled.
[   32.955566]   MEM window: disabled.
[   32.955639]   PREFETCH window: disabled.
[   32.955733] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   32.955788] NET: Registered protocol family 2
[   32.994603] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   32.995777] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   32.996742] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   32.997702] TCP: Hash tables configured (established 16384 bind 16384)
[   32.997787] TCP reno registered
[   33.006969] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   34.430551]  it is
[   36.202084] Freeing initrd memory: 7961k freed
[   36.205464] audit: initializing netlink socket (disabled)
[   36.205614] audit(1215657707.216:1): initialized
[   36.217583] VFS: Disk quotas dquot_6.5.1
[   36.219281] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   36.220102] io scheduler noop registered
[   36.220180] io scheduler anticipatory registered
[   36.220255] io scheduler deadline registered
[   36.220384] io scheduler cfq registered (default)
[   36.220503] PCI: VIA PCI bridge detected. Disabling DAC.
[   36.220586] PCI: Disabling Via external APIC routing
[   36.220700] pci 0000:00:08.0: HCRESET not completed yet!
[   36.220792] pci 0000:00:08.1: HCRESET not completed yet!
[   36.220924] Boot video device is 0000:00:09.0
[   36.222347] isapnp: Scanning for PnP cards...
[   36.577863] isapnp: No Plug & Play device found
[   36.749760] Real Time Clock Driver v1.12ac
[   36.750288] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   36.756373] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   36.756836] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   36.757407] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   36.758236] serio: i8042 KBD port at 0x60,0x64 irq 1
[   36.758328] serio: i8042 AUX port at 0x60,0x64 irq 12
[   36.766098] mice: PS/2 mouse device common for all mice
[   36.766764] EISA: Probing bus 0 at eisa.0
[   36.766877] Cannot allocate resource for EISA slot 4
[   36.766955] Cannot allocate resource for EISA slot 5
[   36.767031] Cannot allocate resource for EISA slot 6
[   36.767121] EISA: Detected 0 cards.
[   36.767198] cpuidle: using governor ladder
[   36.767271] cpuidle: using governor menu
[   36.768066] NET: Registered protocol family 1
[   36.768269] Using IPI No-Shortcut mode
[   36.768472] registered taskstats version 1
[   36.768938]   Magic number: 0:99:662
[   36.769154]   hash matches device ptyed
[   36.769393] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   36.769471] EDD information not available.
[   36.772172] Freeing unused kernel memory: 368k freed
[   36.790160] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   37.782584] fuse init (API version 7.9)
[   37.887814] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   37.888047] ACPI: Processor [CPU0] (supports 2 throttling states)
[   40.120509] SCSI subsystem initialized
[   40.289491] usbcore: registered new interface driver usbfs
[   40.289692] usbcore: registered new interface driver hub
[   40.345376] usbcore: registered new device driver usb
[   40.821287] natsemi dp8381x driver, version 2.1, Sept 11, 2006
[   40.821299]   originally by Donald Becker <becker@scyld.com>
[   40.821306]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[   40.822929] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[   40.823012] PCI: setting IRQ 5 as level-triggered
[   40.823027] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   40.832707] natsemi eth0: NatSemi DP8381[56] at 0xf3000000 (0000:00:0c.0), 00:0f:b5:8a:bf:12, IRQ 5, port TP.
[   40.942984] USB Universal Host Controller Interface driver v3.0
[   40.943411] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   40.943629] uhci_hcd 0000:00:08.0: UHCI Host Controller
[   40.944771] uhci_hcd 0000:00:08.0: new USB bus registered, assigned bus number 1
[   40.944939] uhci_hcd 0000:00:08.0: irq 5, io base 0x0000dc00
[   40.945847] usb usb1: configuration #1 chosen from 1 choice
[   40.946037] hub 1-0:1.0: USB hub found
[   40.946132] hub 1-0:1.0: 2 ports detected
[   41.013163] libata version 3.00 loaded.
[   41.050904] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   41.051008] PCI: setting IRQ 11 as level-triggered
[   41.051022] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   41.051234] uhci_hcd 0000:00:08.1: UHCI Host Controller
[   41.051413] uhci_hcd 0000:00:08.1: new USB bus registered, assigned bus number 2
[   41.051563] uhci_hcd 0000:00:08.1: irq 11, io base 0x0000e000
[   41.052278] usb usb2: configuration #1 chosen from 1 choice
[   41.052458] hub 2-0:1.0: USB hub found
[   41.052551] hub 2-0:1.0: 2 ports detected
[   41.155298] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   41.155402] PCI: setting IRQ 10 as level-triggered
[   41.155417] ACPI: PCI Interrupt 0000:00:08.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   41.155635] ehci_hcd 0000:00:08.2: EHCI Host Controller
[   41.155839] ehci_hcd 0000:00:08.2: new USB bus registered, assigned bus number 3
[   41.156072] ehci_hcd 0000:00:08.2: irq 10, io mem 0xf3001000
[   41.165169] ehci_hcd 0000:00:08.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   41.165811] usb usb3: configuration #1 chosen from 1 choice
[   41.165995] hub 3-0:1.0: USB hub found
[   41.166091] hub 3-0:1.0: 4 ports detected
[   41.270694] pata_via 0000:00:07.1: version 0.3.3
[   41.307026] scsi0 : pata_via
[   41.365105] scsi1 : pata_via
[   41.365398] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[   41.365485] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[   41.577184] ata1.00: ATA-7: MAXTOR STM3402111A, 3.AAJ, max UDMA/100
[   41.577287] ata1.00: 78165360 sectors, multi 16: LBA48 
[   41.660550] ata1.00: configured for UDMA/66
[   41.899422] Floppy drive(s): fd0 is 1.44M
[   41.917647] FDC 0 is a post-1991 82077
[   42.289082] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   42.325278] ata2.00: ATAPI: HL-DT-STDVD-ROM GDR8164B, 0L06, max UDMA/33
[   42.325439] ata2.01: ATAPI: HP DVD Writer 1040r, MH21, max UDMA/66
[   42.325557] ata2.01: limited to UDMA/33 due to 40-wire cable
[   42.467290] usb 1-1: configuration #1 chosen from 1 choice
[   42.497269] ata2.00: configured for UDMA/33
[   42.685204] ata2.01: configured for UDMA/33
[   42.685825] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM340211 3.AA PQ: 0 ANSI: 5
[   42.689859] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8164B 0L06 PQ: 0 ANSI: 5
[   42.691502] scsi 1:0:1:0: CD-ROM            HP       DVD Writer 1040r MH21 PQ: 0 ANSI: 5
[   44.463957] Driver 'sd' needs updating - please use bus_type methods
[   44.469437] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   44.469600] sd 0:0:0:0: [sda] Write Protect is off
[   44.469680] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.469778] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.470122] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   44.470251] sd 0:0:0:0: [sda] Write Protect is off
[   44.470330] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   44.470425] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   44.470536]  sda: sda1 sda2 sda3 sda4
[   44.512724] Driver 'sr' needs updating - please use bus_type methods
[   44.521307] sd 0:0:0:0: [sda] Attached SCSI disk
[   44.560696] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   44.560804] Uniform CD-ROM driver Revision: 3.20
[   44.561094] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   44.561546] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   44.561694] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   44.561978] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   44.569899] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   44.570248] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   50.874733] kjournald starting.  Commit interval 5 seconds
[   50.874873] EXT3-fs: mounted filesystem with ordered data mode.
[   69.976661] Linux agpgart interface v0.102
[   70.189873] agpgart: Detected VIA Apollo MVP3 chipset
[   70.196238] agpgart: AGP aperture is 128M @ 0xe8000000
[   70.303071] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   70.375650] parport_pc: VIA 686A/8231 detected
[   70.375671] parport_pc: probing current configuration
[   70.375704] parport_pc: Current parallel port base: 0x0
[   70.375718] parport_pc: VIA parallel port disabled in BIOS
[   70.448112] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   70.697778] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xe800, speed 1269kHz
[   74.335554] eth0: DSPCFG accepted after 0 usec.
[   74.335666] eth0: link up.
[   74.335771] eth0: Setting full-duplex based on negotiated link capability.
[   75.471130] nvidia: module license 'NVIDIA' taints kernel.
[   77.325736] input: Power Button (FF) as /devices/virtual/input/input2
[   77.337884] ACPI: Power Button (FF) [PWRF]
[   77.338282] input: Power Button (CM) as /devices/virtual/input/input3
[   77.352615] ACPI: Power Button (CM) [PWRB]
[   77.445095] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   78.064119] NET: Registered protocol family 17
[   78.713499] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7A04
[   78.714195] usbcore: registered new interface driver usblp
[   81.540733] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   81.542947] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   81.543338] NVRM: CPU does not support the PAT, falling back to MTRRs.
[   82.221341] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   89.820242] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   89.820354] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   95.893198] lp: driver loaded but no devices found
[   96.971288] EXT3 FS on sda1, internal journal
[   97.922901] device-mapper: uevent: version 1.0.3
[   97.923063] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   99.403053] kjournald starting.  Commit interval 300 seconds
[   99.403487] EXT3 FS on sda2, internal journal
[   99.403512] EXT3-fs: mounted filesystem with ordered data mode.
[   99.577992] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  101.673313] ip_tables: (C) 2000-2006 Netfilter Core Team
[  104.048745] No dock devices found.
[  108.751538] ppdev: user-space parallel port driver
[  109.054558] audit(1215657791.145:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5435 profile="/usr/sbin/cupsd" namespace="default"
[  210.664116] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  210.825488] usb 2-1: configuration #1 chosen from 1 choice
```

And LSUSB gives me this:
```
terminator@terminator-desktop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0c45:8101 Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 03f0:7a04 Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000 
```

---

### Post by ChameleonDave on 2008-07-09
What is the output of "sudo blkid" when the camera is plugged in?

Have you successfully mounted other external media, such as USB flash sticks?

---

### Post by alienexplorers on 2008-07-09
The output of blkid is:

> terminator@terminator-desktop:~$ sudo blkid
[sudo] password for terminator: 
/dev/sda1: UUID="2eed7dda-3209-456c-8867-a36d3716088c" TYPE="ext3" 
/dev/sda2: UUID="64af1f59-71ab-4fc5-b463-092ab5fa4dea" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda3: UUID="F884-CCF8" TYPE="vfat" 
/dev/sda4: TYPE="swap" UUID="56af67af-7b95-43a3-831c-8e778637e77a" 

I have no problems mounting any USB devices.  I use a USB flash card, Scanner and camera (The one in question).

---

### Post by alienexplorers on 2008-07-09
Camera Specifications:

```
Specifications
  Image Sensor       1.3M pixels CMOS Sensor, 1/3-inch
  Lens Specification F 2.8, f =7.3 mm
  Operating System   Microsoft Windows 98SE/ME/2000/XP
  White Balance      Auto
  Exposure Control   Auto
  Flash Strobe       Yes ( Flash Off ,Flash Auto, FlashOn)
  Continuous Picture 3 Pictures
                     VGA 12 fps
  Max Frame Rate &#8211;
                     QVGA 25 fps
  PC Mode
  Still Image
                     SXGA 17 pictures
                     VGA 68 pictures
  Video Capture      AVI frame rate is 7.5 fps and in QVGA mode
  Display            Status LCD
  Interface          USB 1.1
  Storage            Built-in 8MB SDRAM
  Power Source       3 x AAA1.5V Alkaline Batteries (not included)
  Dimension          88 x 27 x 54mm
  Bundled Software   ArcSoft PhotoImpression 5, VideoImpression 2

```

---

### Post by anewguy on 2008-07-10
The usb id starting with 0c45 are all Microdia cameras.  There is a google group trying to work with these in Linux, including a page that talks about a driver:

[http://groups.google.com/group/microdia/web/testing-microdia-driver-draft](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft)


You will need to install GIT and then be able to compile the driver as per the page.

Post back if you have any questions!:)

---

### Post by ChameleonDave on 2008-07-10
As far as I can tell from all my Googling, you cannot make this work as a standard USB mass-storage device.  It uses a proprietary technology that requires the bundled drivers.  No open-source project seems to exist to provide Linux drivers.

I can only suggest trying to run the bundled software in Wine.

Otherwise, I think you just have to give up.

Edit: I spoke too soon!  I should have searched for "Macrodia" instead of just "VistaQuest" and "VQ1100".

---

### Post by alienexplorers on 2008-07-10
My camera is not a web cam, but a regular photo camera.  Not sure if the google drivers would work for it.   How would I go about setting up wine so I can run the normal programs for this camera.  Is there a site with a well written guide to setting up wine.

---

### Post by ChameleonDave on 2008-07-10
I've been reading about other cameras in that series, and they say that they use a special technology so that they can work as webcams.  Even if yours doesn't function as a webcam, it is possible that the idiots who designed it decided to use the same proprietary technology anyway.

To use Wine, just type "wine" before the name of a Windows executable.  For example, use the "cd" command to get to the right directory on the disc, and then run "wine Setup.exe".

I have my doubts about it working in this case, though.  You might have more luck with the drivers from that Google Group.

---

### Post by anewguy on 2008-07-10
I would try the driver in the Google group first.  While it talks about the video cameras, keep in mind this group is focused on Microdia cameras.  A lot of the time, with proprietary communications, the base is the same as they don't feel a need to re-invent the wheel each time.  I personally have hacked some CVS Pharmacy 1-time use digital still cameras and 1-time use digital camcorders to be reusable, and they require some quite unique code to access them.  Someone else had already done the footwork, and I just combined code for each of these into a single GTK based program.  The point is that this code works for several of these types of cameras using the same base - in this case Pure Digital.  Similar results might be found with the driver mentioned, but I have no experience with it so I can't say.  Trying it won't hurt, though.

As for Wine, as long as you have installed it via Synaptics, you should be set to go.  Follow what CameleonDave said above about being in a terminal window and typing "wine" followed by a space and then the name of what you want to do.  I have my doubts about this working in your case, since it needs a really low-level access to the USB, and while I am not sure, I think Wine works with native devices and provides the bridge to Windows applications.  However, try installing (in Wine) the programs you said worked in Windows and give it a try - worst case you'll just need to reboot.

Have fun experimenting - it can get a little aggravating at times, but it is fun and you usually learn more than if something just magically worked.  :)

---

### Post by jess86 on 2010-01-15
I found a vistaquest camcorder at a [win free]("http://www.ezwingame.com/") site there are lots of cool prizes too! it's a good option in case we don't have the money to get it :D

---

