---
title: "still need help with usb"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by wec123 on 2008-04-28
my usb isnt being recognized. lsusb gives me this no matter what device i plug into which usb port:

Bus 003 Device 001: 0000:0000
Bus 002 Device 001: 0000:0000
Bus 001 Device 001: 0000:0000

lshw -businfo gives me this:

WARNING: you should run this program as super-user.
Bus info          Device  Class          Description
====================================================
                          system         Computer
                          bus            Motherboard
                          memory         511MiB System memory
cpu@0                     processor      AMD Athlon(tm) XP 3000+
                          memory         128KiB L1 cache
                          memory         512KiB L2 cache
pci@0000:00:00.0          bridge         nForce2 IGP2
pci@0000:00:00.1          memory         RAM memory
pci@0000:00:00.2          memory         RAM memory
pci@0000:00:00.3          memory         RAM memory
pci@0000:00:00.4          memory         RAM memory
pci@0000:00:00.5          memory         RAM memory
pci@0000:00:01.0          bridge         nForce2 ISA Bridge
pci@0000:00:01.1          bus            nForce2 SMBus (MCP)
pci@0000:00:02.0          bus            nForce2 USB Controller
pci@0000:00:02.1          bus            nForce2 USB Controller
pci@0000:00:02.2          bus            nForce2 USB Controller
pci@0000:00:04.0  eth0    network        nForce2 Ethernet Controller
pci@0000:00:06.0          multimedia     nForce2 AC97 Audio Controler (MCP)
pci@0000:00:08.0          bridge         nForce2 External PCI Bridge
pci@0000:01:09.0          communication  HSF 56k HSFi Modem
pci@0000:00:09.0          storage        nForce2 IDE
pci@0000:00:1e.0          bridge         nForce2 AGP
pci@0000:02:00.0          display        NV34 [GeForce FX 5200]

---

### Post by SOULRiDER on 2008-04-28
Try with ```
lspci
```
Also, you can use ```
dmesg
``` to view kernel messages, use it as soon as you plug some usb device to see if its working or now.

---

### Post by wec123 on 2008-04-28
lspci gives:
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

**dmesg give more than the window would show but heres what i could copy and paste:**

