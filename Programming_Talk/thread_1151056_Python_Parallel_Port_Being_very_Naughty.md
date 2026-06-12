---
title: "Python Parallel Port Being very Naughty"
date: 2009-05-06
forum: Programming Talk
---

### Post by UbuKunubi on 2009-05-06
Hello Folks,

Im working on a CNC project, to build an engraver, and i've got most of the heavy coding done [ [http://ubuntuforums.org/showthread.php?t=1148869]](http://ubuntuforums.org/showthread.php?t=1148869]).

I searched this forum, and the wider web about an error message which gets thrown.
Im using Python 2.6. on Jaunty 9.04.
The error message is:
OSError: [Errno 2] No such file or directory: '/dev/parport0'

Doing a search reveals that i should be doing this:

sudo rmmod lp
sudo modprobe ppdev

Which STILL yeilds the same results....... Can anyone help?

I searched further and then attempted to manually creat the parpoint device with:
~# mknod /dev/parport0 c 99 0
~# chmod a+rw /dev/parport0
 and now the error message (from IDLE) is::

    IOError: [Errno 6] No such device or address

How do I fix this? Will I need my chicken blood for the vodoo??

---

### Post by regomodo on 2009-05-06
#

---

### Post by UbuKunubi on 2009-05-07
I've now been right through the BIOS, and tried booting and then running the program with the following settings:

SPP
EPP (1.9 and 1.7)
ECP (DMA mode 1 & 3)
ECP + EPP 
and Normal

Still no joy.

BUT while booting I get a very quick glimpse of an error message after Jaunty tells me about which device its booting from:

MS-BIOS 8254 bug, ..... ASPIC error 

The line of text blinks into and out of vision so fast its a stuggle to make the complete message out, so I dont think the above error messge is complete.

---

### Post by regomodo on 2009-05-07
#

---

### Post by UbuKunubi on 2009-05-08
Here's the reply from dmesg (as root)

