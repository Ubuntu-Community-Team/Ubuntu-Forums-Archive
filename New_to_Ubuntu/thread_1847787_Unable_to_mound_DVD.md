---
title: "Unable to mound DVD"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by mdavis1231 on 2011-09-21
I'm using Ubuntu 10.04 LTS.  When I insert a DVD into the CDROM, I get this error message.

[[IMG]http://i1223.photobucket.com/albums/dd512/mdavis1231/th_Screenshot.png[/IMG]]("http://s1223.photobucket.com/albums/dd512/mdavis1231/?action=view&current=Screenshot.png")

Can someone PLEASE help me?

---

### Post by ubudog on 2011-09-21
Hi!

Could you please open a terminal (Applications>Accessories>Terminal), and post the output of:
```
dmesg
```
?

---

### Post by mdavis1231 on 2011-09-21
> **ubudog said:**
> Hi!

Could you please open a terminal (Applications>Accessories>Terminal), and post the output of:
```
dmesg
```?

```

[    0.004168] ... max period:             00007fffffffffff
[    0.004169] ... fixed-purpose events:   0
[    0.004170] ... event mask:             000000000000000f
[    0.004173] Checking 'hlt' instruction... OK.
[    0.021543] ACPI: Core revision 20090903
[    0.028007] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028010] ftrace: allocating 21725 entries in 43 pages
[    0.032086] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032538] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073771] CPU0: AMD Athlon(tm) II X2 250 Processor stepping 02
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.160103] CPU1: AMD Athlon(tm) II X2 250 Processor stepping 02
[    0.160109] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164012] Brought up 2 CPUs
[    0.164014] Total of 2 processors activated (12055.11 BogoMIPS).
[    0.164437] CPU0 attaching sched-domain:
[    0.164440]  domain 0: span 0-1 level MC
[    0.164442]   groups: 0 1
[    0.164446] CPU1 attaching sched-domain:
[    0.164447]  domain 0: span 0-1 level MC
[    0.164449]   groups: 1 0
[    0.164499] devtmpfs: initialized
[    0.164499] regulator: core version 0.5
[    0.164499] Time: 16:06:16  Date: 09/21/11
[    0.164499] NET: Registered protocol family 16
[    0.164499] EISA bus registered
[    0.164499] ACPI: bus type pci registered
[    0.164499] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164499] PCI: MCFG area at e0000000 reserved in E820
[    0.164499] PCI: updated MCFG configuration 0: base e0000000 segment 0 buses 0 - 127
[    0.164499] PCI: Using MMCONFIG for extended config space
[    0.164499] PCI: Using configuration type 1 for base access
[    0.164744] bio: create slab <bio-0> at 0
[    0.164744] Trying to unpack rootfs image as initramfs...
[    0.172673] ACPI: EC: Look up EC in DSDT
[    0.177975] ACPI: Interpreter enabled
[    0.177978] ACPI: (supports S0 S3 S4 S5)
[    0.177992] ACPI: Using IOAPIC for interrupt routing
[    0.182849] ACPI: No dock devices found.
[    0.182914] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.183105] pci 0000:00:01.1: reg 10 io port: [0xfc00-0xfc3f]
[    0.183114] pci 0000:00:01.1: reg 20 io port: [0x1c00-0x1c3f]
[    0.183117] pci 0000:00:01.1: reg 24 io port: [0x1c40-0x1c7f]
[    0.183134] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.183139] pci 0000:00:01.1: PME# disabled
[    0.183181] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
[    0.183199] pci 0000:00:02.0: supports D1 D2
[    0.183201] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183203] pci 0000:00:02.0: PME# disabled
[    0.183222] pci 0000:00:02.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
[    0.183245] pci 0000:00:02.1: supports D1 D2
[    0.183246] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183249] pci 0000:00:02.1: PME# disabled
[    0.183302] pci 0000:00:05.0: reg 10 32bit mmio: [0xfe024000-0xfe027fff]
[    0.183325] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.183327] pci 0000:00:05.0: PME# disabled
[    0.183355] pci 0000:00:06.0: reg 20 io port: [0xf000-0xf00f]
[    0.183386] pci 0000:00:07.0: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.183389] pci 0000:00:07.0: reg 14 io port: [0xec00-0xec07]
[    0.183407] pci 0000:00:07.0: supports D1 D2
[    0.183409] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.183412] pci 0000:00:07.0: PME# disabled
[    0.183429] pci 0000:00:08.0: reg 10 io port: [0x9f0-0x9f7]
[    0.183432] pci 0000:00:08.0: reg 14 io port: [0xbf0-0xbf3]
[    0.183435] pci 0000:00:08.0: reg 18 io port: [0x970-0x977]
[    0.183438] pci 0000:00:08.0: reg 1c io port: [0xb70-0xb73]
[    0.183440] pci 0000:00:08.0: reg 20 io port: [0xd800-0xd80f]
[    0.183443] pci 0000:00:08.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.183468] pci 0000:00:08.1: reg 10 io port: [0x9e0-0x9e7]
[    0.183471] pci 0000:00:08.1: reg 14 io port: [0xbe0-0xbe3]
[    0.183474] pci 0000:00:08.1: reg 18 io port: [0x960-0x967]
[    0.183476] pci 0000:00:08.1: reg 1c io port: [0xb60-0xb63]
[    0.183479] pci 0000:00:08.1: reg 20 io port: [0xc400-0xc40f]
[    0.183482] pci 0000:00:08.1: reg 24 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.183512] pci 0000:00:0d.0: reg 10 32bit mmio: [0xfb000000-0xfbffffff]
[    0.183516] pci 0000:00:0d.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.183520] pci 0000:00:0d.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.183523] pci 0000:00:0d.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.183621] pci 0000:01:06.0: reg 10 32bit mmio: [0xfdeff000-0xfdeff0ff]
[    0.183626] pci 0000:01:06.0: reg 14 io port: [0xbc00-0xbc07]
[    0.183631] pci 0000:01:06.0: reg 18 io port: [0xb800-0xb8ff]
[    0.183655] pci 0000:01:06.0: supports D2
[    0.183656] pci 0000:01:06.0: PME# supported from D2 D3hot D3cold
[    0.183659] pci 0000:01:06.0: PME# disabled
[    0.183684] pci 0000:00:04.0: transparent bridge
[    0.183686] pci 0000:00:04.0: bridge io port: [0xb000-0xbfff]
[    0.183688] pci 0000:00:04.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.183691] pci 0000:00:04.0: bridge 32bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.183695] pci_bus 0000:00: on NUMA node 0
[    0.183698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.183817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.207163] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[    0.207246] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207328] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207411] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207492] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207574] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207655] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207735] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207817] ACPI: PCI Interrupt Link [LIGP] (IRQs 5 7 9 10 *11 14 15)
[    0.207898] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.207981] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[    0.208073] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[    0.208155] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[    0.208235] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.208317] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[    0.208405] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[    0.208486] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.208567] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[    0.208654] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[    0.208769] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.208877] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.208984] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.209091] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.209197] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.209304] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.209411] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[    0.209518] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.209626] ACPI: PCI Interrupt Link [AIGP] (IRQs 20 21 22 23) *0
[    0.209734] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.209842] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.209949] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.210057] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.210164] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.210273] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.210380] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.210488] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.210597] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.210705] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.210777] vgaarb: device added: PCI:0000:00:0d.0,decodes=io+mem,owns=io+mem,locks=none
[    0.210780] vgaarb: loaded
[    0.210859] SCSI subsystem initialized
[    0.216022] libata version 3.00 loaded.
[    0.216099] usbcore: registered new interface driver usbfs
[    0.216099] usbcore: registered new interface driver hub
[    0.216099] usbcore: registered new device driver usb
[    0.216136] ACPI: WMI: Mapper loaded
[    0.216138] PCI: Using ACPI for IRQ routing
[    0.216239] NetLabel: Initializing
[    0.216240] NetLabel:  domain hash size = 128
[    0.216241] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.216250] NetLabel:  unlabeled traffic allowed by default
[    0.216279] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.216283] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.218301] Switching to clocksource tsc
[    0.218597] AppArmor: AppArmor Filesystem Enabled
[    0.218597] pnp: PnP ACPI init
[    0.218597] ACPI: bus type pnp registered
[    0.219697] pnp: PnP ACPI: found 14 devices
[    0.219699] ACPI: ACPI bus type pnp unregistered
[    0.219702] PnPBIOS: Disabled by ACPI PNP
[    0.219711] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.219713] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.219715] system 00:01: ioport range 0x1400-0x147f has been reserved
[    0.219717] system 00:01: ioport range 0x1480-0x14ff has been reserved
[    0.219718] system 00:01: ioport range 0x1800-0x187f has been reserved
[    0.219720] system 00:01: ioport range 0x1880-0x18ff has been reserved
[    0.219723] system 00:01: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.219725] system 00:01: iomem range 0xfefe1000-0xfefe10ff has been reserved
[    0.219727] system 00:01: iomem range 0xcc000000-0xcfffffff has been reserved
[    0.219731] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.219733] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.219735] system 00:02: ioport range 0x295-0x296 has been reserved
[    0.219737] system 00:02: ioport range 0x290-0x294 has been reserved
[    0.219742] system 00:0c: iomem range 0xe0000000-0xe7ffffff has been reserved
[    0.219745] system 00:0d: iomem range 0xd0000-0xd3fff has been reserved
[    0.219747] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.219749] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.219751] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.219753] system 00:0d: iomem range 0xcbff0000-0xcbffffff could not be reserved
[    0.219755] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.219757] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.219759] system 00:0d: iomem range 0x100000-0xcbfeffff could not be reserved
[    0.219761] system 00:0d: iomem range 0xcc000000-0xcfffffff has been reserved
[    0.219763] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.219765] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.254383] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.254385] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    0.254388] pci 0000:00:04.0:   MEM window: 0xfde00000-0xfdefffff
[    0.254391] pci 0000:00:04.0:   PREFETCH window: 0xfdf00000-0xfdffffff
[    0.254398] pci 0000:00:04.0: setting latency timer to 64
[    0.254401] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.254403] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.254405] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.254407] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.254409] pci_bus 0000:01: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.254410] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.254412] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.254437] NET: Registered protocol family 2
[    0.254504] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.254718] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.255131] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.255347] TCP: Hash tables configured (established 131072 bind 65536)
[    0.255348] TCP reno registered
[    0.255422] NET: Registered protocol family 1
[    0.289625] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.289670] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.289723] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.289774] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.289825] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.289829] pci 0000:00:0d.0: Boot video device
[    0.289979] cpufreq-nforce2: No nForce2 chipset.
[    0.289996] Scanning for low memory corruption every 60 seconds
[    0.290071] audit: initializing netlink socket (disabled)
[    0.290080] type=2000 audit(1316621176.289:1): initialized
[    0.296094] highmem bounce pool size: 64 pages
[    0.296097] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.296987] VFS: Disk quotas dquot_6.5.2
[    0.297023] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.297376] fuse init (API version 7.13)
[    0.297427] msgmni has been set to 1659
[    0.297570] alg: No test for stdrng (krng)
[    0.297604] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.297606] io scheduler noop registered
[    0.297607] io scheduler anticipatory registered
[    0.297609] io scheduler deadline registered
[    0.297635] io scheduler cfq registered (default)
[    0.297695] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.297709] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.297777] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.297780] ACPI: Power Button [PWRB]
[    0.297817] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.297818] ACPI: Power Button [PWRF]
[    0.298037] processor LNXCPU:00: registered as cooling_device0
[    0.298057] processor LNXCPU:01: registered as cooling_device1
[    0.300991] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.301074] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.301288] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.301906] brd: module loaded
[    0.302170] loop: module loaded
[    0.302219] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.302318] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.302523] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.302527]   alloc irq_desc for 23 on node -1
[    0.302528]   alloc kstat_irqs on node -1
[    0.302536] pata_acpi 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.302546] pata_acpi 0000:00:08.0: setting latency timer to 64
[    0.302550] pata_acpi 0000:00:08.0: PCI INT A disabled
[    0.302731] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.302733]   alloc irq_desc for 22 on node -1
[    0.302734]   alloc kstat_irqs on node -1
[    0.302739] pata_acpi 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.302748] pata_acpi 0000:00:08.1: setting latency timer to 64
[    0.302753] pata_acpi 0000:00:08.1: PCI INT B disabled
[    0.302932] Fixed MDIO Bus: probed
[    0.302951] PPP generic driver version 2.4.2
[    0.302975] tun: Universal TUN/TAP device driver, 1.6
[    0.302976] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.303020] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.303202] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.303203]   alloc irq_desc for 21 on node -1
[    0.303205]   alloc kstat_irqs on node -1
[    0.303210] ehci_hcd 0000:00:02.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.303217] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.303219] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.303238] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.303254] ehci_hcd 0000:00:02.1: debug port 1
[    0.303260] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.303275] ehci_hcd 0000:00:02.1: irq 21, io mem 0xfe02e000
[    0.303309] isapnp: Scanning for PnP cards...
[    0.331757] Freeing initrd memory: 7817k freed
[    0.334305] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.334410] usb usb1: configuration #1 chosen from 1 choice
[    0.334430] hub 1-0:1.0: USB hub found
[    0.334437] hub 1-0:1.0: 10 ports detected
[    0.334490] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.334735] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.334739]   alloc irq_desc for 20 on node -1
[    0.334740]   alloc kstat_irqs on node -1
[    0.334749] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.334762] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.334764] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.334791] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.334813] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    0.391507] usb usb2: configuration #1 chosen from 1 choice
[    0.391526] hub 2-0:1.0: USB hub found
[    0.391534] hub 2-0:1.0: 10 ports detected
[    0.391579] uhci_hcd: USB Universal Host Controller Interface driver
[    0.391633] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.392053] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.392059] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.392105] mice: PS/2 mouse device common for all mice
[    0.392173] rtc_cmos 00:05: RTC can wake from S4
[    0.392196] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.392231] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.392294] device-mapper: uevent: version 1.0.3
[    0.392363] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.392405] device-mapper: multipath: version 1.1.0 loaded
[    0.392407] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.392474] EISA: Probing bus 0 at eisa.0
[    0.392478] Cannot allocate resource for EISA slot 1
[    0.392494] EISA: Detected 0 cards.
[    0.392536] cpuidle: using governor ladder
[    0.392537] cpuidle: using governor menu
[    0.392796] TCP cubic registered
[    0.392888] NET: Registered protocol family 10
[    0.393384] NET: Registered protocol family 17
[    0.393410] powernow-k8: Found 1 AMD Athlon(tm) II X2 250 Processor processors (2 cpu cores) (version 2.20.00)
[    0.393440] powernow-k8:    0 : pstate 0 (3000 MHz)
[    0.393441] powernow-k8:    1 : pstate 1 (2300 MHz)
[    0.393443] powernow-k8:    2 : pstate 2 (1800 MHz)
[    0.393444] powernow-k8:    3 : pstate 3 (800 MHz)
[    0.395574] Using IPI No-Shortcut mode
[    0.395620] PM: Resume from disk failed.
[    0.395627] registered taskstats version 1
[    0.395816]   Magic number: 11:358:136
[    0.395824] block ram1: hash matches
[    0.395891] rtc_cmos 00:05: setting system clock to 2011-09-21 16:06:16 UTC (1316621176)
[    0.395893] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.395894] EDD information not available.
[    0.411355] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.645435] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.656355] isapnp: No Plug & Play device found
[    0.656387] Freeing unused kernel memory: 668k freed
[    0.656655] Write protecting the kernel text: 4676k
[    0.656678] Write protecting the kernel read-only data: 1848k
[    0.672194] udev: starting version 151
[    0.719944] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.720185] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    0.720189] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    0.720193] forcedeth 0000:00:07.0: setting latency timer to 64
[    0.778511] usb 1-2: configuration #1 chosen from 1 choice
[    0.782652] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 3, addr 6c:f0:49:9c:dd:f6
[    0.782655] forcedeth 0000:00:07.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    0.782694] sata_nv 0000:00:08.0: version 3.5
[    0.782708] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.782746] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.782813] scsi0 : sata_nv
[    0.782956] scsi1 : sata_nv
[    0.783088] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 23
[    0.783090] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 23
[    0.783122] pata_amd 0000:00:06.0: version 0.4.1
[    0.783152] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.783247] scsi2 : pata_amd
[    0.783314] scsi3 : pata_amd
[    0.783783] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.783786] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.783840] sata_nv 0000:00:08.1: PCI INT B -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.783874] sata_nv 0000:00:08.1: setting latency timer to 64
[    0.784003] scsi4 : sata_nv
[    0.784046] scsi5 : sata_nv
[    0.784135] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 22
[    0.784137] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 22
[    0.946958] ata3.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
[    0.946961] ata3.00: 78165360 sectors, multi 16: LBA 
[    0.946979] ata3: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
[    0.962743] ata3.00: configured for UDMA/100
[    1.082266] ata5: SATA link down (SStatus 0 SControl 300)
[    1.192036] usb 2-7: new full speed USB device using ohci_hcd and address 2
[    1.228555] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.236163] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB02, max UDMA/100
[    1.416536] usb 2-7: configuration #1 chosen from 1 choice
[    1.844175] ata1.00: configured for UDMA/100
[    1.847535] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB02 PQ: 0 ANSI: 5
[    1.854670] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.854674] Uniform CD-ROM driver Revision: 3.20
[    1.854774] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.854828] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.174260] ata2: SATA link down (SStatus 0 SControl 300)
[    2.174397] scsi 2:0:0:0: Direct-Access     ATA      WDC WD400EB-11CP 06.0 PQ: 0 ANSI: 5
[    2.174528] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.174569] sd 2:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    2.174581] ata4: port disabled. ignoring.
[    2.174624] sd 2:0:0:0: [sda] Write Protect is off
[    2.174626] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.174653] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.174798]  sda: sda1 sda3 < sda5 >
[    2.229351] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.494257] ata6: SATA link down (SStatus 0 SControl 300)
[    2.497086] usbcore: registered new interface driver hiddev
[    2.504460] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:02.0/usb2/2-7/2-7:1.3/input/input4
[    2.504532] generic-usb 0003:046D:0A0C.0001: input,hidraw0: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:02.0-7/input3
[    2.504551] usbcore: registered new interface driver usbhid
[    2.504553] usbhid: v2.6:USB HID core driver
[    2.919302] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   33.923593] udev: starting version 151
[   33.977687] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   33.977715] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   33.988644] vga16fb: initializing
[   33.988649] vga16fb: mapped to 0xc00a0000
[   33.988695] fb0: VGA16 VGA frame buffer device
[   34.011801] Adding 1648632k swap on /dev/sda5.  Priority:-1 extents:1 across:1648632k 
[   34.041524] lp: driver loaded but no devices found
[   34.054975] Linux agpgart interface v0.103
[   34.146543] type=1505 audit(1316621210.248:2):  operation="profile_load" pid=727 name="/sbin/dhclient3"
[   34.146735] type=1505 audit(1316621210.248:3):  operation="profile_load" pid=727 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   34.146845] type=1505 audit(1316621210.248:4):  operation="profile_load" pid=727 name="/usr/lib/connman/scripts/dhclient-script"
[   34.147612] type=1505 audit(1316621210.248:5):  operation="profile_replace" pid=742 name="/sbin/dhclient3"
[   34.147805] type=1505 audit(1316621210.248:6):  operation="profile_replace" pid=742 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   34.147916] type=1505 audit(1316621210.248:7):  operation="profile_replace" pid=742 name="/usr/lib/connman/scripts/dhclient-script"
[   34.185799] nvidia: module license 'NVIDIA' taints kernel.
[   34.185802] Disabling lock debugging due to kernel taint
[   34.273099] Console: switching to colour frame buffer device 80x30
[   34.427548] psmouse serio1: ID: 10 00 64
[   34.889619] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2504
[   34.889632] usbcore: registered new interface driver usblp
[   34.890192] parport_pc 00:09: reported by Plug and Play ACPI
[   34.890234] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   34.898908] ppdev: user-space parallel port driver
[   34.945154] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   34.945159] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   34.945162] hda_intel: Disable MSI for Nvidia chipset
[   34.945181] HDA Intel 0000:00:05.0: setting latency timer to 64
[   34.988677] lp0: using parport0 (interrupt-driven).
[   35.078964] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   35.154513] usbcore: registered new interface driver snd-usb-audio
[   35.528602] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input6
[   35.689332] type=1505 audit(1316621211.792:8):  operation="profile_load" pid=951 name="/usr/share/gdm/guest-session/Xsession"
[   35.689470] type=1505 audit(1316621211.792:9):  operation="profile_replace" pid=952 name="/sbin/dhclient3"
[   35.689675] type=1505 audit(1316621211.792:10):  operation="profile_replace" pid=952 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   35.689791] type=1505 audit(1316621211.792:11):  operation="profile_replace" pid=952 name="/usr/lib/connman/scripts/dhclient-script"
[   35.720911] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
[   35.720917] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
[   35.720922] nvidia 0000:00:0d.0: setting latency timer to 64
[   35.720926] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   35.721043] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   35.752735]   alloc irq_desc for 24 on node -1
[   35.752738]   alloc kstat_irqs on node -1
[   35.752745] forcedeth 0000:00:07.0: irq 24 for MSI/MSI-X
[   40.475560] CPU0 attaching NULL sched-domain.
[   40.475565] CPU1 attaching NULL sched-domain.
[   40.492560] CPU0 attaching sched-domain:
[   40.492564]  domain 0: span 0-1 level MC
[   40.492566]   groups: 0 1
[   40.492571] CPU1 attaching sched-domain:
[   40.492573]  domain 0: span 0-1 level MC
[   40.492574]   groups: 1 0
[   42.697682] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   43.320457] vboxdrv: Found 2 processor cores.
[   43.327655] vboxdrv: fAsync=0 offMin=0x508 offMax=0xbf3
[   43.328342] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   43.328344] vboxdrv: Successfully loaded version 4.1.2 (interface 0x00190000).
[   43.591726] vboxpci: IOMMU not found (not compiled)
[   45.458804] usb 1-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   46.076022] eth0: no IPv6 routers present
[   84.834922] ISOFS: Bad logical zone size 25169
[  189.141686] ISOFS: Interleaved files not (yet) supported.
[  189.141695] ISOFS: File unit size != 0 for ISO file (16576).
[  189.141704] isofs_fill_super: root inode is not a directory. Corrupted media?
[  323.056041] ISOFS: Bad logical zone size 43926

```

---

### Post by ubudog on 2011-09-21
Is the DVD scratched/dirty?

Also, insert the DVD and post the output of:

```
mount
```

and:

```
ls /media
```

---

### Post by mdavis1231 on 2011-09-21
> **ubudog said:**
> Is the DVD scratched/dirty?

Also, insert the DVD and post the output of:

```
mount
```and:

```
ls /media
```

mdavis1231@mdavis1231-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/mdavis1231/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mdavis1231)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sr0 on /media/POSEIDON THE MOVIE type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1002,gid=1002,iocharset=utf8,mode=0400,dmode=0500)


