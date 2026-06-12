---
title: "No network or USB in 64bit"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by jmatteson8 on 2013-11-17
I'm running a 64bit box with a Gigabyte GA-970A-DS3 motherboard, AMD PhenomIIx4 925 with 8 GB of ram. I am running Windows 7 (64bit) on one hard drive and I'm planning on a dual boot system with two separate hard drives.

My problem is:
It seems I can't get several linux "LIVE" 64bit distros to run USB ports or wired network after boot up. I've tried Xubuntu, Ubuntu, LinuxMint, Fedora and LuninuXOS. All of their 32bit versions will boot with USB (Keyboard and mouse) and network with no worries. The board has 8 USB ports on the back and I have two on the top of the case. During the boot up stage all the USB ports work because the system sees the flash drive, booting with F12, no matter what USB port I put it in and I can boot to it. After boot up though, I can only get one other random USB port to work (for the mouse only) but its never the same port twice. I am using a KVM switch but it does the same thing even when I unplug the KVM and plug the keyboard and mouse in directly.

I tried turning things on and off in the bios as far as USB legacy and USB 3.0 but nothing changed. Although I don't think this is a bios issue since everything is working during boot up.

---

### Post by sanderj on 2013-11-17
I don't understand your post:
- does USB always work with any 32-bit Linux?
- does USB never work with 64-bit Linux? Or a few times / once / ...
- how about 'network' in your subject?

Furthermore:
- have you checked 'dmesg'
- which Linux version are you using in all those distributions? Did you use Ubuntu 13.10?

---

### Post by jmatteson8 on 2013-11-17
Thank you for responding.
I'm sorry, its very confusing to me too. I've never seen anything like this either. Everything works in 32 bit. In 64bit, only the USB port that the flash drive is plugged into and one other random USB port would work and the network never works. I've been downloading and booting several distributions over the last few days trying many of them. As I said all the 64bit versions displayed the above issues and the 32 bit versions worked fine. I started with 13.10 64bit Ubuntu but then went to 12.04 and what ever the latest and greatest is of the others I tried. Its impossible to do "dmesg" when you have no mouse or keyboard. When I was able to get the mouse working I still had no keyboard to type anything.

---

### Post by sanderj on 2013-11-18
Long shot: do you have a PCI-USB card lying around which you can use in your mobo, so that you can test that?

Your mobo has one (or two?) PS/2 connectors. Do you have a PS/2 keyboard and/or mouse so that you can start using the system (and look at dmesg)?


[IMG]http://www.gigabyte.com/fileupload/product/2/4122/5564_big.jpg[/IMG]

---

### Post by jmatteson8 on 2013-11-19
Ok, here is where I'm at. I plugged in a PS/2 mouse and keyboard, unplugged all USB peripherals and booted back up to a flash drive of Ubuntu Live 13.10. Still no USB except one port that I could get a mouse to work but not the keyboard and still no ethernet. I installed Ubuntu onto my system. rebooted and the same symptoms continued.

Thank you in advance sanderj for all your help. Although experienced with computers: 15 years in the Mac support field and built several Windows boxes over the years(This system included). But, my exposure to Linux is very limited.