[   20.977570] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[   20.977681] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[   20.977792] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[   20.977901] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   20.978062] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   20.978223] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0
[   20.978382] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[   20.978542] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[   20.978701] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[   20.978861] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   20.978979] ACPI: PCI Interrupt Link [APCS] (IRQs *23)
[   20.979139] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   20.979297] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[   20.979457] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[   20.979617] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   20.979749] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.979782] pnp: PnP ACPI init
[   20.979789] ACPI: bus type pnp registered
[   20.984008] pnp: PnP ACPI: found 15 devices
[   20.984011] ACPI: ACPI bus type pnp unregistered
[   20.984015] PnPBIOS: Disabled by ACPI PNP
[   20.984256] PCI: Using ACPI for IRQ routing
[   20.984261] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.010903] NET: Registered protocol family 8
[   21.010905] NET: Registered protocol family 20
[   21.010988] AppArmor: AppArmor Filesystem Enabled
[   21.014889] Time: tsc clocksource has been installed.
[   21.022917] system 00:00: ioport range 0x4000-0x407f has been reserved
[   21.022921] system 00:00: ioport range 0x4080-0x40ff has been reserved
[   21.022923] system 00:00: ioport range 0x4400-0x447f has been reserved
[   21.022926] system 00:00: ioport range 0x4480-0x44ff has been reserved
[   21.022928] system 00:00: ioport range 0x4200-0x427f has been reserved
[   21.022931] system 00:00: ioport range 0x4280-0x42ff has been reserved
[   21.022936] system 00:01: ioport range 0x5000-0x503f has been reserved
[   21.022938] system 00:01: ioport range 0x5040-0x507f has been reserved
[   21.022944] system 00:02: iomem range 0xd1800-0xd3fff has been reserved
[   21.022947] system 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[   21.022950] system 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[   21.022952] system 00:02: iomem range 0xfc000-0xfffff could not be reserved
[   21.022955] system 00:02: iomem range 0x1fff0000-0x1fffffff could not be reserved
[   21.022957] system 00:02: iomem range 0xffff0000-0xffffffff has been reserved
[   21.022960] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[   21.022963] system 00:02: iomem range 0x100000-0x1ffeffff could not be reserved
[   21.022965] system 00:02: iomem range 0xfec00000-0xfec00fff has been reserved
[   21.022968] system 00:02: iomem range 0xfee00000-0xfee00fff has been reserved
[   21.022973] system 00:04: ioport range 0xb78-0xb7b has been reserved
[   21.022976] system 00:04: ioport range 0xf78-0xf7b has been reserved
[   21.022980] system 00:04: ioport range 0xa78-0xa7b has been reserved
[   21.022983] system 00:04: ioport range 0xe78-0xe7b has been reserved
[   21.022985] system 00:04: ioport range 0xbbc-0xbbf has been reserved
[   21.022988] system 00:04: ioport range 0xfbc-0xfbf has been reserved
[   21.022990] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   21.022992] system 00:04: ioport range 0x294-0x297 has been reserved
[   21.053385] PCI: Bridge: 0000:00:08.0
[   21.053388]   IO window: c000-cfff
[   21.053393]   MEM window: da000000-daffffff
[   21.053396]   PREFETCH window: disabled.
[   21.053403] PCI: Bridge: 0000:00:1e.0
[   21.053404]   IO window: disabled.
[   21.053408]   MEM window: d8000000-d9ffffff
[   21.053411]   PREFETCH window: d0000000-d7ffffff
[   21.053423] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   21.053438] NET: Registered protocol family 2
[   21.090910] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   21.091138] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   21.091325] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   21.091506] TCP: Hash tables configured (established 16384 bind 16384)
[   21.091509] TCP reno registered
[   21.102928] checking if image is initramfs... it is
[   21.554388] Switched to high resolution mode on CPU 0
[   21.700356] Freeing initrd memory: 7677k freed
[   21.701069] audit: initializing netlink socket (disabled)
[   21.701085] audit(1209379700.272:1): initialized
[   21.703070] VFS: Disk quotas dquot_6.5.1
[   21.703147] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.703281] io scheduler noop registered
[   21.703284] io scheduler anticipatory registered
[   21.703286] io scheduler deadline registered
[   21.703295] io scheduler cfq registered (default)
[   21.703338] Boot video device is 0000:02:00.0
[   21.703619] isapnp: Scanning for PnP cards...
[   22.057754] isapnp: No Plug & Play device found
[   22.087294] Real Time Clock Driver v1.12ac
[   22.087415] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.087558] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.087707] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.088284] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.088511] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   22.089358] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.089436] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.089541] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   22.091981] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.091986] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.101794] mice: PS/2 mouse device common for all mice
[   22.101916] EISA: Probing bus 0 at eisa.0
[   22.101939] Cannot allocate resource for EISA slot 4
[   22.101942] Cannot allocate resource for EISA slot 5
[   22.101957] EISA: Detected 0 cards.
[   22.101961] cpuidle: using governor ladder
[   22.101963] cpuidle: using governor menu
[   22.102107] NET: Registered protocol family 1
[   22.102136] Using IPI No-Shortcut mode
[   22.102171] registered taskstats version 1
[   22.102275]   Magic number: 4:937:831
[   22.102401]   hash matches device ptyqe
[   22.102460] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.102462] EDD information not available.
[   22.102874] Freeing unused kernel memory: 364k freed
[   22.145707] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   23.320905] fuse init (API version 7.9)
[   23.336593] ACPI: Fan [FAN] (on)
[   23.344554] ACPI: Thermal Zone [THRM] (56 C)
[   24.195919] usbcore: registered new interface driver usbfs
[   24.195951] usbcore: registered new interface driver hub
[   24.203926] usbcore: registered new device driver usb
[   24.216326] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   24.216673] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   24.216682] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 16
[   24.216690] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   24.231011] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.271655] SCSI subsystem initialized
[   24.307401] libata version 3.00 loaded.
[   24.435337] Floppy drive(s): fd0 is 1.44M
[   24.459137] FDC 0 is a post-1991 82077
[   24.735434] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x57d @ 1, addr 00:0c:76:61:a3:e2
[   24.735440] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[   24.735897] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   24.735906] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 21 (level, high) -> IRQ 17
[   24.735922] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.735926] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   24.736251] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   24.736271] ohci_hcd 0000:00:02.0: irq 17, io mem 0xdb003000
[   24.792999] usb usb1: configuration #1 chosen from 1 choice
[   24.793031] hub 1-0:1.0: USB hub found
[   24.793041] hub 1-0:1.0: 3 ports detected
[   24.895194] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[   24.895205] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 20 (level, high) -> IRQ 18
[   24.895221] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   24.895225] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   24.895250] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   24.895270] ohci_hcd 0000:00:02.1: irq 18, io mem 0xdb004000
[   24.952793] usb usb2: configuration #1 chosen from 1 choice
[   24.952820] hub 2-0:1.0: USB hub found
[   24.952829] hub 2-0:1.0: 3 ports detected
[   25.055272] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   25.055278] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 22 (level, high) -> IRQ 16
[   25.055292] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   25.055295] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   25.055325] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   25.055359] ehci_hcd 0000:00:02.2: debug port 1
[   25.055365] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   25.055377] ehci_hcd 0000:00:02.2: irq 16, io mem 0xdb005000
[   25.066605] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.066757] usb usb3: configuration #1 chosen from 1 choice
[   25.066783] hub 3-0:1.0: USB hub found
[   25.066792] hub 3-0:1.0: 6 ports detected
[   25.174217] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   25.177705] pata_amd 0000:00:09.0: version 0.3.10
[   25.177777] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   25.178232] scsi0 : pata_amd
[   25.179707] scsi1 : pata_amd
[   25.180567] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   25.180571] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   25.351718] ata1.00: ATA-6: WDC WD1200JB-00EVA0, 15.05R15, max UDMA/100
[   25.351723] ata1.00: 234441648 sectors, multi 16: LBA48 
[   25.361288] ata1.01: ATA-4: WDC WD135BA, P74CA30A, max UDMA/66
[   25.361291] ata1.01: 26406576 sectors, multi 16: LBA 
[   25.375600] ata1.00: configured for UDMA/100
[   25.394385] ata1.01: configured for UDMA/66
[   25.629978] hub 3-0:1.0: over-current change on port 1
[   25.981916] ata2.00: ATAPI: LITE-ON LTR-52327S, QS06, max UDMA/33
[   25.981933] ata2.01: ATAPI: JLMS XJ-HD166S, DS18, max UDMA/33
[   26.153654] ata2.00: configured for UDMA/33
[   26.309590] ata2.01: configured for UDMA/33
[   26.309719] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200JB-00E 15.0 PQ: 0 ANSI: 5
[   26.310133] scsi 0:0:1:0: Direct-Access     ATA      WDC WD135BA      P74C PQ: 0 ANSI: 5
[   26.321627] scsi 1:0:0:0: CD-ROM            LITE-ON  LTR-52327S       QS06 PQ: 0 ANSI: 5
[   26.321972] scsi 1:0:1:0: CD-ROM            JLMS     XJ-HD166S        DS18 PQ: 0 ANSI: 5
[   26.330567] Driver 'sd' needs updating - please use bus_type methods
[   26.330674] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   26.330689] sd 0:0:0:0: [sda] Write Protect is off
[   26.330692] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.330710] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.330761] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   26.330771] sd 0:0:0:0: [sda] Write Protect is off
[   26.330773] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.330789] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.330793]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   26.341705]  sda1 sda2 < sda5 >
[   26.367721] sd 0:0:0:0: [sda] Attached SCSI disk
[   26.367799] sd 0:0:1:0: [sdb] 26406576 512-byte hardware sectors (13520 MB)
[   26.367813] sd 0:0:1:0: [sdb] Write Protect is off
[   26.367816] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.367834] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.367879] sd 0:0:1:0: [sdb] 26406576 512-byte hardware sectors (13520 MB)
[   26.367889] sd 0:0:1:0: [sdb] Write Protect is off
[   26.367892] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   26.367907] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.367911]  sdb: sdb1
[   26.378539] sd 0:0:1:0: [sdb] Attached SCSI disk
[   26.386877] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   26.386902] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   26.386922] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   26.386940] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   26.454137] sr0: scsi3-mmc drive: 32x/52x writer cd/rw xa/form2 cdda tray
[   26.454144] Uniform CD-ROM driver Revision: 3.20
[   26.454206] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.456690] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   26.456721] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   26.739575] Attempting manual resume
[   26.739580] swsusp: Resume From Partition 8:5
[   26.739582] PM: Checking swsusp image.
[   26.739761] PM: Resume from disk failed.
[   26.786322] kjournald starting.  Commit interval 5 seconds
[   26.786339] EXT3-fs: mounted filesystem with ordered data mode.
[   28.826557] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   31.791396] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   34.009347] Linux agpgart interface v0.102
[   34.033928] agpgart: Detected NVIDIA nForce2 chipset
[   34.101083] agpgart: AGP aperture is 256M @ 0xc0000000
[   34.340866] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   34.340898] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5040
[   34.592624] input: Power Button (FF) as /devices/virtual/input/input2
[   34.608404] ACPI: Power Button (FF) [PWRF]
[   34.608562] input: Power Button (CM) as /devices/virtual/input/input3
[   34.620369] ACPI: Power Button (CM) [PWRB]
[   34.760241] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   35.107924] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   35.147983] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.734533] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 21
[   36.734539] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 21 (level, high) -> IRQ 17
[   36.734565] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   37.057783] intel8x0_measure_ac97_clock: measured 52778 usecs
[   37.057788] intel8x0: clocking to 47500
[   37.725077] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   37.725100] hub 3-0:1.0: over-current change on port 2
[   37.737244] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   39.452039] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   39.486014] parport_pc 00:0c: reported by Plug and Play ACPI
[   39.486075] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   40.921659] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   41.293373] lp0: using parport0 (interrupt-driven).
[   41.352512] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
[   41.903289] EXT3 FS on sda1, internal journal
[   43.208957] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.520691] No dock devices found.
[   43.886509] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   44.615075] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   44.615082] apm: overridden by ACPI.
[   44.728509] ppdev: user-space parallel port driver
[   44.811135] audit(1209379724.605:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5204 profile="/usr/sbin/cupsd" namespace="default"
[   46.171118] eth0: no link during initialization.
[   46.222964] Bluetooth: Core ver 2.11
[   46.223935] NET: Registered protocol family 31
[   46.223940] Bluetooth: HCI device and connection manager initialized
[   46.223944] Bluetooth: HCI socket layer initialized
[   46.248055] Bluetooth: L2CAP ver 2.9
[   46.248062] Bluetooth: L2CAP socket layer initialized
[   46.296965] Bluetooth: RFCOMM socket layer initialized
[   46.297511] Bluetooth: RFCOMM TTY layer initialized
[   46.297514] Bluetooth: RFCOMM ver 1.8
[   46.851321] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   49.816154] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[   49.816173] hub 3-0:1.0: over-current change on port 3
[   53.012743] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[   55.977579] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[   58.942415] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[   61.907255] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[   61.907366] hub 3-0:1.0: over-current change on port 4
[   65.103841] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   68.068675] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   71.033511] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   73.998346] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[   73.998432] hub 3-0:1.0: over-current change on port 5
[   77.194938] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   80.159775] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   83.124608] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   86.089444] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[   86.089529] hub 3-0:1.0: over-current change on port 6
[   89.286032] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   92.250869] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   95.215705] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[   98.180541] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  141.067726] NET: Registered protocol family 10
[  141.067941] lo: Disabled Privacy Extensions
[  141.069290] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  282.180193] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  285.145036] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  288.109861] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  291.074697] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  294.039534] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[  297.004371] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[  299.969222] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[  302.934048] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[  305.898880] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[  308.863717] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[  311.828554] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[  314.793389] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[  317.758221] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  320.723057] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  323.687897] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  326.652732] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[  329.617572] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  332.582407] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  335.547244] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  338.512078] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[  341.476915] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  344.441745] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  347.406582] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  350.371419] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 1003.162816] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1006.128138] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1009.092474] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1012.057324] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 1015.022162] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 1017.987008] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 1020.951833] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 1023.916667] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 1026.881549] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 1029.846341] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 1032.811175] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 1035.776005] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 1038.740849] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1041.705673] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1044.670524] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1047.635355] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 1050.600191] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 1053.565024] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 1056.533857] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 1059.498700] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 1062.463539] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 1065.428376] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 1068.393199] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 1071.358038] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 4830.398516] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4833.363359] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4836.328185] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4839.293021] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 4842.257857] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 4845.222693] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 4848.187528] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 4851.152366] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 4854.117205] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 4857.082040] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 4860.046877] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 4863.011711] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 4865.976548] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 4868.941384] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 4871.906229] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 4874.871057] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 4877.835892] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 4880.800728] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 4883.765566] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 4886.730402] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 4889.695233] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 4892.660069] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 4895.624905] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 4898.589741] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5008.016970] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5010.981809] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5013.946640] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5016.911477] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5019.876312] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5022.841148] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5025.805985] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5028.770821] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5031.735658] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5034.700492] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5037.665326] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5040.630161] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5043.594998] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5046.559835] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5049.524676] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5052.489511] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5055.454348] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5058.419183] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5061.384020] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5064.348855] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5067.313695] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5070.278522] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5073.243357] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5076.208194] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5125.120001] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5128.084842] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5131.049670] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5134.014507] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5136.979342] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5139.944178] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5142.909014] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5145.873850] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5148.838690] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5151.803526] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5154.768368] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5157.733197] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5160.698033] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5163.662871] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5166.627712] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5169.592547] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5172.557377] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5175.522222] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5178.487062] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5181.451915] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5184.416717] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5187.381569] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5190.346390] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5193.311227] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5253.239279] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5256.204116] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5259.168945] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5262.133781] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5265.098617] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5268.063453] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5271.028290] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5273.993125] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5276.957961] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5279.922798] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5282.887635] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5285.852471] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5288.817307] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5291.782142] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5294.746985] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5297.711819] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5300.676657] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5303.641495] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5306.606332] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5309.571167] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5312.535998] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5315.500834] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5318.465669] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5321.430506] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5392.778371] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5395.743207] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5398.708036] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5401.672871] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 5404.637709] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5407.602543] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5410.567382] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5413.532216] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5416.497055] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5419.461891] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5422.426728] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5425.391563] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 5428.356399] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5431.321236] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5434.286070] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5437.250907] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 5440.215743] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5443.180580] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5446.145418] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5449.110253] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 5452.075084] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5455.039920] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5458.004758] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 5460.969591] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 6759.571351] cdrom: sr0: mrw address space DMA selected
[ 6759.648433] cdrom: sr0: mrw address space DMA selected
[ 6759.681464] UDF-fs: No VRS found
[ 6759.690022] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 6759.704654] ISO 9660 Extensions: RRIP_1991A
[ 7025.755728] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 7028.720565] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 7031.685391] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 7034.650226] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[ 7037.615059] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 7040.579894] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 7043.544731] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 7046.509567] hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 7049.474404] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 7052.439241] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 7055.404075] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 7058.368912] hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[ 7061.333748] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 7064.298585] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 7067.263426] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 7070.228264] hub 3-0:1.0: Cannot enable port 4.  Maybe the USB cable is bad?
[ 7073.193099] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 7076.157935] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 7079.122770] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 7082.087608] hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[ 7085.052435] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 7088.017272] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 7090.982108] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[ 7093.946944] hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[39417.812226] end_request: I/O error, dev fd0, sector 0
[47251.960044] end_request: I/O error, dev fd0, sector 43
[47251.960053] Buffer I/O error on device fd0, logical block 5
[47253.243061] floppy0: data CRC error: track 2, head 0, sector 8, size 2
[47253.442037] floppy0: data CRC error: track 2, head 0, sector 8, size 2
[47253.442045] end_request: I/O error, dev fd0, sector 79
[47253.442051] Buffer I/O error on device fd0, logical block 9
[47257.734934] floppy0: unexpected interrupt 
[47257.735021] floppy0: sensei repl[0]=80 
[47257.735027] floppy0: -- FDC reply error<6>cdrom: This disc doesn't have any tracks I recognize!
[48764.929037] cdrom: sr0: mrw address space DMA selected
[48764.947206] cdrom: sr0: mrw address space DMA selected
[48764.994093] UDF-fs: No VRS found
[48765.015013] ISO 9660 Extensions: Microsoft Joliet Level 3
[48765.016757] ISO 9660 Extensions: RRIP_1991A

---

### Post by wec123 on 2008-04-29
screw it i guess its back to windows UGH:mad:

---

