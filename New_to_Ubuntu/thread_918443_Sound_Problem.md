---
title: "Sound Problem"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Xorg.conF on 2008-09-12
Can anyone help me resolve an issue I'm having with possibly my sound driver.  This doesn't happen every time but occasionally when I suspend my computer and later go back to wake it up, the sound will no longer be working.  Anyone have any ideas?

---

### Post by ajmorris on 2008-09-13
> **Xorg.conF said:**
> Can anyone help me resolve an issue I'm having with possibly my sound driver.  This doesn't happen every time but occasionally when I suspend my computer and later go back to wake it up, the sound will no longer be working.  Anyone have any ideas?


Hi there,
it makes it a little difficult to debug when its not reproducable every time, however, next time it happens, can you run ```
sudo dmesg 
```in a terminal and post the output here.

AJ

---

### Post by Xorg.conF on 2008-09-13
heres the output and it's quite long: 

[   17.453564] FDC 0 is a post-1991 82077
[   17.528861] ACPI: PCI Interrupt 0000:00:1a.2[D] -> GSI 19 (level, low) -> IRQ 19
[   17.528870] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   17.528873] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   17.528888] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   17.528911] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fd00
[   17.528992] usb usb3: configuration #1 chosen from 1 choice
[   17.529011] hub 3-0:1.0: USB hub found
[   17.529016] hub 3-0:1.0: 2 ports detected
[   17.632686] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   17.632701] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.632704] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.632721] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   17.632747] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fc00
[   17.632837] usb usb4: configuration #1 chosen from 1 choice
[   17.632856] hub 4-0:1.0: USB hub found
[   17.632865] hub 4-0:1.0: 2 ports detected
[   17.740604] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   17.740616] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.740620] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.740645] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   17.740670] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fb00
[   17.740783] usb usb5: configuration #1 chosen from 1 choice
[   17.740803] hub 5-0:1.0: USB hub found
[   17.740807] hub 5-0:1.0: 2 ports detected
[   17.840465] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.840473] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.840476] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.840492] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   17.840516] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fa00
[   17.840605] usb usb6: configuration #1 chosen from 1 choice
[   17.840622] hub 6-0:1.0: USB hub found
[   17.840628] hub 6-0:1.0: 2 ports detected
[   17.871682] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   17.943710] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   17.944746] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   17.944756] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   17.944835] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   17.948755] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   17.948767] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdfff000
[   17.999453] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.999571] usb usb7: configuration #1 chosen from 1 choice
[   17.999600] hub 7-0:1.0: USB hub found
[   17.999606] hub 7-0:1.0: 6 ports detected
[   18.103390] r8169 Gigabit Ethernet driver 2.2LK loaded
[   18.103421] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   18.103432] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   18.103806] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   18.104031] eth0: RTL8168c/8111c at 0xffffc2000103a000, 00:1d:09:94:14:5c, XID 3c4000c0 IRQ 508
[   18.104137] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   18.104143] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   18.104196] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   18.108115] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   18.108125] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffe000
[   18.119236] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.119339] usb usb8: configuration #1 chosen from 1 choice
[   18.119360] hub 8-0:1.0: USB hub found
[   18.119364] hub 8-0:1.0: 6 ports detected
[   18.223186] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
[   18.223225] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.223238] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   18.224170] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
[   18.224191] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   18.224201] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[   18.227226] ata_piix 0000:00:1f.2: version 2.12
[   18.227229] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   18.227244] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
[   18.227263] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.227340] scsi0 : ata_piix
[   18.227370] scsi1 : ata_piix
[   18.227798] ata1: SATA max UDMA/133 cmd 0xf900 ctl 0xf800 bmdma 0xf500 irq 19
[   18.227801] ata2: SATA max UDMA/133 cmd 0xf700 ctl 0xf600 bmdma 0xf508 irq 19
[   18.395254] usb 3-1: device not accepting address 2, error -71
[   18.435578] ata1.00: ATA-7: ST3320620AS, 3.ADG, max UDMA/133
[   18.435582] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   18.502100] ata1.00: configured for UDMA/133
[   18.973913] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653B, D300, max UDMA/100
[   18.973915] ata2.00: applying bridge limits
[   19.145601] ata2.00: configured for UDMA/100
[   19.145682] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AD PQ: 0 ANSI: 5
[   19.146564] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653B D300 PQ: 0 ANSI: 5
[   19.146622] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   19.146638] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
[   19.146663] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   19.146878] scsi2 : ata_piix
[   19.146979] scsi3 : ata_piix
[   19.147182] ata3: SATA max UDMA/133 cmd 0xf200 ctl 0xf100 bmdma 0xee00 irq 19
[   19.147184] ata4: SATA max UDMA/133 cmd 0xf000 ctl 0xef00 bmdma 0xee08 irq 19
[   19.185858] usb 3-1: new low speed USB device using uhci_hcd and address 4
[   19.368859] usb 3-1: configuration #1 chosen from 1 choice
[   19.480625] Driver 'sr' needs updating - please use bus_type methods
[   19.481725] Driver 'sd' needs updating - please use bus_type methods
[   19.481784] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   19.481792] sd 0:0:0:0: [sda] Write Protect is off
[   19.481794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.481805] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.481835] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   19.481842] sd 0:0:0:0: [sda] Write Protect is off
[   19.481843] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.481854] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.481857]  sda:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   19.486164] Uniform CD-ROM driver Revision: 3.20
[   19.486205] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   19.489013] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.489029] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   19.497951]  sda1 sda2 sda3 < sda5 > sda4
[   19.526354] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.608604] usb 3-2: new low speed USB device using uhci_hcd and address 5
[   19.784151] usb 3-2: configuration #1 chosen from 1 choice
[   19.787167] usbcore: registered new interface driver hiddev
[   19.800192] input: Dell Dell USB Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb3/3-1/3-1:1.0/input/input1
[   19.816768] input,hidraw0: USB HID v1.11 Mouse [Dell Dell USB Optical Mouse] on usb-0000:00:1a.2-1
[   19.831221] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.2/usb3/3-2/3-2:1.0/input/input2
[   19.841208] input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.2-2
[   19.841218] usbcore: registered new interface driver usbhid
[   19.841220] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.949802] Attempting manual resume
[   19.949804] swsusp: Resume From Partition 8:5
[   19.949805] PM: Checking swsusp image.
[   19.949966] PM: Resume from disk failed.
[   19.975329] ReiserFS: sda4: found reiserfs format "3.6" with standard journal
[   19.975338] ReiserFS: sda4: using ordered data mode
[   19.980350] ReiserFS: sda4: journal params: device sda4, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   19.980755] ReiserFS: sda4: checking transaction log (sda4)
[   20.018087] ReiserFS: sda4: Using r5 hash to sort names
[   26.568782] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.571896] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.684251] input: Power Button (FF) as /devices/virtual/input/input3
[   26.749738] ACPI: Power Button (FF) [PWRF]
[   26.749784] input: Power Button (CM) as /devices/virtual/input/input4
[   26.778015] iTCO_vendor_support: vendor-support=0
[   26.797325] ACPI: Power Button (CM) [PWRB]
[   26.811931] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   27.019506] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   27.019569] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0460)
[   27.019600] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   27.237482] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   27.475295] nvidia: module license 'NVIDIA' taints kernel.
[   27.728099] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.728108] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   27.728202] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.12  Thu Jul 17 18:10:24 PDT 2008
[   27.939023] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   27.939894] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   27.971592] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   28.917370] lp: driver loaded but no devices found
[   28.965891] Adding 3903784k swap on /dev/sda5.  Priority:-1 extents:1 across:3903784k
[   49.420322] ip_tables: (C) 2000-2006 Netfilter Core Team
[   49.828984] No dock devices found.
[   51.070948] ppdev: user-space parallel port driver
[   51.478155] audit(1221334391.753:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5218 profile="/usr/sbin/cupsd" namespace="default"
[   52.534155] r8169: eth0: link up
[   52.534163] r8169: eth0: link up
[   52.686247] Bluetooth: Core ver 2.11
[   52.686624] NET: Registered protocol family 31
[   52.686628] Bluetooth: HCI device and connection manager initialized
[   52.686633] Bluetooth: HCI socket layer initialized
[   52.702591] Bluetooth: L2CAP ver 2.9
[   52.702597] Bluetooth: L2CAP socket layer initialized
[   52.748157] Bluetooth: RFCOMM socket layer initialized
[   52.748172] Bluetooth: RFCOMM TTY layer initialized
[   52.748174] Bluetooth: RFCOMM ver 1.8
[   56.660383] NET: Registered protocol family 17
[  194.374643] r8169: eth0: link up
[  194.461665] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[  196.906114] Syncing filesystems ... done.
[  196.906697] PM: Preparing system for mem sleep
[  196.906702] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  196.907199] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  196.907220] PM: Entering mem sleep
[  196.907222] Suspending console(s)
[  196.941146] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  197.272016] sd 0:0:0:0: [sda] Stopping disk
[  197.272535] ACPI handle has no context!
[  197.272602] ACPI handle has no context!
[  197.272617] NVRM: RmPowerManagement: 4
[  198.047567] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[  198.075731] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[  198.091754] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[  198.107691] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[  198.107726] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[  198.107760] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[  198.123634] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[  198.139637] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
[  198.155628] ACPI: PCI interrupt for device 0000:00:1a.2 disabled
[  198.155662] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
[  198.155696] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
[  198.156518] Disabling non-boot CPUs ...
[  198.156542] CPU0 attaching NULL sched-domain.
[  198.156543] CPU1 attaching NULL sched-domain.
[  198.156544] CPU2 attaching NULL sched-domain.
[  198.156545] CPU3 attaching NULL sched-domain.
[  198.271431] CPU 1 is now offline
[  198.271663] CPU0 attaching sched-domain:
[  198.271665]  domain 0: span 09
[  198.271666]   groups: 01 08
[  198.271668]   domain 1: span 0d
[  198.271669]    groups: 09 04
[  198.271670]    domain 2: span 0d
[  198.271671]     groups: 0d
[  198.271673] CPU2 attaching sched-domain:
[  198.271674]  domain 0: span 0d
[  198.271675]   groups: 04 09
[  198.271676]   domain 1: span 0d
[  198.271677]    groups: 0d
[  198.271678] CPU3 attaching sched-domain:
[  198.271679]  domain 0: span 09
[  198.271680]   groups: 08 01
[  198.271682]   domain 1: span 0d
[  198.271682]    groups: 09 04
[  198.271684]    domain 2: span 0d
[  198.271685]     groups: 0d
[  198.272024] CPU1 is down
[  198.272030] CPU0 attaching NULL sched-domain.
[  198.272031] CPU2 attaching NULL sched-domain.
[  198.272032] CPU3 attaching NULL sched-domain.
[  198.387284] CPU 2 is now offline
[  198.387457] CPU0 attaching sched-domain:
[  198.387459]  domain 0: span 09
[  198.387460]   groups: 01 08
[  198.387461]   domain 1: span 09
[  198.387462]    groups: 09
[  198.387464] CPU3 attaching sched-domain:
[  198.387465]  domain 0: span 09
[  198.387465]   groups: 08 01
[  198.387467]   domain 1: span 09
[  198.387468]    groups: 09
[  198.387692] CPU2 is down
[  198.387695] CPU0 attaching NULL sched-domain.
[  198.387696] CPU3 attaching NULL sched-domain.
[  198.503138] CPU 3 is now offline
[  198.503141] SMP alternatives: switching to UP code
[  198.504192] CPU0 attaching sched-domain:
[  198.504194]  domain 0: span 01
[  198.504195]   groups: 01
[  198.504354] CPU3 is down
[    0.636966] Back to C!
[    0.637295] Enabling non-boot CPUs ...
[    0.637354] CPU0 attaching NULL sched-domain.
[    0.647976] SMP alternatives: switching to SMP code
[    0.648829] Booting processor 1/4 APIC 0x3
[    0.659166] Initializing CPU#1
[    0.735756] Calibrating delay using timer specific routine.. 4790.20 BogoMIPS (lpj=9580414)
[    0.735762] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.735763] CPU: L2 cache: 4096K
[    0.735765] CPU 1/3 -> Node 0
[    0.735766] CPU: Physical Processor ID: 0
[    0.735767] CPU: Processor Core ID: 3
[    0.736190] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.736198] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.756169] Measured 35128515015 cycles TSC warp between CPUs, turning off TSC clock.
[    0.756171] Marking TSC unstable due to check_tsc_sync_source failed
[    0.756175] Time: hpet clocksource has been installed.
[    0.756212] CPU0 attaching sched-domain:
[    0.756214]  domain 0: span 03
[    0.756214]   groups: 01 02
[    0.756216]   domain 1: span 03
[    0.756217]    groups: 03
[    0.756219] CPU1 attaching sched-domain:
[    0.756220]  domain 0: span 03
[    0.756220]   groups: 02 01
[    0.756222]   domain 1: span 03
[    0.756223]    groups: 03
[    0.756564] CPU1 is up
[    0.756648] CPU0 attaching NULL sched-domain.
[    0.756649] CPU1 attaching NULL sched-domain.
[    0.760209] Switched to high resolution mode on CPU 1
[    0.768337] SMP alternatives: switching to SMP code
[    0.769103] Booting processor 2/4 APIC 0x2
[    0.779439] Initializing CPU#2
[    0.859564] Calibrating delay using timer specific routine.. 4788.09 BogoMIPS (lpj=9576189)
[    0.859569] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.859570] CPU: L2 cache: 4096K
[    0.859572] CPU 2/2 -> Node 0
[    0.859573] CPU: Physical Processor ID: 0
[    0.859574] CPU: Processor Core ID: 2
[    0.859998] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.860091] CPU0 attaching sched-domain:
[    0.860093]  domain 0: span 07
[    0.860094]   groups: 01 06
[    0.860096]   domain 1: span 07
[    0.860097]    groups: 07
[    0.860098] CPU1 attaching sched-domain:
[    0.860099]  domain 0: span 06
[    0.860100]   groups: 02 04
[    0.860101]   domain 1: span 07
[    0.860102]    groups: 06 01
[    0.860104]    domain 2: span 07
[    0.860105]     groups: 07
[    0.860106] CPU2 attaching sched-domain:
[    0.860107]  domain 0: span 06
[    0.860108]   groups: 04 02
[    0.860109]   domain 1: span 07
[    0.860110]    groups: 06 01
[    0.860111]    domain 2: span 07
[    0.860112]     groups: 07
[    0.860505] CPU2 is up
[    0.860587] CPU0 attaching NULL sched-domain.
[    0.860588] CPU1 attaching NULL sched-domain.
[    0.860589] CPU2 attaching NULL sched-domain.
[    0.864027] Switched to high resolution mode on CPU 2
[    0.872665] SMP alternatives: switching to SMP code
[    0.873508] Booting processor 3/4 APIC 0x1
[    0.883839] Initializing CPU#3
[    0.963374] Calibrating delay using timer specific routine.. 4788.05 BogoMIPS (lpj=9576113)
[    0.963379] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.963380] CPU: L2 cache: 4096K
[    0.963382] CPU 3/1 -> Node 0
[    0.963383] CPU: Physical Processor ID: 0
[    0.963384] CPU: Processor Core ID: 1
[    0.963807] Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.963866] CPU0 attaching sched-domain:
[    0.963867]  domain 0: span 09
[    0.963868]   groups: 01 08
[    0.963870]   domain 1: span 0f
[    0.963871]    groups: 09 06
[    0.963873]    domain 2: span 0f
[    0.963874]     groups: 0f
[    0.963875] CPU1 attaching sched-domain:
[    0.963876]  domain 0: span 06
[    0.963877]   groups: 02 04
[    0.963878]   domain 1: span 0f
[    0.963879]    groups: 06 09
[    0.963880]    domain 2: span 0f
[    0.963881]     groups: 0f
[    0.963882] CPU2 attaching sched-domain:
[    0.963883]  domain 0: span 06
[    0.963884]   groups: 04 02
[    0.963886]   domain 1: span 0f
[    0.963886]    groups: 06 09
[    0.963888]    domain 2: span 0f
[    0.963889]     groups: 0f
[    0.963890] CPU3 attaching sched-domain:
[    0.963891]  domain 0: span 09
[    0.963892]   groups: 08 01
[    0.963893]   domain 1: span 0f
[    0.963894]    groups: 09 06
[    0.963895]    domain 2: span 0f
[    0.963896]     groups: 0f
[    0.964369] CPU3 is up
[    0.964850] ACPI: Unable to turn cooling device [ffff810129f95100] 'off'
[    0.964876] PM: Writing back config space on device 0000:00:01.0 at offset 1 (was 100007, writing 100407)
[    0.964890] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.964901] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.964906] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    0.964940] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[    0.964944] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    0.964978] ACPI: PCI Interrupt 0000:00:1a.2[D] -> GSI 19 (level, low) -> IRQ 19
[    0.964982] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[    0.967847] Switched to high resolution mode on CPU 3
[    0.979377] PCI: Enabling device 0000:00:1a.7 (0000 -> 0002)
[    0.979380] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[    0.979386] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    0.979399] PM: Writing back config space on device 0000:00:1a.7 at offset f (was 300, writing 30b)
[    0.979415] PM: Writing back config space on device 0000:00:1a.7 at offset 4 (was 0, writing fdfff000)
[    0.995343] PM: Writing back config space on device 0000:00:1b.0 at offset f (was 100, writing 103)
[    0.995357] PM: Writing back config space on device 0000:00:1b.0 at offset 4 (was 4, writing fdff8004)
[    0.995361] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
[    0.995366] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100000, writing 100002)
[    0.995382] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[    0.995387] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[    1.092003] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100007, writing 100407)
[    1.092028] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    1.092047] PM: Writing back config space on device 0000:00:1c.5 at offset 1 (was 100007, writing 100407)
[    1.092097] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    1.092105] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[    1.092109] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    1.092159] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    1.092168] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    1.092213] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    1.092222] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    1.107134] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[    1.107137] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[    1.107143] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    1.107156] PM: Writing back config space on device 0000:00:1d.7 at offset f (was 100, writing 104)
[    1.107172] PM: Writing back config space on device 0000:00:1d.7 at offset 4 (was 0, writing fdffe000)
[    1.107219] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    1.123121] PM: Writing back config space on device 0000:00:1f.2 at offset f (was 100, writing 10b)
[    1.123137] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00000, writing 2b00007)
[    1.123151] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 19 (level, low) -> IRQ 19
[    1.123155] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    1.123183] PM: Writing back config space on device 0000:00:1f.3 at offset 1 (was 2800001, writing 2800003)
[    1.139096] PM: Writing back config space on device 0000:00:1f.5 at offset f (was 100, writing 10b)
[    1.139112] PM: Writing back config space on device 0000:00:1f.5 at offset 1 (was 2b00000, writing 2b00007)
[    1.139126] ACPI: PCI Interrupt 0000:00:1f.5[A] -> GSI 19 (level, low) -> IRQ 19
[    1.139130] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    1.139174] NVRM: RmPowerManagement: 5
[    1.414065] PM: Writing back config space on device 0000:03:00.0 at offset f (was 1ff, writing 10a)
[    1.414080] PM: Writing back config space on device 0000:03:00.0 at offset 8 (was c, writing fdef000c)
[    1.414085] PM: Writing back config space on device 0000:03:00.0 at offset 6 (was 4, writing fd9ff004)
[    1.414091] PM: Writing back config space on device 0000:03:00.0 at offset 4 (was 1, writing ce01)
[    1.414095] PM: Writing back config space on device 0000:03:00.0 at offset 3 (was 0, writing 10)
[    1.414101] PM: Writing back config space on device 0000:03:00.0 at offset 1 (was 100000, writing 100003)
[    1.450663] sd 0:0:0:0: [sda] Starting disk
[    1.630594] ata2.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    1.630596] ata2.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    1.630598] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    1.818353] ata2.00: configured for UDMA/100
[    6.160615] ata1: port is slow to respond, please be patient (Status 0x80)
[    6.604225] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    6.604226] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 filtered out
[    6.604228] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
[    6.707689] ata1.00: configured for UDMA/133
[    6.747221] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    6.747233] sd 0:0:0:0: [sda] Write Protect is off
[    6.747235] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.747252] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.850389] PM: Finishing wakeup.
[    6.850391] Restarting tasks ... done.
[    7.759847] r8169 Gigabit Ethernet driver 2.2LK loaded
[    7.759876] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[    7.759897] PCI: Setting latency timer of device 0000:03:00.0 to 64
[    7.760180] eth0: RTL8168c/8111c at 0xffffc2000103a000, 00:1d:09:94:14:5c, XID 3c4000c0 IRQ 508
[    7.767443] r8169: eth0: link down
[    7.767452] r8169: eth0: link down
[    7.930256] r8169: eth0: link down
[    9.645813] r8169: eth0: link up

also there's something wrong with my network it sometimes has a problem of reconnecting..

---

### Post by Bucky Ball on 2008-09-13
When you come out of suspend, it is not muting your sound is it? Double click on your speaker icon and check if anything has changed in there. Sounds silly, I know, but sillier things have happened.

As for getting the network back up, in a terminal:

                                       sudo /etc/init.d/networking restart


Not a fix, but you can search for the workaround for this. There is a lot of info about this known suspend issue. :)

---

### Post by dRock1286 on 2008-09-13
From what I've read, I believe that there is a problem with the hibernate mode.  It doesn't always fully wake up and I believe that is one thing they are trying to work on in  8.10

---