Below is the "Dmesg" file of my system after installing and rebooting. Several times you'll see it finds a "USB hub found" with "x ports detected" and  "New USB device found". I suppose it would help if I knew what I was looking for, but alas, I do not.
```

[    0.975240] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.975242] ehci-pci: EHCI PCI platform driver
[    0.975337] ehci-pci 0000:00:12.2: EHCI Host Controller
[    0.975344] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.975353] QUIRK: Enable AMD PLL fix
[    0.975355] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.975364] ehci-pci 0000:00:12.2: debug port 1
[    0.975397] ehci-pci 0000:00:12.2: irq 17, io mem 0xfe209000
[    0.983520] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.983539] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.983540] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.983542] usb usb1: Product: EHCI Host Controller
[    0.983544] usb usb1: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.983545] usb usb1: SerialNumber: 0000:00:12.2
[    0.983640] hub 1-0:1.0: USB hub found
[    0.983644] hub 1-0:1.0: 5 ports detected
[    0.983817] ehci-pci 0000:00:13.2: EHCI Host Controller
[    0.983822] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.983825] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.983834] ehci-pci 0000:00:13.2: debug port 1
[    0.983854] ehci-pci 0000:00:13.2: irq 17, io mem 0xfe207000
[    0.995518] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.995533] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.995535] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.995536] usb usb2: Product: EHCI Host Controller
[    0.995538] usb usb2: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    0.995539] usb usb2: SerialNumber: 0000:00:13.2
[    0.995617] hub 2-0:1.0: USB hub found
[    0.995620] hub 2-0:1.0: 5 ports detected
[    0.995787] ehci-pci 0000:00:16.2: EHCI Host Controller
[    0.995792] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    0.995795] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.995804] ehci-pci 0000:00:16.2: debug port 1
[    0.995826] ehci-pci 0000:00:16.2: irq 17, io mem 0xfe204000
[    1.007518] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.007532] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.007533] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.007535] usb usb3: Product: EHCI Host Controller
[    1.007537] usb usb3: Manufacturer: Linux 3.11.0-12-generic ehci_hcd
[    1.007538] usb usb3: SerialNumber: 0000:00:16.2
[    1.007618] hub 3-0:1.0: USB hub found
[    1.007621] hub 3-0:1.0: 4 ports detected
[    1.007711] ehci-platform: EHCI generic platform driver
[    1.007719] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.007720] ohci-platform: OHCI generic platform driver
[    1.007725] uhci_hcd: USB Universal Host Controller Interface driver
[    1.007792] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.007797] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 4
[    1.007888] xhci_hcd 0000:02:00.0: irq 72 for MSI/MSI-X
[    1.007927] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    1.007929] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.007930] usb usb4: Product: xHCI Host Controller
[    1.007932] usb usb4: Manufacturer: Linux 3.11.0-12-generic xhci_hcd
[    1.007933] usb usb4: SerialNumber: 0000:02:00.0
[    1.007991] xHCI xhci_add_endpoint called for root hub
[    1.007993] xHCI xhci_check_bandwidth called for root hub
[    1.008009] hub 4-0:1.0: USB hub found
[    1.008013] hub 4-0:1.0: 2 ports detected
[    1.008062] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.008065] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 5
[    1.008080] usb usb5: New USB device found, idVendor=1d6b, idProduct=0003
[    1.008082] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.008083] usb usb5: Product: xHCI Host Controller
[    1.008085] usb usb5: Manufacturer: Linux 3.11.0-12-generic xhci_hcd
[    1.008086] usb usb5: SerialNumber: 0000:02:00.0
[    1.008136] xHCI xhci_add_endpoint called for root hub
[    1.008137] xHCI xhci_check_bandwidth called for root hub
[    1.008151] hub 5-0:1.0: USB hub found
[    1.008155] hub 5-0:1.0: 2 ports detected
[    1.019605] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.019958] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.019963] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.020080] mousedev: PS/2 mouse device common for all mice
[    1.020196] rtc_cmos 00:06: RTC can wake from S4
[    1.020283] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.020303] rtc_cmos 00:06: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.020352] device-mapper: uevent: version 1.0.3
[    1.020401] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [email]dm-devel@redhat.com[/email]
[    1.020406] cpuidle: using governor ladder
[    1.020407] cpuidle: using governor menu
[    1.020415] ledtrig-cpu: registered to indicate activity on CPUs
[    1.020481] TCP: cubic registered
[    1.020552] NET: Registered protocol family 10
[    1.020710] NET: Registered protocol family 17
[    1.020717] Key type dns_resolver registered
[    1.020937] PM: Hibernation image not present or could not be loaded.
[    1.020939] Loading module verification certificates
[    1.021898] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: fddf6943d8ac4f5b6eb0919a7a3ee3d9088b1bfa'
[    1.021906] registered taskstats version 1
[    1.024062] Key type trusted registered
[    1.025734] Key type encrypted registered
[    1.027263] AppArmor: AppArmor sha1 policy hashing enabled
[    1.027529]   Magic number: 5:406:656
[    1.027605] rtc_cmos 00:06: setting system clock to 2013-11-18 23:36:41 UTC (1384817801)
[    1.027707] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.027817] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.027818] EDD information not available.
[    1.028972] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    1.028974] Write protecting the kernel read-only data: 12288k
[    1.031491] Freeing unused kernel memory: 1040K (ffff8800016fc000 - ffff880001800000)
[    1.033308] Freeing unused kernel memory: 836K (ffff880001b2f000 - ffff880001c00000)
[    1.043580] systemd-udevd[113]: starting version 204
[    1.046752] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.055065] mii: module verification failed: signature and/or required key missing - tainting kernel
[    1.055897] ahci 0000:00:11.0: version 3.0
[    1.056076] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    1.056080] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.056669] scsi0 : ahci
[    1.056762] scsi1 : ahci
[    1.056827] scsi2 : ahci
[    1.057843] scsi3 : ahci
[    1.057895] ata1: SATA max UDMA/133 abar m1024@0xfe20b000 port 0xfe20b100 irq 19
[    1.057898] ata2: SATA max UDMA/133 abar m1024@0xfe20b000 port 0xfe20b180 irq 19
[    1.057900] ata3: SATA max UDMA/133 abar m1024@0xfe20b000 port 0xfe20b200 irq 19
[    1.057902] ata4: SATA max UDMA/133 abar m1024@0xfe20b000 port 0xfe20b280 irq 19
[    1.058384] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.058395] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.058602] r8169 0000:03:00.0: irq 73 for MSI/MSI-X
[    1.058752] r8169 0000:03:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c28000, 94:de:80:71:00:2a, XID 0c900800 IRQ 73
[    1.058754] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.060966] scsi4 : pata_atiixp
[    1.061292] scsi5 : pata_atiixp
[    1.061501] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.061503] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.319484] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    1.375507] ata4: SATA link down (SStatus 0 SControl 300)
[    1.431470] usb 3-1: device descriptor read/64, error -32
[    1.547472] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.547496] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.547519] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.548838] ata3.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    1.548841] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.550026] ata2.00: ATAPI: HL-DT-ST DVDRAM GH24NS95, RN01, max UDMA/133
[    1.550606] ata3.00: configured for UDMA/133
[    1.551640] ata2.00: configured for UDMA/133
[    1.553092] ata1.00: ATA-8: SAMSUNG HD502HJ, 1AJ100E4, max UDMA/133
[    1.553095] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.558739] ata1.00: configured for UDMA/133
[    1.558901] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD502HJ  1AJ1 PQ: 0 ANSI: 5
[    1.559039] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.559067] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.559129] sd 0:0:0:0: [sda] Write Protect is off
[    1.559134] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.559171] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.561756] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS95  RN01 PQ: 0 ANSI: 5
[    1.564713] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.564716] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.564831] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.564893] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.565030] scsi 2:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    1.565215] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.565238] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.565307] sd 2:0:0:0: [sdb] Write Protect is off
[    1.565311] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.565351] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.570540]  sda: sda1
[    1.570879] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.593151]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    1.593580] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.651445] usb 3-1: device descriptor read/64, error -32
[    1.867475] usb 3-1: new high-speed USB device number 3 using ehci-pci
[    1.939386] tsc: Refined TSC clocksource calibration: 2812.899 MHz
[    1.974923] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
[    1.979371] usb 3-1: device descriptor read/64, error -32
[    2.195389] usb 3-1: device descriptor read/64, error -32
[    2.411351] usb 3-1: new high-speed USB device number 4 using ehci-pci
[    2.819329] usb 3-1: device not accepting address 4, error -32
[    2.931338] usb 3-1: new high-speed USB device number 5 using ehci-pci
[    2.939357] Switched to clocksource tsc
[    3.339266] usb 3-1: device not accepting address 5, error -32
[    3.339280] hub 3-0:1.0: unable to enumerate USB device on port 1
[    4.485926] Adding 3905532k swap on /dev/sdb5.  Priority:-1 extents:1 across:3905532k FS
[    4.874173] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro
[    5.160362] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    5.180183] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.390577] systemd-udevd[374]: starting version 204
[    5.835988] lp: driver loaded but no devices found
[    6.356415] ohci-pci: OHCI PCI platform driver
[    6.356529] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    6.356539] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 6
[    6.356567] ohci-pci 0000:00:12.0: irq 18, io mem 0xfe20a000
[    6.390608] microcode: CPU0: patch_level=0x010000c8
[    6.400331] MCE: In-kernel MCE decoding enabled.
[    6.414923] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    6.414931] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.414933] usb usb6: Product: OHCI PCI host controller
[    6.414935] usb usb6: Manufacturer: Linux 3.11.0-12-generic ohci_hcd
[    6.414936] usb usb6: SerialNumber: 0000:00:12.0
[    6.415042] hub 6-0:1.0: USB hub found
[    6.415047] hub 6-0:1.0: 5 ports detected
[    6.415230] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    6.415236] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 7
[    6.415250] ohci-pci 0000:00:13.0: irq 18, io mem 0xfe208000
[    6.450715] EDAC MC: Ver: 3.0.0
[    6.474121] AMD64 EDAC driver v3.4.0
[    6.474912] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    6.474915] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.474916] usb usb7: Product: OHCI PCI host controller
[    6.474918] usb usb7: Manufacturer: Linux 3.11.0-12-generic ohci_hcd
[    6.474919] usb usb7: SerialNumber: 0000:00:13.0
[    6.475023] hub 7-0:1.0: USB hub found
[    6.475028] hub 7-0:1.0: 5 ports detected
[    6.475193] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    6.475200] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 8
[    6.475214] ohci-pci 0000:00:14.5: irq 18, io mem 0xfe206000
[    6.476208] microcode: CPU1: patch_level=0x010000c8
[    6.476220] microcode: CPU2: patch_level=0x010000c8
[    6.476227] microcode: CPU3: patch_level=0x010000c8
[    6.476273] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    6.510750] kvm: Nested Virtualization enabled
[    6.510754] kvm: Nested Paging enabled
[    6.534910] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    6.534914] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.534916] usb usb8: Product: OHCI PCI host controller
[    6.534918] usb usb8: Manufacturer: Linux 3.11.0-12-generic ohci_hcd
[    6.534919] usb usb8: SerialNumber: 0000:00:14.5
[    6.535046] hub 8-0:1.0: USB hub found
[    6.535052] hub 8-0:1.0: 2 ports detected
[    6.535230] ohci-pci 0000:00:16.0: OHCI PCI host controller
[    6.535236] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 9
[    6.535252] ohci-pci 0000:00:16.0: irq 18, io mem 0xfe205000
[    6.562376] [drm] Initialized drm 1.1.0 20060810
[    6.594936] usb usb9: New USB device found, idVendor=1d6b, idProduct=0001
[    6.594939] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    6.594941] usb usb9: Product: OHCI PCI host controller
[    6.594943] usb usb9: Manufacturer: Linux 3.11.0-12-generic ohci_hcd
[    6.594944] usb usb9: SerialNumber: 0000:00:16.0
[    6.595059] hub 9-0:1.0: USB hub found
[    6.595064] hub 9-0:1.0: 4 ports detected
[    6.595300] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    6.595838] EDAC amd64: DRAM ECC disabled.
[    6.595846] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    6.595846]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    6.595846]  (Note that use of the override may cause unknown side effects.)
[    6.643622] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[    6.643677] sp5100_tco: PCI Revision ID: 0x42
[    6.643708] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[    6.643719] sp5100_tco: Last reboot was not triggered by watchdog.
[    6.643763] sp5100_tco: initialized (0xffffc90000c2ab00). heartbeat=60 sec (nowayout=0)
[    6.647088] wmi: Mapper loaded
[    6.718701] hda-intel 0000:00:14.2: Using LPIB position fix
[    6.722208] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[    6.743647] SKU: Nid=0x1d sku_cfg=0x4004c601
[    6.743649] SKU: port_connectivity=0x1
[    6.743650] SKU: enable_pcbeep=0x0
[    6.743651] SKU: check_sum=0x00000004
[    6.743652] SKU: customization=0x000000c6
[    6.743653] SKU: external_amp=0x0
[    6.743654] SKU: platform_type=0x0
[    6.743655] SKU: swap=0x0
[    6.743655] SKU: override=0x1
[    6.743964] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[    6.743965]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    6.743966]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    6.743967]    mono: mono_out=0x0
[    6.743968]    dig-out=0x11/0x0
[    6.743969]    inputs:
[    6.743970]      Rear Mic=0x18
[    6.743971]      Front Mic=0x19
[    6.743972]      Line=0x1a
[    6.743973]      CD=0x1c
[    6.743974] realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
[    6.743976] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0887
[    6.755215] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input3
[    6.755298] input: HDA ATI SB Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input4
[    6.755362] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[    6.755415] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[    6.755469] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[    6.755763] hda_intel: Disabling MSI
[    6.755773] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    6.755801] hda-intel 0000:01:00.1: Disabling 64bit DMA
[    6.759131] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[    6.856860] psmouse serio1: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    6.930886] usb 9-1: new full-speed USB device number 2 using ohci-pci
[    7.070887] usb 9-1: device descriptor read/64, error -32
[    7.112520] Bluetooth: Core ver 2.16
[    7.112543] NET: Registered protocol family 31
[    7.112544] Bluetooth: HCI device and connection manager initialized
[    7.112553] Bluetooth: HCI socket layer initialized
[    7.112555] Bluetooth: L2CAP socket layer initialized
[    7.112560] Bluetooth: SCO socket layer initialized
[    7.218401] Bluetooth: RFCOMM TTY layer initialized
[    7.218411] Bluetooth: RFCOMM socket layer initialized
[    7.218412] Bluetooth: RFCOMM ver 1.11
[    7.244829] init: avahi-cups-reload main process (542) terminated with status 1
[    7.246899] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    7.246902] Bluetooth: BNEP filters: protocol multicast
[    7.246909] Bluetooth: BNEP socket layer initialized
[    7.322867] usb 9-1: device descriptor read/64, error -32
[    7.369023] type=1400 audit(1384835807.835:2): apparmor="STATUS" operation="profile_load" parent=517 profile="unconfined" name="/sbin/dhclient" pid=519 comm="apparmor_parser"
[    7.369029] type=1400 audit(1384835807.835:3): apparmor="STATUS" operation="profile_load" parent=517 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=519 comm="apparmor_parser"
[    7.369033] type=1400 audit(1384835807.835:4): apparmor="STATUS" operation="profile_load" parent=517 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=519 comm="apparmor_parser"
[    7.369046] type=1400 audit(1384835807.835:5): apparmor="STATUS" operation="profile_replace" parent=521 profile="unconfined" name="/sbin/dhclient" pid=522 comm="apparmor_parser"
[    7.369054] type=1400 audit(1384835807.835:6): apparmor="STATUS" operation="profile_replace" parent=521 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=522 comm="apparmor_parser"
[    7.369058] type=1400 audit(1384835807.835:7): apparmor="STATUS" operation="profile_replace" parent=521 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=522 comm="apparmor_parser"
[    7.369597] type=1400 audit(1384835807.835:8): apparmor="STATUS" operation="profile_replace" parent=517 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=519 comm="apparmor_parser"
[    7.369603] type=1400 audit(1384835807.835:9): apparmor="STATUS" operation="profile_replace" parent=517 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=519 comm="apparmor_parser"
[    7.369623] type=1400 audit(1384835807.835:10): apparmor="STATUS" operation="profile_replace" parent=521 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=522 comm="apparmor_parser"
[    7.369627] type=1400 audit(1384835807.835:11): apparmor="STATUS" operation="profile_replace" parent=521 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=522 comm="apparmor_parser"
[    7.486891] ppdev: user-space parallel port driver
[    7.562815] usb 9-1: new full-speed USB device number 3 using ohci-pci
[    7.578877] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input8
[    7.578955] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input9
[    7.579011] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input10
[    7.579066] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input11
[    7.580236] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x0ce000a1
[    7.580239] nouveau  [  DEVICE][0000:01:00.0] Chipset: GF114 (NVCE)
[    7.580241] nouveau  [  DEVICE][0000:01:00.0] Family : NVC0
[    7.581638] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[    7.641357] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input12
[    7.677174] init: failsafe main process (561) killed by TERM signal
[    7.680216] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[    7.680218] nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[    7.680366] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    7.680368] nouveau  [   VBIOS][0000:01:00.0] version 70.24.35.00.02
[    7.702600] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR5
[    7.702602] nouveau  [     PFB][0000:01:00.0] RAM size: 1024 MiB
[    7.702603] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[    7.702788] usb 9-1: device descriptor read/64, error -32
[    7.727430] nouveau  [  PTHERM][0000:01:00.0] FAN control: PWM
[    7.727436] nouveau  [  PTHERM][0000:01:00.0] fan management: disabled
[    7.727439] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[    7.729298] [TTM] Zone  kernel: Available graphics memory: 4111046 kiB
[    7.729299] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    7.729300] [TTM] Initializing pool allocator
[    7.729304] [TTM] Initializing DMA pool allocator
[    7.729312] nouveau  [     DRM] VRAM: 1024 MiB
[    7.729313] nouveau  [     DRM] GART: 1048576 MiB
[    7.729317] nouveau  [     DRM] TMDS table version 2.0
[    7.729318] nouveau  [     DRM] DCB version 4.0
[    7.729320] nouveau  [     DRM] DCB outp 00: 02000300 00000000
[    7.729323] nouveau  [     DRM] DCB outp 01: 01000302 00020030
[    7.729324] nouveau  [     DRM] DCB outp 02: 04011380 00000000
[    7.729326] nouveau  [     DRM] DCB outp 03: 08011382 00020030
[    7.729327] nouveau  [     DRM] DCB outp 04: 02022362 00020010
[    7.729329] nouveau  [     DRM] DCB conn 00: 00001030
[    7.729331] nouveau  [     DRM] DCB conn 01: 00010130
[    7.729332] nouveau  [     DRM] DCB conn 02: 00002261
[    7.730051] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    7.730052] [drm] No driver support for vblank timestamp query.
[    7.730227] nouveau  [     DRM] 3 available performance level(s)
[    7.730230] nouveau  [     DRM] 0: core 50MHz shader 101MHz memory 135MHz voltage 950mV
[    7.730232] nouveau  [     DRM] 1: core 405MHz shader 810MHz memory 324MHz voltage 950mV
[    7.730235] nouveau  [     DRM] 3: core 822MHz shader 1645MHz memory 2004MHz voltage 962mV-1050mV
[    7.730237] nouveau  [     DRM] c: core 50MHz shader 101MHz memory 135MHz voltage 950mV fanspeed 40%
[    7.733528] nouveau  [     DRM] MM: using COPY0 for buffer copies
[    7.886771] nouveau  [     DRM] allocated 1920x1200 fb: 0x60000, bo ffff8802227aac00
[    7.886845] fbcon: nouveaufb (fb0) is primary device
[    7.945819] Console: switching to colour frame buffer device 240x75
[    7.946775] usb 9-1: device descriptor read/64, error -32
[    7.957765] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[    7.957767] nouveau 0000:01:00.0: registered panic notifier
[    7.957771] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 0
[    8.218775] usb 9-1: new full-speed USB device number 4 using ohci-pci
[    8.630682] usb 9-1: device not accepting address 4, error -32
[    8.794715] usb 9-1: new full-speed USB device number 5 using ohci-pci
[    9.202651] usb 9-1: device not accepting address 5, error -32
[    9.202696] hub 9-0:1.0: unable to enumerate USB device on port 1
[   10.644512] r8169 0000:03:00.0 eth0: link down
[   10.644534] r8169 0000:03:00.0 eth0: link down
[   10.644556] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.644758] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.010388] init: alsa-restore main process (912) terminated with status 99
[   12.202590] r8169 0000:03:00.0 eth0: link up
[   12.202598] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   66.880760] ------------[ cut here ]------------
[   66.880779] WARNING: CPU: 3 PID: 0 at /build/buildd/linux-3.11.0/net/sched/sch_generic.c:260 dev_watchdog+0x26a/0x280()
[   66.880781] NETDEV WATCHDOG: eth0 (r8169): transmit queue 0 timed out
[   66.880787] Modules linked in: parport_pc(F) ppdev(F) snd_hda_codec_hdmi bnep rfcomm bluetooth nouveau snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) mxm_wmi wmi snd_seq(F) sp5100_tco snd_seq_device(F) snd_timer(F) video(F) ttm snd(F) drm_kms_helper drm soundcore(F) i2c_algo_bit kvm_amd(F) kvm(F) psmouse(F) edac_core i2c_piix4 edac_mce_amd microcode(F) serio_raw(F) k10temp ohci_pci mac_hid lp(F) parport(F) pata_acpi pata_atiixp r8169 ahci(F) libahci(F) mii(F)
[   66.880822] CPU: 3 PID: 0 Comm: swapper/3 Tainted: GF            3.11.0-12-generic #19-Ubuntu
[   66.880824] Hardware name: Gigabyte Technology Co., Ltd. To be filled by O.E.M./970A-DS3, BIOS FD 01/23/2013
[   66.880828]  0000000000000009 ffff88022fd83d78 ffffffff816e547a ffff88022fd83dc0
[   66.880832]  ffff88022fd83db0 ffffffff81061dbd ffff8802204ac000 0000000000000000
[   66.880834]  0000000000000003 ffff880220150880 ffff880220150800 ffff88022fd83e10
[   66.880837] Call Trace:
[   66.880838]  <IRQ>  [<ffffffff816e547a>] dump_stack+0x45/0x56
[   66.880851]  [<ffffffff81061dbd>] warn_slowpath_common+0x7d/0xa0
[   66.880853]  [<ffffffff81061e2c>] warn_slowpath_fmt+0x4c/0x50
[   66.880857]  [<ffffffff8160e14a>] dev_watchdog+0x26a/0x280
[   66.880862]  [<ffffffff8160dee0>] ? dev_deactivate_queue.constprop.32+0x60/0x60
[   66.880865]  [<ffffffff8106e886>] call_timer_fn+0x36/0x110
[   66.880867]  [<ffffffff8160dee0>] ? dev_deactivate_queue.constprop.32+0x60/0x60
[   66.880877]  [<ffffffff8106f95d>] run_timer_softirq+0x1fd/0x2b0
[   66.880879]  [<ffffffff81067397>] __do_softirq+0xf7/0x240
[   66.880881]  [<ffffffff81067675>] irq_exit+0xb5/0xc0
[   66.880887]  [<ffffffff816f7516>] do_IRQ+0x56/0xc0
[   66.880889]  [<ffffffff816ecb2d>] common_interrupt+0x6d/0x6d
[   66.880890]  <EOI>  [<ffffffff8104d386>] ? native_safe_halt+0x6/0x10
[   66.880897]  [<ffffffff810bdaaf>] ? clockevents_notify+0x4f/0x210
[   66.880902]  [<ffffffff8101b22f>] default_idle+0x1f/0xc0
[   66.880904]  [<ffffffff8101b34a>] amd_e400_idle+0x7a/0x100
[   66.880909]  [<ffffffff8101baf6>] arch_cpu_idle+0x26/0x30
[   66.880912]  [<ffffffff810b54ee>] cpu_startup_entry+0xce/0x280
[   66.880916]  [<ffffffff8103eef7>] start_secondary+0x217/0x2c0
[   66.880918] ---[ end trace 1c70833b77b5d06f ]---
[   66.887002] r8169 0000:03:00.0 eth0: link up
[   70.129703] systemd-hostnamed[1795]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  162.881295] r8169 0000:03:00.0 eth0: link up
john@Ubuntu-v1:~$
```