[    0.304001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.304001] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.304001] ..... (found apic 0 pin 0) ...
[    0.340446] ....... works.
[    0.340449] CPU0: AMD Athlon(tm)  stepping 00
[    0.448001] Brought up 1 CPUs
[    0.448001] Total of 1 processors activated (2200.03 BogoMIPS).
[    0.448001] CPU0 attaching NULL sched-domain.
[    0.448001] net_namespace: 776 bytes
[    0.448001] Booting paravirtualized kernel on bare hardware
[    0.448001] Time:  6:57:49  Date: 05/08/09
[    0.448001] regulator: core version 0.5
[    0.448001] NET: Registered protocol family 16
[    0.448001] EISA bus registered
[    0.478441] PCI: PCI BIOS revision 2.10 entry at 0xfbe50, last bus=2
[    0.478446] PCI: Using configuration type 1 for base access
[    0.480173] ACPI: Interpreter disabled.
[    0.480475] SCSI subsystem initialized
[    0.480562] libata version 3.00 loaded.
[    0.480658] usbcore: registered new interface driver usbfs
[    0.480686] usbcore: registered new interface driver hub
[    0.480743] usbcore: registered new device driver usb
[    0.480976] PCI: Probing PCI hardware
[    0.480982] PCI: Probing PCI hardware (bus 00)
[    0.481053] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    0.481362] pci 0000:00:01.1: reg 10 io port: [0xec00-0xec1f]
[    0.481404] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.481411] pci 0000:00:01.1: PME# disabled
[    0.481454] pci 0000:00:02.0: reg 10 32bit mmio: [0xeb001000-0xeb001fff]
[    0.481494] pci 0000:00:02.0: supports D1 D2
[    0.481498] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.481505] pci 0000:00:02.0: PME# disabled
[    0.481540] pci 0000:00:02.1: reg 10 32bit mmio: [0xeb002000-0xeb002fff]
[    0.481580] pci 0000:00:02.1: supports D1 D2
[    0.481584] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.481590] pci 0000:00:02.1: PME# disabled
[    0.481633] pci 0000:00:02.2: reg 10 32bit mmio: [0xeb003000-0xeb0030ff]
[    0.481676] pci 0000:00:02.2: supports D1 D2
[    0.481680] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.481687] pci 0000:00:02.2: PME# disabled
[    0.481731] pci 0000:00:04.0: reg 10 32bit mmio: [0xeb000000-0xeb000fff]
[    0.481741] pci 0000:00:04.0: reg 14 io port: [0xe800-0xe807]
[    0.481776] pci 0000:00:04.0: supports D1 D2
[    0.481780] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.481786] pci 0000:00:04.0: PME# disabled
[    0.481822] pci 0000:00:06.0: reg 10 io port: [0xe000-0xe0ff]
[    0.481832] pci 0000:00:06.0: reg 14 io port: [0xe400-0xe47f]
[    0.481841] pci 0000:00:06.0: reg 18 32bit mmio: [0xeb004000-0xeb004fff]
[    0.481872] pci 0000:00:06.0: supports D1 D2
[    0.481957] pci 0000:00:09.0: reg 20 io port: [0xf000-0xf00f]
[    0.482074] pci 0000:02:07.0: reg 10 32bit mmio: [0xe8000000-0xe8001fff]
[    0.482166] pci 0000:00:08.0: bridge 32bit mmio: [0xe8000000-0xe8ffffff]
[    0.482217] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xd7ffffff]
[    0.482227] pci 0000:01:00.0: reg 14 io port: [0xd000-0xd0ff]
[    0.482236] pci 0000:01:00.0: reg 18 32bit mmio: [0xea000000-0xea00ffff]
[    0.482261] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.482275] pci 0000:01:00.0: supports D1 D2
[    0.482313] pci 0000:01:00.1: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.482323] pci 0000:01:00.1: reg 14 32bit mmio: [0xea010000-0xea01ffff]
[    0.482359] pci 0000:01:00.1: supports D1 D2
[    0.482414] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.482421] pci 0000:00:1e.0: bridge 32bit mmio: [0xe9000000-0xeaffffff]
[    0.482428] pci 0000:00:1e.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.483160] pci 0000:00:00.0: default IRQ router [10de:01e0]
[    0.483212] pci 0000:02:07.0: PCI->APIC IRQ transform: INT A -> IRQ 19
[    0.483356] Bluetooth: Core ver 2.13
[    0.483356] NET: Registered protocol family 31
[    0.483356] Bluetooth: HCI device and connection manager initialized
[    0.483356] Bluetooth: HCI socket layer initialized
[    0.483356] NET: Registered protocol family 8
[    0.483356] NET: Registered protocol family 20
[    0.483356] NetLabel: Initializing
[    0.483356] NetLabel:  domain hash size = 128
[    0.483356] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.483356] NetLabel:  unlabeled traffic allowed by default
[    0.483356] AppArmor: AppArmor Filesystem Enabled
[    0.483356] pnp: PnP ACPI: disabled
[    0.483356] PnPBIOS: Scanning system for PnP BIOS support...
[    0.483356] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc8c0
[    0.483356] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc8f0, dseg 0xf0000
[    0.484383] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[    0.484412] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[    0.484419] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[    0.484425] system 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.484430] system 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[    0.484436] system 00:07: iomem range 0x100000-0xffffff could not be reserved
[    0.484446] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[    0.484452] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[    0.484457] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
[    0.484462] system 00:08: iomem range 0xd1800-0xd3fff has been reserved
[    0.484802] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.484807] pci 0000:00:08.0:   IO window: disabled
[    0.484816] pci 0000:00:08.0:   MEM window: 0xe8000000-0xe8ffffff
[    0.484822] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.484836] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.484841] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.484849] pci 0000:00:1e.0:   MEM window: 0xe9000000-0xeaffffff
[    0.484856] pci 0000:00:1e.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.484874] pci 0000:00:08.0: setting latency timer to 64
[    0.484886] bus: 00 index 0 io port: [0x00-0xffff]
[    0.484890] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.484894] bus: 02 index 0 mmio: [0x0-0x0]
[    0.484898] bus: 02 index 1 mmio: [0xe8000000-0xe8ffffff]
[    0.484902] bus: 02 index 2 mmio: [0x0-0x0]
[    0.484905] bus: 02 index 3 mmio: [0x0-0x0]
[    0.484909] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.484913] bus: 01 index 1 mmio: [0xe9000000-0xeaffffff]
[    0.484917] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.484921] bus: 01 index 3 mmio: [0x0-0x0]
[    0.484936] NET: Registered protocol family 2
[    0.485145] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.485834] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.488355] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.489640] TCP: Hash tables configured (established 131072 bind 65536)
[    0.489645] TCP reno registered
[    0.489862] NET: Registered protocol family 1
[    0.490116] checking if image is initramfs... it is
[    1.622774] Freeing initrd memory: 7349k freed
[    1.622978] cpufreq: Detected nForce2 chipset revision C1
[    1.622982] cpufreq: FSB changing is maybe unstable and can lead to crashes and data loss.
[    1.623002] cpufreq: FSB currently at 100 MHz, FID 11.0
[    1.623296] audit: initializing netlink socket (disabled)
[    1.623328] type=2000 audit(1241765870.620:1): initialized
[    1.637466] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.639878] VFS: Disk quotas dquot_6.5.1
[    1.639992] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.641152] fuse init (API version 7.10)
[    1.641294] msgmni has been set to 1498
[    1.641648] alg: No test for stdrng (krng)
[    1.641673] io scheduler noop registered
[    1.641677] io scheduler anticipatory registered
[    1.641681] io scheduler deadline registered
[    1.641723] io scheduler cfq registered (default)
[    1.641994] pci 0000:01:00.0: Boot video device
[    1.642157] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.642174] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.642299] isapnp: Scanning for PnP cards...
[    1.996775] isapnp: No Plug & Play device found
[    1.998734] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.998864] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.999382] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.000738] brd: module loaded
[    2.001323] loop: module loaded
[    2.001454] Fixed MDIO Bus: probed
[    2.001466] PPP generic driver version 2.4.2
[    2.001577] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.001626] Driver 'sd' needs updating - please use bus_type methods
[    2.001643] Driver 'sr' needs updating - please use bus_type methods
[    2.002059] pata_amd 0000:00:09.0: version 0.3.10
[    2.002165] pata_amd 0000:00:09.0: setting latency timer to 64
[    2.002339] scsi0 : pata_amd
[    2.002529] scsi1 : pata_amd
[    2.002592] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.002597] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    2.220614] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
[    2.220619] ata1.00: 156301488 sectors, multi 1: LBA48 
[    2.220660] ata1: nv_mode_filter: 0x3f39f&0xfffff->0x3f39f, BIOS=0x0 (0x0) ACPI=0x0
[    2.236570] ata1.00: configured for UDMA/100
[    2.400385] ata2.00: ATAPI: LITE-ON DVDRW SOHW-1633S, BS0C, max UDMA/66
[    2.400424] ata2: nv_mode_filter: 0x1f39f&0xfffff->0x1f39f, BIOS=0x0 (0x0) ACPI=0x0
[    2.416360] ata2.00: configured for UDMA/66
[    2.417027] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
[    2.417219] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.417259] sd 0:0:0:0: [sda] Write Protect is off
[    2.417264] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.417325] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.417464] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    2.417498] sd 0:0:0:0: [sda] Write Protect is off
[    2.417503] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.417561] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.417570]  sda: sda1 sda2 < sda5 >
[    2.446234] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.446332] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.447217] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW SOHW-1633S BS0C PQ: 0 ANSI: 5
[    2.451256] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.451263] Uniform CD-ROM driver Revision: 3.20
[    2.451433] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.451515] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.452353] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.452427] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    2.452434] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    2.452566] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    2.452637] ehci_hcd 0000:00:02.2: debug port 1
[    2.452645] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    2.452672] ehci_hcd 0000:00:02.2: irq 11, io mem 0xeb003000
[    2.464028] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    2.464165] usb usb1: configuration #1 chosen from 1 choice
[    2.464220] hub 1-0:1.0: USB hub found
[    2.464241] hub 1-0:1.0: 8 ports detected
[    2.464456] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.464499] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.464505] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.464585] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.464614] ohci_hcd 0000:00:02.0: irq 9, io mem 0xeb001000
[    2.522116] usb usb2: configuration #1 chosen from 1 choice
[    2.522163] hub 2-0:1.0: USB hub found
[    2.522184] hub 2-0:1.0: 4 ports detected
[    2.522347] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    2.522353] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    2.522446] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    2.522478] ohci_hcd 0000:00:02.1: irq 10, io mem 0xeb002000
[    2.578106] usb usb3: configuration #1 chosen from 1 choice
[    2.578152] hub 3-0:1.0: USB hub found
[    2.578171] hub 3-0:1.0: 4 ports detected
[    2.578329] uhci_hcd: USB Universal Host Controller Interface driver
[    2.578440] usbcore: registered new interface driver libusual
[    2.578501] usbcore: registered new interface driver usbserial
[    2.578521] USB Serial support registered for generic
[    2.578554] usbcore: registered new interface driver usbserial_generic
[    2.578558] usbserial: USB Serial Driver core
[    2.578643] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    2.580953] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.580964] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.581166] mice: PS/2 mouse device common for all mice
[    2.581328] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.581361] rtc0: alarms up to one day, 114 bytes nvram
[    2.581468] device-mapper: uevent: version 1.0.3
[    2.581687] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.581790] device-mapper: multipath: version 1.0.5 loaded
[    2.581796] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.581953] EISA: Probing bus 0 at eisa.0
[    2.582006] EISA: Detected 0 cards.
[    2.582081] cpuidle: using governor ladder
[    2.582085] cpuidle: using governor menu
[    2.583042] TCP cubic registered
[    2.583223] NET: Registered protocol family 10
[    2.584002] lo: Disabled Privacy Extensions
[    2.584659] NET: Registered protocol family 17
[    2.584692] Bluetooth: L2CAP ver 2.11
[    2.584696] Bluetooth: L2CAP socket layer initialized
[    2.584702] Bluetooth: SCO (Voice Link) ver 0.6
[    2.584705] Bluetooth: SCO socket layer initialized
[    2.584760] Bluetooth: RFCOMM socket layer initialized
[    2.584774] Bluetooth: RFCOMM TTY layer initialized
[    2.584778] Bluetooth: RFCOMM ver 1.10
[    2.584818] powernow-k8: Processor cpuid 6a0 not supported
[    2.584832] Using IPI No-Shortcut mode
[    2.584966] registered taskstats version 1
[    2.585164]   Magic number: 9:669:973
[    2.585296] rtc_cmos 00:03: setting system clock to 2009-05-08 06:57:51 UTC (1241765871)
[    2.585303] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.585306] EDD information not available.
[    2.586301] Freeing unused kernel memory: 532k freed
[    2.586533] Write protecting the kernel text: 4128k
[    2.586609] Write protecting the kernel read-only data: 1532k
[    2.622966] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.776091] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    2.909600] usb 1-4: configuration #1 chosen from 1 choice
[    2.909882] hub 1-4:1.0: USB hub found
[    2.910197] hub 1-4:1.0: 4 ports detected
[    3.328070] usb 3-3: new full speed USB device using ohci_hcd and address 2
[    3.428287] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.428319] forcedeth 0000:00:04.0: setting latency timer to 64
[    3.428411] nv_probe: set workaround bit for reversed mac addr
[    3.467739] ssb: Sonics Silicon Backplane found on PCI device 0000:02:07.0
[    3.551364] usb 3-3: configuration #1 chosen from 1 choice
[    3.624377] usb 1-4.3: new high speed USB device using ehci_hcd and address 4
[    3.718506] usb 1-4.3: configuration #1 chosen from 1 choice
[    3.740403] Initializing USB Mass Storage driver...
[    3.747209] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.752851] usbcore: registered new interface driver usb-storage
[    3.752862] USB Mass Storage support registered.
[    3.753043] usb-storage: device found at 4
[    3.753047] usb-storage: waiting for device to settle before scanning
[    3.812371] usb 1-4.4: new high speed USB device using ehci_hcd and address 5
[    3.905763] usb 1-4.4: configuration #1 chosen from 1 choice
[    3.906150] hub 1-4.4:1.0: USB hub found
[    3.906458] hub 1-4.4:1.0: 4 ports detected
[    3.949783] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:11:09:60:8f:c4
[    3.949793] forcedeth 0000:00:04.0: csum timirq lnktim desc-v2
[    4.443099] PM: Starting manual resume from disk
[    4.443107] PM: Resume from partition 8:5
[    4.443110] PM: Checking hibernation image.
[    4.443329] PM: Resume from disk failed.
[    4.490132] kjournald starting.  Commit interval 5 seconds
[    4.490155] EXT3-fs: mounted filesystem with ordered data mode.
[    8.752357] usb-storage: device scan complete
[    8.753036] scsi 2:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[    8.754551] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    8.754690] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.279795] udev: starting version 141
[   10.474373] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   10.474464] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[   10.550446] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   10.550693] usbcore: registered new interface driver btusb
[   10.651587] Linux agpgart interface v0.103
[   10.896463] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.115193] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   11.126433] agpgart: Detected NVIDIA nForce2 chipset
[   11.142208] agpgart-nvidia 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   11.322145] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.763053] Intel ICH 0000:00:06.0: setting latency timer to 64
[   11.809138] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.827764] psmouse serio1: ID: 10 00 64nf_conntrack version 0.5.0 (12287 buckets, 49148 max)
[   11.881918] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   11.881925] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   11.881930] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.084094] intel8x0_measure_ac97_clock: measured 53892 usecs
[   12.084102] intel8x0: clocking to 47465
[   12.350660] lp: driver loaded but no devices found
[   12.445463] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   12.530425] Adding 2241028k swap on /dev/sda5.  Priority:-1 extents:1 across:2241028k
[   13.103392] EXT3 FS on sda1, internal journal
[   14.352347] type=1505 audit(1241765883.266:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1872
[   14.463331] type=1505 audit(1241765883.374:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1876
[   14.463713] type=1505 audit(1241765883.374:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1876
[   14.463848] type=1505 audit(1241765883.374:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1876
[   14.463984] type=1505 audit(1241765883.374:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1876
[   14.786506] type=1505 audit(1241765883.698:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1881
[   14.787082] type=1505 audit(1241765883.698:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1881
[   14.851711] type=1505 audit(1241765883.762:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1885
[   19.793793] eth0: no link during initialization.
[   19.794503] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.557321] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.557328] Bluetooth: BNEP filters: protocol multicast
[   20.601886] Bridge firewalling registered
[   21.962375] ppdev: user-space parallel port driver
[   22.078605] [drm] Initialized drm 1.1.0 20060810
[   22.159189] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   22.648798] agpgart-nvidia 0000:00:00.0: AGP 2.0 bridge
[   22.648831] agpgart-nvidia 0000:00:00.0: putting AGP V2 device into 4x mode
[   22.648904] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   22.891801] [drm] Setting GART location based on new memory map
[   22.891816] [drm] Loading R200 Microcode
[   22.891871] [drm] writeback test succeeded in 1 usecs
[   83.641030] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[  610.621194] PPP BSD Compression module registered
[  610.660713] PPP Deflate Compression module registered
[31270.859863] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=65076 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=95 ] 
[31272.903746] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=65077 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=95 ] 
[31276.819766] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=65078 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=95 ] 
[31281.639801] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=20980 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=95 ] 
[31281.687789] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=65079 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=95 ] 
[31283.619751] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=65080 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=95 ] 
[31283.639911] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=20981 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=95 ] 
[31287.639934] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=20982 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=95 ] 
[31287.671835] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=65081 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=95 ] 
[31294.999828] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=20983 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=95 ] 
[31297.127863] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=20984 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=95 ] 
[31301.479855] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=143 TOS=0x00 PREC=0x00 TTL=54 ID=20985 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=115 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=95 ] 
[31447.884749] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=144 TOS=0x00 PREC=0x00 TTL=54 ID=65094 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[31447.904749] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=144 TOS=0x00 PREC=0x00 TTL=54 ID=20986 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=116 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=96 ] 
[31448.004763] Inbound IN=ppp0 OUT= MAC= SRC=80.245.116.126 DST=10.46.148.170 LEN=89 TOS=0x00 PREC=0x00 TTL=111 ID=17106 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=80.245.116.126 LEN=61 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=42919 DPT=21091 LEN=41 ] 
[31448.744859] Inbound IN=ppp0 OUT= MAC= SRC=80.245.116.126 DST=10.46.148.170 LEN=77 TOS=0x00 PREC=0x00 TTL=111 ID=17359 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=80.245.116.126 LEN=49 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=42919 DPT=21091 LEN=29 ] 
[31449.884782] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=144 TOS=0x00 PREC=0x00 TTL=54 ID=65095 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[31449.904806] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=144 TOS=0x00 PREC=0x00 TTL=54 ID=20987 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=116 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=96 ] 
[31449.924984] Inbound IN=ppp0 OUT= MAC= SRC=80.245.116.126 DST=10.46.148.170 LEN=89 TOS=0x00 PREC=0x00 TTL=111 ID=17772 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=80.245.116.126 LEN=61 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=42919 DPT=21091 LEN=41 ] 
[31450.524777] Inbound IN=ppp0 OUT= MAC= SRC=80.245.116.126 DST=10.46.148.170 LEN=77 TOS=0x00 PREC=0x00 TTL=111 ID=18007 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=80.245.116.126 LEN=49 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=42919 DPT=21091 LEN=29 ] 
[31453.904800] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.46.148.170 LEN=144 TOS=0x00 PREC=0x00 TTL=54 ID=20988 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.58 LEN=116 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=47639 LEN=96 ] 
[31454.008852] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.46.148.170 LEN=144 TOS=0x00 PREC=0x00 TTL=54 ID=65096 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=56 ID=0 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[31454.084817] Inbound IN=ppp0 OUT= MAC= SRC=80.245.116.126 DST=10.46.148.170 LEN=89 TOS=0x00 PREC=0x00 TTL=111 ID=19254 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=80.245.116.126 LEN=61 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=42919 DPT=21091 LEN=41 ] 
[31454.568804] Inbound IN=ppp0 OUT= MAC= SRC=80.245.116.126 DST=10.46.148.170 LEN=77 TOS=0x00 PREC=0x00 TTL=111 ID=19399 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.46.148.170 DST=80.245.116.126 LEN=49 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=42919 DPT=21091 LEN=29 ] 
[32151.181548] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39000 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=57552 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[32153.020934] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39001 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=65515 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[32156.980927] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39002 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=15154 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[32163.561524] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=36580 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.58 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=37218 DF PROTO=UDP SPT=42919 DPT=47639 LEN=96 ] 
[32163.568940] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39003 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=37279 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[32164.358756] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39004 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=45958 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[32164.358796] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=36581 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.58 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=45959 DF PROTO=UDP SPT=42919 DPT=47639 LEN=96 ] 
[32168.209003] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.58 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=36582 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.58 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=63611 DF PROTO=UDP SPT=42919 DPT=47639 LEN=96 ] 
[32168.485097] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39005 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=64766 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[32738.176340] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39006 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=60967 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[32739.213863] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39007 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=65138 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
[32743.257323] Inbound IN=ppp0 OUT= MAC= SRC=78.141.177.16 DST=10.96.20.148 LEN=144 TOS=0x00 PREC=0x00 TTL=53 ID=39008 PROTO=ICMP TYPE=3 CODE=3 [SRC=10.96.20.148 DST=78.141.177.16 LEN=116 TOS=0x00 PREC=0x00 TTL=55 ID=14320 DF PROTO=UDP SPT=42919 DPT=50604 LEN=96 ] 
root@nigel-desktop:~# 

