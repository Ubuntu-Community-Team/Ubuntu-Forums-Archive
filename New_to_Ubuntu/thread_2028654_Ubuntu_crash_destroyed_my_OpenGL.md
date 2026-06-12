---
title: "Ubuntu crash destroyed my OpenGL"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by bergj on 2012-07-18
I am a student in a 3d graphics program and I switched a few days ago to Ubuntu 12 to work on my project. All was going well until for some reason - just a few minutes ago - the project froze on me and then I couldnt move my cursor at all so I opened up a terminal and did 

sudo reboot -h 0

on reboot, none of my 3d programs will show the 3d viewport (maya, mari). I was so close to finishing the project which I have to present to the class in 3 hours. Now, I am probably completly F'ED because of this. I cannot port my project to windows at this point because i have no time to do that.

It says - "Bad Window"  in one program, unable to obtain OpenGL version information in another.

What should I do???? This is very time sensetive at this point

:(

---

### Post by Cheesemill on 2012-07-18
Please post the outputs of:
```
dmesg
sudo tail -f 100 /var/log/kern.log
sudo tail -f 100 /var/log/syslog
sudo cat /var/log/Xorg.0.log
```

This is a forum made up of volunteers, It make take at least several days before you can get a fix to your problem.

---

### Post by bergj on 2012-07-18
> **Cheesemill said:**
> Please post the outputs of:
```
dmesg
sudo tail -f 100 /var/log/kern.log
sudo tail -f 100 /var/log/syslog
sudo cat /var/log/Xorg.0.log
```This is a forum made up of volunteers, It make take at least several days before you can get a fix to your problem.



I applied some "fixes" by some from blogs with similar problems and now my situation is 10x worse. Im now stuck in a 640x480 resolution on a single screen, and my programs cant find GLX  and I cant increase my resolution because this god damn nvidia x server says that I appear not to be using its driver

and Im going to get a bad grade on this presentation and there is no way to transfer it to windows and keep my work. I seriously have not been this dissappointed in a really really really long time. I feel like Im likely to lose ALL my work

My graphics card is nvidia gtx 570

Here is the ouputs of that stuff


```

[    1.427419] ata_piix 0000:00:1f.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.427422] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.427447] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.427624] scsi8 : ata_piix
[    1.427664] scsi9 : ata_piix
[    1.428314] ata9: SATA max UDMA/133 cmd 0x9000 ctl 0x8c00 bmdma 0x8480 irq 20
[    1.428318] ata10: SATA max UDMA/133 cmd 0x8880 ctl 0x8800 bmdma 0x8488 irq 20
[    1.428330] ata_piix 0000:00:1f.5: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.428333] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    1.428358] ata_piix 0000:00:1f.5: setting latency timer to 64
[    1.428490] scsi10 : ata_piix
[    1.428533] scsi11 : ata_piix
[    1.429156] ata11: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 20
[    1.429159] ata12: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 20
[    1.429367] Fixed MDIO Bus: probed
[    1.429379] tun: Universal TUN/TAP device driver, 1.6
[    1.429380] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.429411] PPP generic driver version 2.4.2
[    1.429469] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.429480] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.429490] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.429492] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.429522] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    1.429540] ehci_hcd 0000:00:1a.7: debug port 1
[    1.433410] ehci_hcd 0000:00:1a.7: cache line size of 256 is not supported
[    1.433420] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9dff000
[    1.446389] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.446500] hub 1-0:1.0: USB hub found
[    1.446503] hub 1-0:1.0: 6 ports detected
[    1.446561] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.446570] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.446573] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.446608] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.446625] ehci_hcd 0000:00:1d.7: debug port 1
[    1.450493] ehci_hcd 0000:00:1d.7: cache line size of 256 is not supported
[    1.450503] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9dfe000
[    1.466379] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.466479] hub 2-0:1.0: USB hub found
[    1.466482] hub 2-0:1.0: 6 ports detected
[    1.466538] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.466548] uhci_hcd: USB Universal Host Controller Interface driver
[    1.466558] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.466563] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.466566] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.466596] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.466623] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000a800
[    1.466700] hub 3-0:1.0: USB hub found
[    1.466703] hub 3-0:1.0: 2 ports detected
[    1.466749] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.466754] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.466756] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.466788] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.466814] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000a880
[    1.466887] hub 4-0:1.0: USB hub found
[    1.466890] hub 4-0:1.0: 2 ports detected
[    1.466937] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.466942] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.466944] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.466973] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    1.467000] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000ac00
[    1.467075] hub 5-0:1.0: USB hub found
[    1.467078] hub 5-0:1.0: 2 ports detected
[    1.467123] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.467128] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.467130] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.467157] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    1.467177] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000a080
[    1.467250] hub 6-0:1.0: USB hub found
[    1.467252] hub 6-0:1.0: 2 ports detected
[    1.467298] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.467303] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.467305] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.467332] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    1.467353] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    1.467427] hub 7-0:1.0: USB hub found
[    1.467430] hub 7-0:1.0: 2 ports detected
[    1.467475] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.467479] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.467482] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.467510] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    1.467530] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a480
[    1.467606] hub 8-0:1.0: USB hub found
[    1.467609] hub 8-0:1.0: 2 ports detected
[    1.467667] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
[    1.467677] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    1.467679] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.467709] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.573328] xhci_hcd 0000:02:00.0: irq 29, io mem 0xf9ffe000
[    1.573369] xhci_hcd 0000:02:00.0: irq 67 for MSI/MSI-X
[    1.573372] xhci_hcd 0000:02:00.0: irq 68 for MSI/MSI-X
[    1.573376] xhci_hcd 0000:02:00.0: irq 69 for MSI/MSI-X
[    1.573379] xhci_hcd 0000:02:00.0: irq 70 for MSI/MSI-X
[    1.573382] xhci_hcd 0000:02:00.0: irq 71 for MSI/MSI-X
[    1.573386] xhci_hcd 0000:02:00.0: irq 72 for MSI/MSI-X
[    1.573389] xhci_hcd 0000:02:00.0: irq 73 for MSI/MSI-X
[    1.573392] xhci_hcd 0000:02:00.0: irq 74 for MSI/MSI-X
[    1.573512] xHCI xhci_add_endpoint called for root hub
[    1.573513] xHCI xhci_check_bandwidth called for root hub
[    1.573532] hub 9-0:1.0: USB hub found
[    1.573536] hub 9-0:1.0: 2 ports detected
[    1.573576] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.573609] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 10
[    1.576705] xHCI xhci_add_endpoint called for root hub
[    1.576706] xHCI xhci_check_bandwidth called for root hub
[    1.576723] hub 10-0:1.0: USB hub found
[    1.576727] hub 10-0:1.0: 2 ports detected
[    1.622369] usbcore: registered new interface driver libusual
[    1.622396] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.625161] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.625165] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.625245] mousedev: PS/2 mouse device common for all mice
[    1.625336] rtc_cmos 00:03: RTC can wake from S4
[    1.625415] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.625437] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.625486] device-mapper: uevent: version 1.0.3
[    1.625529] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [email]dm-devel@redhat.com[/email]
[    1.625655] cpuidle: using governor ladder
[    1.625852] cpuidle: using governor menu
[    1.625854] EFI Variables Facility v0.08 2004-May-17
[    1.626006] TCP cubic registered
[    1.626074] NET: Registered protocol family 10
[    1.626417] NET: Registered protocol family 17
[    1.626420] Registering the dns_resolver key type
[    1.626525] PM: Hibernation image not present or could not be loaded.
[    1.626533] registered taskstats version 1
[    1.645682]   Magic number: 4:880:289
[    1.645718] tty tty22: hash matches
[    1.645961] rtc_cmos 00:03: setting system clock to 2012-07-18 17:17:23 UTC (1342631843)
[    1.647899] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.647900] EDD information not available.
[    1.742458] ata8: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.742479] ata7: SATA link down (SStatus 0 SControl 300)
[    1.742598] ata8.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    1.742826] ata8.00: configured for UDMA/66
[    1.746438] ata3: SATA link down (SStatus 0 SControl 300)
[    1.746459] ata5: SATA link down (SStatus 0 SControl 300)
[    1.746480] ata4: SATA link down (SStatus 0 SControl 300)
[    1.750461] ata6: SATA link down (SStatus 0 SControl 300)
[    1.750480] ata2: SATA link down (SStatus 0 SControl 300)
[    1.754444] ata1: SATA link down (SStatus 0 SControl 300)
[    1.762848] scsi 7:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    1.763138] scsi 7:0:0:0: Attached scsi generic sg0 type 3
[    1.782382] usb 2-3: new high-speed USB device number 2 using ehci_hcd
[    1.902310] ata12: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.902416] ata11: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.910693] ata11.00: ATA-8: ST31000528AS, CC3E, max UDMA/133
[    1.910697] ata11.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.915311] hub 2-3:1.0: USB hub found
[    1.915485] hub 2-3:1.0: 4 ports detected
[    1.926761] ata11.00: configured for UDMA/133
[    1.926973] ata12.00: ATA-8: OCZ-AGILITY3, 2.22, max UDMA/133
[    1.926977] ata12.00: 117231408 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.958780] ata12.00: configured for UDMA/133
[    2.138156] Refined TSC clocksource calibration: 3073.635 MHz.
[    2.138161] Switching to clocksource tsc
[    2.138338] usb 10-1: new SuperSpeed USB device number 2 using xhci_hcd
[    2.159966] Initializing USB Mass Storage driver...
[    2.160244] scsi12 : usb-storage 10-1:1.0
[    2.160281] usbcore: registered new interface driver usb-storage
[    2.160282] USB Mass Storage support registered.
[    2.218099] ata10.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.218114] ata10.01: SATA link down (SStatus 0 SControl 300)
[    2.218125] ata10.01: link offline, clearing class 3 to NONE
[    2.226222] ata10.00: ATAPI: ATAPI   DVD A  DH24AYS, BP5X, max UDMA/100
[    2.230144] ata9.00: SATA link down (SStatus 0 SControl 300)
[    2.230158] ata9.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.230218] usb 2-3.1: new low-speed USB device number 4 using ehci_hcd
[    2.246286] ata10.00: configured for UDMA/100
[    2.259229] ata9.01: ATA-8: WDC WD10EARS-00Z5B1, 80.00A80, max UDMA/133
[    2.259233] ata9.01: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.267221] ata9.01: configured for UDMA/133
[    2.267458] scsi 8:0:1:0: Direct-Access     ATA      WDC WD10EARS-00Z 80.0 PQ: 0 ANSI: 5
[    2.267654] sd 8:0:1:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.267670] sd 8:0:1:0: Attached scsi generic sg1 type 0
[    2.267698] sd 8:0:1:0: [sda] Write Protect is off
[    2.267700] sd 8:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    2.267714] sd 8:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.269249] scsi 9:0:0:0: CD-ROM            ATAPI    DVD A  DH24AYS   BP5X PQ: 0 ANSI: 5
[    2.271667] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.271672] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.271880] sr 9:0:0:0: Attached scsi CD-ROM sr0
[    2.272151] sr 9:0:0:0: Attached scsi generic sg2 type 5
[    2.272599] scsi 10:0:0:0: Direct-Access     ATA      ST31000528AS     CC3E PQ: 0 ANSI: 5
[    2.272761] sd 10:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.272801] sd 10:0:0:0: [sdb] Write Protect is off
[    2.272803] sd 10:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.272814] sd 10:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.272836] sd 10:0:0:0: Attached scsi generic sg3 type 0
[    2.273229] scsi 11:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.22 PQ: 0 ANSI: 5
[    2.273544] sd 11:0:0:0: Attached scsi generic sg4 type 0
[    2.273547] sd 11:0:0:0: [sdc] 117231408 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    2.274037] sd 11:0:0:0: [sdc] Write Protect is off
[    2.274040] sd 11:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.274196] sd 11:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.276865]  sdc: sdc1 sdc2
[    2.278171] sd 11:0:0:0: [sdc] Attached SCSI disk
[    2.292329]  sdb: sdb1
[    2.292891] sd 10:0:0:0: [sdb] Attached SCSI disk
[    2.307384]  sda: sda1 sda2 < sda5 >
[    2.308121] sd 8:0:1:0: [sda] Attached SCSI disk
[    2.309360] Freeing unused kernel memory: 920k freed
[    2.309441] Write protecting the kernel read-only data: 12288k
[    2.313097] Freeing unused kernel memory: 1616k freed
[    2.315966] Freeing unused kernel memory: 1200k freed
[    2.331737] udevd[144]: starting version 175
[    2.336579] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1:1.0/input/input2
[    2.336907] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.7-3.1/input0
[    2.336925] usbcore: registered new interface driver usbhid
[    2.336927] usbhid: USB HID core driver
[    2.355684] sky2: driver version 1.30
[    2.355708] sky2 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.355717] sky2 0000:05:00.0: setting latency timer to 64
[    2.355741] sky2 0000:05:00.0: Yukon-2 EC Ultra chip revision 3
[    2.355823] sky2 0000:05:00.0: irq 75 for MSI/MSI-X
[    2.356593] sky2 0000:05:00.0: eth0: addr 20:cf:30:e3:e0:a0
[    2.360182] firewire_ohci 0000:07:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.406264] usb 2-3.4: new full-speed USB device number 5 using ehci_hcd
[    2.426076] firewire_ohci: Added fw-ohci device 0000:07:02.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    2.741905] usb 7-2: new full-speed USB device number 2 using uhci_hcd
[    2.866521] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.926043] firewire_core: created device fw0: GUID 001e8c0000352392, S400
[    2.936874] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input3
[    2.937106] generic-usb 0003:046D:C318.0002: input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:00:1d.1-2/input0
[    2.941942] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input4
[    2.942327] generic-usb 0003:046D:C318.0003: input,hiddev0,hidraw2: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:00:1d.1-2/input1
[    3.158547] scsi 12:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 0001 PQ: 0 ANSI: 6
[    3.159584] sd 12:0:0:0: Attached scsi generic sg5 type 0
[    3.159788] sd 12:0:0:0: [sdd] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    3.160255] sd 12:0:0:0: [sdd] Write Protect is off
[    3.160259] sd 12:0:0:0: [sdd] Mode Sense: 1f 00 00 08
[    3.160759] sd 12:0:0:0: [sdd] No Caching mode page present
[    3.160762] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[    3.162254] sd 12:0:0:0: [sdd] No Caching mode page present
[    3.162257] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[    3.520395]  sdd: sdd1
[    3.522486] sd 12:0:0:0: [sdd] No Caching mode page present
[    3.522490] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[    3.522493] sd 12:0:0:0: [sdd] Attached SCSI disk
[    5.093966] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.166529] udevd[490]: starting version 175
[    5.286875] Adding 34056188k swap on /dev/sda5.  Priority:-1 extents:1 across:34056188k 
[    6.005795] lp: driver loaded but no devices found
[    6.526923] EDAC MC: Ver: 2.1.0
[    6.558454] wmi: Mapper loaded
[    6.634982] EDAC MC0: Giving out device to 'i7core_edac.c' 'i7 core #0': DEV 0000:ff:03.0
[    6.634994] EDAC PCI0: Giving out device to module 'i7core_edac' controller 'EDAC PCI controller': DEV '0000:ff:03.0' (POLLED)
[    6.635001] EDAC i7core: Driver loaded, 1 memory controller(s) found.
[    6.815426] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    6.932417] input: Wacom Bamboo Pen Pen as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4:1.0/input/input5
[    6.935047] input: Wacom Bamboo Pen Finger as /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4:1.1/input/input6
[    6.935171] usbcore: registered new interface driver wacom
[    6.935173] wacom: v1.53:USB Wacom tablet driver
[    7.768990] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.769028] snd_hda_intel 0000:00:1b.0: irq 76 for MSI/MSI-X
[    7.769045] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[    7.873568] hda_codec: ALC889: BIOS auto-probing.
[    7.881723] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    7.881811] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    7.881893] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    7.881973] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    7.882054] input: HDA Intel Line-Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    7.882134] input: HDA Intel Line-Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    7.882209] input: HDA Intel Line-Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    7.882282] input: HDA Intel Line-Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    7.882481] snd_hda_intel 0000:03:00.1: PCI INT B -> GSI 34 (level, low) -> IRQ 34
[    7.882483] hda_intel: Disabling MSI
[    7.882516] snd_hda_intel 0000:03:00.1: setting latency timer to 64
[    7.937688] type=1400 audit(1342646249.790:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=771 comm="apparmor_parser"
[    7.937696] type=1400 audit(1342646249.790:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=785 comm="apparmor_parser"
[    7.937951] type=1400 audit(1342646249.790:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=785 comm="apparmor_parser"
[    7.937974] type=1400 audit(1342646249.790:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=771 comm="apparmor_parser"
[    7.938100] type=1400 audit(1342646249.790:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=785 comm="apparmor_parser"
[    7.938142] type=1400 audit(1342646249.790:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=771 comm="apparmor_parser"
[    8.578824] init: failsafe main process (970) killed by TERM signal
[    8.783055] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[    8.807014] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[    8.831000] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[    8.859026] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[    8.859149] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card1/input15
[    8.859336] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card1/input16
[    8.859447] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card1/input17
[    8.859568] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:03:00.1/sound/card1/input18
[    9.245000] type=1400 audit(1342646251.098:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1050 comm="apparmor_parser"
[    9.245252] type=1400 audit(1342646251.098:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1050 comm="apparmor_parser"
[    9.245397] type=1400 audit(1342646251.098:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1050 comm="apparmor_parser"
[    9.299493] type=1400 audit(1342646251.154:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1049 comm="apparmor_parser"
[   10.195690] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   10.195692] vesafb: scrolling: redraw
[   10.195693] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   10.199357] vesafb: framebuffer at 0xd7000000, mapped to 0xffffc90013480000, using 5120k, total 5120k
[   10.199507] Console: switching to colour frame buffer device 160x64
[   10.199534] fb0: VESA VGA frame buffer device
[   10.204499] ppdev: user-space parallel port driver
[   10.551351] init: bumblebeed main process (1121) terminated with status 1
[   10.551368] init: bumblebeed main process ended, respawning
[   10.887964] Bluetooth: Core ver 2.16
[   10.887976] NET: Registered protocol family 31
[   10.887977] Bluetooth: HCI device and connection manager initialized
[   10.887978] Bluetooth: HCI socket layer initialized
[   10.887979] Bluetooth: L2CAP socket layer initialized
[   10.887983] Bluetooth: SCO socket layer initialized
[   11.200417] Bluetooth: RFCOMM TTY layer initialized
[   11.200422] Bluetooth: RFCOMM socket layer initialized
[   11.200423] Bluetooth: RFCOMM ver 1.11
[   11.216424] init: bumblebeed main process (1143) terminated with status 1
[   11.216440] init: bumblebeed main process ended, respawning
[   11.223082] init: bumblebeed main process (1178) terminated with status 1
[   11.223099] init: bumblebeed main process ended, respawning
[   11.227465] init: bumblebeed main process (1182) terminated with status 1
[   11.227486] init: bumblebeed main process ended, respawning
[   11.362314] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.362317] Bluetooth: BNEP filters: protocol multicast
[   11.377635] init: bumblebeed main process (1184) terminated with status 1
[   11.377651] init: bumblebeed main process ended, respawning
[   11.380558] init: bumblebeed main process (1190) terminated with status 1
[   11.380581] init: bumblebeed main process ended, respawning
[   11.383353] init: bumblebeed main process (1192) terminated with status 1
[   11.383383] init: bumblebeed main process ended, respawning
[   11.385983] init: bumblebeed main process (1193) terminated with status 1
[   11.386009] init: bumblebeed main process ended, respawning
[   11.388504] init: bumblebeed main process (1194) terminated with status 1
[   11.388520] init: bumblebeed main process ended, respawning
[   11.391004] init: bumblebeed main process (1195) terminated with status 1
[   11.391019] init: bumblebeed main process ended, respawning
[   11.393496] init: bumblebeed main process (1196) terminated with status 1
[   11.393511] init: bumblebeed respawning too fast, stopped
[   13.224000] /dev/vmmon[1213]: Module vmmon: registered with major=10 minor=165
[   13.224008] /dev/vmmon[1213]: Initial HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   13.224024] /dev/vmmon[1213]: HV check: anyNotCapable=0 anyUnlocked=0 anyEnabled=1 anyDisabled=0
[   13.224026] /dev/vmmon[1213]: Module vmmon: initialized
[   13.306884] [1221]: VMCI: shared components initialized.
[   13.306911] [1221]: VMCI: host components initialized.
[   13.306974] [1221]: VMCI: Module registered (name=vmci,major=10,minor=57).
[   13.306976] [1221]: VMCI: Using host personality
[   13.306977] [1221]: VMCI: Module (name=vmci) is initialized
[   14.347943] sky2 0000:05:00.0: eth0: enabling interface
[   14.349003] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.349431] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.859343] /dev/vmnet: open called by PID 1311 (vmnet-netifup)
[   16.859348] /dev/vmnet: hub 1 does not exist, allocating memory.
[   16.859361] /dev/vmnet: port on hub 1 successfully opened
[   16.951379] sky2 0000:05:00.0: eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   16.952233] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.952558] /dev/vmnet: open called by PID 1304 (vmnet-bridge)
[   16.952565] /dev/vmnet: hub 0 does not exist, allocating memory.
[   16.952577] /dev/vmnet: port on hub 0 successfully opened
[   16.952590] bridge-eth0: up
[   16.952591] bridge-eth0: attached
[   17.434781] /dev/vmnet: open called by PID 1316 (vmnet-dhcpd)
[   17.434789] /dev/vmnet: port on hub 1 successfully opened
[   17.478018] /dev/vmnet: open called by PID 1324 (vmnet-natd)
[   17.478022] /dev/vmnet: hub 8 does not exist, allocating memory.
[   17.478035] /dev/vmnet: port on hub 8 successfully opened
[   17.508792] userif-3: sent link down event.
[   17.508794] userif-3: sent link up event.
[   17.509655] /dev/vmnet: open called by PID 1325 (vmnet-netifup)
[   17.509660] /dev/vmnet: port on hub 8 successfully opened
[   17.615639] /dev/vmnet: open called by PID 1330 (vmnet-dhcpd)
[   17.615652] /dev/vmnet: port on hub 8 successfully opened
[   17.957237] userif-3: sent link down event.
[   17.957241] userif-3: sent link up event.
[   26.906506] vmnet1: no IPv6 routers present
[   27.382293] eth0: no IPv6 routers present
[   27.602213] vmnet8: no IPv6 routers present
[   30.718671] userif-3: sent link down event.
[   30.718676] userif-3: sent link up event.
[   30.864933] init: plymouth-stop pre-start process (1844) terminated with status 1
[   56.157826] audit_printk_skb: 45 callbacks suppressed
[   56.157828] type=1400 audit(1342646298.028:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/tmp/" pid=2288 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

```

root@aleksUbuntu:~# sudo tail -f 100 /var/log/kern.log
tail: cannot open `100' for reading: No such file or directory
==> /var/log/kern.log <==
Jul 18 17:17:39 aleksUbuntu kernel: [   17.957237] userif-3: sent link down event.
Jul 18 17:17:48 aleksUbuntu kernel: [   17.957241] userif-3: sent link up event.
Jul 18 17:17:48 aleksUbuntu kernel: [   26.906506] vmnet1: no IPv6 routers present
Jul 18 17:17:49 aleksUbuntu kernel: [   27.382293] eth0: no IPv6 routers present
Jul 18 17:17:49 aleksUbuntu kernel: [   27.602213] vmnet8: no IPv6 routers present
Jul 18 17:17:52 aleksUbuntu kernel: [   30.718671] userif-3: sent link down event.
Jul 18 17:17:52 aleksUbuntu kernel: [   30.718676] userif-3: sent link up event.
Jul 18 17:17:52 aleksUbuntu kernel: [   30.864933] init: plymouth-stop pre-start process (1844) terminated with status 1
Jul 18 17:18:18 aleksUbuntu kernel: [   56.157826] audit_printk_skb: 45 callbacks suppressed
Jul 18 17:18:18 aleksUbuntu kernel: [   56.157828] type=1400 audit(1342646298.028:27): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/tmp/" pid=2288 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```


```

tail: cannot open `100' for reading: No such file or directory
==> /var/log/syslog <==
Jul 18 17:19:02 aleksUbuntu dbus[1074]: [system] Successfully activated service 'com.ubuntu.SystemService'
Jul 18 17:19:18 aleksUbuntu dbus[1074]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
Jul 18 17:19:18 aleksUbuntu AptDaemon: INFO: Initializing daemon
Jul 18 17:19:19 aleksUbuntu AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jul 18 17:19:19 aleksUbuntu dbus[1074]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jul 18 17:19:19 aleksUbuntu AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jul 18 17:19:19 aleksUbuntu AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/55cb34636d9c423ca381aabe216370a0
Jul 18 17:19:19 aleksUbuntu AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/55cb34636d9c423ca381aabe216370a0
Jul 18 17:19:21 aleksUbuntu AptDaemon.PackageKit: INFO: Get updates()
Jul 18 17:19:22 aleksUbuntu AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/55cb34636d9c423ca381aabe216370a0




    17.307]     BitsPerPixel: 32