mdavis1231@mdavis1231-desktop:~$ ls /media
POSEIDON THE MOVIE

---

### Post by ubudog on 2011-09-22
Try:

```
cd /media/POSEIDON\ THE\ MOVIE
```

and then post the output of:
```
ls
```

---

### Post by mdavis1231 on 2011-09-23
OK, I reinstalled Ubuntu 10.04, and Totem was playing DVD's fine until I completely uninstalled PulseAudio. Now it opens to start playing the DVD, then immediately closes.
 
Has anyone else had this problem, and is there a solution? Mplayer will play the DVD's just fine, but I prefer Totem. It's what I've always used.
 
Any help would be greatly appreciated.

---

### Post by mdavis1231 on 2011-09-24
OK, I figured out what happened.  The reason that I can't have PulseAudio on my Ubuntu is that I use Skype with a Logitech USB headset, which will only work with ALSA.  As long as PulseAudio is present, the newest Skype will ONLY use PulseAudio.

Up until Ubuntu 10.04.2, I had been using a method called "Elegantly Disabling PulseAudio" - [http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12) - because when trying to completely remove PulseAudio, it was saying that I would also remove ubuntu-desktop **(I have since learned that the "ubuntu-desktop" listed that will be removed is only a 'dummy' package to discourage you from removing PulseAudio - _it_ _doesn't_ _actually_ _remove_ _your_ _desktop_)**.  Somewhere in between Ubuntu 10.04.2 and Ubuntu 10.04.3, an update caused "Elegantly Disabling PulseAudio" to no longer work, thus breaking Totem's ability to play DVD's. (?)

I reinstalled Ubuntu 10.04.3, and _**completely**_ removed PulseAudio using 'sudo apt-get purge pulseaudio'.  Then, I used 'sudo apt-get remove indicator-sound' to remove the sound indicator for PulseAudio.  I then added:

deb [http://ppa.launchpad.net/dtl131/ppa/ubuntu](http://ppa.launchpad.net/dtl131/ppa/ubuntu) [COLOR=green]lucid[/COLOR] main
deb-src [http://ppa.launchpad.net/dtl131/ppa/ubuntu](http://ppa.launchpad.net/dtl131/ppa/ubuntu) [COLOR=green]lucid[/COLOR] main

to software sources and ran:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com F76FFEBE
sudo apt-get update && sudo apt-get upgrade

to restore the ALSA volume controls in gnome-panel.

Now I've completely and _**safely**_ removed PulseAudio, and everything is working perfectly!!!

I put a lot of time into figuring this out, so if anyone has any questions or needs any help, please feel free to send me a message, and I'll get back to you as quickly as possible.

---

### Post by Lisiano on 2011-09-24
I'd like to say... Why did you remove Pulse? It works fine with Skype.
Only thing that changes is that Skype will list only Pulse in it's config but you can easily change what's the input (Mic) and output (Headphones/speaker) in the sound applet or by using pavucontrol and directly tell Pulse to only use your USB headset in Skype (Persistent until you set a new default input)


Also the "ubuntu-desktop" package is not there to discourage you from uninstalling Pulse, it's there to help you update and install Ubuntu if you run Kubuntu, Xubuntu, Lubuntu, Ubuntu Server. Same for "kubuntu-desktop", "xubuntu-desktop", "lubuntu-desktop".

EDIT: If you use ALSA without Pulse, you can't play music AND use Skype to chat, view videos and Skype, etc. You can only have 1 sound source on 1 output. No exceptions. Pulse works around that by mixing the sounds together, it still uses ALSA. Also anything that works with ALSA will work with Pulse.

---