I'm new to Linux, and Ubuntu, and green when it comes to Janty (9.04); what are you looking for in all that ??

---

### Post by UbuKunubi on 2009-05-12
Bump!

Can anyone give me a pointer please?

---

### Post by Zugzwang on 2009-05-12
Did you check that the "/dev/parport0" file (so to speak) is actually there?

---

### Post by UbuKunubi on 2009-05-12
Zugzwang,

I just checked again, and its gone!
it was there I swear it!

I take it that it SHOULD be there? how do i create it?
Thanks for you question, this seems to be going towards a solution! :-)

---

### Post by UbuKunubi on 2009-05-13
Bump!

How do I make the missing device?

---

### Post by SKLP on 2009-05-13
You can create devices with mkdev although that should not be needed with udev

---

### Post by UbuKunubi on 2009-05-13
Do I just type sudo mkdev parport0?

---

### Post by UbuKunubi on 2009-05-14
Bump!

I tried (as root) to create the missing /dev/parport0 with makedev /dev/parport0, but I got an error message saying the program could not be found.

The same also happen when I tried mkdev /dev/parport0.

I'd be really grateful if anyone can help me with this.

Many thanks,
Ubu.

---

### Post by UbuKunubi on 2009-05-18
Bump.

---

### Post by John Q (be) on 2009-05-18
Hi all;

