---
title: "how to transfer data off external hdd"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by coolman121$ on 2008-07-16
i have a external 60gb and i would like to find a way to change the format without deleting anything .... i no ubuntu is only compat with fat and such ...

---

### Post by iaculallad on 2008-07-16
> **coolman121$ said:**
> i have a external 60gb and i would like to find a way to change the format without deleting anything .... i no ubuntu is only compat with fat and such ...

Change the format? As in the drive's formated files ystem? You don't need to, if you're using NTFS format, just install the ntfs-3g driver which is needed to mount that drive.

```
sudo apt-get install ntfs-3g
```

---

### Post by SunnyRabbiera on 2008-07-16
right, if you have what is needed it should read a ntfs drive.

---

### Post by coolman121$ on 2008-07-16
it says i already have the latest version but i still cannot mount..
here is the thing that comes up........
Unable to mount the volume 'Local Disk'. then a long list of things that make some sense
 then mount error

---

### Post by phidia on 2008-07-16
After you have tried to mount it and got the error-open a terminal (from Applications>Acessories>terminal) and type dmesg | tail copy & paste the output of that here.

---

### Post by coolman121$ on 2008-07-16
[    0.000000] Detected 1398.857 MHz processor.
[    8.746996] Console: colour VGA+ 80x25
[    8.747001] console [tty0] enabled
[    8.747396] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.747910] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.808474] Memory: 1285812k/1309568k available (2177k kernel code, 22488k reserved, 1006k data, 368k init, 392064k highmem)
[    8.808484] virtual kernel memory layout:
[    8.808486]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.808488]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.808489]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.808491]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.808492]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.808494]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[    8.808495]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[    8.808500] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.808567] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.888594] Calibrating delay using timer specific routine.. 2799.67 BogoMIPS (lpj=5599348)
[    8.888637] Security Framework initialized
[    8.888649] SELinux:  Disabled at boot.
[    8.888670] AppArmor: AppArmor initialized
[    8.888675] Failure registering capabilities with primary security module.
[    8.888686] Mount-cache hash table entries: 512
[    8.888865] Initializing cgroup subsys ns
[    8.888871] Initializing cgroup subsys cpuacct
[    8.888887] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000 00000000
[    8.888901] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.888904] CPU: L2 cache: 2048K
[    8.888908] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000 00000000
[    8.888920] Compat vDSO mapped to ffffe000.
[    8.888938] Checking 'hlt' instruction... OK.
[    8.905035] SMP alternatives: switching to UP code
[    8.907222] Freeing SMP alternatives: 11k freed
[    8.907359] Early unpacking initramfs... done
[    9.342519] ACPI: Core revision 20070126
[    9.342601] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.345405] ACPI: setting ELCR to 0200 (from 0440)
[    9.358924] CPU0: Intel(R) Pentium(R) M processor 1.40GHz stepping 06
[    9.358930] SMP motherboard not detected.
[    9.358933] Local APIC not detected. Using dummy APIC emulation.
[    9.358980] Brought up 1 CPUs
[    9.358998] CPU0 attaching sched-domain:
[    9.359001]  domain 0: span 01
[    9.359004]   groups: 01
[    9.359197] net_namespace: 64 bytes
[    9.359205] Booting paravirtualized kernel on bare hardware
[    9.359738] Time:  1:40:06  Date: 07/17/08
[    9.359766] NET: Registered protocol family 16
[    9.359985] EISA bus registered
[    9.359999] ACPI: bus type pci registered
[    9.361269] PCI: PCI BIOS revision 2.10 entry at 0xfd782, last bus=2
[    9.361272] PCI: Using configuration type 1
[    9.361280] Setting up standard PCI resources
[    9.379606] ACPI: EC: Look up EC in DSDT
[    9.382497] ACPI: Interpreter enabled
[    9.382501] ACPI: (supports S0 S3 S4 S5)
[    9.382514] ACPI: Using PIC for interrupt routing
[    9.403661] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    9.403665] ACPI: EC: driver started in poll mode
[    9.403709] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.404128] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    9.404132] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    9.404715] PCI: Transparent bridge - 0000:00:1e.0
[    9.404824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.405075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    9.405094] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    9.407788] ACPI: PCI Interrupt Link [LNKA] (IRQs *6)
[    9.407893] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    9.407995] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    9.408097] ACPI: PCI Interrupt Link [LNKD] (IRQs *6)
[    9.408198] ACPI: PCI Interrupt Link [LNKE] (IRQs *10)
[    9.408298] ACPI: PCI Interrupt Link [LNKF] (IRQs 10) *0, disabled.
[    9.408401] ACPI: PCI Interrupt Link [LNKG] (IRQs 6) *0, disabled.
[    9.408503] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[    9.408641] ACPI: Power Resource [PFN0] (off)
[    9.408681] ACPI: Power Resource [PFN1] (off)
[    9.408725] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.408759] pnp: PnP ACPI init
[    9.408767] ACPI: bus type pnp registered
[    9.411619] pnp: PnP ACPI: found 9 devices
[    9.411622] ACPI: ACPI bus type pnp unregistered
[    9.411625] PnPBIOS: Disabled by ACPI PNP
[    9.411874] PCI: Using ACPI for IRQ routing
[    9.411877] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.428595] NET: Registered protocol family 8
[    9.428598] NET: Registered protocol family 20
[    9.428662] AppArmor: AppArmor Filesystem Enabled
[    9.432586] Time: tsc clocksource has been installed.
[    9.440629] system 00:04: ioport range 0x164e-0x164f has been reserved
[    9.440633] system 00:04: ioport range 0x600-0x60f has been reserved
[    9.440636] system 00:04: ioport range 0x700-0x70f has been reserved
[    9.440640] system 00:04: ioport range 0x800-0x80f has been reserved
[    9.440643] system 00:04: ioport range 0x1000-0x107f has been reserved
[    9.440646] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    9.440650] system 00:04: ioport range 0x1c0-0x1cf has been reserved
[    9.440654] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    9.440657] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    9.440660] system 00:04: ioport range 0x610-0x61f has been reserved
[    9.440664] system 00:04: iomem range 0xfec10000-0xfec1ffff could not be reserved
[    9.440668] system 00:04: iomem range 0xff800000-0xffbfffff could not be reserved
[    9.440672] system 00:04: iomem range 0xfff00000-0xffffffff could not be reserved
[    9.440676] system 00:04: iomem range 0x0-0x9ffff could not be reserved
[    9.440679] system 00:04: iomem range 0xe0000-0xfffff could not be reserved
[    9.440683] system 00:04: iomem range 0xdf800-0xdffff has been reserved
[    9.440687] system 00:04: iomem range 0x0-0x0 could not be reserved
[    9.471147] PCI: Bridge: 0000:00:01.0
[    9.471150]   IO window: 3000-3fff
[    9.471154]   MEM window: d0100000-d01fffff
[    9.471158]   PREFETCH window: d8000000-dfffffff
[    9.471166] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[    9.471169]   IO window: 00004000-000040ff
[    9.471173]   IO window: 00004400-000044ff
[    9.471177]   PREFETCH window: 64000000-67ffffff
[    9.471181]   MEM window: 68000000-6bffffff
[    9.471185] PCI: Bridge: 0000:00:1e.0
[    9.471188]   IO window: 4000-4fff
[    9.471193]   MEM window: d0200000-d05fffff
[    9.471197]   PREFETCH window: disabled.
[    9.471211] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.471223] PCI: Enabling device 0000:02:06.0 (0104 -> 0107)
[    9.471393] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    9.471397] PCI: setting IRQ 10 as level-triggered
[    9.471401] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[    9.471416] NET: Registered protocol family 2
[    9.508655] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.508922] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.509861] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.510430] TCP: Hash tables configured (established 131072 bind 65536)
[    9.510434] TCP reno registered
[    9.520764] checking if image is initramfs... it is
[    9.972599] Switched to high resolution mode on CPU 0
[   10.374160] Freeing initrd memory: 7297k freed
[   10.382577] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   10.383345] Simple Boot Flag at 0x37 set to 0x1
[   10.383722] audit: initializing netlink socket (disabled)
[   10.383739] audit(1216258806.568:1): initialized
[   10.383941] highmem bounce pool size: 64 pages
[   10.386189] VFS: Disk quotas dquot_6.5.1
[   10.386281] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.386434] io scheduler noop registered
[   10.386437] io scheduler anticipatory registered
[   10.386440] io scheduler deadline registered
[   10.386453] io scheduler cfq registered (default)
[   10.386526] Boot video device is 0000:01:00.0
[   10.386857] isapnp: Scanning for PnP cards...
[   10.740747] isapnp: No Plug & Play device found
[   10.772248] Real Time Clock Driver v1.12ac
[   10.772369] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.772772] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   10.773540] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   10.773545] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   10.773555] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   10.774264] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.774347] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.774460] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOU2] at 0x60,0x64 irq 1,12
[   10.777072] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.778030] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.778035] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.778038] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.778041] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.778044] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.784577] mice: PS/2 mouse device common for all mice
[   10.784700] EISA: Probing bus 0 at eisa.0
[   10.784708] Cannot allocate resource for EISA slot 1
[   10.784711] Cannot allocate resource for EISA slot 2
[   10.784714] Cannot allocate resource for EISA slot 3
[   10.784716] Cannot allocate resource for EISA slot 4
[   10.784735] EISA: Detected 0 cards.
[   10.784738] cpuidle: using governor ladder
[   10.784741] cpuidle: using governor menu
[   10.784848] NET: Registered protocol family 1
[   10.784881] Using IPI No-Shortcut mode
[   10.784917] registered taskstats version 1
[   10.785024]   Magic number: 0:518:660
[   10.785054]   hash matches device ptyeb
[   10.785120] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.785122] EDD information not available.
[   10.785346] Freeing unused kernel memory: 368k freed
[   10.824473] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.039714] fuse init (API version 7.9)
[   12.055412] ACPI: Transitioning device [FAN0] to D3
[   12.055416] ACPI: Transitioning device [FAN0] to D3
[   12.055420] ACPI: Fan [FAN0] (off)
[   12.055537] ACPI: Transitioning device [FAN1] to D3
[   12.055539] ACPI: Transitioning device [FAN1] to D3
[   12.055543] ACPI: Fan [FAN1] (off)
[   12.061193] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   12.061199] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.066697] ACPI: Thermal Zone [THRM] (59 C)
[   12.844360] usbcore: registered new interface driver usbfs
[   12.844782] usbcore: registered new interface driver hub
[   12.864208] usbcore: registered new device driver usb
[   12.876295] USB Universal Host Controller Interface driver v3.0
[   12.876578] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 6
[   12.876582] PCI: setting IRQ 6 as level-triggered
[   12.876586] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6
[   12.876598] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.876603] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.876929] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.876955] uhci_hcd 0000:00:1d.0: irq 6, io base 0x00001800
[   12.877107] usb usb1: configuration #1 chosen from 1 choice
[   12.877134] hub 1-0:1.0: USB hub found
[   12.877141] hub 1-0:1.0: 2 ports detected
[   12.970125] SCSI subsystem initialized
[   12.980592] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 6
[   12.980597] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[   12.980609] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.980614] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.980641] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.980665] uhci_hcd 0000:00:1d.1: irq 6, io base 0x00001820
[   12.980801] usb usb2: configuration #1 chosen from 1 choice
[   12.980828] hub 2-0:1.0: USB hub found
[   12.980834] hub 2-0:1.0: 2 ports detected
[   13.076265] libata version 3.00 loaded.
[   13.084591] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 6
[   13.084595] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[   13.084608] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.084613] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.084647] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   13.084670] uhci_hcd 0000:00:1d.2: irq 6, io base 0x00001840
[   13.084800] usb usb3: configuration #1 chosen from 1 choice
[   13.084827] hub 3-0:1.0: USB hub found
[   13.084833] hub 3-0:1.0: 2 ports detected
[   13.188738] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   13.188744] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   13.188759] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.188763] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.188793] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   13.192704] ehci_hcd 0000:00:1d.7: debug port 1
[   13.192710] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.192719] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xd0000000
[   13.208292] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.208434] usb usb4: configuration #1 chosen from 1 choice
[   13.208463] hub 4-0:1.0: USB hub found
[   13.208471] hub 4-0:1.0: 6 ports detected
[   13.314317] ACPI: PCI Interrupt 0000:02:06.2[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[   13.364094] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d020a000-d020a7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   13.372692] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[   13.392279] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[   13.392286] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[   13.392292] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[   13.432279] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[   13.432308] b44.c:v2.0
[   13.432329] ata_piix 0000:00:1f.1: version 2.12
[   13.432342] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   13.432350] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 6 (level, low) -> IRQ 6
[   13.432388] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.433518] scsi0 : ata_piix
[   13.434088] scsi1 : ata_piix
[   13.435056] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[   13.435060] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[   13.452600] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:6a:de:e1
[   13.596779] ata1.00: ATA-6: IC25N080ATMR04-0, MO4OAD4A, max UDMA/100
[   13.596784] ata1.00: 156301488 sectors, multi 16: LBA48 
[   13.612656] ata1.00: configured for UDMA/100
[   13.916184] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   13.932447] ata2.00: ATAPI: Slimtype DVDRW SOSW-852S, PRS9, max UDMA/33
[   14.091786] usb 3-2: configuration #1 chosen from 1 choice
[   14.104390] ata2.00: configured for UDMA/33
[   14.104521] scsi 0:0:0:0: Direct-Access     ATA      IC25N080ATMR04-0 MO4O PQ: 0 ANSI: 5
[   14.105177] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-852S  PRS9 PQ: 0 ANSI: 5
[   14.124328] usbcore: registered new interface driver hiddev
[   14.130232] Driver 'sd' needs updating - please use bus_type methods
[   14.130321] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   14.130335] sd 0:0:0:0: [sda] Write Protect is off
[   14.130338] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.130357] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.130409] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   14.130420] sd 0:0:0:0: [sda] Write Protect is off
[   14.130423] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.130441] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.130445]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   14.137043] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb3/3-2/3-2:1.0/input/input2
[   14.148214] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2
[   14.148231] usbcore: registered new interface driver usbhid
[   14.148236] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   14.158866]  sda1 sda2 < sda5 >
[   14.186034] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.192318] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.192339] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   14.194487] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   14.194492] Uniform CD-ROM driver Revision: 3.20
[   14.194538] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   14.464533] Attempting manual resume
[   14.464537] swsusp: Resume From Partition 8:5
[   14.464539] PM: Checking swsusp image.
[   14.464693] PM: Resume from disk failed.
[   14.522549] kjournald starting.  Commit interval 5 seconds
[   14.522560] EXT3-fs: mounted filesystem with ordered data mode.
[   14.644233] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f0000323c3b]
[   30.887285] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.938684] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.006625] Linux agpgart interface v0.102
[   31.154600] intel_rng: FWH not detected
[   31.214683] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   31.354945] agpgart: Detected an Intel 855GM Chipset.
[   31.375514] agpgart: AGP aperture is 256M @ 0xe0000000
[   31.546572] iTCO_vendor_support: vendor-support=0
[   31.576726] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.576811] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   31.576843] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.642721] input: Power Button (FF) as /devices/virtual/input/input4
[   31.654576] ACPI: Power Button (FF) [PWRF]
[   31.654671] input: Lid Switch as /devices/virtual/input/input5
[   31.656432] ACPI: Lid Switch [LID]
[   31.656512] input: Sleep Button (CM) as /devices/virtual/input/input6
[   31.666537] ACPI: Sleep Button (CM) [SLPB]
[   32.190515] irda_init()
[   32.190533] NET: Registered protocol family 23
[   32.354580] ACPI: WMI-Acer: Mapper loaded
[   32.466562] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   32.466583] nsc-ircc, chip->init
[   32.466593] nsc-ircc, Found chip at base=0x164e
[   32.466618] nsc-ircc, driver loaded (Dag Brattli)
[   32.466625] nsc_ircc_open(), can't get iobase of 0x2f8
[   32.466652] nsc-ircc, Found chip at base=0x164e
[   32.466677] nsc-ircc, driver loaded (Dag Brattli)
[   32.466680] nsc_ircc_open(), can't get iobase of 0x2f8
[   32.466850] nsc-ircc 00:08: disabled
[   32.830455] acer_acpi: Acer Laptop ACPI Extras version 0.11.1
[   32.830473] acer_acpi: No or unsupported WMI interface, unable to load.
[   33.050491] Yenta: CardBus bridge found at 0000:02:06.0 [1025:0064]
[   33.050508] Yenta: Enabling burst memory read transactions
[   33.050512] Yenta: Using CSCINT to route CSC interrupts to PCI
[   33.050515] Yenta: Routing CardBus interrupts to PCI
[   33.050520] Yenta TI: socket 0000:02:06.0, mfunc 0x01a21b22, devctl 0x64
[   33.126504] ieee80211_crypt: registered algorithm 'NULL'
[   33.181355] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   33.181359] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   33.283376] Yenta: ISA IRQ mask 0x08b8, PCI irq 10
[   33.283381] Socket status: 30000006
[   33.283384] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   33.283391] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   33.283395] cs: IO port probe 0x4000-0x4fff: clean.
[   33.283710] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd05fffff
[   33.589123] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   33.701341] [fglrx] Maximum main memory to use for locked dma buffers: 1171 MBytes.
[   33.701390] [fglrx] ASYNCIO init succeed!
[   33.702089] [fglrx] PAT is enabled successfully!
[   33.703094] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   33.790370] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   33.790376] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   33.790477] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   33.834003] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   34.096655] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:02/LNXVIDEO:00/input/input7
[   34.106322] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   34.167294] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   34.208684] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   35.610406] ACPI: SBS HC: EC = 0xf7c56480, offset = 0x18, query_bit = 0x20
[   35.761118] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line)
[   36.222938] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present)
[   36.259596] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT1] (battery present)
[   37.409793] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   37.409838] ACPI: PCI Interrupt 0000:02:06.3[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[   37.409932] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   37.409947] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   37.517738] cs: IO port probe 0x100-0x3af: clean.
[   37.519342] cs: IO port probe 0x3e0-0x4ff: clean.
[   37.520039] cs: IO port probe 0x820-0x8ff: clean.
[   37.520621] cs: IO port probe 0xc00-0xcf7: clean.
[   37.521372] cs: IO port probe 0xa00-0xaff: clean.
[   37.725980] intel8x0_measure_ac97_clock: measured 54118 usecs
[   37.725985] intel8x0: clocking to 48000
[   38.208080] lp: driver loaded but no devices found
[   38.493713] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[  171.638351] EXT3 FS on sda1, internal journal
[  172.702922] ip_tables: (C) 2000-2006 Netfilter Core Team
[  173.144015] No dock devices found.
[  173.165949] ACPI: \_SB_.PCI0.IDE0.SECN.BAY1: found ejectable bay
[  173.165955] ACPI: \_SB_.PCI0.IDE0.SECN.BAY1: Adding notify handler
[  173.165992] ACPI: Error installing bay notify handler
[  173.165995] ACPI: Bay [\_SB_.PCI0.IDE0.SECN.BAY1] Added
[  151.692729] Marking TSC unstable due to: cpufreq changes.
[  151.695199] Time: acpi_pm clocksource has been installed.
[  152.459050] apm: BIOS not found.
[  152.623366] ppdev: user-space parallel port driver
[  152.757075] audit(1216258971.767:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=6100 profile="/usr/sbin/cupsd" namespace="default"
[  155.639855] ttyS1: LSR safety check engaged!
[  155.965157] Bluetooth: Core ver 2.11
[  155.971745] NET: Registered protocol family 31
[  155.971750] Bluetooth: HCI device and connection manager initialized
[  155.971754] Bluetooth: HCI socket layer initialized
[  208.171650] Bluetooth: L2CAP ver 2.9
[  208.171656] Bluetooth: L2CAP socket layer initialized
[  156.097222] Bluetooth: RFCOMM socket layer initialized
[  156.097420] Bluetooth: RFCOMM TTY layer initialized
[  156.097424] Bluetooth: RFCOMM ver 1.8
[  157.655427] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 6 (level, low) -> IRQ 6
[  159.945328] [fglrx] Internal AGP support requested, but kernel AGP support active.
[  159.945335] [fglrx] Have to use kernel AGP support to avoid conflicts.
[  159.945339] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[  159.945967] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  159.946133] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  159.946310] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  159.946486] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[  159.950253] [fglrx] GART Table is not in FRAME_BUFFER range 
[  159.950260] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  159.950263] [fglrx] Reserve Block - 1 offset =  0X3ff5000 length = 0Xb000
[  160.052915] [fglrx] interrupt source 20008000 successfully enabled
[  160.052921] [fglrx] enable ID = 0x00000004
[  160.053256] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  160.053475] [fglrx] interrupt source 10000000 successfully enabled
[  160.053478] [fglrx] enable ID = 0x00000005
[  160.053718] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  164.646302] Clocksource tsc unstable (delta = -137376382 ns)
[  532.315687] NET: Registered protocol family 10
[  532.316832] lo: Disabled Privacy Extensions
[  532.319220] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  532.320100] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  556.079419] NET: Registered protocol family 17
[  208.704301] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  601.229865] eth1: no IPv6 routers present
[ 2167.073652] hub 4-0:1.0: over-current change on port 4
[ 2167.316268] hub 2-0:1.0: over-current change on port 2
[ 2172.224973] usb 4-3: new high speed USB device using ehci_hcd and address 3
[ 2177.965100] usb 4-3: configuration #1 chosen from 1 choice
[ 1089.207257] usbcore: registered new interface driver libusual
[ 1089.265831] Initializing USB Mass Storage driver...
[ 1089.272765] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1089.274063] usbcore: registered new interface driver usb-storage
[ 1089.274070] USB Mass Storage support registered.
[ 1089.274527] usb-storage: device found at 3
[ 1089.274531] usb-storage: waiting for device to settle before scanning
[  820.686957] usb-storage: device scan complete
[  820.687767] scsi 2:0:0:0: Direct-Access              TOSHIBA MK6021GA GA02 PQ: 0 ANSI: 0 CCS
[  820.700841] sd 2:0:0:0: [sdb] 117210240 512-byte hardware sectors (60012 MB)
[  820.703419] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  820.703423] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  820.704292] sd 2:0:0:0: [sdb] 117210240 512-byte hardware sectors (60012 MB)
[  820.706918] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  820.706923] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  820.706927]  sdb: sdb1
[  821.141675] sd 2:0:0:0: [sdb] Attached SCSI disk
[  821.141722] sd 2:0:0:0: Attached scsi generic sg2 type 0

