---
title: "Vodafone 3g modem card"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by fm-1 on 2008-06-10
hi guys im a noobie to ubuntu,but recently today went back to windows because i had issues with installing the vodafone 3g card on ubuntu,i get all packages installed and everything.software is installed and then when i click on it,nothing happens.any help to bring me back to linux

---

### Post by ibutho on 2008-06-10
Hi.

Can you plugin the device and then boot up Linux. After that run Applications -> Accessories -> Terminal and enter the command
```
dmesg
```
Look at the various messages printed on the screen and let us know if there is a section that describes your modem and which device node it is attached (post this info back). Also post back the ouput of running
```
lsusb
```

---

### Post by fm-1 on 2008-06-11
Vodafone

HUAWEI Mobile connect model : E630



Can you plugin the device and then boot up Linux. After that run Applications -> Accessories -> Terminal and enter the command

Code:

dmesg



[    0.000000] ACPI: MCFG 3F7E5A00, 003C (r1 HP     30AA            1 HP          1)
[    0.000000] ACPI: TCPA 3F7E5A3C, 0032 (r2 HP     30AA            1 HP          1)
[    0.000000] ACPI: SSDT 3F7F5078, 033A (r1 HP       HPQPAT        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 3F7F53B2, 01DB (r1 HP      Cpu0Cst     3001 INTL 20050624)
[    0.000000] ACPI: SSDT 3F7F558D, 04E7 (r1 HP        CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:bf400000)
[    0.000000] Built 1 zonelists.  Total pages: 258017
[    0.000000] Kernel command line: root=UUID=556f26d4-4e0b-40e8-b6a6-53b3c0142fc3 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1729.138 MHz processor.
[   12.218783] Console: colour VGA+ 80x25
[   12.219079] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   12.219481] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.252213] Memory: 1019308k/1040192k available (2015k kernel code, 20152k reserved, 916k data, 364k init, 122688k highmem)
[   12.252222] virtual kernel memory layout:
[   12.252224]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   12.252225]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.252226]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   12.252228]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   12.252229]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   12.252230]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   12.252231]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   12.252235] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.252275] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   12.332276] Calibrating delay using timer specific routine.. 3462.11 BogoMIPS (lpj=6924239)
[   12.332306] Security Framework v1.0.0 initialized
[   12.332316] SELinux:  Disabled at boot.
[   12.332330] Mount-cache hash table entries: 512
[   12.332465] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   12.332475] monitor/mwait feature present.
[   12.332477] using mwait in idle threads.
[   12.332482] CPU: L1 I cache: 32K, L1 D cache: 32K
[   12.332484] CPU: L2 cache: 1024K
[   12.332487] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   12.332498] Compat vDSO mapped to ffffe000.
[   12.332511] Checking 'hlt' instruction... OK.
[   12.348403] SMP alternatives: switching to UP code
[   12.348636] Freeing SMP alternatives: 11k freed
[   12.348930] Early unpacking initramfs... done
[   12.697539] ACPI: Core revision 20070126
[   12.697661] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.773391] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08
[   12.773420] Total of 1 processors activated (3462.11 BogoMIPS).
[   12.773616] ENABLING IO-APIC IRQs
[   12.773822] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.920116] Brought up 1 CPUs
[   12.920223] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[   12.920226] Booting paravirtualized kernel on bare hardware
[   12.920315] Time: 19:54:33  Date: 05/10/108
[   12.920337] NET: Registered protocol family 16
[   12.920421] EISA bus registered
[   12.920439] ACPI: bus type pci registered
[   12.921662] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=8
[   12.921664] PCI: Using configuration type 1
[   12.921666] Setting up standard PCI resources
[   12.923354] ACPI: EC: Look up EC in DSDT
[   12.923971] ACPI: EC: GPE=0x16, ports=0x66, 0x62
[   12.952003] ACPI: Interpreter enabled
[   12.952007] ACPI: (supports S0 S3 S4 S5)
[   12.952021] ACPI: Using IOAPIC for interrupt routing
[   12.961700] ACPI: EC: GPE=0x16, ports=0x66, 0x62
[   12.961769] ACPI: PCI Root Bridge [C002] (0000:00)
[   12.961782] PCI: Probing PCI hardware (bus 00)
[   12.962470] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   12.962475] PCI quirk: region 1100-113f claimed by ICH6 GPIO
[   12.963191] PCI: Transparent bridge - 0000:00:1e.0
[   12.963301] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[   12.963634] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C092._PRT]
[   12.963797] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C0FB._PRT]
[   12.995439] ACPI: PCI Interrupt Link [C107] (IRQs 10 *11)
[   12.995666] ACPI: PCI Interrupt Link [C108] (IRQs 10 *11)
[   12.995891] ACPI: PCI Interrupt Link [C109] (IRQs *10 11)
[   12.996117] ACPI: PCI Interrupt Link [C10A] (IRQs *10 11)
[   12.996342] ACPI: PCI Interrupt Link [C123] (IRQs *10 11)
[   12.996566] ACPI: PCI Interrupt Link [C124] (IRQs 10 *11)
[   12.996782] ACPI: PCI Interrupt Link [C125] (IRQs 10 11) *0, disabled.
[   12.996890] ACPI Exception (pci_link-0179): AE_NOT_FOUND, Evaluating _PRS [20070126]
[   12.997100] ACPI: Power Resource [C20F] (on)
[   12.997153] ACPI: Power Resource [C217] (off)
[   12.997272] ACPI: Power Resource [C311] (off)
[   12.997380] ACPI: Power Resource [C312] (off)
[   12.997486] ACPI: Power Resource [C313] (off)
[   12.997592] ACPI: Power Resource [C314] (off)
[   12.997605] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.997617] pnp: PnP ACPI init
[   12.997625] ACPI: bus type pnp registered
[   13.005289] pnp: PnP ACPI: found 11 devices
[   13.005292] ACPI: ACPI bus type pnp unregistered
[   13.005296] PnPBIOS: Disabled by ACPI PNP
[   13.005344] PCI: Using ACPI for IRQ routing
[   13.005347] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.068667] NET: Registered protocol family 8
[   13.068671] NET: Registered protocol family 20
[   13.068727] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   13.068730] pnp: 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   13.068734] pnp: 00:00: iomem range 0x100000-0x3f7fffff could not be reserved
[   13.068742] pnp: 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   13.068745] pnp: 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[   13.068751] pnp: 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   13.068754] pnp: 00:09: ioport range 0x1000-0x107f has been reserved
[   13.068757] pnp: 00:09: ioport range 0x1100-0x113f has been reserved
[   13.068760] pnp: 00:09: ioport range 0x1200-0x121f has been reserved
[   13.068763] pnp: 00:09: iomem range 0xf8000000-0xfbffffff has been reserved
[   13.068767] pnp: 00:09: iomem range 0xfec00000-0xfec000ff could not be reserved
[   13.068770] pnp: 00:09: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   13.068773] pnp: 00:09: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   13.068778] pnp: 00:0a: iomem range 0xfeda0000-0xfedbffff could not be reserved
[   13.068781] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   13.072024] Time: tsc clocksource has been installed.
[   13.099061] PCI: Bridge: 0000:00:1c.0
[   13.099062]   IO window: disabled.
[   13.099069]   MEM window: e8000000-e80fffff
[   13.099073]   PREFETCH window: disabled.
[   13.099081] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[   13.099084]   IO window: 00002000-000020ff
[   13.099089]   IO window: 00002400-000024ff
[   13.099095]   PREFETCH window: 40000000-43ffffff
[   13.099100]   MEM window: 44000000-47ffffff
[   13.099106] PCI: Bridge: 0000:00:1e.0
[   13.099109]   IO window: 2000-2fff
[   13.099115]   MEM window: e8100000-e83fffff
[   13.099120]   PREFETCH window: 40000000-43ffffff
[   13.099152] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.099159] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.099173] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.099191] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 17
[   13.099207] NET: Registered protocol family 2
[   13.136030] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   13.136107] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   13.137366] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   13.137764] TCP: Hash tables configured (established 131072 bind 65536)
[   13.137768] TCP reno registered
[   13.148144] checking if image is initramfs... it is
[   13.599839] Switched to high resolution mode on CPU 0
[   13.836802] Freeing initrd memory: 7349k freed
[   13.837246] audit: initializing netlink socket (disabled)
[   13.837260] audit(1213127673.148:1): initialized
[   13.837330] highmem bounce pool size: 64 pages
[   13.839101] VFS: Disk quotas dquot_6.5.1
[   13.839150] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.839238] io scheduler noop registered
[   13.839240] io scheduler anticipatory registered
[   13.839243] io scheduler deadline registered
[   13.839258] io scheduler cfq registered (default)
[   13.839271] Boot video device is 0000:00:02.0
[   13.839437] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.839494] assign_interrupt_mode Found MSI capability
[   13.839498] Allocate Port Service[0000:00:1c.0:pcie00]
[   13.839529] Allocate Port Service[0000:00:1c.0:pcie02]
[   13.839679] isapnp: Scanning for PnP cards...
[   14.193885] isapnp: No Plug & Play device found
[   14.217638] Real Time Clock Driver v1.12ac
[   14.217755] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.218905] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.219089] input: Macintosh mouse button emulation as /class/input/input0
[   14.219163] PNP: PS/2 Controller [PNP0303:C20C,PNP0f13:C20D] at 0x60,0x64 irq 1,12
[   14.221647] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.222454] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.222460] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.222463] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.222465] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.222468] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.222673] mice: PS/2 mouse device common for all mice
[   14.222864] EISA: Probing bus 0 at eisa.0
[   14.222872] Cannot allocate resource for EISA slot 1
[   14.222875] Cannot allocate resource for EISA slot 2
[   14.222889] Cannot allocate resource for EISA slot 6
[   14.222899] EISA: Detected 0 cards.
[   14.222999] TCP cubic registered
[   14.223014] NET: Registered protocol family 1
[   14.223038] Using IPI No-Shortcut mode
[   14.223261]   Magic number: 12:656:950
[   14.223286]   hash matches device ttya5
[   14.223433]   hash matches device tty7
[   14.223635] Freeing unused kernel memory: 364k freed
[   14.295935] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.432758] AppArmor: AppArmor initialized<5>audit(1213127674.648:2):  type=1505 info="AppArmor initialized" pid=1239
[   15.438496] fuse init (API version 7.8)
[   15.442819] Failure registering capabilities with primary security module.
[   15.446540] ACPI: Transitioning device [C315] to D3
[   15.446543] ACPI: Transitioning device [C315] to D3
[   15.446547] ACPI: Fan [C315] (off)
[   15.446754] ACPI: Transitioning device [C316] to D3
[   15.446756] ACPI: Transitioning device [C316] to D3
[   15.446759] ACPI: Fan [C316] (off)
[   15.446963] ACPI: Transitioning device [C317] to D3
[   15.446965] ACPI: Transitioning device [C317] to D3
[   15.446970] ACPI: Fan [C317] (off)
[   15.447190] ACPI: Transitioning device [C318] to D3
[   15.447192] ACPI: Transitioning device [C318] to D3
[   15.447195] ACPI: Fan [C318] (off)
[   15.455875] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   15.455881] ACPI: Processor [CPU0] (supports 8 throttling states)
[   15.455894] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    3.056000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.056000] ACPI: Thermal Zone [TZ0] (52 C)
[    3.060000] Time: acpi_pm clocksource has been installed.
[    3.072000] ACPI: Thermal Zone [TZ1] (47 C)
[    3.084000] ACPI: Thermal Zone [TZ2] (40 C)
[    3.096000] ACPI: Thermal Zone [TZ3] (23 C)
[    3.096000] ACPI: Thermal Zone [TZ4] (20 C)
[    3.584000] usbcore: registered new interface driver usbfs
[    3.584000] usbcore: registered new interface driver hub
[    3.584000] usbcore: registered new device driver usb
[    3.584000] USB Universal Host Controller Interface driver v3.0
[    3.584000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[    3.584000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.584000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.584000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.584000] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006020
[    3.584000] usb usb1: configuration #1 chosen from 1 choice
[    3.584000] hub 1-0:1.0: USB hub found
[    3.584000] hub 1-0:1.0: 2 ports detected
[    3.688000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
[    3.688000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.688000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.688000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.688000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006040
[    3.688000] usb usb2: configuration #1 chosen from 1 choice
[    3.688000] hub 2-0:1.0: USB hub found
[    3.688000] hub 2-0:1.0: 2 ports detected
[    3.696000] SCSI subsystem initialized
[    3.700000] libata version 2.21 loaded.
[    3.792000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[    3.792000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.792000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.792000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.792000] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00006060
[    3.792000] usb usb3: configuration #1 chosen from 1 choice
[    3.792000] hub 3-0:1.0: USB hub found
[    3.792000] hub 3-0:1.0: 2 ports detected
[    3.896000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 20
[    3.896000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.896000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.896000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.896000] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00006080
[    3.896000] usb usb4: configuration #1 chosen from 1 choice
[    3.896000] hub 4-0:1.0: USB hub found
[    3.896000] hub 4-0:1.0: 2 ports detected
[    4.000000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[    4.000000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.000000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.000000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.000000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.000000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.000000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xe8584000
[    4.004000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.004000] usb usb5: configuration #1 chosen from 1 choice
[    4.004000] hub 5-0:1.0: USB hub found
[    4.004000] hub 5-0:1.0: 8 ports detected
[    4.108000] ata_piix 0000:00:1f.2: version 2.11
[    4.108000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.108000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 21
[    4.108000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.108000] scsi0 : ata_piix
[    4.108000] scsi1 : ata_piix
[    4.108000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000160a0 irq 14
[    4.108000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000160a8 irq 15
[    4.172000] Clocksource tsc unstable (delta = -152082446 ns)
[    4.272000] ata1.00: ATA-7: ST96812AS, 7.24, max UDMA/100
[    4.272000] ata1.00: 117231408 sectors, multi 16: LBA48 
[    4.288000] ata1.00: configured for UDMA/100
[    4.624000] ata2.00: ATAPI: TSSTcorpCDW/DVD TS-L462C, HP10, max MWDMA2
[    4.828000] ata2.00: configured for MWDMA2
[    4.828000] scsi 0:0:0:0: Direct-Access     ATA      ST96812AS        7.24 PQ: 0 ANSI: 5
[    4.848000] scsi 1:0:0:0: CD-ROM            TSSTcorp CDW/DVD TS-L462C HP10 PQ: 0 ANSI: 5
[    4.848000] ACPI: PCI Interrupt 0000:02:06.1[B] -> GSI 19 (level, low) -> IRQ 20
[    4.900000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[e8101000-e81017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.900000] b44.c:v1.01 (Jun 16, 2006)
[    4.900000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 16 (level, low) -> IRQ 16
[    4.904000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:17:08:47:de:54
[    4.916000] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[    4.916000] sd 0:0:0:0: [sda] Write Protect is off
[    4.916000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.916000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.920000] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[    4.920000] sd 0:0:0:0: [sda] Write Protect is off
[    4.920000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.920000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.920000]  sda: sda1 sda2 sda3 < sda5 >
[    5.020000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.024000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.024000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.156000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.156000] Uniform CD-ROM driver Revision: 3.20
[    5.156000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.348000] Attempting manual resume
[    5.348000] swsusp: Resume From Partition 8:5
[    5.348000] PM: Checking swsusp image.
[    5.348000] PM: Resume from disk failed.
[    5.388000] kjournald starting.  Commit interval 5 seconds
[    5.388000] EXT3-fs: mounted filesystem with ordered data mode.
[   13.420000] Linux agpgart interface v0.102 (c) Dave Jones
[   13.460000] agpgart: Detected an Intel 945GM Chipset.
[   13.460000] agpgart: Detected 7932K stolen memory.
[   13.476000] agpgart: AGP aperture is 256M @ 0xd0000000
[   13.572000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.580000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.284000] iTCO_vendor_support: vendor-support=0
[   14.284000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   14.284000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   14.284000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.300000] intel_rng: FWH not detected
[   14.640000] Yenta: CardBus bridge found at 0000:02:06.0 [103c:30aa]
[   14.640000] Yenta: Enabling burst memory read transactions
[   14.640000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   14.640000] Yenta: Routing CardBus interrupts to PCI
[   14.640000] Yenta TI: socket 0000:02:06.0, mfunc 0x01a61b22, devctl 0x64
[   14.736000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x2580b1, caps: 0xa04793/0x300000
[   14.736000] serio: Synaptics pass-through port at isa0060/serio4/input0
[   14.776000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   14.872000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   14.872000] Socket status: 30000820
[   14.872000] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   14.872000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   14.872000] cs: IO port probe 0x2000-0x2fff: clean.
[   14.872000] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe83fffff
[   14.872000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   14.904000] input: PC Speaker as /class/input/input3
[   14.920000] ieee80211_crypt: registered algorithm 'NULL'
[   14.920000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.920000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.972000] bcm43xx driver
[   14.972000] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.972000] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   15.424000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   15.424000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.508000] pccard: CardBus card inserted into slot 0
[   15.548000] cs: IO port probe 0x100-0x3af: clean.
[   15.552000] cs: IO port probe 0x3e0-0x4ff: clean.
[   15.552000] cs: IO port probe 0x820-0x8ff: clean.
[   15.552000] cs: IO port probe 0xc00-0xcf7: clean.
[   15.552000] cs: IO port probe 0xa00-0xaff: clean.
[   15.592000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.336000] si3054: cannot initialize. EXT MID = 0000
[   16.356000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   16.356000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 17
[   16.356000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   16.356000] ohci_hcd 0000:03:00.0: OHCI Host Controller
[   16.356000] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 6
[   16.356000] ohci_hcd 0000:03:00.0: irq 17, io mem 0x44000000
[   16.440000] usb usb6: configuration #1 chosen from 1 choice
[   16.440000] hub 6-0:1.0: USB hub found
[   16.440000] hub 6-0:1.0: 1 port detected
[   16.544000] PCI: Enabling device 0000:03:00.1 (0000 -> 0002)
[   16.544000] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 18 (level, low) -> IRQ 17
[   16.544000] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   16.544000] ohci_hcd 0000:03:00.1: OHCI Host Controller
[   16.544000] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 7
[   16.544000] ohci_hcd 0000:03:00.1: irq 17, io mem 0x44001000
[   16.628000] usb usb7: configuration #1 chosen from 1 choice
[   16.628000] hub 7-0:1.0: USB hub found
[   16.628000] hub 7-0:1.0: 1 port detected
[   17.128000] lp: driver loaded but no devices found
[   17.184000] Adding 1188768k swap on /dev/sda5.  Priority:-1 extents:1 across:1188768k
[   17.596000] EXT3 FS on sda2, internal journal
[   18.364000] usb 6-1: new full speed USB device using ohci_hcd and address 2
[   18.576000] usb 6-1: configuration #1 chosen from 1 choice
[   18.736000] usbcore: registered new interface driver usbserial
[   18.736000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   18.736000] usbcore: registered new interface driver usbserial_generic
[   18.736000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   18.744000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[   18.744000] option 6-1:1.0: GSM modem (1-port) converter detected
[   18.744000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB0
[   18.744000] option 6-1:1.1: GSM modem (1-port) converter detected
[   18.744000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB1
[   18.744000] option 6-1:1.2: GSM modem (1-port) converter detected
[   18.744000] usb 6-1: GSM modem (1-port) converter now attached to ttyUSB2
[   18.744000] usbcore: registered new interface driver option
[   18.744000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[   18.760000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[   18.764000] usbcore: registered new interface driver pl2303
[   18.764000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
[   18.864000] ACPI: Battery Slot [C1B5] (battery present)
[   18.864000] ACPI: Battery Slot [C1B4] (battery absent)
[   18.924000] ACPI: AC Adapter [C1B3] (on-line)
[   18.940000] No dock devices found.
[   18.984000] ACPI: Video Device [C07F] (multi-head: yes  rom: no  post: no)
[   19.084000] input: Power Button (FF) as /class/input/input4
[   19.084000] ACPI: Power Button (FF) [PWRF]
[   19.104000] input: Sleep Button (CM) as /class/input/input5
[   19.104000] ACPI: Sleep Button (CM) [C235]
[   19.116000] input: Lid Switch as /class/input/input6
[   19.116000] ACPI: Lid Switch [C22E]
[   20.456000] ppdev: user-space parallel port driver
[   20.488000] b44: eth0: BUG!  Timeout waiting for bit 00000002 of register 42c to clear.
[   21.200000] audit(1213120494.062:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4789 profile="/usr/sbin/cupsd"
[   21.276000] apm: BIOS not found.
[   21.544000] Failure registering capabilities with primary security module.
[   21.712000] Bluetooth: Core ver 2.11
[   21.712000] NET: Registered protocol family 31
[   21.712000] Bluetooth: HCI device and connection manager initialized
[   21.712000] Bluetooth: HCI socket layer initialized
[   21.732000] Bluetooth: L2CAP ver 2.8
[   21.732000] Bluetooth: L2CAP socket layer initialized
[   21.816000] Bluetooth: RFCOMM socket layer initialized
[   21.816000] Bluetooth: RFCOMM TTY layer initialized
[   21.816000] Bluetooth: RFCOMM ver 1.8
[   25.608000] [drm] Initialized drm 1.1.0 20060810
[   25.612000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.616000] [drm] Initialized i915 1.6.0 20060119 on minor 0

Look at the various messages printed on the screen and let us know if there is a section that describes your modem and which device node it is attached (post this info back). Also post back the ouput of running

Code:

lsusb
lusb output

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 12d1:1001  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

[IMG]http://i191.photobucket.com/albums/z219/fawaazm/Screenshot.png[/IMG]

---

### Post by ibutho on 2008-06-11
It seems like the system recognises the modem and its attached to /dev/ttyUSB0. You need to install a dialer application like gnomeppp, configure the modem and enter details like the dial up number, username and password and then use that to dial out.

---