I'm experiencing a same story;

I've searched the Forum and here is the listing of the command's  that most of you depicted, but of which i can't deduce much (I'm no expert at all)

Here below you can find the most relevant loggings (i think)
_Can one advise me how to bring up a parallel port, check it's existence, mapping and check the connectivity?_

Thanks 
John
:-)

**The Bios setting:**
[INDENT]Parallel port address 378h *
*note the parallel port is build in and disables when an expansion slot is filled with a parallel port

In this PC there are no PCI devices or what so ever present! This is a thing i checked![/INDENT]

**The command's:**
[INDENT]
**ls -al /dev/lp0**
ls: cannot access /dev/lp0: No such file or directory
**ls /dev/lp***
ls: cannot access /dev/lp*: No such file or directory
**ls /dev/p***
/dev/port  /dev/ppp  /dev/psaux  /dev/ptmx

/dev/pktcdvd:
control

/dev/pts:
0
**ls /dev/l* **
/dev/log    /dev/loop1  /dev/loop3  /dev/loop5  /dev/loop7
/dev/loop0  /dev/loop2  /dev/loop4  /dev/loop6
**lsmod | grep lp**
lp                     17156  0 
parport                42220  2 ppdev,lp
**lsof | grep dev | grep lp**
**ls -al /dev/lp***
ls: cannot access /dev/lp*: No such file or directory
**ls -al /dev/p***
crw-r----- 1 root kmem   1, 4 2009-05-18 12:33 /dev/port
crw------- 1 root root 108, 0 2009-05-14 12:26 /dev/ppp
crw-rw---- 1 root root  10, 1 2009-05-18 12:33 /dev/psaux
crw-rw-rw- 1 root tty    5, 2 2009-05-18 12:38 /dev/ptmx