---

### Post by Morpheun on 2008-07-16
You shouldn't be getting that... What command did you use?

---

### Post by coolman121$ on 2008-07-16
dmesg and i no i shouldnt be getting tht i have tried everything

---

### Post by iaculallad on 2008-07-16
Post your /etc/fstab file (external drive connected):

```
cat /etc/fstab
```

do include whatever displays when you issue:

```
sudo fdisk -l
```

---

### Post by coolman121$ on 2008-07-16
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=645a2c93-1623-46a3-97d1-a8b87231d144 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=bbc368e4-9fd1-409e-a0bf-0df2bdec8d58 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

fdisk -l=
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=645a2c93-1623-46a3-97d1-a8b87231d144 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=bbc368e4-9fd1-409e-a0bf-0df2bdec8d58 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
jordan@jordan-laptop:~$ 
jordan@jordan-laptop:~$ sudo fdisk-l
sudo: fdisk-l: command not found
jordan@jordan-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000452dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b49c53d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7296    58605088+   7  HPFS/NTFS

---

### Post by iaculallad on 2008-07-16
Let's try to mount /dev/sdb1 (You're 60GB NTFS drive):

-Make sure ntfs-3g drive is installed:

```
sudo apt-get install ntfs-3g
```

-Create the mount point:

```
sudo mkdir /media/60Gig
```

