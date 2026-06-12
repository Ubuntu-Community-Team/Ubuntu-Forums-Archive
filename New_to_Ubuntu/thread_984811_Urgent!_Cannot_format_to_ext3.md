---
title: "Urgent! Cannot format to ext3"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by urk_nono on 2008-11-17
Vista screwed up my friends computer, and after several tries I decied to go for Intrepid.

**Computer specs:**

HP Pavilion dv7 1095eo
2,53 ghz core 2 Duo T9400 (x64)
2 x 250 (5300RPM)
4096MB DDR2 SDRAM (2 DIMM)
GeForce 9600 GT 512MB DDR2

**What I have tried so far (and failed miserably):**

- Restore vista to an earlier point.
- Reinstalling Vista.
- Installing XP.
- Formatting sda1 to ext3.
- Installing Intrepid.

When I come to the point where partitioning and formatting to ext3 takes place, it locks up. I've searched numerous posts without any luck. Now my sda1 only reads as **"unallocated space"**.

**I tried issuing the following commands:**

$ sudo fsck dev/sda1
```
fsck 1.41.3 (12-Oct-2008)
```
*there wasn't anything else*

$ lscpi
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
```

$ dmesg
```
[    1.393236] bus: 06 index 3 mmio: [0, 0]
[    1.393237] bus: 07 index 0 io port: [1000, 1fff]
[    1.393239] bus: 07 index 1 mmio: [d9100000, da0fffff]
[    1.393240] bus: 07 index 2 mmio: [d8100000, d90fffff]
[    1.393241] bus: 07 index 3 mmio: [0, 0]
[    1.393242] bus: 0a index 0 mmio: [0, 0]
[    1.393243] bus: 0a index 1 mmio: [0, 0]
[    1.393245] bus: 0a index 2 mmio: [0, 0]
[    1.393246] bus: 0a index 3 io port: [0, ffff]
[    1.393247] bus: 0a index 4 mmio: [0, ffffffffffffffff]
[    1.393253] NET: Registered protocol family 2
[    1.432120] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.433073] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.436277] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.436784] TCP: Hash tables configured (established 524288 bind 65536)
[    1.436786] TCP reno registered
[    1.448112] NET: Registered protocol family 1
[    1.448212] checking if image is initramfs... it is
[    2.090493] Freeing initrd memory: 8979k freed
[    2.093381] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    2.093384] Simple Boot Flag at 0x44 set to 0x1
[    2.094156] audit: initializing netlink socket (disabled)
[    2.094179] type=2000 audit(1226904288.092:1): initialized
[    2.099030] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.100927] VFS: Disk quotas dquot_6.5.1
[    2.100988] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.101073] msgmni has been set to 7914
[    2.101165] io scheduler noop registered
[    2.101166] io scheduler anticipatory registered
[    2.101168] io scheduler deadline registered
[    2.101264] io scheduler cfq registered (default)
[   10.100006] pci 0000:00:1a.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   18.100006] pci 0000:00:1d.7: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[   18.100156] pci 0000:01:00.0: Boot video device
[   18.100254] pcieport-driver 0000:00:01.0: setting latency timer to 64
[   18.100280] pcieport-driver 0000:00:01.0: found MSI capability
[   18.100304] pci_express 0000:00:01.0:pcie00: allocate port service
[   18.100334] pci_express 0000:00:01.0:pcie02: allocate port service
[   18.100363] pci_express 0000:00:01.0:pcie03: allocate port service
[   18.100430] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[   18.100472] pcieport-driver 0000:00:1c.0: found MSI capability
[   18.100516] pci_express 0000:00:1c.0:pcie00: allocate port service
[   18.100544] pci_express 0000:00:1c.0:pcie02: allocate port service
[   18.100572] pci_express 0000:00:1c.0:pcie03: allocate port service
[   18.100663] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[   18.100704] pcieport-driver 0000:00:1c.1: found MSI capability
[   18.100745] pci_express 0000:00:1c.1:pcie00: allocate port service
[   18.100777] pci_express 0000:00:1c.1:pcie02: allocate port service
[   18.100805] pci_express 0000:00:1c.1:pcie03: allocate port service
[   18.100894] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[   18.100936] pcieport-driver 0000:00:1c.2: found MSI capability
[   18.100977] pci_express 0000:00:1c.2:pcie00: allocate port service
[   18.101005] pci_express 0000:00:1c.2:pcie02: allocate port service
[   18.101032] pci_express 0000:00:1c.2:pcie03: allocate port service
[   18.101122] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[   18.101164] pcieport-driver 0000:00:1c.3: found MSI capability
[   18.101204] pci_express 0000:00:1c.3:pcie00: allocate port service
[   18.101233] pci_express 0000:00:1c.3:pcie02: allocate port service
[   18.101260] pci_express 0000:00:1c.3:pcie03: allocate port service
[   18.101356] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[   18.101399] pcieport-driver 0000:00:1c.4: found MSI capability
[   18.101439] pci_express 0000:00:1c.4:pcie00: allocate port service
[   18.101468] pci_express 0000:00:1c.4:pcie02: allocate port service
[   18.101495] pci_express 0000:00:1c.4:pcie03: allocate port service
[   18.101586] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[   18.101627] pcieport-driver 0000:00:1c.5: found MSI capability
[   18.101668] pci_express 0000:00:1c.5:pcie00: allocate port service
[   18.101698] pci_express 0000:00:1c.5:pcie02: allocate port service
[   18.101727] pci_express 0000:00:1c.5:pcie03: allocate port service
[   18.125577] hpet_resources: 0xfed00000 is busy
[   18.125645] Linux agpgart interface v0.103
[   18.125649] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   18.127310] brd: module loaded
[   18.127365] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.127451] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[   18.176633] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.176637] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.204578] mice: PS/2 mouse device common for all mice
[   18.204662] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[   18.204690] rtc0: alarms up to one month, hpet irqs
[   18.204718] cpuidle: using governor ladder
[   18.204719] cpuidle: using governor menu
[   18.204999] TCP cubic registered
[   18.205141] registered taskstats version 1
[   18.205269]   Magic number: 0:626:721
[   18.205367] rtc_cmos 00:03: setting system clock to 2008-11-17 06:45:05 UTC (1226904305)
[   18.205369] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   18.205370] EDD information not available.
[   18.205422] Freeing unused kernel memory: 536k freed
[   18.205609] Write protecting the kernel read-only data: 4348k
[   18.236578] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.330267] fuse init (API version 7.9)
[   18.439540] fan PNP0C0B:00: registered as cooling_device0
[   18.439545] ACPI: Fan [FAN] (on)
[   18.463962] ACPI: SSDT BFC77C18, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[   18.464468] ACPI: SSDT BFC75618, 0594 (r1  PmRef  Cpu0Cst     3001 INTL 20060912)
[   18.464927] Monitor-Mwait will be used to enter C-1 state
[   18.464930] Monitor-Mwait will be used to enter C-2 state
[   18.464931] Monitor-Mwait will be used to enter C-3 state
[   18.494727] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.494770] processor ACPI0007:00: registered as cooling_device1
[   18.494773] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.495241] ACPI: SSDT BFC76E18, 01CF (r1  PmRef    ApIst     3000 INTL 20060912)
[   18.495683] ACPI: SSDT BFC77F18, 008D (r1  PmRef    ApCst     3000 INTL 20060912)
[   18.496286] Marking TSC unstable due to TSC halts in idle
[   18.496425] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   18.496464] processor ACPI0007:01: registered as cooling_device2
[   18.496467] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.510465] thermal LNXTHERM:01: registered as thermal_zone0
[   18.538458] ACPI: Thermal Zone [THRM] (51 C)
[   18.642787] usbcore: registered new interface driver usbfs
[   18.642803] usbcore: registered new interface driver hub
[   18.647702] usbcore: registered new device driver usb
[   18.649042] USB Universal Host Controller Interface driver v3.0
[   18.649084] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.649100] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[   18.649109] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   18.649139] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   18.649231] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000090e0
[   18.649369] usb usb1: configuration #1 chosen from 1 choice
[   18.649388] hub 1-0:1.0: USB hub found
[   18.649393] hub 1-0:1.0: 2 ports detected
[   18.856238] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   18.856261] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[   18.856265] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   18.856283] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   18.856382] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000090c0
[   18.856476] usb usb2: configuration #1 chosen from 1 choice
[   18.856495] hub 2-0:1.0: USB hub found
[   18.856500] hub 2-0:1.0: 2 ports detected
[   18.950583] No dock devices found.
[   18.960303] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   18.960316] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[   18.960319] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   18.960340] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[   18.964264] ehci_hcd 0000:00:1a.7: debug port 1
[   18.964270] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[   18.964285] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xdf304c00
[   18.968172] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   18.969496] SCSI subsystem initialized
[   18.980031] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.980107] usb usb3: configuration #1 chosen from 1 choice
[   18.980126] hub 3-0:1.0: USB hub found
[   18.980133] hub 3-0:1.0: 4 ports detected
[   18.980160] libata version 3.00 loaded.
[   19.047663] hub 1-0:1.0: unable to enumerate USB device on port 1
[   19.188380] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   19.188391] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   19.188399] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.188418] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   19.188514] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000090a0
[   19.188610] usb usb4: configuration #1 chosen from 1 choice
[   19.188629] hub 4-0:1.0: USB hub found
[   19.188634] hub 4-0:1.0: 2 ports detected
[   19.292511] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   19.292528] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   19.292537] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.292557] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   19.292701] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00009080
[   19.292811] usb usb5: configuration #1 chosen from 1 choice
[   19.292830] hub 5-0:1.0: USB hub found
[   19.292834] hub 5-0:1.0: 2 ports detected
[   19.396296] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   19.396312] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   19.396320] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.396344] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   19.396403] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00009060
[   19.396488] usb usb6: configuration #1 chosen from 1 choice
[   19.396506] hub 6-0:1.0: USB hub found
[   19.396512] hub 6-0:1.0: 2 ports detected
[   19.604404] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[   19.604424] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   19.604434] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   19.604450] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 7
[   19.604585] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00009040
[   19.604692] usb usb7: configuration #1 chosen from 1 choice
[   19.604710] hub 7-0:1.0: USB hub found
[   19.604715] hub 7-0:1.0: 2 ports detected
[   19.652511] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   19.708748] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   19.708773] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   19.708784] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   19.708800] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   19.712834] ehci_hcd 0000:00:1d.7: debug port 1
[   19.712866] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   19.712870] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdf304800
[   19.780150] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.780318] usb usb8: configuration #1 chosen from 1 choice
[   19.780337] hub 8-0:1.0: USB hub found
[   19.780349] hub 8-0:1.0: 8 ports detected
[   19.831404] usb 1-1: configuration #1 chosen from 1 choice
[   19.988535] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   19.988550] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   19.988571] r8169 0000:05:00.0: setting latency timer to 64
[   19.989342] ahci 0000:00:1f.2: version 3.0
[   19.989377] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[   19.989855] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[   19.989857] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ems 
[   19.989872] ahci 0000:00:1f.2: setting latency timer to 64
[   19.990744] eth0: RTL8168c/8111c at 0xffffc20000644000, 00:1e:ec:7b:a9:80, XID 3c4000c0 IRQ 2296
[   19.993316] ohci1394 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.993334] ohci1394 0000:06:00.0: setting latency timer to 64
[   20.045119] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[da100000-da1007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   20.050346] scsi0 : ahci
[   20.050474] scsi1 : ahci
[   20.050568] scsi2 : ahci
[   20.050671] scsi3 : ahci
[   20.050758] scsi4 : ahci
[   20.051997] scsi5 : ahci
[   20.052175] ata1: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304100 irq 2295
[   20.052185] ata2: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304180 irq 2295
[   20.052186] ata3: DUMMY
[   20.052187] ata4: DUMMY
[   20.052194] ata5: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304300 irq 2295
[   20.052203] ata6: SATA max UDMA/133 abar m2048@0xdf304000 port 0xdf304380 irq 2295
[   20.160045] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   20.318457] usb 1-2: configuration #1 chosen from 1 choice
[   20.500510] Clocksource tsc unstable (delta = -154341024 ns)
[   20.540050] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   20.541444] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   20.541666] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   20.541866] ata1.00: ACPI cmd ef/10:02:00:00:00:a0 succeeded
[   20.541868] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   20.542071] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   20.542271] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   20.543017] ata1.00: ATA-8: Hitachi HTS542525K9A300, BBFOC3MP, max UDMA/100
[   20.543019] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   20.544597] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   20.544824] ata1.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   20.544826] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   20.545049] ata1.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   20.545258] ata1.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   20.545265] ata1.00: configured for UDMA/100
[   20.560117] usb 8-5: new high speed USB device using ehci_hcd and address 2
[   20.720705] usb 8-5: configuration #1 chosen from 1 choice
[   21.325045] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[863f0200883540d9]
[   21.448119] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   21.449632] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.449930] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.450159] ata2.00: ACPI cmd ef/10:02:00:00:00:b0 succeeded
[   21.450162] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   21.450373] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.450586] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.451345] ata2.00: ATA-8: Hitachi HTS542525K9A300, BBFOC3MP, max UDMA/100
[   21.451349] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   21.453098] ata2.00: ACPI cmd 00/00:00:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.453359] ata2.00: ACPI cmd ef/10:01:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.453362] ata2.00: ACPI cmd ef/10:03:00:00:00:b0 filtered out
[   21.453581] ata2.00: ACPI cmd ef/10:04:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.453799] ata2.00: ACPI cmd ef/10:05:00:00:00:b0 rejected by device (Stat=0x51 Err=0x04)
[   21.453811] ata2.00: configured for UDMA/100
[   21.956119] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.960063] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.960204] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.960581] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.960584] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   21.960844] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.961068] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.961072] ata5.00: ATAPI: Optiarc BD ROM BC-5500S, 1.83, max UDMA/100
[   21.964063] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.964446] ata5.00: ACPI cmd ef/10:01:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.964708] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.964711] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[   21.965011] ata5.00: ACPI cmd ef/10:04:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.965161] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 rejected by device (Stat=0x51 Err=0x04)
[   21.965172] ata5.00: configured for UDMA/100
[   22.300155] ata6: SATA link down (SStatus 0 SControl 300)
[   22.316255] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[   22.316371] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[   22.318970] scsi 4:0:0:0: CD-ROM            Optiarc  BD ROM BC-5500S  1.83 PQ: 0 ANSI: 5
[   22.324706] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[   22.324734] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[   22.324761] scsi 4:0:0:0: Attached scsi generic sg2 type 5
[   22.336306] Driver 'sd' needs updating - please use bus_type methods
[   22.336582] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   22.336598] sd 0:0:0:0: [sda] Write Protect is off
[   22.336600] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.336625] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.336695] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   22.336709] sd 0:0:0:0: [sda] Write Protect is off
[   22.336710] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.336736] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.336738]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.659476]  sda1 sda2 < sda5 >
[   22.685102] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.685166] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   22.685181] sd 1:0:0:0: [sdb] Write Protect is off
[   22.685182] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.685208] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.685256] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   22.685270] sd 1:0:0:0: [sdb] Write Protect is off
[   22.685271] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   22.685297] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.685300]  sdb: sdb1
[   23.002258] sd 1:0:0:0: [sdb] Attached SCSI disk
[   23.004893] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.004896] Uniform CD-ROM driver Revision: 3.20
[   23.004945] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   28.997338] ISO 9660 Extensions: Microsoft Joliet Level 3
[   29.045534] ISO 9660 Extensions: RRIP_1991A
[   29.295673] aufs 20080922
[   29.300053] loop: module loaded
[   29.594178] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[   96.450826] udevd version 124 started
[   97.111810] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   97.174823] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   97.644178] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   97.965883] ACPI: Battery Slot [BAT0] (battery present)
[   97.967089] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   97.976021] ACPI: Power Button (FF) [PWRF]
[   97.976157] ACPI: WMI: Mapper loaded
[   98.116287] ACPI: AC Adapter [AC] (on-line)
[   98.116382] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   98.144060] ACPI: Power Button (CM) [PWRB]
[   98.144145] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   98.144242] ACPI: Lid Switch [LID0]
[   98.144323] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   98.176065] ACPI: Sleep Button (CM) [SLPB]
[   98.237958] Bluetooth: Core ver 2.13
[   98.239830] NET: Registered protocol family 31
[   98.239831] Bluetooth: HCI device and connection manager initialized
[   98.239834] Bluetooth: HCI socket layer initialized
[   98.245820] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   98.245897] usbcore: registered new interface driver btusb
[   98.933960] sdhci: Secure Digital Host Controller Interface driver
[   98.933963] sdhci: Copyright(c) Pierre Ossman
[   99.042180] Linux video capture interface: v2.00
[   99.260114] sdhci-pci 0000:06:00.1: SDHCI controller found [197b:2382] (rev 0)
[   99.260135] sdhci-pci 0000:06:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   99.260168] sdhci-pci 0000:06:00.1: setting latency timer to 64
[   99.260262] mmc0: SDHCI controller on PCI [0000:06:00.1] using DMA
[   99.264892] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 0)
[   99.264907] sdhci-pci 0000:06:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   99.264915] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[   99.264921] sdhci-pci 0000:06:00.2: PCI INT A disabled
[   99.334438] uvcvideo: Found UVC 1.00 device HP Webcam  (046d:09b8)
[   99.339280] input: HP Webcam  as /devices/pci0000:00/0000:00:1d.7/usb8/8-5/8-5:1.0/input/input7
[   99.360479] acpi device:04: registered as cooling_device3
[   99.360872] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input8
[   99.368657] usbcore: registered new interface driver uvcvideo
[   99.368676] USB Video Class driver (v0.1.0)
[   99.432676] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   99.457892] acpi device:09: registered as cooling_device4
[   99.459145] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/device:08/input/input9
[   99.512109] ACPI: Video Device [EVGA] (multi-head: yes  rom: no  post: no)
[   99.547068] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   99.547071] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   99.547153] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   99.547161] iwlagn 0000:02:00.0: setting latency timer to 64
[   99.547183] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   99.576750] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   99.576977] iwlagn 0000:02:00.0: PCI INT A disabled
[   99.577646] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   99.692742] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   99.692750] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[   99.692769] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  100.242866] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04751/0xa00000
[  100.396534] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[  100.728509] hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[  103.837836] Adding 6000236k swap on /dev/sda5.  Priority:-1 extents:1 across:6000236k
[  104.522134] ip_tables: (C) 2000-2006 Netfilter Core Team
[  108.623042] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  108.815359] lp: driver loaded but no devices found
[  108.917574] ppdev: user-space parallel port driver
[  115.666541] Bluetooth: L2CAP ver 2.11
[  115.666554] Bluetooth: L2CAP socket layer initialized
[  115.966752] Bluetooth: RFCOMM socket layer initialized
[  115.966783] Bluetooth: RFCOMM TTY layer initialized
[  115.966788] Bluetooth: RFCOMM ver 1.10
[  115.969394] Bluetooth: SCO (Voice Link) ver 0.6
[  115.969404] Bluetooth: SCO socket layer initialized
[  116.233302] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  116.233318] Bluetooth: BNEP filters: protocol multicast
[  116.830664] Bridge firewalling registered
[  116.830982] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[  121.541591] r8169: eth0: link down
[  121.563979] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  121.564110] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[  121.568430] firmware: requesting iwlwifi-5000-1.ucode
[  124.015130] Registered led device: iwl-phy0:radio
[  124.015733] Registered led device: iwl-phy0:assoc
[  124.016220] Registered led device: iwl-phy0:RX
[  124.017525] Registered led device: iwl-phy0:TX
[  124.447436] NET: Registered protocol family 17
[  125.969698] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  126.168267] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  126.368309] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  126.568279] wlan0: authentication with AP 00:08:a1:a3:f0:ad timed out
[  176.593825] CPU0 attaching NULL sched-domain.
[  176.593837] CPU1 attaching NULL sched-domain.
[  176.612625] CPU0 attaching sched-domain:
[  176.612632]  domain 0: span 0-1 level MC
[  176.612635]   groups: 0 1
[  176.612640]   domain 1: span 0-1 level NODE
[  176.612642]    groups: 0-1
[  176.612646] CPU1 attaching sched-domain:
[  176.612648]  domain 0: span 0-1 level MC
[  176.612650]   groups: 1 0
[  176.612654]   domain 1: span 0-1 level NODE
[  176.612656]    groups: 0-1
[  338.413241] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  338.612283] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  338.812287] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  339.012282] wlan0: authentication with AP 00:08:a1:a3:f0:ad timed out
[  350.374104] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  350.572282] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  350.772283] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  350.972281] wlan0: authentication with AP 00:08:a1:a3:f0:ad timed out
[  361.502456] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  361.700324] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  361.900281] wlan0: authenticate with AP 00:08:a1:a3:f0:ad
[  362.100281] wlan0: authentication with AP 00:08:a1:a3:f0:ad timed out
[  386.750237] wlan0: authenticate with AP 00:1c:10:bf:a3:bd
[  386.750658] wlan0: authenticate with AP 00:1c:10:bf:a3:bd
[  386.755091] wlan0: authenticated
[  386.755102] wlan0: associate with AP 00:1c:10:bf:a3:bd
[  386.759391] wlan0: RX AssocResp from 00:1c:10:bf:a3:bd (capab=0x411 status=0 aid=2)
[  386.759401] wlan0: associated
[  420.021501] NET: Registered protocol family 10
[  420.022705] lo: Disabled Privacy Extensions
[  420.023577] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  430.108255] wlan0: no IPv6 routers present
[  600.724105] CE: hpet increasing min_delta_ns to 15000 nsec
[  600.724206] CE: hpet increasing min_delta_ns to 22500 nsec
[  851.856609] CE: hpet increasing min_delta_ns to 33750 nsec
[  852.744097] CE: hpet increasing min_delta_ns to 50624 nsec
[ 1744.120254] CE: hpet increasing min_delta_ns to 75936 nsec
[ 1753.072781] CE: hpet increasing min_delta_ns to 113904 nsec
[ 3427.156276] CE: hpet increasing min_delta_ns to 170856 nsec
```



I've done some reading on this post: [http://ubuntuforums.org/showthread.php?t=875408]("http://ubuntuforums.org/showthread.php?t=875408"), but I'm afraid I might damage the system even further.

I'd appreciate ANY contribution, especially comments degrading Windows to dung.

Thanks in advance

---

### Post by Keen101 on 2008-11-17
hmm... i've heard weird things when formatting and partitioning when vista is involved. Some people have recommended using vista's partitioning software when shrinking a vista partition. But, you said you couldn't even reinstall it. strange. have you tried the Gparted Live-cd?

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by handydan918 on 2008-11-17
> **urk_nono said:**
> Vista screwed up my friends computer, and after several tries I decied to go for Intrepid.

**Computer specs:**

HP Pavilion dv7 1095eo
2,53 ghz core 2 Duo T9400 (x64)
2 x 250 (5300RPM)
4096MB DDR2 SDRAM (2 DIMM)
GeForce 9600 GT 512MB DDR2

**What I have tried so far (and failed miserably):**

- Restore vista to an earlier point.
- Reinstalling Vista.
- Installing XP.
- Formatting sda1 to ext3.
- Installing Intrepid.

When I come to the point where partitioning and formatting to ext3 takes place, it locks up. I've searched numerous posts without any luck. Now my sda1 only reads as **"unallocated space"**.

I've done some reading on this post: [http://ubuntuforums.org/showthread.php?t=875408]("http://ubuntuforums.org/showthread.php?t=875408"), but I'm afraid I might damage the system even further.At this point, that doesn't seem likely...> 

I'd appreciate ANY contribution, especially comments degrading Windows to dung.Ridiculous. Dung is useful as fertilizer. Windows, not so much.
If you can boot the live cd, I guess i'd try using fdisk to format the drive. It's destructive, unlike gparted, so don't use it if there are data on the drive yo wish to preserve. Failing that, you might try downloading a gparted cd to try this with.

---

### Post by bumanie on 2008-11-17
Well...unallocated space at least means you have got rid of vista. If the live cd is not working re formatting, you have two main choices A) Download the alternate install cd and try that, it's text-based and usually installs when the live cd won't or B) Format with gparted live cd, although available on the ubuntu live cd, gparted live cd is a dedicated partitioning/formatting tool and IMO is slightly better than the ubuntu one. If neither of those work, wipe the drive with something like dban or get a 'wiper' from the HDD manufacturers site and then try gparted again.
As for your last request - you may get a few takers, but basically we don't bag "other OSes" - having used "other OSes" in the past and no longer using them, is a testament to what most linux users think of the "other OSes".

---

### Post by urk_nono on 2008-11-17
**Update:**

Thank you for your contributions. I greatly appreciate you all taking time to look into my problem.

I downloaded DBAN, Ubuntu alternate install disc and Gparted live-disc and ran them. Unfortunately without any luck.

The Gparted live-disc gave the same results as the one implemented in the ubuntu live-CD, it locked up during partitioning. I suspect that Vista screwed up the hard drive.

When I ran DBAN I recieved this message:
"DBAN finished with non-fatal errors.
 This is usually caused by disks with bad sectors"

After the DBAN finished I ran the ubuntu live-cd to check if there was any changes to the hard drive, but still there was nothing. 

I then tried to install intrepid with the anternate cd, but it couldn't mount the hard drive.

Right now I have one hard drive which is unallocated, and the other with my friends personal files. I suspect that I could be able to install Vista/Intrepid on the other hard drive, but I have no idea what the outcome might be. Perhaps I would be able to fix the broken hard drive once I get Vista/Intrepid up and running?

Once more, thanks for your concern.

---

### Post by bumanie on 2008-11-17
Most of the hard drive manufacturers have free .iso files to download that will do hard drive diagnostic tests via a live cd - try that. If they can't 'repair/rejuvenate' the hard drive, you will probably need a new hard drive. Even though I am no fan of vista's it is unlikely to have caused the problem if the hard drive is fragged, it is more likely a standard hardware failure.

---