/dev/pktcdvd:
total 0
drwxr-xr-x  2 root root      60 2009-05-18 12:33 .
drwxr-xr-x 14 root root    3660 2009-05-18 12:33 ..
crw-rw----  1 root cdrom 10, 62 2009-05-18 12:33 control

/dev/pts:
total 0
drwxr-xr-x  2 root       root      0 2009-05-18 12:33 .
drwxr-xr-x 14 root       root   3660 2009-05-18 12:33 ..
crw--w----  1 callserver tty  136, 0 2009-05-18 12:38 0
[/INDENT]


**The DMESG traces:**
[INDENT]> [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] last_pfn = 0x10000 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000093000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000010000000 (usable)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 10000000 @ 10000-15000
[    0.000000] RAMDISK: 0f8be000 - 0ffef716
[    0.000000] ACPI Error (tbxfroot-0218): A valid RSDP was not found [20080926]
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 10000000
[    0.000000]   low ram: 00000000 - 10000000
[    0.000000]   bootmap 00011000 - 00013000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0010000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000f8be000 - 000ffef716]          RAMDISK ==> [000f8be000 - 000ffef716]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000013000]          BOOTMAP ==> [0000011000 - 0000013000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00010000
[    0.000000]   HighMem  0x00010000 -> 0x00010000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000093
[    0.000000]     0: 0x00000100 -> 0x00010000
[    0.000000] On node 0 totalpages: 65414
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3942 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60960 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000093000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:efe00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64902
[    0.000000] Kernel command line: root=UUID=81f2d1c7-676f-4bc2-a8fc-9dbbbed3bd28 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: Using PIT calibration value
[    0.000000] Detected 548.273 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1310720 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 242672k/262144k available (4126k kernel code, 18672k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0800000 - 0xff3fe000   ( 747 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004028] Calibrating delay loop (skipped), value calculated using timer frequency.. 1096.54 BogoMIPS (lpj=2193092)
[    0.004105] Security Framework initialized
[    0.004137] SELinux:  Disabled at boot.
[    0.004228] AppArmor: AppArmor initialized
[    0.004266] Mount-cache hash table entries: 512
[    0.004785] Initializing cgroup subsys ns
[    0.004802] Initializing cgroup subsys cpuacct
[    0.004812] Initializing cgroup subsys memory
[    0.004829] Initializing cgroup subsys freezer
[    0.004884] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004897] CPU: L2 cache: 512K
[    0.004950] Checking 'hlt' instruction... OK.
[    0.021459] SMP alternatives: switching to UP code
[    0.613099] Freeing SMP alternatives: 18k freed
[    0.613361] weird, boot CPU (#0) not listedby the BIOS.
[    0.613371] SMP motherboard not detected.
[    0.613382] Local APIC not detected. Using dummy APIC emulation.
[    0.613390] SMP disabled
[    0.614925] Brought up 1 CPUs
[    0.614938] Total of 1 processors activated (1096.54 BogoMIPS).
[    0.614999] CPU0 attaching NULL sched-domain.
[    0.616208] net_namespace: 776 bytes
[    0.616262] Booting paravirtualized kernel on bare hardware
[    0.617282] Time:  9:33:23  Date: 05/18/09
[    0.617306] regulator: core version 0.5
[    0.617457] NET: Registered protocol family 16
[    0.618063] EISA bus registered
[    0.649013] PCI: PCI BIOS revision 2.10 entry at 0xfcaee, last bus=1
[    0.649025] PCI: Using configuration type 1 for base access
[    0.654027] ACPI: Interpreter disabled.
[    0.654775] SCSI subsystem initialized
[    0.655026] libata version 3.00 loaded.
[    0.655288] usbcore: registered new interface driver usbfs
[    0.655365] usbcore: registered new interface driver hub
[    0.655539] usbcore: registered new device driver usb
[    0.656209] PCI: Probing PCI hardware
[    0.656221] PCI: Probing PCI hardware (bus 00)
[    0.656361] pci 0000:00:00.0: reg 10 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.656583] pci 0000:00:07.1: reg 20 io port: [0xffa0-0xffaf]
[    0.656667] pci 0000:00:07.2: reg 20 io port: [0xdce0-0xdcff]
[    0.656724] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[    0.656731] * this clock source is slow. Consider trying other clock sources
[    0.656802] pci 0000:00:07.3: quirk: region 0800-083f claimed by PIIX4 ACPI
[    0.656816] pci 0000:00:07.3: quirk: region 0850-085f claimed by PIIX4 SMB
[    0.656896] pci 0000:00:11.0: reg 10 io port: [0xdc00-0xdc7f]
[    0.656913] pci 0000:00:11.0: reg 14 32bit mmio: [0xff000000-0xff00007f]
[    0.656952] pci 0000:00:11.0: reg 30 32bit mmio: [0xfb000000-0xfb01ffff]
[    0.656974] pci 0000:00:11.0: supports D1 D2
[    0.656984] pci 0000:00:11.0: PME# supported from D1 D2 D3hot
[    0.656997] pci 0000:00:11.0: PME# disabled
[    0.657082] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.657100] pci 0000:01:00.0: reg 14 io port: [0xec00-0xecff]
[    0.657117] pci 0000:01:00.0: reg 18 32bit mmio: [0xfcfff000-0xfcffffff]
[    0.657150] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.657223] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.657237] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfeffffff]
[    0.657251] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf9000000-0xf9ffffff]
[    0.658158] pci 0000:00:07.0: PIIX/ICH IRQ router [8086:7110]
[    0.658418] Bluetooth: Core ver 2.13
[    0.658418] NET: Registered protocol family 31
[    0.658418] Bluetooth: HCI device and connection manager initialized
[    0.658418] Bluetooth: HCI socket layer initialized
[    0.658418] NET: Registered protocol family 8
[    0.658418] NET: Registered protocol family 20
[    0.658418] NetLabel: Initializing
[    0.658418] NetLabel:  domain hash size = 128
[    0.658418] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.658418] NetLabel:  unlabeled traffic allowed by default
[    0.658418] AppArmor: AppArmor Filesystem Enabled
[    0.658418] pnp: PnP ACPI: disabled
[    0.658418] PnPBIOS: Scanning system for PnP BIOS support...
[    0.658418] PnPBIOS: Found PnP BIOS installation structure at 0xc00fe2d0
[    0.658418] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xe2f4, dseg 0x40
[    0.661395] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[    0.661441] system 00:00: ioport range 0x800-0x83f has been reserved
[    0.661454] system 00:00: ioport range 0x850-0x85f has been reserved
[    0.661468] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.661481] system 00:00: iomem range 0x100000-0xfffffff could not be reserved
[    0.661493] system 00:00: iomem range 0xffe00000-0xffffffff has been reserved
[    0.661505] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.662363] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.662377] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.662391] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfeffffff
[    0.662404] pci 0000:00:01.0:   PREFETCH window: 0x000000f9000000-0x000000f9ffffff
[    0.662435] bus: 00 index 0 io port: [0x00-0xffff]
[    0.662446] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.662456] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.662465] bus: 01 index 1 mmio: [0xfc000000-0xfeffffff]
[    0.662475] bus: 01 index 2 mmio: [0xf9000000-0xf9ffffff]
[    0.662484] bus: 01 index 3 mmio: [0x0-0x0]
[    0.662521] NET: Registered protocol family 2
[    0.663083] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.664198] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.664473] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.664738] TCP: Hash tables configured (established 8192 bind 8192)
[    0.664749] TCP reno registered
[    0.665098] NET: Registered protocol family 1
[    0.665600] checking if image is initramfs... it is
[    3.098500] Freeing initrd memory: 7365k freed
[    3.098716] cpufreq: No nForce2 chipset.
[    3.099201] audit: initializing netlink socket (disabled)
[    3.099303] type=2000 audit(1242639205.096:1): initialized
[    3.129908] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.136341] VFS: Disk quotas dquot_6.5.1
[    3.136650] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.140120] fuse init (API version 7.10)
[    3.140617] msgmni has been set to 489
[    3.141541] alg: No test for stdrng (krng)
[    3.141624] io scheduler noop registered
[    3.141634] io scheduler anticipatory registered
[    3.141643] io scheduler deadline registered
[    3.141764] io scheduler cfq registered (default)
[    3.141811] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    3.141881] pci 0000:01:00.0: Boot video device
[    3.142156] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.142239] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.142575] isapnp: Scanning for PnP cards...
[    3.245394]  01:01: card 'CS4236B'
[    3.245405] isapnp: 1 Plug & Play card detected total
[    3.251248] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.251437] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.251648] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.252415] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.252815] 00:02: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    3.257151] brd: module loaded
[    3.258828] loop: module loaded
[    3.259168] Fixed MDIO Bus: probed
[    3.259195] PPP generic driver version 2.4.2
[    3.259486] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.259621] Driver 'sd' needs updating - please use bus_type methods
[    3.259681] Driver 'sr' needs updating - please use bus_type methods
[    3.259956] ata_piix 0000:00:07.1: version 2.12
[    3.260541] scsi0 : ata_piix
[    3.261028] scsi1 : ata_piix
[    3.261216] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.261229] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.425038] ata1.00: ATA-4: QUANTUM FIREBALLlct08 06, A05.0X00, max UDMA/66
[    3.425052] ata1.00: 12594960 sectors, multi 8: LBA 
[    3.441034] ata1.00: configured for UDMA/33
[    3.604724] ata2.00: ATAPI: CRD-8482B, 1.05, max UDMA/33
[    3.604750] ata2.00: device is on DMA blacklist, disabling DMA
[    3.612651] ata2.00: configured for PIO4
[    3.613359] scsi 0:0:0:0: Direct-Access     ATA      QUANTUM FIREBALL A05. PQ: 0 ANSI: 5
[    3.613840] sd 0:0:0:0: [sda] 12594960 512-byte hardware sectors: (6.44 GB/6.00 GiB)
[    3.613953] sd 0:0:0:0: [sda] Write Protect is off
[    3.613966] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.614160] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.614494] sd 0:0:0:0: [sda] 12594960 512-byte hardware sectors: (6.44 GB/6.00 GiB)
[    3.614603] sd 0:0:0:0: [sda] Write Protect is off
[    3.614615] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.614810] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.614831]  sda: sda1 sda2 < sda5 >
[    3.655222] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.655454] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.655975] scsi 1:0:0:0: CD-ROM            LG       CD-ROM CRD-8482B 1.05 PQ: 0 ANSI: 5
[    3.658925] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    3.658939] Uniform CD-ROM driver Revision: 3.20
[    3.659353] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.659552] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.662422] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.662515] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.662590] uhci_hcd: USB Universal Host Controller Interface driver
[    3.662733] PCI: setting IRQ 11 as level-triggered
[    3.662745] uhci_hcd 0000:00:07.2: found PCI INT D -> IRQ 11
[    3.662782] uhci_hcd 0000:00:07.2: sharing IRQ 11 with 0000:00:11.0
[    3.662813] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    3.663146] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    3.663208] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000dce0
[    3.663625] usb usb1: configuration #1 chosen from 1 choice
[    3.663788] hub 1-0:1.0: USB hub found
[    3.663836] hub 1-0:1.0: 2 ports detected
[    3.664462] usbcore: registered new interface driver libusual
[    3.664622] usbcore: registered new interface driver usbserial
[    3.664674] USB Serial support registered for generic
[    3.664737] usbcore: registered new interface driver usbserial_generic
[    3.664748] usbserial: USB Serial Driver core
[    3.664966] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    3.667104] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.667130] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.667681] mice: PS/2 mouse device common for all mice
[    3.668118] rtc_cmos 00:0c: rtc core: registered rtc_cmos as rtc0
[    3.668161] rtc0: alarms up to one day, 242 bytes nvram
[    3.668588] device-mapper: uevent: version 1.0.3
[    3.669135] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.669455] device-mapper: multipath: version 1.0.5 loaded
[    3.669469] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.669962] EISA: Probing bus 0 at eisa.0
[    3.670036] EISA: Detected 0 cards.
[    3.670192] cpuidle: using governor ladder
[    3.670203] cpuidle: using governor menu
[    3.672727] TCP cubic registered
[    3.673372] NET: Registered protocol family 10
[    3.675385] lo: Disabled Privacy Extensions
[    3.676936] NET: Registered protocol family 17
[    3.677045] Bluetooth: L2CAP ver 2.11
[    3.677054] Bluetooth: L2CAP socket layer initialized
[    3.677068] Bluetooth: SCO (Voice Link) ver 0.6
[    3.677076] Bluetooth: SCO socket layer initialized
[    3.677244] Bluetooth: RFCOMM socket layer initialized
[    3.677279] Bluetooth: RFCOMM TTY layer initialized
[    3.677288] Bluetooth: RFCOMM ver 1.10
[    3.677431] IO APIC resources could be not be allocated.
[    3.677500] Using IPI No-Shortcut mode
[    3.677849] registered taskstats version 1
[    3.678153]   Magic number: 9:328:576
[    3.678314] rtc_cmos 00:0c: setting system clock to 2009-05-18 09:33:26 UTC (1242639206)
[    3.678328] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.678337] EDD information not available.
[    3.680518] Freeing unused kernel memory: 532k freed
[    3.681048] Write protecting the kernel text: 4128k
[    3.681210] Write protecting the kernel read-only data: 1532k
[    3.700466] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.973720] usb 1-2: new full speed USB device using uhci_hcd and address 2
[    4.166627] usb 1-2: configuration #1 chosen from 1 choice
[    4.224831] Initializing USB Mass Storage driver...
[    4.232519] scsi2 : SCSI emulation for USB Mass Storage devices
[    4.240577] usbcore: registered new interface driver usb-storage
[    4.240594] USB Mass Storage support registered.
[    4.241028] usb-storage: device found at 2
[    4.241038] usb-storage: waiting for device to settle before scanning
[    5.110677] 3c59x 0000:00:11.0: found PCI INT A -> IRQ 11
[    5.110715] 3c59x 0000:00:11.0: sharing IRQ 11 with 0000:00:07.2
[    5.110826] 3c59x: Donald Becker and others.
[    5.110852] 0000:00:11.0: 3Com PCI 3c905B Cyclone 100baseTx at d08d8000.
[    6.350327] PM: Starting manual resume from disk
[    6.350344] PM: Resume from partition 8:1
[    6.350351] PM: Checking hibernation image.
[    6.350873] PM: Resume from disk failed.
[    6.391244] kjournald starting.  Commit interval 5 seconds
[    6.391290] EXT3-fs: mounted filesystem with ordered data mode.
[    9.243064] usb-storage: device scan complete
[    9.246023] scsi 2:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9339 PQ: 0 ANSI: 0
[    9.249375] scsi 2:0:0:1: Direct-Access     Generic  STORAGE DEVICE   9339 PQ: 0 ANSI: 0
[    9.251975] scsi 2:0:0:2: Direct-Access     Generic  STORAGE DEVICE   9339 PQ: 0 ANSI: 0
[    9.255199] scsi 2:0:0:3: Direct-Access     Generic  STORAGE DEVICE   9339 PQ: 0 ANSI: 0
[    9.262339] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    9.262607] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    9.268199] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    9.268413] sd 2:0:0:1: Attached scsi generic sg3 type 0
[    9.273241] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    9.273480] sd 2:0:0:2: Attached scsi generic sg4 type 0
[    9.279224] sd 2:0:0:3: [sde] Attached SCSI removable disk
[    9.279444] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   18.616187] udev: starting version 141
[   19.117747] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.340311] Linux agpgart interface v0.103
[   19.459011] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   19.485677] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf4000000
[   19.722412] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[   19.914650] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   19.974075] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   20.138489] psmouse serio1: ID: 00 00 28<6>input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input3
[   20.553345] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.557848] lp: driver loaded but no devices found
[   21.942319] Adding 995988k swap on /dev/sda1.  Priority:-1 extents:1 across:995988k
[   22.347400] EXT3 FS on sda5, internal journal
[   23.886119] type=1505 audit(1242639226.704:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1666
[   24.133892] type=1505 audit(1242639226.952:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1670
[   24.134705] type=1505 audit(1242639226.952:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1670
[   24.135022] type=1505 audit(1242639226.952:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1670
[   24.135469] type=1505 audit(1242639226.956:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1670
[   24.867918] type=1505 audit(1242639227.688:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1675
[   24.869154] type=1505 audit(1242639227.688:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1675
[   25.015710] type=1505 audit(1242639227.836:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1679
[   29.334053] RPC: Registered udp transport module.
[   29.334068] RPC: Registered tcp transport module.
[   29.567594] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   29.870092] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   29.883293] NFSD: starting 90-second grace period
[   32.484185] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.484263] Bluetooth: BNEP filters: protocol multicast
[   32.747318] Bridge firewalling registered
[   34.487786] ppdev: user-space parallel port driver
[   38.182760] eth0:  setting full-duplex.
[   48.894376] eth0: no IPv6 routers present[/INDENT]

---

### Post by UbuKunubi on 2009-05-18
Many thanks for your reply John!
As soon as I get back to the machine in question I'll update with progress.

---

### Post by UbuKunubi on 2009-05-19
Bump!!

I have been search, asking, and thinking about this parallel port problem.

Is this a bug with Jaunty 9.04?
Has anyone else lost their parallel port?
Can anyone tell me how to create the missing port?

---

### Post by John Q (be) on 2009-05-19
Hi;

In 9.04 the problem can be solved via this command:
> sudo modprobe parport_pc

> After you modprobe the appropriate driver, /dev/lp0 will work and CUPS will alert you of a printer on that parallel port. To keep this working across reboots, add parport_pc to /etc/modules . It now should just work.

see 
[http://ubuntuforums.org/showthread.php?t=1135964](http://ubuntuforums.org/showthread.php?t=1135964) 

for the entire history

Greetzzzz
John

---

### Post by UbuKunubi on 2009-05-19
Hi John,

Many, many thanks for your help!

I'll make the changes so the parallel port is still brought up after reboot.

I'm away from the machine in question, so I'll update as soon as I can.

Cheers,
Ubu

---

### Post by UbuKunubi on 2009-05-27
John Q (be),
thanks for your input!

Im back in the saddle on this project for the rest of the week now.

My only concern is the port vanishing when I have to do a weekly reboot of the machine in question (not my choice-i'd leave it on for ever :-(  ho hum!)

All the best,
Ubu

---

### Post by UbuKunubi on 2009-05-27
OK!
Now I have verified that the hardware is working, I need to crack on with the software.


Can anyone either supply a pointer to a website, or a sample of python code that:
a)turns a LED on and off.
b) tests a pin for being high or low.

The end result will be a relay control with the Skype API, so I can turn on the heating with my Skype phone.

Please note that my internet connection is via my mobile phone (3) and they often prevent me from seeing the 'entire' internet! 

Many thanks,
Ubu

EDIT:::::
When running the code of:
```

# -*- coding: utf-8 -*-
#!/usr/bin/env python
  
import Image
import os,sys
import parallel
import time

print "Parallel port program starting"

p=parallel.Parallel()
p.setData(0)    #set all the port pins to off
p.setData(0x55)

```

I am getting the following error message when running as root:
root@nigel-desktop:/home/nigel/NDSPython# python NDSparallelPORT.py
Parallel port program starting
Traceback (most recent call last):
  File "NDSparallelPORT.py", line 11, in <module>
    p=parallel.Parallel()
  File "/usr/lib/python2.6/dist-packages/parallel/parallelppdev.py", line 188, in __init__
    self.PPCLAIM()
  File "/usr/lib/python2.6/dist-packages/parallel/parallelppdev.py", line 215, in PPCLAIM
    fcntl.ioctl(self._fd, PPCLAIM)
IOError: [Errno 6] No such device or address
Exception IOError: (22, 'Invalid argument') in <bound method Parallel.__del__ of <parallel.parallelppdev.Parallel instance at 0xb7c8148c>> ignored


Can anyone help? please?
F.Y.I. I am running Jaunty 9.04

Edit 2:::

The below shows that there IS a parallel port!!!!!
root@nigel-desktop:/home/nigel/NDSPython# ls /dev/p*
/dev/parport0  /dev/port  /dev/ppp  /dev/psaux  /dev/ptmx

/dev/pktcdvd:
control

/dev/pts:
0  1

I found:
[http://theorieswithproblems.com/2008/04/22/python-parallel-port-programming-on-ubuntu-linux/](http://theorieswithproblems.com/2008/04/22/python-parallel-port-programming-on-ubuntu-linux/)

and followed these instructions:


I&#8217;m trying to get my parallel port to work nicely with Python and Ubuntu Linux. So far this is what I got:

pia@pia-desktop:~$ sudo apt-get install python-parallel
pia@pia-desktop:~$ sudo rmmod lp
pia@pia-desktop:~$ sudo modprobe ppdev
pia@pia-desktop:~$ python
Python 2.5.1 (r251:54863, Mar  7 2008, 04:10:12)
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import parallel
>>> p = parallel.Parallel()
>>> p.setData(0x55)


And got NO errors, So Im connecting an LED and will test the reality of the situation!


edit 4:::
LED confirms that all is working OK

Now to test for port input and nearly done!! :-)

---

### Post by UbuKunubi on 2009-05-28
Yesterday I was able to see an LED flashing with the following code:

```

# -*- coding: utf-8 -*-
#!/usr/bin/env python
  
import Image
import os,sys
import parallel
import time

print "Parallel port program starting"

p=parallel.Parallel()
while 1:
    p.setData(0x55)
    time.sleep(1)
    p.setData(0)    #set all the port pins to off
    time.sleep(1)

```


And all was well, I was looking forward to getting the software completed today, but I starting to wonder if this is a bug, because when I went to run the code again I got the following message:
```

root@nigel-desktop:/home/nigel/NDSPython# python NDSparallelPORT.py
Parallel port program starting
Traceback (most recent call last):
  File "NDSparallelPORT.py", line 11, in <module>
    p=parallel.Parallel()
  File "/usr/lib/python2.6/dist-packages/parallel/parallelppdev.py", line 186, in __init__
    self._fd = os.open(self.device, os.O_RDWR)
OSError: [Errno 2] No such file or directory: '/dev/parport0'
Exception AttributeError: "Parallel instance has no attribute '_fd'" in <bound method Parallel.__del__ of <parallel.parallelppdev.Parallel instance at 0x965748c>> ignored
root@nigel-desktop:/home/nigel/NDSPython# 

```

SO I then used the same commands as before, which got everything working:
```

# sudo apt-get install python-parallel
# sudo rmmod lp
# sudo modprobe ppdev

```

And still met with failure.

Can anyone please help, is this a bug or is there some other special voodoo I've not cast upon my system?

Many thanks,
Ubu

E D I T :::::
SOLVED
I ran the following commands:
```

sudo modprobe parport
sudo modprobe parport_pc

```

and all is working as far as flashing the LEDs is concerned, now to FIJNALLY get on and complete the program

---