[    17.307]     NumberOfBanks: 1
[    17.307]     MemoryModel: 6
[    17.307]     BankSize: 0
[    17.307]     NumberOfImages: 1
[    17.307]     RedMaskSize: 8
[    17.307]     RedFieldPosition: 16
[    17.307]     GreenMaskSize: 8
[    17.307]     GreenFieldPosition: 8
[    17.307]     BlueMaskSize: 8
[    17.307]     BlueFieldPosition: 0
[    17.307]     RsvdMaskSize: 8
[    17.307]     RsvdFieldPosition: 24
[    17.307]     DirectColorModeInfo: 0
[    17.307]     PhysBasePtr: 0xd7000000
[    17.307]     LinBytesPerScanLine: 5120
[    17.307]     BnkNumberOfImagePages: 1
[    17.307]     LinNumberOfImagePages: 1
[    17.307]     LinRedMaskSize: 8
[    17.307]     LinRedFieldPosition: 16
[    17.307]     LinGreenMaskSize: 8
[    17.307]     LinGreenFieldPosition: 8
[    17.307]     LinBlueMaskSize: 8
[    17.307]     LinBlueFieldPosition: 0
[    17.307]     LinRsvdMaskSize: 8
[    17.307]     LinRsvdFieldPosition: 24
[    17.307]     MaxPixelClock: 229500000
[    17.307] 
[    17.307] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    17.307] (II) VESA(0): Monitor0: Using hsync range of 28.00-33.00 kHz
[    17.307] (II) VESA(0): Monitor0: Using vrefresh range of 43.00-72.00 Hz
[    17.307] (II) VESA(0): Monitor0: Using maximum pixel clock of 175.00 MHz
[    17.307] (WW) VESA(0): Unable to estimate virtual size
[    17.307] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    17.307] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    17.307] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    17.307] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    17.308] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    17.308] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    17.308] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    17.308] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    17.308] (--) VESA(0): Virtual size is 640x480 (pitch 640)
[    17.308] (**) VESA(0): *Built-in mode "640x480"
[    17.308] (**) VESA(0): Display dimensions: (470, 300) mm
[    17.308] (**) VESA(0): DPI set to (34, 40)
[    17.308] (**) VESA(0): Using "Shadow Framebuffer"
[    17.308] (II) Loading sub module "shadow"
[    17.308] (II) LoadModule: "shadow"
[    17.308] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    17.368] (II) Module shadow: vendor="X.Org Foundation"
[    17.368]     compiled for 1.11.3, module version = 1.1.0
[    17.368]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.368] (II) Loading sub module "fb"
[    17.368] (II) LoadModule: "fb"
[    17.369] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.383] (II) Module fb: vendor="X.Org Foundation"
[    17.383]     compiled for 1.11.3, module version = 1.0.0
[    17.383]     ABI class: X.Org ANSI C Emulation, version 0.4
[    17.384] (II) UnloadModule: "fbdev"
[    17.384] (II) Unloading fbdev
[    17.384] (II) UnloadModule: "fbdevhw"
[    17.384] (II) Unloading fbdevhw
[    17.384] (==) Depth 24 pixmap format is 32 bpp
[    17.384] (II) Loading sub module "int10"
[    17.384] (II) LoadModule: "int10"
[    17.384] (II) Loading /usr/lib/xorg/modules/libint10.so
[    17.384] (II) Module int10: vendor="X.Org Foundation"
[    17.384]     compiled for 1.11.3, module version = 1.0.0
[    17.384]     ABI class: X.Org Video Driver, version 11.0
[    17.384] (II) VESA(0): initializing int10
[    17.384] (II) VESA(0): Bad V_BIOS checksum
[    17.384] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    17.444] (II) VESA(0): VESA BIOS detected
[    17.444] (II) VESA(0): VESA VBE Version 3.0
[    17.444] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    17.444] (II) VESA(0): VESA VBE OEM: NVIDIA
[    17.444] (II) VESA(0): VESA VBE OEM Software Rev: 112.16
[    17.444] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    17.444] (II) VESA(0): VESA VBE OEM Product: GF110 Board - 12610005
[    17.444] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    17.446] (II) VESA(0): virtual address = 0x7f4bf0e95000,
    physical address = 0xd7000000, size = 14680064