-Open your /etc/fstab and insert the line of text below to the last part of the file.

```
/dev/sdb1       /media/60Gig ntfs-3g  defaults  0   0
```

-Save and close the file. Open your terminal and test it:

```
sudo mount -a
```

---

### Post by dreamstalker on 2008-07-17
srry my coolman121$ account was banned i am now uasing this one but anyways that doesnt work because permission is only to root and when i logged in as root my computer fed up and anyways that didnt work..........

---

### Post by ByteJuggler on 2008-07-17
> **dreamstalker said:**
> srry my coolman121$ account was banned i am now uasing this one but anyways that doesnt work because permission is only to root and when i logged in as root my computer fed up and anyways that didnt work..........

Ummm... for your information "sudo" ensures the command is run as root, that's the whole point.

Anyway, can you please post the exact output of each of those commands, the exact error messages is the only way we'll know how to further help you.

---

### Post by dreamstalker on 2008-07-17
> **ByteJuggler said:**
> Ummm... for your information "sudo" ensures the command is run as root, that's the whole point.

Anyway, can you please post the exact output of each of those commands, the exact error messages is the only way we'll know how to further help you.

ok for yourinfo i was trying to edit fstab so if you can find a way to edit fstab without using root then ill give you fifty bucks but other than thatstop complaning

---

### Post by ByteJuggler on 2008-07-18
> **dreamstalker said:**
> ok for yourinfo i was trying to edit fstab so if you can find a way to edit fstab without using root then ill give you fifty bucks but other than thatstop complaning

For your information I did not complain and neither did I suggest you can/should edit the /etc/fstab file without using root access.  

What I did say was:
1) Using "sudo" from a command prompt/terminal window (or "gksudo" for GUI applications/from the GUI desktop) is effectively the same as logging in as root and running something, without requiring actually logging in as root.    This is better for several good reasons.  My point: **Use "sudo" or "gksudo", do not log in as root.**  

2) **Please post the output of the commands you issued, without it we can't help you further.**


Aside: To edit the /etc/fstab file, you can (from the Ubuntu desktop), press alt-f2, then type 

```
gksudo gedit /etc/fstab
``` 

Alternaively, you can also open a terminal, then enter in there 

```
sudo gedit /etc/fstab
```

Hope that helps.

---

