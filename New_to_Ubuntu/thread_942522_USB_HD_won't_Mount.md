---
title: "USB HD won't Mount"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by WarTor on 2008-10-09
Hello,

I am very new to Ubuntu, and I have external HD (USB) and I need to retrieve the information stored in it, but every time i plug it in, it gives an error message stating that Cannot Mount Volume. Unable to mount the Volume "WD Passport"

any help, PLEASE??

I really need the information :(

thanks to everyone!

---

### Post by jigsaws on 2008-10-09
Is it ntfs (Windows) filesystem? 
If yes: Have you unmounted it correctly in Windows (remove hardware icon on system tray)?

---

### Post by WarTor on 2008-10-09
yes its ntfs, and yes i did remove it correctly :)

---

### Post by Nxion on 2008-10-09
Can you post the output of this AFTER you get the error when you plug in the hard drive:

```
dmesg
```and

```
tail /var/log/messages
```

---

### Post by WarTor on 2008-10-09
okay, here is what i got after i typed those 2 commands, and thanks for the help :)

> [   20.017874] SMP alternatives: switching to SMP code
[   20.018535] Booting processor 1/1 eip 3000
[   20.028883] Initializing CPU#1
[   20.106733] Calibrating delay using timer specific routine.. 6400.06 BogoMIPS (lpj=12800134)
[   20.106742] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e4bd 00000000 00000001 00000000
[   20.106747] monitor/mwait feature present.
[   20.106752] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   20.106754] CPU: L2 cache: 2048K
[   20.106756] CPU: Physical Processor ID: 0
[   20.106757] CPU: Processor Core ID: 1
[   20.106758] CPU: After all inits, caps: bfebfbff 20100000 00000000 0000b180 0000e4bd 00000000 00000001 00000000
[   20.107222] CPU1: Intel(R) Pentium(R) D CPU 3.20GHz stepping 04
[   20.107256] Total of 2 processors activated (12806.49 BogoMIPS).
[   20.107478] ENABLING IO-APIC IRQs
[   20.107673] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   20.254359] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   20.274319] Brought up 2 CPUs
[   20.274346] CPU0 attaching sched-domain:
[   20.274349]  domain 0: span 03
[   20.274351]   groups: 01 02
[   20.274355] CPU1 attaching sched-domain:
[   20.274356]  domain 0: span 03
[   20.274358]   groups: 02 01
[   20.274547] net_namespace: 64 bytes
[   20.274555] Booting paravirtualized kernel on bare hardware
[   20.275110] Time: 16:05:33  Date: 10/09/08
[   20.275132] NET: Registered protocol family 16
[   20.275355] EISA bus registered
[   20.275360] ACPI: bus type pci registered
[   20.307904] PCI: PCI BIOS revision 3.00 entry at 0xfa8e0, last bus=2
[   20.307907] PCI: Using configuration type 1
[   20.307914] Setting up standard PCI resources
[   20.312966] ACPI: EC: Look up EC in DSDT
[   20.319449] ACPI: Interpreter enabled
[   20.319452] ACPI: (supports S0 S1 S3 S4 S5)
[   20.319470] ACPI: Using IOAPIC for interrupt routing
[   20.329313] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.331342] PCI: Transparent bridge - 0000:00:0f.0
[   20.331365] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.331846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   20.409633] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.409825] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   20.410008] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.410195] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 *11 14 15)
[   20.410379] ACPI: PCI Interrupt Link [LXV5] (IRQs 5 7 9 *10 11 14 15)
[   20.410562] ACPI: PCI Interrupt Link [LXV6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.410746] ACPI: PCI Interrupt Link [LXV7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.410931] ACPI: PCI Interrupt Link [LXV8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.411116] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   20.411302] ACPI: PCI Interrupt Link [LMC1] (IRQs *5 7 9 10 11 14 15)
[   20.411486] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   20.411674] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   20.411858] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.412043] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   20.412227] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   20.412413] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 9 *10 11 14 15)
[   20.412605] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 9 10 *11 14 15)
[   20.412790] ACPI: PCI Interrupt Link [LSA2] (IRQs 5 7 9 10 *11 14 15)
[   20.413019] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   20.413242] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   20.413461] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   20.413681] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   20.413910] ACPI: PCI Interrupt Link [AXV5] (IRQs 16) *0
[   20.414129] ACPI: PCI Interrupt Link [AXV6] (IRQs 16) *0, disabled.
[   20.414349] ACPI: PCI Interrupt Link [AXV7] (IRQs 16) *0, disabled.
[   20.414568] ACPI: PCI Interrupt Link [AXV8] (IRQs 16) *0, disabled.
[   20.414788] ACPI: PCI Interrupt Link [AUBA] (IRQs 20 21 22 23) *0
[   20.415008] ACPI: PCI Interrupt Link [AMA1] (IRQs 20 21 22 23) *0
[   20.415229] ACPI: PCI Interrupt Link [AMAC] (IRQs 20 21 22 23) *0
[   20.415450] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   20.415671] ACPI: PCI Interrupt Link [AACI] (IRQs 20 21 22 23) *0, disabled.
[   20.415892] ACPI: PCI Interrupt Link [AMCI] (IRQs 20 21 22 23) *0, disabled.
[   20.416113] ACPI: PCI Interrupt Link [ASMB] (IRQs 20 21 22 23) *0, disabled.
[   20.416335] ACPI: PCI Interrupt Link [AUS2] (IRQs 20 21 22 23) *0
[   20.416555] ACPI: PCI Interrupt Link [AIDE] (IRQs 20 21 22 23) *0, disabled.
[   20.416777] ACPI: PCI Interrupt Link [ASA0] (IRQs 20 21 22 23) *0
[   20.416997] ACPI: PCI Interrupt Link [ASA1] (IRQs 20 21 22 23) *0
[   20.417216] ACPI: PCI Interrupt Link [ASA2] (IRQs 20 21 22 23) *0
[   20.417379] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.417416] pnp: PnP ACPI init
[   20.417424] ACPI: bus type pnp registered
[   20.421612] pnp: PnP ACPI: found 12 devices
[   20.421615] ACPI: ACPI bus type pnp unregistered
[   20.421618] PnPBIOS: Disabled by ACPI PNP
[   20.421886] PCI: Using ACPI for IRQ routing
[   20.421889] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.541380] NET: Registered protocol family 8
[   20.541383] NET: Registered protocol family 20
[   20.541432] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[   20.541442] hpet0: 3 32-bit timers, 25000000 Hz
[   20.542477] AppArmor: AppArmor Filesystem Enabled
[   20.545365] Time: tsc clocksource has been installed.
[   20.545377] Switched to high resolution mode on CPU 0
[   20.545468] Switched to high resolution mode on CPU 1
[   20.553352] system 00:00: ioport range 0x1000-0x107f has been reserved
[   20.553356] system 00:00: ioport range 0x1080-0x10ff has been reserved
[   20.553363] system 00:00: ioport range 0x1400-0x147f has been reserved
[   20.553366] system 00:00: ioport range 0x1480-0x14ff has been reserved
[   20.553368] system 00:00: ioport range 0x1800-0x187f has been reserved
[   20.553370] system 00:00: ioport range 0x1880-0x18ff has been reserved
[   20.553377] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   20.553380] system 00:02: ioport range 0x295-0x314 has been reserved
[   20.553382] system 00:02: ioport range 0x880-0x88f has been reserved
[   20.553392] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[   20.553399] system 00:0b: iomem range 0xd0000-0xd3fff has been reserved
[   20.553401] system 00:0b: iomem range 0xd5800-0xd7fff has been reserved
[   20.553404] system 00:0b: iomem range 0xf0000-0xfbfff could not be reserved
[   20.553406] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[   20.553409] system 00:0b: iomem range 0x9fef0000-0x9fefffff could not be reserved
[   20.553411] system 00:0b: iomem range 0xffff0000-0xffffffff could not be reserved
[   20.553414] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   20.553416] system 00:0b: iomem range 0x100000-0x9feeffff could not be reserved
[   20.553419] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[   20.553422] system 00:0b: iomem range 0xd0000000-0xdfffffff could not be reserved
[   20.553424] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[   20.553427] system 00:0b: iomem range 0xfeff0000-0xfeff0000 could not be reserved
[   20.583826] PCI: Bridge: 0000:00:03.0
[   20.583830]   IO window: 9000-9fff
[   20.583834]   MEM window: ca000000-cdffffff
[   20.583838]   PREFETCH window: a0000000-bfffffff
[   20.583842] PCI: Bridge: 0000:00:0f.0
[   20.583845]   IO window: 8000-8fff
[   20.583849]   MEM window: cfe00000-cfefffff
[   20.583852]   PREFETCH window: disabled.
[   20.583869] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   20.583881] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   20.583893] NET: Registered protocol family 2
[   20.621168] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.621444] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.621983] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.622253] TCP: Hash tables configured (established 131072 bind 65536)
[   20.622255] TCP reno registered
[   20.633197] checking if image is initramfs... it is
[   21.174505] Freeing initrd memory: 7296k freed
[   21.175547] audit: initializing netlink socket (disabled)
[   21.175567] audit(1223568333.416:1): initialized
[   21.175834] highmem bounce pool size: 64 pages
[   21.178748] VFS: Disk quotas dquot_6.5.1
[   21.178859] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.179027] io scheduler noop registered
[   21.179030] io scheduler anticipatory registered
[   21.179032] io scheduler deadline registered
[   21.179047] io scheduler cfq registered (default)
[   21.179239] pci 0000:00:03.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0e.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0e.1: Quirk disabling HT MSI mapping<6>pci 0000:00:0e.2: Quirk disabling HT MSI mapping<6>pci 0000:00:0f.0: Quirk disabling HT MSI mapping<6>pci 0000:00:0f.1: Quirk disabling HT MSI mapping<6>pci 0000:00:11.0: Quirk disabling HT MSI mapping<6>pci 0000:00:12.0: Quirk disabling HT MSI mapping<7>Boot video device is 0000:01:00.0
[   21.191897] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   21.191956] assign_interrupt_mode Found MSI capability
[   21.191998] Allocate Port Service[0000:00:03.0:pcie00]
[   21.192408] isapnp: Scanning for PnP cards...
[   21.542935] isapnp: No Plug & Play device found
[   21.586802] Real Time Clock Driver v1.12ac
[   21.587035] hpet_resources: 0xfeff0000 is busy
[   21.587082] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.587236] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.588144] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   21.589321] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.589420] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.589646] PNP: No PS/2 controller found. Probing ports directly.
[   21.592295] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.592301] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.602139] mice: PS/2 mouse device common for all mice
[   21.602282] EISA: Probing bus 0 at eisa.0
[   21.602289] Cannot allocate resource for EISA slot 1
[   21.602308] Cannot allocate resource for EISA slot 8
[   21.602310] EISA: Detected 0 cards.
[   21.602316] cpuidle: using governor ladder
[   21.602319] cpuidle: using governor menu
[   21.602393] NET: Registered protocol family 1
[   21.602422] Using IPI No-Shortcut mode
[   21.602449] registered taskstats version 1
[   21.602584]   Magic number: 12:908:84
[   21.602741] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.602742] EDD information not available.
[   21.602934] Freeing unused kernel memory: 368k freed
[   22.822535] fuse init (API version 7.9)
[   22.846049] ACPI: SSDT 9FEF8740, 026C (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[   22.846309] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.846472] ACPI: SSDT 9FEF8C00, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[   22.846693] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   22.846707] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.339067] SCSI subsystem initialized
[   23.369216] libata version 3.00 loaded.
[   23.370099] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   23.370494] ACPI: PCI Interrupt Link [AMAC] enabled at IRQ 23
[   23.370500] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [AMAC] -> GSI 23 (level, low) -> IRQ 16
[   23.370508] PCI: Setting latency timer of device 0000:00:11.0 to 64
[   23.456667] usbcore: registered new interface driver usbfs
[   23.456694] usbcore: registered new interface driver hub
[   23.458342] usbcore: registered new device driver usb
[   23.461657] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   23.508800] FDC 0 is a post-1991 82077
[   23.887190] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:04:4b:02:4a:ae
[   23.887195] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   23.887599] ACPI: PCI Interrupt Link [AMA1] enabled at IRQ 22
[   23.887605] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [AMA1] -> GSI 22 (level, low) -> IRQ 17
[   23.887612] PCI: Setting latency timer of device 0000:00:12.0 to 64
[   24.405536] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 2, addr 00:04:4b:02:4a:af
[   24.405540] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   24.409334] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   24.409343] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 18
[   24.410364] pata_amd 0000:00:0d.0: version 0.3.10
[   24.410413] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   24.410480] scsi0 : pata_amd
[   24.410635] scsi1 : pata_amd
[   24.411181] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xec00 irq 14
[   24.411184] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xec08 irq 15
[   24.458922] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[cfeff000-cfeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   24.574697] ata2: port disabled. ignoring.
[   24.575153] ACPI: PCI Interrupt Link [AUS2] enabled at IRQ 21
[   24.575158] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [AUS2] -> GSI 21 (level, low) -> IRQ 19
[   24.575168] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   24.575172] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   24.575371] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   24.575397] ehci_hcd 0000:00:0b.1: debug port 1
[   24.575402] PCI: cache line size of 128 is not supported by device 0000:00:0b.1
[   24.575411] ehci_hcd 0000:00:0b.1: irq 19, io mem 0xcfffe000
[   24.585468] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.585623] usb usb1: configuration #1 chosen from 1 choice
[   24.585650] hub 1-0:1.0: USB hub found
[   24.585656] hub 1-0:1.0: 10 ports detected
[   24.688917] ACPI: PCI Interrupt Link [ASA0] enabled at IRQ 20
[   24.688923] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [ASA0] -> GSI 20 (level, low) -> IRQ 20
[   24.688955] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   24.688967] ACPI: PCI interrupt for device 0000:00:0e.0 disabled
[   24.689310] ACPI: PCI Interrupt Link [ASA1] enabled at IRQ 23
[   24.689313] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [ASA1] -> GSI 23 (level, low) -> IRQ 16
[   24.689337] PCI: Setting latency timer of device 0000:00:0e.1 to 64
[   24.689346] ACPI: PCI interrupt for device 0000:00:0e.1 disabled
[   24.689680] ACPI: PCI Interrupt Link [ASA2] enabled at IRQ 22
[   24.689683] ACPI: PCI Interrupt 0000:00:0e.2[C] -> Link [ASA2] -> GSI 22 (level, low) -> IRQ 17
[   24.689706] PCI: Setting latency timer of device 0000:00:0e.2 to 64
[   24.689715] ACPI: PCI interrupt for device 0000:00:0e.2 disabled
[   24.690067] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 21
[   24.690070] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [AUBA] -> GSI 21 (level, low) -> IRQ 19
[   24.690079] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   24.690082] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   24.690113] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   24.690126] ohci_hcd 0000:00:0b.0: irq 19, io mem 0xcffff000
[   24.746064] usb usb2: configuration #1 chosen from 1 choice
[   24.746092] hub 2-0:1.0: USB hub found
[   24.746101] hub 2-0:1.0: 10 ports detected
[   24.847854] sata_nv 0000:00:0e.0: version 3.5
[   24.847868] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [ASA0] -> GSI 20 (level, low) -> IRQ 20
[   24.847916] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   24.848410] scsi2 : sata_nv
[   24.848737] scsi3 : sata_nv
[   24.848909] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[   24.848912] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[   25.167611] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   25.300132] usb 1-2: configuration #1 chosen from 1 choice
[   25.314163] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   25.366429] ata3.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
[   25.366434] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.432857] ata3.00: configured for UDMA/133
[   25.728939] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0d4b620300044b03]
[   25.896298] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   25.904524] ata4.00: ATA-7: WDC WD800JD-55MSA1, 10.01E01, max UDMA/133
[   25.904528] ata4.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.912517] ata4.00: configured for UDMA/133
[   25.912655] scsi 2:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
[   25.913008] scsi 3:0:0:0: Direct-Access     ATA      WDC WD800JD-55MS 10.0 PQ: 0 ANSI: 5
[   25.913083] ACPI: PCI Interrupt 0000:00:0e.1[B] -> Link [ASA1] -> GSI 23 (level, low) -> IRQ 16
[   25.913118] PCI: Setting latency timer of device 0000:00:0e.1 to 64
[   25.913374] scsi4 : sata_nv
[   25.913522] scsi5 : sata_nv
[   25.913690] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 16
[   25.913693] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 16
[   25.972043] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   26.195520] usb 2-1: configuration #1 chosen from 1 choice
[   26.227805] ata5: SATA link down (SStatus 0 SControl 300)
[   26.506897] usb 2-3: new low speed USB device using ohci_hcd and address 3
[   26.546770] ata6: SATA link down (SStatus 0 SControl 300)
[   26.556927] ACPI: PCI Interrupt 0000:00:0e.2[C] -> Link [ASA2] -> GSI 22 (level, low) -> IRQ 17
[   26.556974] PCI: Setting latency timer of device 0000:00:0e.2 to 64
[   26.557040] scsi6 : sata_nv
[   26.557274] scsi7 : sata_nv
[   26.557446] ata7: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb000 irq 17
[   26.557450] ata8: SATA max UDMA/133 cmd 0xb800 ctl 0xb400 bmdma 0xb008 irq 17
[   26.719875] usb 2-3: configuration #1 chosen from 1 choice
[   26.865783] ata7: SATA link down (SStatus 0 SControl 300)
[   27.025252] usb 2-4: new low speed USB device using ohci_hcd and address 4
[   27.184747] ata8: SATA link down (SStatus 0 SControl 300)
[   27.201890] Driver 'sd' needs updating - please use bus_type methods
[   27.201969] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   27.201984] sd 2:0:0:0: [sda] Write Protect is off
[   27.201987] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.202010] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.202060] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   27.202073] sd 2:0:0:0: [sda] Write Protect is off
[   27.202075] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.202097] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.202101]  sda: sda1 sda2 < sda5 >
[   27.238513] sd 2:0:0:0: [sda] Attached SCSI disk
[   27.238565] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   27.238578] sd 3:0:0:0: [sdb] Write Protect is off
[   27.238580] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   27.238602] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.238643] sd 3:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[   27.238663] sd 3:0:0:0: [sdb] Write Protect is off
[   27.238666] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   27.238687] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.238691]  sdb: sdb1 sdb2 <<6>usb 2-4: configuration #1 chosen from 1 choice
[   27.261297] usbcore: registered new interface driver libusual
[   27.261398] usbcore: registered new interface driver hiddev
[   27.267588] Initializing USB Mass Storage driver...
[   27.267643] scsi8 : SCSI emulation for USB Mass Storage devices
[   27.267704] usb-storage: device found at 3
[   27.267706] usb-storage: waiting for device to settle before scanning
[   27.268118]  sdb5 >
[   27.268213] sd 3:0:0:0: [sdb] Attached SCSI disk
[   27.271202] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/input/input1
[   27.275437] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   27.275458] sd 3:0:0:0: Attached scsi generic sg1 type 0
[   27.295939] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-3
[   27.307156] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input2
[   27.319863] input,hidraw1: USB HID v1.11 Keyboard [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:0b.0-4
[   27.348866] input: Chicony Saitek Eclipse II Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.1/input/input3
[   27.359681] input,hiddev96,hidraw2: USB HID v1.11 Device [Chicony Saitek Eclipse II Keyboard] on usb-0000:00:0b.0-4
[   27.359699] usbcore: registered new interface driver usbhid
[   27.359702] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   27.359996] usbcore: registered new interface driver usb-storage
[   27.359999] USB Mass Storage support registered.
[   27.501878] Attempting manual resume
[   27.501883] swsusp: Resume From Partition 8:21
[   27.501884] PM: Checking swsusp image.
[   27.502024] PM: Resume from disk failed.
[   27.540115] kjournald starting.  Commit interval 5 seconds
[   27.540126] EXT3-fs: mounted filesystem with ordered data mode.
[   32.248201] usb-storage: device scan complete
[   32.249823] scsi 8:0:0:0: CD-ROM            SONY     DVD RW DRU-840A  SS01 PQ: 0 ANSI: 0
[   32.250182] scsi 8:0:0:0: Attached scsi generic sg2 type 5
[   34.873472] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   34.943527] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   34.979427] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   35.088911] i2c-adapter i2c-0: nForce2 SMBus adapter at 0xf400
[   35.088932] i2c-adapter i2c-1: nForce2 SMBus adapter at 0xf000
[   35.140660] input: Power Button (FF) as /devices/virtual/input/input5
[   35.243529] ACPI: Power Button (FF) [PWRF]
[   35.243602] input: Power Button (CM) as /devices/virtual/input/input6
[   35.306324] ACPI: Power Button (CM) [PWRB]
[   36.184732] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   36.184740] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 21
[   36.201123] Linux agpgart interface v0.102
[   36.251033] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   36.251038] ACPI: PCI Interrupt 0000:00:0f.1[B] -> Link [AAZA] -> GSI 20 (level, low) -> IRQ 20
[   36.251057] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   36.289879] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   36.336764] nvidia: module license 'NVIDIA' taints kernel.
[   36.616690] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2D11
[   36.616713] usbcore: registered new interface driver usblp
[   36.654865] ACPI: PCI Interrupt Link [AXV5] enabled at IRQ 16
[   36.654873] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [AXV5] -> GSI 16 (level, low) -> IRQ 22
[   36.654882] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   36.655012] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   36.804109] Driver 'sr' needs updating - please use bus_type methods
[   36.826279] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   36.826284] Uniform CD-ROM driver Revision: 3.20
[   36.826336] sr 8:0:0:0: Attached scsi CD-ROM sr0
[   37.725897] lp: driver loaded but no devices found
[   37.857998] Adding 3229024k swap on /dev/sdb5.  Priority:-1 extents:1 across:3229024k
[   38.408465] EXT3 FS on sdb1, internal journal
[   39.534959] ip_tables: (C) 2000-2006 Netfilter Core Team
[   39.973168] No dock devices found.
[   41.179398] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   41.179403] apm: disabled - APM is not SMP safe.
[   41.309350] ppdev: user-space parallel port driver
[   41.493042] audit(1223568354.897:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5342 profile="/usr/sbin/cupsd" namespace="default"
[   43.038643] eth1: no link during initialization.
[   43.173641] Bluetooth: Core ver 2.11
[   43.173963] NET: Registered protocol family 31
[   43.173968] Bluetooth: HCI device and connection manager initialized
[   43.173972] Bluetooth: HCI socket layer initialized
[   43.216663] Bluetooth: L2CAP ver 2.9
[   43.216669] Bluetooth: L2CAP socket layer initialized
[   43.222381] Bluetooth: RFCOMM socket layer initialized
[   43.222396] Bluetooth: RFCOMM TTY layer initialized
[   43.222399] Bluetooth: RFCOMM ver 1.8
[   46.809501] NET: Registered protocol family 17
[   51.207757] NET: Registered protocol family 10
[   51.208093] lo: Disabled Privacy Extensions
[   51.209453] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   62.036662] eth0: no IPv6 routers present
[  744.191775] usb 1-9: new high speed USB device using ehci_hcd and address 6
[  744.326790] usb 1-9: configuration #1 chosen from 1 choice
[  744.327524] scsi9 : SCSI emulation for USB Mass Storage devices
[  744.327962] usb-storage: device found at 6
[  744.327967] usb-storage: waiting for device to settle before scanning
[  749.311636] usb-storage: device scan complete
[  749.314376] scsi 9:0:0:0: Direct-Access     WDC WD80 0UE-00KVT0       0000 PQ: 0 ANSI: 0
[  749.318718] sd 9:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[  749.320716] sd 9:0:0:0: [sdc] Write Protect is off
[  749.320721] sd 9:0:0:0: [sdc] Mode Sense: 27 00 00 00
[  749.320724] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[  749.324699] sd 9:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[  749.326698] sd 9:0:0:0: [sdc] Write Protect is off
[  749.326704] sd 9:0:0:0: [sdc] Mode Sense: 27 00 00 00
[  749.326707] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[  749.326712]  sdc: sdc1
[  749.371144] sd 9:0:0:0: [sdc] Attached SCSI disk
[  749.371191] sd 9:0:0:0: Attached scsi generic sg3 type 0
raf@blkbox:~$ tail /var/log/messages
Oct  9 12:17:40 blkbox kernel: [  744.327524] scsi9 : SCSI emulation for USB Mass Storage devices
Oct  9 12:17:45 blkbox kernel: [  749.314376] scsi 9:0:0:0: Direct-Access     WDC WD80 0UE-00KVT0       0000 PQ: 0 ANSI: 0
Oct  9 12:17:45 blkbox kernel: [  749.318718] sd 9:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
Oct  9 12:17:45 blkbox kernel: [  749.320716] sd 9:0:0:0: [sdc] Write Protect is off
Oct  9 12:17:45 blkbox kernel: [  749.324699] sd 9:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
Oct  9 12:17:45 blkbox kernel: [  749.326698] sd 9:0:0:0: [sdc] Write Protect is off
Oct  9 12:17:45 blkbox kernel: [  749.326712]  sdc: sdc1
Oct  9 12:17:45 blkbox kernel: [  749.371144] sd 9:0:0:0: [sdc] Attached SCSI disk
Oct  9 12:17:45 blkbox kernel: [  749.371191] sd 9:0:0:0: Attached scsi generic sg3 type 0
Oct  9 12:45:53 blkbox -- MARK --