[    17.450] (II) VESA(0): Setting up VESA Mode 0x112 (640x480)
[    17.584] (==) VESA(0): Default visual is TrueColor
[    17.652] (==) VESA(0): Backing store disabled
[    17.652] (**) VESA(0): DPMS enabled
[    17.652] (==) RandR enabled
[    17.652] (II) Initializing built-in extension Generic Event Extension
[    17.652] (II) Initializing built-in extension SHAPE
[    17.652] (II) Initializing built-in extension MIT-SHM
[    17.652] (II) Initializing built-in extension XInputExtension
[    17.652] (II) Initializing built-in extension XTEST
[    17.652] (II) Initializing built-in extension BIG-REQUESTS
[    17.652] (II) Initializing built-in extension SYNC
[    17.652] (II) Initializing built-in extension XKEYBOARD
[    17.652] (II) Initializing built-in extension XC-MISC
[    17.652] (II) Initializing built-in extension SECURITY
[    17.652] (II) Initializing built-in extension XINERAMA
[    17.652] (II) Initializing built-in extension XFIXES
[    17.652] (II) Initializing built-in extension RENDER
[    17.652] (II) Initializing built-in extension RANDR
[    17.652] (II) Initializing built-in extension COMPOSITE
[    17.652] (II) Initializing built-in extension DAMAGE
[    17.674] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    17.846] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.163] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.163] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.163] (II) LoadModule: "evdev"
[    18.163] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.184] (II) Module evdev: vendor="X.Org Foundation"
[    18.184]     compiled for 1.11.3, module version = 2.7.0
[    18.184]     Module class: X.Org XInput Driver
[    18.184]     ABI class: X.Org XInput driver, version 16.0
[    18.184] (II) Using input driver 'evdev' for 'Power Button'
[    18.184] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.184] (**) Power Button: always reports core events
[    18.184] (**) evdev: Power Button: Device: "/dev/input/event1"
[    18.184] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.184] (--) evdev: Power Button: Found keys
[    18.184] (II) evdev: Power Button: Configuring as keyboard
[    18.184] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    18.184] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.184] (**) Option "xkb_rules" "evdev"
[    18.184] (**) Option "xkb_model" "pc105"
[    18.184] (**) Option "xkb_layout" "us"
[    18.184] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.184] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.184] (II) Using input driver 'evdev' for 'Power Button'
[    18.184] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.184] (**) Power Button: always reports core events
[    18.184] (**) evdev: Power Button: Device: "/dev/input/event0"
[    18.184] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.184] (--) evdev: Power Button: Found keys
[    18.184] (II) evdev: Power Button: Configuring as keyboard
[    18.184] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.184] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    18.184] (**) Option "xkb_rules" "evdev"
[    18.184] (**) Option "xkb_model" "pc105"
[    18.184] (**) Option "xkb_layout" "us"
[    18.185] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event15)
[    18.185] (II) No input driver specified, ignoring this device.
[    18.185] (II) This device may have been added with another device file.
[    18.185] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event16)
[    18.185] (II) No input driver specified, ignoring this device.
[    18.185] (II) This device may have been added with another device file.
[    18.185] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event17)
[    18.185] (II) No input driver specified, ignoring this device.
[    18.185] (II) This device may have been added with another device file.
[    18.185] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event18)
[    18.185] (II) No input driver specified, ignoring this device.
[    18.185] (II) This device may have been added with another device file.
[    18.185] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event10)
[    18.185] (II) No input driver specified, ignoring this device.
[    18.185] (II) This device may have been added with another device file.
[    18.185] (II) config/udev: Adding input device HDA Intel Line-Out Side (/dev/input/event11)
[    18.185] (II) No input driver specified, ignoring this device.
[    18.185] (II) This device may have been added with another device file.
[    18.185] (II) config/udev: Adding input device HDA Intel Line-Out CLFE (/dev/input/event12)
[    18.185] (II) No input driver specified, ignoring this device.
[    18.185] (II) This device may have been added with another device file.
[    18.186] (II) config/udev: Adding input device HDA Intel Line-Out Surround (/dev/input/event13)
[    18.186] (II) No input driver specified, ignoring this device.
[    18.186] (II) This device may have been added with another device file.
[    18.186] (II) config/udev: Adding input device HDA Intel Line-Out Front (/dev/input/event14)
[    18.186] (II) No input driver specified, ignoring this device.
[    18.186] (II) This device may have been added with another device file.
[    18.186] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event7)
[    18.186] (II) No input driver specified, ignoring this device.
[    18.186] (II) This device may have been added with another device file.
[    18.186] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event8)
[    18.186] (II) No input driver specified, ignoring this device.
[    18.186] (II) This device may have been added with another device file.
[    18.186] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event9)
[    18.186] (II) No input driver specified, ignoring this device.
[    18.186] (II) This device may have been added with another device file.
[    18.186] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event3)
[    18.186] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.186] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[    18.186] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.186] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[    18.186] (**) evdev: Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event3"
[    18.187] (--) evdev: Logitech Logitech Illuminated Keyboard: Vendor 0x46d Product 0xc318
[    18.187] (--) evdev: Logitech Logitech Illuminated Keyboard: Found keys
[    18.187] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[    18.187] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input3/event3"
[    18.187] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD, id 8)
[    18.187] (**) Option "xkb_rules" "evdev"
[    18.187] (**) Option "xkb_model" "pc105"
[    18.187] (**) Option "xkb_layout" "us"
[    18.187] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event4)
[    18.187] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.187] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[    18.187] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.187] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[    18.187] (**) evdev: Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event4"
[    18.187] (--) evdev: Logitech Logitech Illuminated Keyboard: Vendor 0x46d Product 0xc318
[    18.187] (--) evdev: Logitech Logitech Illuminated Keyboard: Found 1 mouse buttons
[    18.187] (--) evdev: Logitech Logitech Illuminated Keyboard: Found scroll wheel(s)
[    18.187] (--) evdev: Logitech Logitech Illuminated Keyboard: Found relative axes
[    18.187] (II) evdev: Logitech Logitech Illuminated Keyboard: Forcing relative x/y axes to exist.
[    18.187] (--) evdev: Logitech Logitech Illuminated Keyboard: Found absolute axes
[    18.187] (II) evdev: Logitech Logitech Illuminated Keyboard: Forcing absolute x/y axes to exist.
[    18.187] (--) evdev: Logitech Logitech Illuminated Keyboard: Found keys
[    18.187] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as mouse
[    18.187] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[    18.187] (II) evdev: Logitech Logitech Illuminated Keyboard: Adding scrollwheel support
[    18.187] (**) evdev: Logitech Logitech Illuminated Keyboard: YAxisMapping: buttons 4 and 5
[    18.187] (**) evdev: Logitech Logitech Illuminated Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.187] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input4/event4"
[    18.187] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD, id 9)
[    18.187] (**) Option "xkb_rules" "evdev"
[    18.187] (**) Option "xkb_model" "pc105"
[    18.187] (**) Option "xkb_layout" "us"
[    18.187] (II) evdev: Logitech Logitech Illuminated Keyboard: initialized for relative axes.
[    18.187] (WW) evdev: Logitech Logitech Illuminated Keyboard: ignoring absolute axes.
[    18.187] (**) Logitech Logitech Illuminated Keyboard: (accel) keeping acceleration scheme 1
[    18.187] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration profile 0
[    18.187] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration factor: 2.000
[    18.187] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration threshold: 4
[    18.187] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event2)
[    18.187] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[    18.188] (II) Using input driver 'evdev' for 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)'
[    18.188] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.188] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[    18.188] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
[    18.188] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Vendor 0x45e Product 0x40
[    18.188] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[    18.188] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[    18.188] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[    18.188] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[    18.188] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[    18.188] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[    18.188] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[    18.188] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.188] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.1/2-3.1:1.0/input/input2/event2"
[    18.188] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE, id 10)
[    18.188] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[    18.188] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[    18.188] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[    18.188] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[    18.188] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[    18.188] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[    18.188] (II) No input driver specified, ignoring this device.
[    18.188] (II) This device may have been added with another device file.
[    18.188] (II) config/udev: Adding input device Wacom Bamboo Pen Pen (/dev/input/event5)
[    18.188] (**) Wacom Bamboo Pen Pen: Applying InputClass "evdev tablet catchall"
[    18.188] (**) Wacom Bamboo Pen Pen: Applying InputClass "Wacom class"
[    18.188] (II) LoadModule: "wacom"
[    18.188] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    18.211] (II) Module wacom: vendor="X.Org Foundation"
[    18.211]     compiled for 1.11.3, module version = 0.14.0
[    18.211]     Module class: X.Org XInput Driver
[    18.211]     ABI class: X.Org XInput driver, version 16.0
[    18.211] (II) Using input driver 'wacom' for 'Wacom Bamboo Pen Pen'
[    18.211] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    18.211] (**) Wacom Bamboo Pen Pen: always reports core events
[    18.211] (**) Option "Device" "/dev/input/event5"
[    18.211] (II) Wacom Bamboo Pen Pen: type not specified, assuming 'stylus'.
[    18.211] (II) Wacom Bamboo Pen Pen: other types will be automatically added.
[    18.212] (--) Wacom Bamboo Pen Pen stylus: using pressure threshold of 27 for button 1
[    18.212] (--) Wacom Bamboo Pen Pen stylus: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=100000 resY=100000  tilt=disabled
[    18.212] (II) Wacom Bamboo Pen Pen stylus: hotplugging dependent devices.
[    18.212] (EE) Wacom Bamboo Pen Pen stylus: Invalid type 'cursor' for this device.
[    18.212] (EE) Wacom Bamboo Pen Pen stylus: Invalid type 'touch' for this device.
[    18.212] (EE) Wacom Bamboo Pen Pen stylus: Invalid type 'pad' for this device.
[    18.212] (II) Wacom Bamboo Pen Pen stylus: hotplugging completed.
[    18.360] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4:1.0/input/input5/event5"
[    18.360] (II) XINPUT: Adding extended input device "Wacom Bamboo Pen Pen stylus" (type: STYLUS, id 11)
[    18.360] (**) Wacom Bamboo Pen Pen stylus: (accel) keeping acceleration scheme 1
[    18.360] (**) Wacom Bamboo Pen Pen stylus: (accel) acceleration profile 0
[    18.360] (**) Wacom Bamboo Pen Pen stylus: (accel) acceleration factor: 2.000
[    18.360] (**) Wacom Bamboo Pen Pen stylus: (accel) acceleration threshold: 4
[    18.360] (II) config/udev: Adding input device Wacom Bamboo Pen Pen (/dev/input/mouse1)
[    18.360] (II) No input driver specified, ignoring this device.
[    18.360] (II) This device may have been added with another device file.
[    18.360] (II) config/udev: Adding input device Wacom Bamboo Pen Finger (/dev/input/event6)
[    18.360] (**) Wacom Bamboo Pen Finger: Applying InputClass "evdev touchpad catchall"
[    18.360] (**) Wacom Bamboo Pen Finger: Applying InputClass "touchpad catchall"
[    18.360] (**) Wacom Bamboo Pen Finger: Applying InputClass "Wacom class"
[    18.360] (II) Using input driver 'wacom' for 'Wacom Bamboo Pen Finger'
[    18.360] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    18.360] (**) Wacom Bamboo Pen Finger: always reports core events
[    18.360] (**) Option "Device" "/dev/input/event6"
[    18.360] (EE) Wacom Bamboo Pen Finger: Invalid type 'stylus' for this device.
[    18.360] (EE) Wacom Bamboo Pen Finger: Invalid type 'eraser' for this device.
[    18.360] (EE) Wacom Bamboo Pen Finger: Invalid type 'cursor' for this device.
[    18.360] (II) Wacom Bamboo Pen Finger: type not specified, assuming 'touch'.
[    18.360] (II) Wacom Bamboo Pen Finger: other types will be automatically added.
[    18.360] (--) Wacom Bamboo Pen Finger touch: using pressure threshold of 27 for button 1
[    18.360] (--) Wacom Bamboo Pen Finger touch: Wacom USB Bamboo tablet maxX=15360 maxY=10240 maxZ=0 resX=128000 resY=128000 
[    18.360] (II) Wacom Bamboo Pen Finger touch: hotplugging dependent devices.
[    18.360] (EE) Wacom Bamboo Pen Finger touch: Invalid type 'stylus' for this device.
[    18.360] (EE) Wacom Bamboo Pen Finger touch: Invalid type 'eraser' for this device.
[    18.360] (EE) Wacom Bamboo Pen Finger touch: Invalid type 'cursor' for this device.
[    18.360] (II) Wacom Bamboo Pen Finger touch: hotplugging completed.
[    18.460] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4:1.1/input/input6/event6"
[    18.460] (II) XINPUT: Adding extended input device "Wacom Bamboo Pen Finger touch" (type: TOUCH, id 12)
[    18.460] (**) Wacom Bamboo Pen Finger touch: (accel) keeping acceleration scheme 1
[    18.460] (**) Wacom Bamboo Pen Finger touch: (accel) acceleration profile 0
[    18.460] (**) Wacom Bamboo Pen Finger touch: (accel) acceleration factor: 2.000
[    18.460] (**) Wacom Bamboo Pen Finger touch: (accel) acceleration threshold: 4
[    18.460] (II) config/udev: Adding input device Wacom Bamboo Pen Finger (/dev/input/mouse2)
[    18.460] (**) Wacom Bamboo Pen Finger: Ignoring device from InputClass "touchpad ignore duplicates"
[    18.463] (**) Wacom Bamboo Pen Pen eraser: Applying InputClass "evdev tablet catchall"
[    18.463] (**) Wacom Bamboo Pen Pen eraser: Applying InputClass "Wacom class"
[    18.463] (II) Using input driver 'wacom' for 'Wacom Bamboo Pen Pen eraser'
[    18.463] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    18.463] (**) Wacom Bamboo Pen Pen eraser: always reports core events
[    18.463] (**) Option "Device" "/dev/input/event5"
[    18.463] (**) Option "Type" "eraser"
[    18.463] (--) Wacom Bamboo Pen Pen eraser: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=100000 resY=100000  tilt=disabled
[    18.464] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4:1.0/input/input5/event5"
[    18.464] (II) XINPUT: Adding extended input device "Wacom Bamboo Pen Pen eraser" (type: ERASER, id 13)
[    18.464] (**) Wacom Bamboo Pen Pen eraser: (accel) keeping acceleration scheme 1
[    18.464] (**) Wacom Bamboo Pen Pen eraser: (accel) acceleration profile 0
[    18.464] (**) Wacom Bamboo Pen Pen eraser: (accel) acceleration factor: 2.000
[    18.464] (**) Wacom Bamboo Pen Pen eraser: (accel) acceleration threshold: 4
[    18.464] (**) Wacom Bamboo Pen Finger pad: Applying InputClass "evdev touchpad catchall"
[    18.464] (**) Wacom Bamboo Pen Finger pad: Applying InputClass "touchpad catchall"
[    18.464] (**) Wacom Bamboo Pen Finger pad: Applying InputClass "Wacom class"
[    18.464] (II) Using input driver 'wacom' for 'Wacom Bamboo Pen Finger pad'
[    18.464] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    18.464] (**) Wacom Bamboo Pen Finger pad: always reports core events
[    18.464] (**) Option "Device" "/dev/input/event6"
[    18.464] (**) Option "Type" "pad"
[    18.464] (--) Wacom Bamboo Pen Finger pad: Wacom USB Bamboo tablet maxX=15360 maxY=10240 maxZ=0 resX=128000 resY=128000 
[    18.520] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3.4/2-3.4:1.1/input/input6/event6"
[    18.520] (II) XINPUT: Adding extended input device "Wacom Bamboo Pen Finger pad" (type: PAD, id 14)
[    18.520] (**) Wacom Bamboo Pen Finger pad: (accel) keeping acceleration scheme 1
[    18.520] (**) Wacom Bamboo Pen Finger pad: (accel) acceleration profile 0
[    18.520] (**) Wacom Bamboo Pen Finger pad: (accel) acceleration factor: 2.000
[    18.520] (**) Wacom Bamboo Pen Finger pad: (accel) acceleration threshold: 4
[    34.176] (II) XKB: generating xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[   106.387] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm

