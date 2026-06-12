---
title: "USB Drive Doesnt Work"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by cafeinoz on 2008-09-12
I just bought a new usb drive and it worked on Ubuntu and windows but after making it a live Ubuntu usb (which didn't work) it now only works on windows.

---

### Post by crazypenguin2008 on 2008-09-12
there is a command to mount a usb drive for linux ill try to find it real fast.

---

### Post by jalirious on 2008-09-12
sudo su
apt-get install gparted
gparted
format/repair

---

### Post by crazypenguin2008 on 2008-09-12
sudo suapt-get install gparted 

gparted format/repair

beat me to it lol

---

### Post by cafeinoz on 2008-09-12
Gparted can not detect any devices

---

### Post by DFlame on 2008-09-12
Plug the drive in, and please post up the outputs of:

```
dmesg
```

and 

```
lsusb
```

from the terminal :)

---

### Post by cafeinoz on 2008-09-12
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517774
[    0.000000] Kernel command line: root=UUID=d5a40d60-2860-499c-9633-47b9c782a87d ro quiet splash vga=786
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.137 MHz processor.
[   30.663616] Console: colour dummy device 80x25
[   30.663619] console [tty0] enabled
[   30.663939] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   30.664266] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.744677] Memory: 2056752k/2087400k available (2176k kernel code, 29304k reserved, 1007k data, 368k init, 1169824k highmem)
[   30.744684] virtual kernel memory layout:
[   30.744684]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   30.744685]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.744686]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   30.744687]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   30.744688]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   30.744689]       .data : 0xc0320134 - 0xc041bdc4   (1007 kB)
[   30.744690]       .text : 0xc0100000 - 0xc0320134   (2176 kB)
[   30.744693] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.744735] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   30.744869] hpet clockevent registered
[   30.824831] Calibrating delay using timer specific routine.. 3994.62 BogoMIPS (lpj=7989247)
[   30.824853] Security Framework initialized
[   30.824859] SELinux:  Disabled at boot.
[   30.824872] AppArmor: AppArmor initialized
[   30.824876] Failure registering capabilities with primary security module.
[   30.824883] Mount-cache hash table entries: 512
[   30.825004] Initializing cgroup subsys ns
[   30.825010] Initializing cgroup subsys cpuacct
[   30.825020] CPU: After generic identify, caps: afebfbff 20100000 00000000 00000000 0000e31d 00000000 00000001 00000000
[   30.825026] monitor/mwait feature present.
[   30.825028] using mwait in idle threads.
[   30.825032] CPU: L1 I cache: 32K, L1 D cache: 32K
[   30.825034] CPU: L2 cache: 1024K
[   30.825037] CPU: After all inits, caps: afebfbff 20100000 00000000 00003940 0000e31d 00000000 00000001 00000000
[   30.825046] Compat vDSO mapped to ffffe000.
[   30.825058] Checking 'hlt' instruction... OK.
[   30.841188] SMP alternatives: switching to UP code
[   30.842605] Freeing SMP alternatives: 11k freed
[   30.842694] Early unpacking initramfs... done
[   31.152306] ACPI: Core revision 20070126
[   31.152354] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   31.201386] CPU0: Intel(R) Celeron(R) CPU          550  @ 2.00GHz stepping 01
[   31.201408] Total of 1 processors activated (3994.62 BogoMIPS).
[   31.201600] ENABLING IO-APIC IRQs
[   31.201788] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   31.348575] Brought up 1 CPUs
[   31.348594] CPU0 attaching sched-domain:
[   31.348597]  domain 0: span 01
[   31.348598]   groups: 01
[   31.348728] net_namespace: 64 bytes
[   31.348738] Booting paravirtualized kernel on bare hardware
[   31.349137] Time:  9:28:09  Date: 09/12/08
[   31.349156] NET: Registered protocol family 16
[   31.349313] EISA bus registered
[   31.349318] ACPI: bus type pci registered
[   31.349535] PCI: Using configuration type 1
[   31.349536] Setting up standard PCI resources
[   31.350870] ACPI: EC: Look up EC in DSDT
[   31.373926] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   31.375768] ACPI: Interpreter enabled
[   31.375771] ACPI: (supports S0 S3 S4 S5)
[   31.375784] ACPI: Using IOAPIC for interrupt routing
[   31.377042] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   31.515563] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   31.515565] ACPI: EC: driver started in interrupt mode
[   31.515599] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.516332] PCI quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[   31.516337] PCI quirk: region 0500-053f claimed by ICH6 GPIO
[   31.516942] PCI: Transparent bridge - 0000:00:1e.0
[   31.516975] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.517269] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[   31.517364] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[   31.522372] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[   31.522471] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[   31.522567] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[   31.522662] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[   31.522756] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[   31.522850] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[   31.522944] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[   31.523038] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[   31.523154] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.523180] pnp: PnP ACPI init
[   31.523186] ACPI: bus type pnp registered
[   31.577703] pnp: PnP ACPI: found 9 devices
[   31.577705] ACPI: ACPI bus type pnp unregistered
[   31.577709] PnPBIOS: Disabled by ACPI PNP
[   31.577888] PCI: Using ACPI for IRQ routing
[   31.577891] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.588420] NET: Registered protocol family 8
[   31.588421] NET: Registered protocol family 20
[   31.588452] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   31.588455] hpet0: 3 64-bit timers, 14318180 Hz
[   31.589488] AppArmor: AppArmor Filesystem Enabled
[   31.592399] Time: tsc clocksource has been installed.
[   31.592412] Switched to high resolution mode on CPU 0
[   31.600385] system 00:01: ioport range 0x164e-0x164f has been reserved
[   31.600387] system 00:01: ioport range 0x600-0x60f has been reserved
[   31.600389] system 00:01: ioport range 0x610-0x610 has been reserved
[   31.600392] system 00:01: ioport range 0x800-0x80f has been reserved
[   31.600394] system 00:01: ioport range 0x810-0x817 has been reserved
[   31.600395] system 00:01: ioport range 0x400-0x47f has been reserved
[   31.600400] system 00:01: ioport range 0x500-0x53f has been reserved
[   31.600402] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[   31.600405] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   31.600407] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   31.600410] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   31.600412] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   31.600414] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   31.600416] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   31.600419] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   31.630750] PCI: Bridge: 0000:00:1c.0
[   31.630753]   IO window: 2000-2fff
[   31.630759]   MEM window: 91300000-923fffff
[   31.630764]   PREFETCH window: 90000000-90ffffff
[   31.630770] PCI: Bridge: 0000:00:1e.0
[   31.630773]   IO window: 1000-1fff
[   31.630779]   MEM window: 91200000-912fffff
[   31.630783]   PREFETCH window: disabled.
[   31.630816] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 18 (level, low) -> IRQ 16
[   31.630823] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   31.630838] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.630847] NET: Registered protocol family 2
[   31.668375] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.668576] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.669080] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.669418] TCP: Hash tables configured (established 131072 bind 65536)
[   31.669420] TCP reno registered
[   31.680460] checking if image is initramfs... it is
[   32.280256] Freeing initrd memory: 8023k freed
[   32.280418] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[   32.280420] Simple Boot Flag at 0x44 set to 0x1
[   32.280833] audit: initializing netlink socket (disabled)
[   32.280847] audit(1221211689.384:1): initialized
[   32.281022] highmem bounce pool size: 64 pages
[   32.282613] VFS: Disk quotas dquot_6.5.1
[   32.282674] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.282791] io scheduler noop registered
[   32.282793] io scheduler anticipatory registered
[   32.282795] io scheduler deadline registered
[   32.282804] io scheduler cfq registered (default)
[   32.282815] Boot video device is 0000:00:02.0
[   32.283074] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   32.283136] assign_interrupt_mode Found MSI capability
[   32.283188] Allocate Port Service[0000:00:1c.0:pcie00]
[   32.283217] Allocate Port Service[0000:00:1c.0:pcie02]
[   32.283432] isapnp: Scanning for PnP cards...
[   32.637725] isapnp: No Plug & Play device found
[   32.659092] Real Time Clock Driver v1.12ac
[   32.659272] hpet_resources: 0xfed00000 is busy
[   32.659301] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.660343] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.660402] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   32.660487] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   32.696593] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.696597] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.707841] mice: PS/2 mouse device common for all mice
[   32.707933] EISA: Probing bus 0 at eisa.0
[   32.707940] Cannot allocate resource for EISA slot 1
[   32.707941] Cannot allocate resource for EISA slot 2
[   32.707943] Cannot allocate resource for EISA slot 3
[   32.707964] EISA: Detected 0 cards.
[   32.707967] cpuidle: using governor ladder
[   32.707968] cpuidle: using governor menu
[   32.708040] NET: Registered protocol family 1
[   32.708066] Using IPI No-Shortcut mode
[   32.708090] registered taskstats version 1
[   32.708172]   Magic number: 8:797:474
[   32.708249] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   32.708250] EDD information not available.
[   32.708425] Freeing unused kernel memory: 368k freed
[   32.731792] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   32.791839] vesafb: framebuffer at 0x80000000, mapped to 0xf8880000, using 2400k, total 7616k
[   32.791843] vesafb: mode is 640x480x32, linelength=2560, pages=5
[   32.791844] vesafb: scrolling: redraw
[   32.791846] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   32.791934] Console: switching to colour frame buffer device 80x30
[   32.805942] fb0: VESA VGA frame buffer device
[   33.917915] fuse init (API version 7.9)
[   33.934492] Monitor-Mwait will be used to enter C-1 state
[   33.934496] Monitor-Mwait will be used to enter C-2 state
[   33.934498] Monitor-Mwait will be used to enter C-3 state
[   33.934599] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   33.934603] ACPI: Processor [CPU0] (supports 8 throttling states)
[   33.934615] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   33.937746] ACPI: Thermal Zone [TZ01] (63 C)
[   34.430935] usbcore: registered new interface driver usbfs
[   34.430957] usbcore: registered new interface driver hub
[   34.442925] usbcore: registered new device driver usb
[   34.456965] USB Universal Host Controller Interface driver v3.0
[   34.457023] ACPI: PCI Interrupt 0000:00:1d.0[D] -> GSI 21 (level, low) -> IRQ 17
[   34.457033] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   34.457037] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   34.457260] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   34.457295] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00003080
[   34.457415] usb usb1: configuration #1 chosen from 1 choice
[   34.457437] hub 1-0:1.0: USB hub found
[   34.457441] hub 1-0:1.0: 2 ports detected
[   34.518849] 8139too Fast Ethernet driver 0.9.28
[   34.551009] SCSI subsystem initialized
[   34.558890] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 20 (level, low) -> IRQ 18
[   34.558902] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   34.558906] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   34.558925] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   34.558959] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003060
[   34.559063] usb usb2: configuration #1 chosen from 1 choice
[   34.559083] hub 2-0:1.0: USB hub found
[   34.559086] hub 2-0:1.0: 2 ports detected
[   34.590800] libata version 3.00 loaded.
[   34.662851] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 19 (level, low) -> IRQ 19
[   34.662863] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   34.662867] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   34.662887] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   34.662922] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00003040
[   34.663019] usb usb3: configuration #1 chosen from 1 choice
[   34.663038] hub 3-0:1.0: USB hub found
[   34.663042] hub 3-0:1.0: 2 ports detected
[   34.766925] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   34.766939] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   34.766943] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   34.766964] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   34.770875] ehci_hcd 0000:00:1d.7: debug port 1
[   34.770881] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   34.770889] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x92404800
[   34.786693] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.786824] usb usb4: configuration #1 chosen from 1 choice
[   34.786844] hub 4-0:1.0: USB hub found
[   34.786849] hub 4-0:1.0: 6 ports detected
[   34.890822] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 16 (level, low) -> IRQ 21
[   34.890835] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   34.891832] eth0: RealTek RTL8139 at 0x1000, 00:1e:ec:15:14:da, IRQ 21
[   34.891835] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   34.893296] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   34.893328] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   34.893340] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   34.893515] ahci 0000:00:1f.2: version 3.0
[   34.893542] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 17 (level, low) -> IRQ 22
[   34.893586] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   34.893588] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   34.894267] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   35.130497] usb 4-5: new high speed USB device using ehci_hcd and address 2
[   35.277666] usb 4-5: configuration #1 chosen from 1 choice
[   35.394351] Clocksource tsc unstable (delta = -1306455128 ns)
[   35.403337] Time: hpet clocksource has been installed.
[   35.406397] usbcore: registered new interface driver libusual
[   35.411868] Initializing USB Mass Storage driver...
[   35.412838] scsi0 : SCSI emulation for USB Mass Storage devices
[   35.413327] usbcore: registered new interface driver usb-storage
[   35.413330] USB Mass Storage support registered.
[   35.413399] usb-storage: device found at 2
[   35.413400] usb-storage: waiting for device to settle before scanning
[   35.436803] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   35.436806] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part 
[   35.436812] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   35.436997] scsi1 : ahci
[   35.437195] scsi2 : ahci
[   35.437314] scsi3 : ahci
[   35.437400] ata1: SATA max UDMA/133 abar m2048@0x92404000 port 0x92404100 irq 222
[   35.437404] ata2: SATA max UDMA/133 abar m2048@0x92404000 port 0x92404180 irq 222
[   35.437407] ata3: SATA max UDMA/133 abar m2048@0x92404000 port 0x92404200 irq 222
[   35.486027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   35.487200] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[   35.487974] ata1.00: ATA-8: Hitachi HTS542580K9SA00, BBBOC32P, max UDMA/100
[   35.487976] ata1.00: 156301488 sectors, multi 16: LBA48 
[   35.489287] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[   35.490069] ata1.00: configured for UDMA/100
[   35.496568] ata2: SATA link down (SStatus 0 SControl 0)
[   35.502481] ata3: SATA link down (SStatus 0 SControl 0)
[   35.502585] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54258 BBBO PQ: 0 ANSI: 5
[   35.508011] ata_piix 0000:00:1f.1: version 2.12
[   35.508029] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ 19
[   35.508063] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   35.508426] scsi4 : ata_piix
[   35.508761] scsi5 : ata_piix
[   35.509173] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30a0 irq 14
[   35.509176] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30a8 irq 15
[   35.514531] Driver 'sd' needs updating - please use bus_type methods
[   35.516732] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   35.516743] sd 1:0:0:0: [sda] Write Protect is off
[   35.516745] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.516759] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.516801] sd 1:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   35.516809] sd 1:0:0:0: [sda] Write Protect is off
[   35.516811] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   35.516823] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.516826]  sda: sda1 sda2 < sda5 >
[   35.561421] sd 1:0:0:0: [sda] Attached SCSI disk
[   35.566375] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   35.827858] ata4.00: ATAPI: TSSTcorp CDDVDW TS-L632H, HS02, max MWDMA2
[   35.850814] Attempting manual resume
[   35.850817] swsusp: Resume From Partition 8:5
[   35.850818] PM: Checking swsusp image.
[   35.850965] PM: Resume from disk failed.
[   35.863028] EXT3-fs: INFO: recovery required on readonly filesystem.
[   35.863032] EXT3-fs: write access will be enabled during recovery.
[   35.996894] ata4.00: configured for MWDMA2
[   36.166926] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  HS02 PQ: 0 ANSI: 5
[   36.167000] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[   36.174670] Driver 'sr' needs updating - please use bus_type methods
[   36.198618] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   36.198622] Uniform CD-ROM driver Revision: 3.20
[   36.198676] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   37.205498] kjournald starting.  Commit interval 5 seconds
[   37.205512] EXT3-fs: sda1: orphan cleanup on readonly fs
[   37.205517] ext3_orphan_cleanup: deleting unreferenced inode 2883617
[   37.205533] EXT3-fs: sda1: 1 orphan inode deleted
[   37.205535] EXT3-fs: recovery complete.
[   37.226146] EXT3-fs: mounted filesystem with ordered data mode.
[   38.693178] usb-storage: device scan complete
[   38.699421] scsi 0:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   38.700685] sd 0:0:0:0: [sdb] Attached SCSI removable disk
[   38.700714] sd 0:0:0:0: Attached scsi generic sg2 type 0
[   47.513334] Linux agpgart interface v0.102
[   47.561084] agpgart: Detected an Intel 965GM Chipset.
[   47.561337] agpgart: Detected 7676K stolen memory.
[   47.657038] agpgart: AGP aperture is 256M @ 0x80000000
[   47.812913] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.868924] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.120838] input: Power Button (FF) as /devices/virtual/input/input2
[   48.132666] ACPI: Power Button (FF) [PWRF]
[   48.132774] input: Power Button (CM) as /devices/virtual/input/input3
[   48.148646] ACPI: Power Button (CM) [PWRB]
[   48.148729] input: Lid Switch as /devices/virtual/input/input4
[   48.148788] ACPI: Lid Switch [LID0]
[   48.148841] input: Sleep Button (CM) as /devices/virtual/input/input5
[   48.164654] ACPI: Sleep Button (CM) [SLPB]
[   48.236710] ACPI: AC Adapter [AC] (on-line)
[   48.342894] ath_hal: module license 'Proprietary' taints kernel.
[   48.390143] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   48.390883] ACPI: Battery Slot [BAT0] (battery present)
[   48.390936] ACPI: WMI-Acer: Mapper loaded
[   48.564441] wlan: 0.9.4
[   48.632702] ath_pci: 0.9.4
[   48.633338] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   48.633355] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   48.681838] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   48.681854] ACPI: PCI interrupt for device 0000:01:00.0 disabled
[   48.904583] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   48.916179] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   49.352130] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   49.352159] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   49.679736] iTCO_vendor_support: vendor-support=0
[   49.707718] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   49.707839] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0460)
[   49.707888] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   50.247673] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   51.073221] input: PS/2 Mouse as /devices/virtual/input/input8
[   51.128046] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
[   52.189688] lp: driver loaded but no devices found
[   52.355465] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   52.841856] EXT3 FS on sda1, internal journal
[   52.952239] device-mapper: uevent: version 1.0.3
[   52.952264] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   53.600361] ip_tables: (C) 2000-2006 Netfilter Core Team
[   54.017011] No dock devices found.
[   55.191417] apm: BIOS not found.
[   55.316257] ppdev: user-space parallel port driver
[   55.473622] audit(1221211717.308:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5034 profile="/usr/sbin/cupsd" namespace="default"
[   57.290649] eth0: link down
[   57.386505] Bluetooth: Core ver 2.11
[   57.386996] NET: Registered protocol family 31
[   57.386999] Bluetooth: HCI device and connection manager initialized
[   57.387002] Bluetooth: HCI socket layer initialized
[   57.426128] Bluetooth: L2CAP ver 2.9
[   57.426132] Bluetooth: L2CAP socket layer initialized
[   57.510335] Bluetooth: RFCOMM socket layer initialized
[   57.510532] Bluetooth: RFCOMM TTY layer initialized
[   57.510535] Bluetooth: RFCOMM ver 1.8
[   59.368160] [drm] Initialized drm 1.1.0 20060810
[   59.370773] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 21
[   59.370781] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   59.370844] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   66.953862] NET: Registered protocol family 10
[   66.954231] lo: Disabled Privacy Extensions
[   66.954656] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.121616] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   74.271678] usb 2-1: configuration #1 chosen from 1 choice
[   74.425015] prism2usb_init: prism2_usb.o: 0.2.8 Loaded
[   74.425020] prism2usb_init: dev_info is: prism2_usb
[   75.882698] ident: nic h/w: id=0x8026 1.0.0
[   75.883700] ident: pri f/w: id=0x15 1.1.3
[   75.884700] ident: sta f/w: id=0x1f 1.7.0
[   75.885697] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[   75.886696] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[   75.887695] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[   75.888696] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/12
[   75.889694] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[   75.890694] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[   75.891692] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[   75.892694] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[   75.896711] usbcore: registered new interface driver prism2_usb
[   76.294473] linkstatus=DISCONNECTED (unhandled)
[   76.298017] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.674276] linkstatus=CONNECTED
[   76.682619] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   77.847348] usb 4-2: new high speed USB device using ehci_hcd and address 4
[   77.982396] usb 4-2: configuration #1 chosen from 1 choice
[   77.990474] scsi6 : SCSI emulation for USB Mass Storage devices
[   77.995269] usb-storage: device found at 4
[   77.995274] usb-storage: waiting for device to settle before scanning
[   82.997340] usb-storage: device scan complete
[   87.258730] wlan0: no IPv6 routers present
[   88.605925] usb 4-2: reset high speed USB device using ehci_hcd and address 4
[  103.712715] usb 4-2: device descriptor read/64, error -110
[  118.919464] usb 4-2: device descriptor read/64, error -110
[  119.135341] usb 4-2: reset high speed USB device using ehci_hcd and address 4
[  126.439932] linkstatus=DISCONNECTED (unhandled)
[  126.809712] linkstatus=CONNECTED
[  126.817064] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  132.303545] usb 4-2: USB disconnect, address 4
[  132.303658] scsi 6:0:0:0: Device offlined - not ready after error recovery
[  135.402459] wlan0: no IPv6 routers present
[  403.103002] usb 4-2: new high speed USB device using ehci_hcd and address 5
[  403.235959] usb 4-2: configuration #1 chosen from 1 choice
[  403.262887] scsi7 : SCSI emulation for USB Mass Storage devices
[  403.263178] usb-storage: device found at 5
[  403.263180] usb-storage: waiting for device to settle before scanning
[  406.089643] usb-storage: device scan complete
[  411.634982] usb 4-2: reset high speed USB device using ehci_hcd and address 5
[  424.788516] linkstatus=DISCONNECTED (unhandled)
[  426.512550] linkstatus=CONNECTED
[  426.519926] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  426.737739] usb 4-2: device descriptor read/64, error -110
[  433.358509] NET: Registered protocol family 17
[  433.648617] linkstatus=DISCONNECTED (unhandled)
[  434.101379] linkstatus=CONNECTED
[  436.815600] wlan0: no IPv6 routers present
[  439.269518] linkstatus=DISCONNECTED (unhandled)
[  441.040466] linkstatus=CONNECTED
[  441.047917] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  441.944482] usb 4-2: device descriptor read/64, error -110
[  442.160355] usb 4-2: reset high speed USB device using ehci_hcd and address 5
[  449.365970] linkstatus=DISCONNECTED (unhandled)
[  451.406743] linkstatus=CONNECTED
[  451.414160] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  457.263163] usb 4-2: device descriptor read/64, error -110
[  465.890836] wlan0: no IPv6 routers present
[  472.463596] usb 4-2: device descriptor read/64, error -110
[  472.679327] usb 4-2: reset high speed USB device using ehci_hcd and address 5
[  482.940973] usb 4-2: device not accepting address 5, error -110
[  482.962634] usb 4-2: reset high speed USB device using ehci_hcd and address 5
[  493.359061] usb 4-2: device not accepting address 5, error -110
[  493.359185] usb 4-2: USB disconnect, address 5
[  493.359299] scsi 7:0:0:0: Device offlined - not ready after error recovery
[  493.470935] usb 4-2: new high speed USB device using ehci_hcd and address 6
[  508.566196] usb 4-2: device descriptor read/64, error -110
[  523.765332] usb 4-2: device descriptor read/64, error -110
[  523.981102] usb 4-2: new high speed USB device using ehci_hcd and address 7
[  539.014004] usb 4-2: device descriptor read/64, error -110
[  554.185952] usb 4-2: device descriptor read/64, error -110
[  554.401713] usb 4-2: new high speed USB device using ehci_hcd and address 8
[  564.707464] usb 4-2: device not accepting address 8, error -110
[  564.719514] usb 4-2: new high speed USB device using ehci_hcd and address 9
[  575.115928] usb 4-2: device not accepting address 9, error -110
[ 2156.919810] usb 4-1: new high speed USB device using ehci_hcd and address 10
[ 2157.052802] usb 4-1: configuration #1 chosen from 1 choice
[ 2157.058140] scsi8 : SCSI emulation for USB Mass Storage devices
[ 2157.063774] usb-storage: device found at 10
[ 2157.063778] usb-storage: waiting for device to settle before scanning
[ 2162.060844] usb-storage: device scan complete
[ 2162.061345] scsi 8:0:0:0: Direct-Access     Generic  USB Flash Drive  1.00 PQ: 0 ANSI: 2
[ 2162.079159] sd 8:0:0:0: [sdc] 16343041 512-byte hardware sectors (8368 MB)
[ 2162.080354] sd 8:0:0:0: [sdc] Write Protect is off
[ 2162.080359] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 2162.080362] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2162.082932] sd 8:0:0:0: [sdc] 16343041 512-byte hardware sectors (8368 MB)
[ 2162.083427] sd 8:0:0:0: [sdc] Write Protect is off
[ 2162.083430] sd 8:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 2162.083432] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 2162.083436]  sdc: sdc1
[ 2162.087141] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 2162.087180] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 2430.875965] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[ 2430.998166] usb 2-1: USB disconnect, address 2
[ 2433.304745] usb 4-3: new high speed USB device using ehci_hcd and address 11
[ 2433.437642] usb 4-3: configuration #1 chosen from 1 choice
[ 2433.468656] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2433.476652] usb-storage: device found at 11
[ 2433.476656] usb-storage: waiting for device to settle before scanning
[ 2438.473787] usb-storage: device scan complete
[ 2444.082879] usb 4-3: reset high speed USB device using ehci_hcd and address 11
[ 2459.184979] usb 4-3: device descriptor read/64, error -110
[ 2474.391710] usb 4-3: device descriptor read/64, error -110
[ 2474.607577] usb 4-3: reset high speed USB device using ehci_hcd and address 11
[ 2489.710376] usb 4-3: device descriptor read/64, error -110
[ 2504.917111] usb 4-3: device descriptor read/64, error -110
[ 2505.132991] usb 4-3: reset high speed USB device using ehci_hcd and address 11
[ 2515.534650] usb 4-3: device not accepting address 11, error -110
[ 2515.646575] usb 4-3: reset high speed USB device using ehci_hcd and address 11
[ 2526.048334] usb 4-3: device not accepting address 11, error -110
[ 2526.048497] usb 4-3: USB disconnect, address 11
[ 2526.048619] scsi 9:0:0:0: Device offlined - not ready after error recovery
[ 2526.160180] usb 4-3: new high speed USB device using ehci_hcd and address 12
cafeinoz@cafeinoz-laptop:~$ 

lsusb didnt do anything

---

### Post by DFlame on 2008-09-12
I'd suggest reformatting the drive in Windows. Right click it there, hit Format... and set the file system to FAT or FAT32. After that, try it in Ubuntu again.

That's about the only help I can offer for now and I'm leaving the computer. Someone greater than I may be able to offer more insight. Good luck,

DFlame

---

### Post by forger on 2008-09-12
Is it ntfs? What do you have on that usb currently?

If it's ntfs, boot in windows, scandisk and disconnect the drive **properly** (not plain shutdown, but first click the green "arrow" icon in the tray area)

---