---

### Post by medic2000 on 2008-10-09
Try to mount with ntfs-3g force option:

mount -t ntfs-3g -o force /dev/disk1s1 /Volumes/C-DRIVE

Instead of the /dev/disk1s1 write the name of your partition and for /Volumes/C-DRIVE write where you want to mount.

---

### Post by WarTor on 2008-10-09
it gave me this:

> raf@blkbox:~$ mount -t ntfs-3g -o force/dev/disk1 s1 volumes/C-Drive
mount: only root can do that
raf@blkbox:~$ sudo mount -t ntfs-3g -o force/dev/disk1 s1 volumes/C-Drive
[sudo] password for raf: 
ntfs-3g: Failed to access volume 's1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
raf@blkbox:~$ 


---

### Post by WWSmith36 on 2008-10-09
> Instead of the /dev/disk1s1 write the name of your partition and for /Volumes/C-DRIVE write where you want to mount.

I think you were supposed to change the names for your specific device.  Looks like the device is sdc1.  If you mount it to the media folder it should show up on your desktop

```
sudo mkdir /media/external
sudo mount -t ntfs-3g /dev/sdc1 /media/external -o force
```

Hope this helps

---

### Post by WarTor on 2008-10-09
> **medic2000 said:**
> Try to mount with ntfs-3g force option:

mount -t ntfs-3g -o force /dev/disk1s1 /Volumes/C-DRIVE

Instead of the /dev/disk1s1 write the name of your partition and for /Volumes/C-DRIVE write where you want to mount.

im not sure what you mean when you said " where you wanted it mount"? can you please explain? thanks!

---

### Post by WarTor on 2008-10-09
> **WWSmith36 said:**
> I think you were supposed to change the names for your specific device.  Looks like the device is sdc1.  If you mount it to the media folder it should show up on your desktop

```
sudo mkdir /media/external
sudo mount -t ntfs-3g /dev/sdc1 /media/external -o force
```

Hope this helps

thanks!

---

### Post by WarTor on 2008-10-09
YOU GUYS ROCK!!!!

it worked just fine!

thanks to all for the help!

:D :D

---

### Post by medic2000 on 2008-10-09
> **WarTor said:**
> YOU GUYS ROCK!!!!

it worked just fine!

thanks to all for the help!

:D :D

You are welcome :)

---

### Post by medic2000 on 2008-10-09
**CAUTION** Be careful using force mount. Use this when you have to only.

[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by WarTor on 2008-10-09
thanks for the advice :)

i will make sure to go with :D

---