---

### Post by sanderj on 2013-11-19
Did you see this: [http://ubuntuforums.org/showthread.php?t=2114055&page=2&p=12851570#post12851570](http://ubuntuforums.org/showthread.php?t=2114055&page=2&p=12851570#post12851570) ?

---

### Post by jmatteson8 on 2013-11-19
AWESOME!!! Worked like a charm! Although, gksudo wasn't on my system by default so I couldn't use it and I of course couldn't download it but, I was able to use sudo instead and it worked fine. Thanks so much for finding this other post. You have no idea how long I searched through the forums and didn't find it myself. The magic of the right keyword, right?

---

### Post by DuckHook on 2013-11-19
Glad you got it worked out. I have only a minor alert: you never stated which 'buntu flavour you were currently running, so gksudo might not have been the right invocation. If Kubuntu, then you use kdesudo. All other 'buntus use gksudo. It is important to use gksudo/kdesudo for all graphical apps that you want to give temporary root privileges. Sudo is used only with console apps and can mess up your permissions if used with GUI apps. Minor matter compared to what sanderj fixed, but didn't want it to pass uncorrected.

---

### Post by jmatteson8 on 2013-11-19
> **DuckHook said:**
> Glad you got it worked out. I have only a minor alert: you never stated which 'buntu flavour you were currently running, so gksudo might not have been the right invocation. If Kubuntu, then you use kdesudo. All other 'buntus use gksudo. It is important to use gksudo/kdesudo for all graphical apps that you want to give temporary root privileges. Sudo is used only with console apps and can mess up your permissions if used with GUI apps. Minor matter compared to what sanderj fixed, but didn't want it to pass uncorrected.

Thanks, for the input and it is well taken. I hope I have no issues but I really didn't have a choice.

Since I hadn't landed on a flavor of Linux. I've been trying several to find the one I like best. As I had stated, the issue was happening with all the Linux flavors I tried not just the 'buntu flavors. In the troubleshooting stages, I figured I had to pick one and see if installing to the hard drive would solve no USB and no network so I had chosen Ubuntu but as I said, gksudo wasn't installed out of the box and I had no network connection so I couldn't get gksudo installed. At least thats what the OS said when I tried to get it and install it.

---

### Post by DuckHook on 2013-11-20
gksu would work too.

---

### Post by sanderj on 2013-11-20
> **jmatteson8 said:**
> AWESOME!!! Worked like a charm! Although, gksudo wasn't on my system by default so I couldn't use it and I of course couldn't download it but, I was able to use sudo instead and it worked fine. Thanks so much for finding this other post. You have no idea how long I searched through the forums and didn't find it myself. The magic of the right keyword, right?

It was a matter of **serendipity**: suddenly I got two thread updates with the same problem & the IOMMU solution/workaround.

Great it's solved. Strange it only happens in 64-bit.

---