```

---

### Post by Cheesemill on 2012-07-18
It's probably a problem with the Bumblebee drivers. Linux support for Nvidia Optimus systems is still in the experimental stage and shouldn't be relied upon for production systems.

This is because Nvidia haven't yet released official Optimus drivers for Linux.

Your best option is probably to restore the OS and files from your most recent backup.

Switching OS to something that isn't supported by your hardware probably isn't the best choice if you are on a deadline.

---

### Post by QIII on 2012-07-18
If the OP just switched, he's not likely to have known that NVIDIA does not yet have a straight answer for us on Optimus and the dangers of Bumblebee.

However, the adage about switching horses in the middle of the river still applies.

bergj:  This really sucks, and I feel for you.  My advice, however, would be to use Windows (again) while you are in school if that is the common platform.  There is absolutely nothing wrong with that.

If you can get any credit for a late turn-in, you may be able to recover and back up your files, then reinstall Windows and do the conversion.

It is unfortunate for you in this case that you found out that OEMs put a great deal of effort into Windows support, but Linux support sometimes lags.

---

### Post by mebomechanicno1 on 2012-07-18
In my (teaching) experience, examination boards want to PASS students, not fail them, so I strongly recommend you put together a reasoned explanation of what went wrong and exhibit a print of this thread by way of evidence and try for some credit for what you did.  Luck.

---

