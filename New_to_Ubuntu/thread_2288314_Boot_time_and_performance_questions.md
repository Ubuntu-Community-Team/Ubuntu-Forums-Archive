---
title: "Boot time and performance questions"
date: 2015-07-26
forum: New to Ubuntu
---

### Post by Ivan_Mihaylov on 2015-07-26
Hi there,

I never used Ubuntu or any Linux distribution before (exept Knopix when i must repair some non booting win), but after my latest disapointment with windows i decided to go for Ubuntu.

I'm pretty embarassed to say it, but i have no idea what the hell is going on in my computer... For advanced user with 10+ years software and hardware maintenance experience i'm now feeling like in first grade without knowing how to write anything... 

So my first question is why this thing loads more than 5 min on black screen. I don't think that it's normal live cd to boot for 10-30 sec and the OS itself to take so long. I tried to read something by typing DMESG but I hardly understand anything. This is what it returns:

```
[    1.437385] usb usb5: Manufacturer: Linux 3.16.0-44-generic ohci_hcd[    1.437387] usb usb5: SerialNumber: 0000:00:14.5
[    1.437767] hub 5-0:1.0: USB hub found
[    1.437825] hub 5-0:1.0: 2 ports detected
[    1.438025] ohci-platform: OHCI generic platform driver
[    1.438046] uhci_hcd: USB Universal Host Controller Interface driver
[    1.438387] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.438397] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.438629] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
[    1.438633] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
[    1.438637] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    1.438741] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    1.438743] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.438746] usb usb6: Product: xHCI Host Controller
[    1.438748] usb usb6: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.438750] usb usb6: SerialNumber: 0000:00:10.0
[    1.439141] hub 6-0:1.0: USB hub found
[    1.439202] hub 6-0:1.0: 2 ports detected
[    1.439348] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.439354] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    1.442040] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
[    1.442042] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.442045] usb usb7: Product: xHCI Host Controller
[    1.442047] usb usb7: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.442049] usb usb7: SerialNumber: 0000:00:10.0
[    1.442277] hub 7-0:1.0: USB hub found
[    1.442305] hub 7-0:1.0: 2 ports detected
[    1.442831] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.442839] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    1.443068] xhci_hcd 0000:00:10.1: irq 43 for MSI/MSI-X
[    1.443073] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
[    1.443077] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
[    1.443178] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.443180] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.443182] usb usb8: Product: xHCI Host Controller
[    1.443185] usb usb8: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.443187] usb usb8: SerialNumber: 0000:00:10.1
[    1.443529] hub 8-0:1.0: USB hub found
[    1.443589] hub 8-0:1.0: 2 ports detected
[    1.443808] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.443814] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
[    1.446477] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.446479] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.446482] usb usb9: Product: xHCI Host Controller
[    1.446484] usb usb9: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.446486] usb usb9: SerialNumber: 0000:00:10.1
[    1.446771] hub 9-0:1.0: USB hub found
[    1.446830] hub 9-0:1.0: 2 ports detected
[    1.447079] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.449333] i8042: Detected active multiplexing controller, rev 1.1
[    1.450464] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.450470] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.450507] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.450535] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.450561] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.451134] mousedev: PS/2 mouse device common for all mice
[    1.451847] rtc_cmos 00:03: RTC can wake from S4
[    1.451988] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.452022] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.452122] device-mapper: uevent: version 1.0.3
[    1.452318] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.452345] ledtrig-cpu: registered to indicate activity on CPUs
[    1.452471] TCP: cubic registered
[    1.452634] NET: Registered protocol family 10
[    1.453007] NET: Registered protocol family 17
[    1.453036] Key type dns_resolver registered
[    1.453554] Loading compiled-in X.509 certificates
[    1.454967] Loaded X.509 cert 'Magrathea: Glacier signing key: 4b6de31c0185e45a0c0d73ca36f8fa02edc6253a'
[    1.454987] registered taskstats version 1
[    1.457965] Key type trusted registered
[    1.463524] Key type encrypted registered
[    1.463538] AppArmor: AppArmor sha1 policy hashing enabled
[    1.463543] ima: No TPM chip found, activating TPM-bypass!
[    1.463568] evm: HMAC attrs: 0x1
[    1.464206]   Magic number: 7:465:884
[    1.464329] rtc_cmos 00:03: setting system clock to 2015-07-26 11:51:45 UTC (1437911505)
[    1.464552] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.464720] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.464721] EDD information not available.
[    1.464819] PM: Hibernation image not present or could not be loaded.
[    1.467271] Freeing unused kernel memory: 1352K (ffffffff81d1c000 - ffffffff81e6e000)
[    1.467275] Write protecting the kernel read-only data: 12288k
[    1.469543] Freeing unused kernel memory: 552K (ffff880001776000 - ffff880001800000)
[    1.471365] Freeing unused kernel memory: 480K (ffff880001b88000 - ffff880001c00000)
[    1.479579] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.494019] systemd-udevd[103]: starting version 204
[    1.518587] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.518604] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.518950] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
[    1.519175] r8169 0000:02:00.0 eth0: RTL8168e/8111e at 0xffffc9000003a000, e4:11:5b:40:3b:c6, XID 0c200000 IRQ 46
[    1.519178] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.524468] sdhci: Secure Digital Host Controller Interface driver
[    1.524473] sdhci: Copyright(c) Pierre Ossman
[    1.526634] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2392] (rev 30)
[    1.526814] mmc0: no vqmmc regulator found
[    1.526816] mmc0: no vmmc regulator found
[    1.535341] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[    1.535369] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 30)
[    1.535519] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
[    1.557155] usb 1-5: new high-speed USB device number 2 using ehci-pci
[    1.557899] ahci 0000:00:11.0: version 3.0
[    1.558258] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
[    1.558627] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.558633] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.559286] scsi0 : ahci
[    1.559482] scsi1 : ahci
[    1.559586] ata1: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151100 irq 47
[    1.559590] ata2: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151180 irq 47
[    1.738414] usb 1-5: New USB device found, idVendor=0461, idProduct=4dc7
[    1.738426] usb 1-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.738433] usb 1-5: Product: HP HD Webcam [Fixed]
[    1.738438] usb 1-5: Manufacturer: Primax Electronics Ltd.
[    1.738442] usb 1-5: SerialNumber: PMX02
[    2.049399] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.049441] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.050054] ata1.00: ATA-8: TOSHIBA MK6476GSX, GS001C, max UDMA/100
[    2.050060] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.050465] ata1.00: configured for UDMA/100
[    2.050955] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6476GS 1C   PQ: 0 ANSI: 5
[    2.051604] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.051607] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.051658] sd 0:0:0:0: [sda] Write Protect is off
[    2.051660] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.051679] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.053908] ata2.00: ATAPI: hp       DVDRAM GT50N, MP00, max UDMA/100
[    2.059474] ata2.00: configured for UDMA/100
[    2.063989] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT50N     MP00 PQ: 0 ANSI: 5
[    2.085677] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.085687] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.085903] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.085962] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.117397] tsc: Refined TSC clocksource calibration: 1896.552 MHz
[    2.132545]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.133416] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.265435] usb 4-5: new full-speed USB device number 2 using ohci-pci
[    2.421277] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..4876]
[    2.426515] usb 4-5: New USB device found, idVendor=03f0, idProduct=311d
[    2.426527] usb 4-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.494243] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x640000/0xa0400, board id: 1397, fw id: 780218
[    2.541703] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[    2.590622] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.117722] Switched to clocksource tsc
[    3.237375] random: init urandom read with 101 bits of entropy available
[    3.624070] random: nonblocking pool is initialized
[    3.729976] init: plymouth-upstart-bridge main process (165) terminated with status 1
[    3.729993] init: plymouth-upstart-bridge main process ended, respawning
[    3.733487] init: plymouth-upstart-bridge main process (177) terminated with status 1
[    3.733501] init: plymouth-upstart-bridge main process ended, respawning
[    3.735991] init: plymouth-upstart-bridge main process (179) terminated with status 1
[    3.736008] init: plymouth-upstart-bridge main process ended, respawning
[    3.739644] init: plymouth-upstart-bridge main process (180) terminated with status 1
[    3.739658] init: plymouth-upstart-bridge main process ended, respawning
[    3.742128] init: plymouth-upstart-bridge main process (182) terminated with status 1
[    3.742144] init: plymouth-upstart-bridge main process ended, respawning
[    3.745567] init: plymouth-upstart-bridge main process (183) terminated with status 1
[    3.745581] init: plymouth-upstart-bridge main process ended, respawning
[    3.748479] init: plymouth-upstart-bridge main process (185) terminated with status 1
[    3.748491] init: plymouth-upstart-bridge main process ended, respawning
[    3.751730] init: plymouth-upstart-bridge main process (186) terminated with status 1
[    3.751744] init: plymouth-upstart-bridge main process ended, respawning
[    3.754350] init: plymouth-upstart-bridge main process (188) terminated with status 1
[    3.754367] init: plymouth-upstart-bridge main process ended, respawning
[    3.757693] init: plymouth-upstart-bridge main process (189) terminated with status 1
[    3.757706] init: plymouth-upstart-bridge main process ended, respawning
[    3.761684] init: plymouth-upstart-bridge main process (191) terminated with status 1
[    3.761697] init: plymouth-upstart-bridge respawning too fast, stopped
[    9.460962] Adding 20970492k swap on /dev/sda5.  Priority:-1 extents:1 across:20970492k FS
[    9.558856] systemd-udevd[294]: starting version 204
[    9.652692] lp: driver loaded but no devices found
[    9.661948] ppdev: user-space parallel port driver
[    9.691686] [drm] Initialized drm 1.1.0 20060810
[    9.706346] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.710742] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.738125] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    9.777307] [drm] radeon kernel modesetting enabled.
[    9.777332] VGA switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[    9.777370] checking generic (b0000000 410000) vs hw (b0000000 10000000)
[    9.777372] fb: switching to radeondrmfb from VESA VGA
[    9.777404] Console: switching to colour dummy device 80x25
[    9.784281] acpi device:00: registered as cooling_device2
[    9.784407] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
[    9.785143] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
[    9.785791] acpi device:0a: registered as cooling_device3
[    9.785908] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input13
[    9.785954] hp_accel: laptop model unknown, using default axes configuration
[    9.786613] lis3lv02d: 8 bits 3DC sensor found
[    9.787463] [drm] initializing kernel modesetting (SUMO2 0x1002:0x9649 0x103C:0x168C).
[    9.787485] [drm] register mmio base: 0xD8100000
[    9.787487] [drm] register mmio size: 262144
[    9.788092] ATOM BIOS: HP
[    9.788159] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    9.788162] radeon 0000:00:01.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    9.788164] [drm] Detected VRAM RAM=512M, BAR=256M
[    9.788166] [drm] RAM width 32bits DDR
[    9.792743] [TTM] Zone  kernel: Available graphics memory: 3814136 kiB
[    9.792747] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    9.792749] [TTM] Initializing pool allocator
[    9.792759] [TTM] Initializing DMA pool allocator
[    9.792790] [drm] radeon: 512M of VRAM memory ready
[    9.792792] [drm] radeon: 1024M of GTT memory ready.
[    9.792814] [drm] Loading SUMO2 Microcode
[    9.833697] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input14
[    9.862216] wmi: Mapper loaded
[    9.897135] [drm] Internal thermal controller without fan control
[    9.897222] [drm] Found smc ucode version: 0x00011200
[    9.897298] [drm] radeon: dpm initialized
[    9.898951] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    9.933457] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[    9.933587] cfg80211: Calling CRDA to update world regulatory domain
[    9.933760] radeon 0000:00:01.0: WB enabled
[    9.933766] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff88008af9ac00
[    9.933769] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff88008af9ac0c
[    9.934517] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90011bb2118
[    9.940175] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    9.940182] [drm] Driver supports precise vblank timestamp query.
[    9.940188] radeon 0000:00:01.0: radeon: MSI limited to 32-bit
[    9.940217] radeon 0000:00:01.0: irq 48 for MSI/MSI-X
[    9.940234] radeon 0000:00:01.0: radeon: using MSI.
[    9.940266] [drm] radeon: irq initialized.
[    9.968579] [drm] ring test on 0 succeeded in 1 usecs
[    9.968591] [drm] ring test on 3 succeeded in 3 usecs
[   10.028344] [drm] ring test on 5 succeeded in 1 usecs
[   10.031799] audit: type=1400 audit(1437900714.061:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=390 comm="apparmor_parser"
[   10.031810] audit: type=1400 audit(1437900714.061:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=390 comm="apparmor_parser"
[   10.031816] audit: type=1400 audit(1437900714.061:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   10.032460] audit: type=1400 audit(1437900714.061:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=390 comm="apparmor_parser"
[   10.032468] audit: type=1400 audit(1437900714.061:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   10.032803] audit: type=1400 audit(1437900714.061:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   10.038368] ath: phy0: ASPM enabled: 0x42
[   10.038374] ath: EEPROM regdomain: 0x60
[   10.038376] ath: EEPROM indicates we should expect a direct regpair map
[   10.038379] ath: Country alpha2 being used: 00
[   10.038381] ath: Regpair used: 0x60
[   10.053270] [drm] UVD initialized successfully.
[   10.058147] [drm] ib test on ring 0 succeeded in 0 usecs
[   10.058184] [drm] ib test on ring 3 succeeded in 0 usecs
[   10.061010] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.061525] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011180000, irq=19
[   10.076485] WARNING! power/level is deprecated; use power/control instead
[   10.080161] [drm] ib test on ring 5 succeeded
[   10.103243] Bluetooth: Core ver 2.19
[   10.103288] NET: Registered protocol family 31
[   10.103291] Bluetooth: HCI device and connection manager initialized
[   10.103300] Bluetooth: HCI socket layer initialized
[   10.103304] Bluetooth: L2CAP socket layer initialized
[   10.103315] Bluetooth: SCO socket layer initialized
[   10.104425] [drm] radeon atom DIG backlight initialized
[   10.104430] [drm] Radeon Display Connectors
[   10.104432] [drm] Connector 0:
[   10.104434] [drm]   VGA-1
[   10.104436] [drm]   HPD2
[   10.104438] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   10.104439] [drm]   Encoders:
[   10.104441] [drm]     CRT1: INTERNAL_UNIPHY2
[   10.104442] [drm]     CRT1: NUTMEG
[   10.104444] [drm] Connector 1:
[   10.104445] [drm]   LVDS-1
[   10.104446] [drm]   HPD1
[   10.104448] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   10.104449] [drm]   Encoders:
[   10.104450] [drm]     LCD1: INTERNAL_UNIPHY2
[   10.104451] [drm]     LCD1: TRAVIS
[   10.104453] [drm] Connector 2:
[   10.104454] [drm]   HDMI-A-1
[   10.104455] [drm]   HPD4
[   10.104457] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[   10.104458] [drm]   Encoders:
[   10.104459] [drm]     DFP1: INTERNAL_UNIPHY
[   10.126323] usbcore: registered new interface driver btusb
[   10.268188] [drm] fb mappable at 0xB0477000
[   10.268193] [drm] vram apper at 0xB0000000
[   10.268195] [drm] size 4325376
[   10.268197] [drm] fb depth is 24
[   10.268198] [drm]    pitch is 5632
[   10.269211] fbcon: radeondrmfb (fb0) is primary device
[   10.269253] Console: switching to colour frame buffer device 170x48
[   10.269286] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[   10.269289] radeon 0000:00:01.0: registered panic notifier
[   10.302710] [drm] Initialized radeon 2.39.0 20080528 for 0000:00:01.0 on minor 0
[   10.303205] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[   10.303879] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B06 (\_SB_.PCI0.SMBS.SMBO) (20140424/utaddress-254)
[   10.303887] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.304527] snd_hda_intel 0000:00:01.1: irq 49 for MSI/MSI-X
[   10.304926] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6760 0x103C:0x168C).
[   10.304953] [drm] register mmio base: 0xD8000000
[   10.304955] [drm] register mmio size: 131072
[   10.304958] vga_switcheroo: enabled
[   10.305100] ATPX version 1, functions 0x00000003
[   10.348307] kvm: disabled by bios
[   10.348866] sound hdaudioC1D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   10.348877] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   10.348881] sound hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   10.348883] sound hdaudioC1D0:    mono: mono_out=0x0
[   10.348885] sound hdaudioC1D0:    inputs:
[   10.348888] sound hdaudioC1D0:      Internal Mic=0x11
[   10.348891] sound hdaudioC1D0:      Mic=0xc
[   10.355680] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input15
[   10.383285] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
[   10.383380] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input17
[   10.623032] cfg80211: World regulatory domain updated:
[   10.623039] cfg80211:  DFS Master region: unset
[   10.623042] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.623046] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.623049] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.623051] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.623054] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.623056] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.672908] Bluetooth: RFCOMM TTY layer initialized
[   10.672921] Bluetooth: RFCOMM socket layer initialized
[   10.672934] Bluetooth: RFCOMM ver 1.11
[   10.762386] audit: type=1400 audit(1437900714.793:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=587 comm="apparmor_parser"
[   10.762400] audit: type=1400 audit(1437900714.793:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=587 comm="apparmor_parser"
[   10.763072] audit: type=1400 audit(1437900714.793:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=587 comm="apparmor_parser"
[   10.781815] media: Linux media interface: v0.10
[   10.792701] Linux video capture interface: v2.00
[   10.811553] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (0461:4dc7)
[   10.814014] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.814019] Bluetooth: BNEP filters: protocol multicast
[   10.814029] Bluetooth: BNEP socket layer initialized
[   10.866663] usbcore: registered new interface driver ath3k
[   10.882884] usb 4-5: USB disconnect, device number 2
[   10.916423] init: failsafe main process (572) killed by TERM signal
[   10.953253] init: cups main process (596) killed by HUP signal
[   10.953267] init: cups main process ended, respawning
[   11.034985] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input19
[   11.035363] usbcore: registered new interface driver uvcvideo
[   11.035367] USB Video Class driver (1.1.1)
[   11.147783] audit: type=1400 audit(1437900715.177:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=725 comm="apparmor_parser"
[   11.628128] input: HP WMI hotkeys as /devices/virtual/input/input18
[   11.854589] usb 4-5: new full-speed USB device number 3 using ohci-pci
[   12.032115] usb 4-5: New USB device found, idVendor=0cf3, idProduct=3005
[   12.032121] usb 4-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   12.106414] r8169 0000:02:00.0 eth0: link down
[   12.106470] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.148315] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.588250] ATOM BIOS: HP
[   13.589344] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   13.589347] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[   13.589349] [drm] Detected VRAM RAM=1024M, BAR=256M
[   13.589350] [drm] RAM width 64bits DDR
[   13.589371] [drm] radeon: 1024M of VRAM memory ready
[   13.589372] [drm] radeon: 1024M of GTT memory ready.
[   13.589391] [drm] Loading CAICOS Microcode
[   13.616717] [drm] Internal thermal controller with fan control
[   13.621212] [drm] radeon: dpm initialized
[   13.621260] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   13.626444] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[   13.626576] radeon 0000:01:00.0: WB enabled
[   13.626581] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff88008739dc00
[   13.626583] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff88008739dc0c
[   13.628134] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90012cb2118
[   13.628138] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   13.628139] [drm] Driver supports precise vblank timestamp query.
[   13.628141] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[   13.628171] radeon 0000:01:00.0: irq 50 for MSI/MSI-X
[   13.628189] radeon 0000:01:00.0: radeon: using MSI.
[   13.628242] [drm] radeon: irq initialized.
[   13.645204] [drm] ring test on 0 succeeded in 2 usecs
[   13.645220] [drm] ring test on 3 succeeded in 7 usecs
[   13.831574] [drm] ring test on 5 succeeded in 2 usecs
[   13.831584] [drm] UVD initialized successfully.
[   13.832174] [drm] ib test on ring 0 succeeded in 0 usecs
[   13.832257] [drm] ib test on ring 3 succeeded in 0 usecs
[   13.982729] hp_wmi: Unknown event_id - 0 - 0x0
[   13.982818] hp_wmi: Unknown event_id - 0 - 0x0
[   13.982959] radeon 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   13.982971] pci 0000:00:14.4: PCI bridge to [bus 07]
[   13.983266] radeon 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   13.983271] pci 0000:00:14.4: PCI bridge to [bus 07]
[   13.984499] [drm] ib test on ring 5 succeeded
[   13.985460] [drm] Radeon Display Connectors
[   13.993012] radeon 0000:01:00.0: No connectors reported connected with modes
[   13.993017] [drm] Cannot find any crtc or sizes - going 1024x768
[   13.995169] [drm] fb mappable at 0xC0474000
[   13.995171] [drm] vram apper at 0xC0000000
[   13.995172] [drm] size 3145728
[   13.995173] [drm] fb depth is 24
[   13.995174] [drm]    pitch is 4096
[   13.995279] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[   13.995785] [drm:radeon_acpi_init] *ERROR* Cannot find a backlight controller
[   13.995922] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 1
[   14.062160] init: plymouth-splash main process (1042) terminated with status 1
[   15.249449] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   15.249457] vgaarb: device changed decodes: PCI:0000:00:01.0,olddecodes=io+mem,decodes=none:owns=none
[   22.368368] radeon 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   22.368383] pci 0000:00:14.4: PCI bridge to [bus 07]
[   22.368420] radeon 0000:01:00.0: Max Payload Size 16384, but upstream 0000:00:03.0 set to 128; if necessary, use "pci=pcie_bus_safe" and report a bug
[   40.920008] audit_printk_skb: 150 callbacks suppressed
[   40.920014] audit: type=1400 audit(1437900744.945:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1582 comm="apparmor_parser"
[   40.920026] audit: type=1400 audit(1437900744.945:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1582 comm="apparmor_parser"
[   40.920595] audit: type=1400 audit(1437900744.945:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1582 comm="apparmor_parser"
[ 1007.570793] systemd-hostnamed[2237]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!



```

The posibility to install it wrong is pretty much high. I wanted to keep the NTFS partition with my files and to use my ex-win system partition for linux install. This is my current setup:

```
NAME   FSTYPE   SIZE MOUNTPOINT                   LABELsda           596,2G                              
&#9500;&#9472;sda1 vfat     7,8G /media/ivan/F6F9-F5F5        
&#9500;&#9472;sda2 ext4    97,7G /                            
&#9500;&#9472;sda3 ntfs   465,7G /media/ivan/4CDC0493DC047A0A 
&#9500;&#9472;sda4            1K                              
&#9492;&#9472;sda5 swap      20G [SWAP]                       
sr0            1024M   
```

So after that 5 min boot i manage to enter into my pc, but then I began to get some no responding windows and quite some freezing which i was hoping to bypass by using linux. 

I know that this is quite some stupid questions, but please bear with me and give me some advice what to do. And please keep it sipmle, like you try to teach your 2 old neighbor kid... 

Thanks in advance to all,
Ivan

---

### Post by grahammechanical on 2015-07-26
Yes, 5 minutes is too long. It indicates to me that the system is trying to start some process and failing and then trying again and again and again until it gives up.

If you look through that printout you will see on the left side the times at which various actions were carried out. Compare the last two lines. There is a big jump from 40.920595 to 1007.570793.

SystemD is what Linux developers call an init system. It initializes - starts and also stops system processes. And it is systemd-host name that has hit a problem that just may be the cause of the excess time it is taking to load. I do not know. Nor, do I know the solution. The little research I have just done suggests that it may not be wise to install nss-myhostname. Here is the link

[URL="http://askubuntu.com/questions/453072/what-is-nss-myhostname-and-why-is-it-not-installable"]http://askubuntu.com/questions/453072/what-is-nss-myhostname-and-why-is-it-not-installable

[/URL]Ubuntu has only recently switched over to systemd. I am running the development version of the next release of Ubuntu (15.10) and systemd has been in charge from the first day of the development period. I do not experience a long delay in loading Ubuntu. In fact loading time have improved in the weeks since systemd was introduced.

Regards.

---

### Post by Ivan_Mihaylov on 2015-07-26
> **grahammechanical said:**
> Yes, 5 minutes is too long. It indicates to me that the system is trying to start some process and failing and then trying again and again and again until it gives up.

If you look through that printout you will see on the left side the times at which various actions were carried out. Compare the last two lines. There is a big jump from 40.920595 to 1007.570793.

SystemD is what Linux developers call an init system. It initializes - starts and also stops system processes. And it is systemd-host name that has hit a problem that just may be the cause of the excess time it is taking to load. I do not know. Nor, do I know the solution. The little research I have just done suggests that it may not be wise to install nss-myhostname. Here is the link

[URL="http://askubuntu.com/questions/453072/what-is-nss-myhostname-and-why-is-it-not-installable"]http://askubuntu.com/questions/453072/what-is-nss-myhostname-and-why-is-it-not-installable

[/URL]Ubuntu has only recently switched over to systemd. I am running the development version of the next release of Ubuntu (15.10) and systemd has been in charge from the first day of the development period. I do not experience a long delay in loading Ubuntu. In fact loading time have improved in the weeks since systemd was introduced.

Regards.

Thanks for the suggestion! Actually i already installed nss-myhostname, but that dosn't changed a thing... I begin to think that it is somehow related to the switchable amd graphics as when i boot in recovery and then proceed into OS it boots normaly but it's working pretty slow... 

Also I just saw that cpu usage is around 80-100% which could explain the laggy working. Any idea how to check what and why it's using so much resources?

Thanks in advance,

---

### Post by ajgreeny on 2015-07-26
According to the error message showing in the dmesg output you should check that you have the package **libnss-myhostname** installed with command ```
dpkg-query -s libnss-myhostname
```The second line of the output will tell you if it is installed or not; if not install it.

EDIT:
Beaten by grahammechanical.

Sorry his fix did not do the job.  I've no other ideas, I'm afraid, except to ask 
1) Did you check the md5sum of the iso file you used?  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) What hardware are you using, particularly CPU, RAM, and graphic card?

Have a look at bumblebee for your switchable graphics (nvidia optimus?) as that is apparently now working quite well.  Note that I have never had an nvidia card so speak only from reading about this, not ever using it.
[https://launchpad.net/~bumblebee/+archive/ubuntu/stable](https://launchpad.net/~bumblebee/+archive/ubuntu/stable)
[http://askubuntu.com/questions/466269/how-to-purge-and-reinstall-bumblebee-completely](http://askubuntu.com/questions/466269/how-to-purge-and-reinstall-bumblebee-completely)

---

### Post by Ivan_Mihaylov on 2015-07-26
I just downloaded and installed "flgrx" from amd website and now it's booting perfectly (5-10 sec), but after login i began to get system errors. 

I think it's this one:


```
Jul 26 17:35:29 ivan-HP-ProBook-4535s gnome-session[2072]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed

```

Could this be the cause of the performance issues?

Also i was thinking that Ubuntu don't need any drivers but after the graphics issue could you tell me what should I install so that my computer would work smoothly.

Best regards,

---

### Post by Ivan_Mihaylov on 2015-07-26
> **ajgreeny said:**
> According to the error message showing in the dmesg output you should check that you have the package **libnss-myhostname** installed with command ```
dpkg-query -s libnss-myhostname
```The second line of the output will tell you if it is installed or not; if not install it.

EDIT:
Beaten by grahammechanical.

Sorry his fix did not do the job.  I've no other ideas, I'm afraid, except to ask 
1) Did you check the md5sum of the iso file you used?  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
2) What hardware are you using, particularly CPU, RAM, and graphic card?

Have a look at bumblebee for your switchable graphics (nvidia optimus?) as that is apparently now working quite well.  Note that I have never had an nvidia card so speak only from reading about this, not ever using it.
[https://launchpad.net/~bumblebee/+archive/ubuntu/stable](https://launchpad.net/~bumblebee/+archive/ubuntu/stable)
[http://askubuntu.com/questions/466269/how-to-purge-and-reinstall-bumblebee-completely](http://askubuntu.com/questions/466269/how-to-purge-and-reinstall-bumblebee-completely)

Hey @ajgreeny,

Sorry i saw your reply quite late and already I won the fight with the graphic card (I hope at least).

I installed "[COLOR=#000000][FONT=Calibri]AMD Catalyst&#8482; 15.7 Proprietary Ubuntu 14.04 x86_64 Minimal Video Driver for Graphics Accelerators (Non-X Support)[/FONT][/COLOR]"

I'm attaching my hardware info so if you could check if i got the right one amd:

[ATTACH]263401[/ATTACH]

Any other ideas for the performance issues?

EDIT: Actully if it is the right one shouldn't i get more resolutions than 1366x768?

---

### Post by oldfred on 2015-07-26
I do not know AMD.
But you had another longer time stamp gap. And it had this suggestion, have you tried it?
 22.368420   use pci=pcie_bus_safe

That would be a boot option that you add likenomodeset on linux line in grub menu. Test just by booting and editing grub. That is a one time change but if it works then it can be made permanent.

If you only have Ubuntu and do not get grub menu hold shift key from BIOS until menu appears.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Generally best to not download drivers directly from vendor. Ubuntu repository has drivers, but often not most current. But most current driver usually only needed for very new systems. And for those very new systems other users create ppa's with updated drivers that will work.
Driver has to be re-integrated into every kernel you get. If from repository that is automatic. If downloaded from vendor you have to do that before rebooting after a new kernel is downloaded.

I have not followed AMD, as I have nVidia, but it is important to have the correct version driver to match your card/chip. And versions vary a lot.
      
 #To see video:
           
 sudo lshw | grep -A 11 display
lspci | grep VGA

 #What is installed
dkms status

---

### Post by ajgreeny on 2015-07-26
Forget about my bumblebee comment as that is for nvidia only as far as I'm aware, and you obviously have AMD graphics.

Sorry for confusion.

---

### Post by Ivan_Mihaylov on 2015-07-26
> **oldfred said:**
> I do not know AMD.
But you had another longer time stamp gap. And it had this suggestion, have you tried it?
 22.368420   use pci=pcie_bus_safe

That would be a boot option that you add likenomodeset on linux line in grub menu. Test just by booting and editing grub. That is a one time change but if it works then it can be made permanent.

If you only have Ubuntu and do not get grub menu hold shift key from BIOS until menu appears.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Generally best to not download drivers directly from vendor. Ubuntu repository has drivers, but often not most current. But most current driver usually only needed for very new systems. And for those very new systems other users create ppa's with updated drivers that will work.
Driver has to be re-integrated into every kernel you get. If from repository that is automatic. If downloaded from vendor you have to do that before rebooting after a new kernel is downloaded.

I have not followed AMD, as I have nVidia, but it is important to have the correct version driver to match your card/chip. And versions vary a lot.
      
 #To see video:
           
 sudo lshw | grep -A 11 display
lspci | grep VGA

 #What is installed
dkms status

I used the pci mode suggestion and the nomodest. The boot results are:

```
[    1.123685] Console: switching to colour frame buffer device 170x48[    1.123713] fb0: VESA VGA frame buffer device
[    1.124146] ACPI: AC Adapter [AC] (on-line)
[    1.124458] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    1.124463] ACPI: Sleep Button [SLPB]
[    1.124514] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    1.124586] ACPI: Lid Switch [LID]
[    1.124636] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.124639] ACPI: Power Button [PWRF]
[    1.124798] ACPI: acpi_idle registered with cpuidle
[    1.154579] thermal LNXTHERM:00: registered as thermal_zone0
[    1.154585] ACPI: Thermal Zone [CPUZ] (65 C)
[    1.178447] thermal LNXTHERM:01: registered as thermal_zone1
[    1.178453] ACPI: Thermal Zone [GFXZ] (57 C)
[    1.193333] thermal LNXTHERM:02: registered as thermal_zone2
[    1.193339] ACPI: Thermal Zone [EXTZ] (44 C)
[    1.208271] thermal LNXTHERM:03: registered as thermal_zone3
[    1.208277] ACPI: Thermal Zone [LOCZ] (54 C)
[    1.223238] thermal LNXTHERM:04: registered as thermal_zone4
[    1.223244] ACPI: Thermal Zone [BATZ] (31 C)
[    1.223317] GHES: HEST is not enabled!
[    1.223834] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.227570] Linux agpgart interface v0.103
[    1.230332] brd: module loaded
[    1.231848] loop: module loaded
[    1.232163] libphy: Fixed MDIO Bus: probed
[    1.232167] tun: Universal TUN/TAP device driver, 1.6
[    1.232169] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.232282] PPP generic driver version 2.4.2
[    1.232391] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.232398] ehci-pci: EHCI PCI platform driver
[    1.232763] QUIRK: Enable AMD PLL fix
[    1.232799] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.232807] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.232813] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.232826] ehci-pci 0000:00:12.2: debug port 1
[    1.232877] ehci-pci 0000:00:12.2: irq 17, io mem 0xd814f000
[    1.241108] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.241226] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.241230] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.241232] usb usb1: Product: EHCI Host Controller
[    1.241235] usb usb1: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
[    1.241237] usb usb1: SerialNumber: 0000:00:12.2
[    1.241512] hub 1-0:1.0: USB hub found
[    1.241520] hub 1-0:1.0: 5 ports detected
[    1.242172] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.242180] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.242186] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.242201] ehci-pci 0000:00:13.2: debug port 1
[    1.242239] ehci-pci 0000:00:13.2: irq 17, io mem 0xd814d000
[    1.253093] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.253208] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.253211] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.253214] usb usb2: Product: EHCI Host Controller
[    1.253216] usb usb2: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
[    1.253218] usb usb2: SerialNumber: 0000:00:13.2
[    1.253537] hub 2-0:1.0: USB hub found
[    1.253545] hub 2-0:1.0: 5 ports detected
[    1.253952] ehci-platform: EHCI generic platform driver
[    1.253972] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.253979] ohci-pci: OHCI PCI platform driver
[    1.254342] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.254350] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.254387] ohci-pci 0000:00:12.0: irq 18, io mem 0xd8150000
[    1.270170] ACPI: Battery Slot [BAT0] (battery present)
[    1.313162] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.313166] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.313168] usb usb3: Product: OHCI PCI host controller
[    1.313171] usb usb3: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
[    1.313173] usb usb3: SerialNumber: 0000:00:12.0
[    1.313582] hub 3-0:1.0: USB hub found
[    1.313644] hub 3-0:1.0: 5 ports detected
[    1.314173] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.314182] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.314216] ohci-pci 0000:00:13.0: irq 18, io mem 0xd814e000
[    1.373317] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.373323] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.373326] usb usb4: Product: OHCI PCI host controller
[    1.373328] usb usb4: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
[    1.373330] usb usb4: SerialNumber: 0000:00:13.0
[    1.373733] hub 4-0:1.0: USB hub found
[    1.373793] hub 4-0:1.0: 5 ports detected
[    1.374327] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.374335] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 5
[    1.374368] ohci-pci 0000:00:14.5: irq 18, io mem 0xd814c000
[    1.433226] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.433231] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.433233] usb usb5: Product: OHCI PCI host controller
[    1.433235] usb usb5: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
[    1.433236] usb usb5: SerialNumber: 0000:00:14.5
[    1.433637] hub 5-0:1.0: USB hub found
[    1.433697] hub 5-0:1.0: 2 ports detected
[    1.433908] ohci-platform: OHCI generic platform driver
[    1.433929] uhci_hcd: USB Universal Host Controller Interface driver
[    1.434267] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.434277] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.434504] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
[    1.434508] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
[    1.434512] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    1.434617] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    1.434619] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.434622] usb usb6: Product: xHCI Host Controller
[    1.434624] usb usb6: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.434627] usb usb6: SerialNumber: 0000:00:10.0
[    1.435014] hub 6-0:1.0: USB hub found
[    1.435074] hub 6-0:1.0: 2 ports detected
[    1.435261] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.435267] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    1.437918] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
[    1.437921] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.437923] usb usb7: Product: xHCI Host Controller
[    1.437926] usb usb7: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.437928] usb usb7: SerialNumber: 0000:00:10.0
[    1.438173] hub 7-0:1.0: USB hub found
[    1.438222] hub 7-0:1.0: 2 ports detected
[    1.438705] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.438713] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    1.438941] xhci_hcd 0000:00:10.1: irq 43 for MSI/MSI-X
[    1.438946] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
[    1.438950] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
[    1.439052] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.439054] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.439057] usb usb8: Product: xHCI Host Controller
[    1.439059] usb usb8: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.439061] usb usb8: SerialNumber: 0000:00:10.1
[    1.439389] hub 8-0:1.0: USB hub found
[    1.439448] hub 8-0:1.0: 2 ports detected
[    1.439650] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.439656] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
[    1.442344] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.442347] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.442348] usb usb9: Product: xHCI Host Controller
[    1.442350] usb usb9: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.442352] usb usb9: SerialNumber: 0000:00:10.1
[    1.442611] hub 9-0:1.0: USB hub found
[    1.442670] hub 9-0:1.0: 2 ports detected
[    1.442917] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.445277] i8042: Detected active multiplexing controller, rev 1.1
[    1.446422] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.446427] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.446460] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.446488] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.446515] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.447082] mousedev: PS/2 mouse device common for all mice
[    1.447506] rtc_cmos 00:03: RTC can wake from S4
[    1.447645] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.447680] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.447779] device-mapper: uevent: version 1.0.3
[    1.447895] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.447922] ledtrig-cpu: registered to indicate activity on CPUs
[    1.448047] TCP: cubic registered
[    1.448197] NET: Registered protocol family 10
[    1.448560] NET: Registered protocol family 17
[    1.448584] Key type dns_resolver registered
[    1.449189] Loading compiled-in X.509 certificates
[    1.450604] Loaded X.509 cert 'Magrathea: Glacier signing key: 4b6de31c0185e45a0c0d73ca36f8fa02edc6253a'
[    1.450623] registered taskstats version 1
[    1.453622] Key type trusted registered
[    1.459083] Key type encrypted registered
[    1.459097] AppArmor: AppArmor sha1 policy hashing enabled
[    1.459101] ima: No TPM chip found, activating TPM-bypass!
[    1.459136] evm: HMAC attrs: 0x1
[    1.459726]   Magic number: 7:701:96
[    1.459881] rtc_cmos 00:03: setting system clock to 2015-07-26 21:05:44 UTC (1437944744)
[    1.460097] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.460252] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.460253] EDD information not available.
[    1.460344] PM: Hibernation image not present or could not be loaded.
[    1.462585] Freeing unused kernel memory: 1352K (ffffffff81d1c000 - ffffffff81e6e000)
[    1.462589] Write protecting the kernel read-only data: 12288k
[    1.464849] Freeing unused kernel memory: 552K (ffff880001776000 - ffff880001800000)
[    1.466735] Freeing unused kernel memory: 480K (ffff880001b88000 - ffff880001c00000)
[    1.471790] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.490379] systemd-udevd[103]: starting version 204
[    1.516021] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.516037] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.516288] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
[    1.516507] r8169 0000:02:00.0 eth0: RTL8168e/8111e at 0xffffc9000003a000, e4:11:5b:40:3b:c6, XID 0c200000 IRQ 46
[    1.516510] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.524036] sdhci: Secure Digital Host Controller Interface driver
[    1.524040] sdhci: Copyright(c) Pierre Ossman
[    1.526871] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2392] (rev 30)
[    1.527840] mmc0: no vqmmc regulator found
[    1.527844] mmc0: no vmmc regulator found
[    1.528059] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[    1.528083] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 30)
[    1.528196] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
[    1.555029] ahci 0000:00:11.0: version 3.0
[    1.556000] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
[    1.556064] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.556069] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.556611] scsi0 : ahci
[    1.556743] scsi1 : ahci
[    1.556855] ata1: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151100 irq 47
[    1.556858] ata2: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151180 irq 47
[    1.557095] usb 1-5: new high-speed USB device number 2 using ehci-pci
[    1.742168] usb 1-5: New USB device found, idVendor=0461, idProduct=4dc7
[    1.742180] usb 1-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.742187] usb 1-5: Product: HP HD Webcam [Fixed]
[    1.742192] usb 1-5: Manufacturer: Primax Electronics Ltd.
[    1.742196] usb 1-5: SerialNumber: PMX02
[    2.045198] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.045237] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.046163] ata1.00: ATA-8: TOSHIBA MK6476GSX, GS001C, max UDMA/100
[    2.046171] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.046878] ata1.00: configured for UDMA/100
[    2.047341] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6476GS 1C   PQ: 0 ANSI: 5
[    2.047747] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.047792] sd 0:0:0:0: [sda] Write Protect is off
[    2.047794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.047813] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.047823] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.049400] ata2.00: ATAPI: hp       DVDRAM GT50N, MP00, max UDMA/100
[    2.053671] ata2.00: configured for UDMA/100
[    2.058160] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT50N     MP00 PQ: 0 ANSI: 5
[    2.077929] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.077939] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.078260] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.078343] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.106385]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.107239] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.113300] tsc: Refined TSC clocksource calibration: 1896.551 MHz
[    2.269231] usb 4-5: new full-speed USB device number 2 using ohci-pci
[    2.419325] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..4876]
[    2.430431] usb 4-5: New USB device found, idVendor=0cf3, idProduct=3005
[    2.430437] usb 4-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.494488] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x640000/0xa0400, board id: 1397, fw id: 780218
[    2.543485] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[    2.553163] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.113758] Switched to clocksource tsc
[    3.235298] random: init urandom read with 111 bits of entropy available
[    3.459277] random: nonblocking pool is initialized
[    3.803888] init: plymouth-upstart-bridge main process (164) terminated with status 1
[    3.803904] init: plymouth-upstart-bridge main process ended, respawning
[    3.807426] init: plymouth-upstart-bridge main process (178) terminated with status 1
[    3.807442] init: plymouth-upstart-bridge main process ended, respawning
[    3.810148] init: plymouth-upstart-bridge main process (180) terminated with status 1
[    3.810168] init: plymouth-upstart-bridge main process ended, respawning
[    3.813743] init: plymouth-upstart-bridge main process (181) terminated with status 1
[    3.813760] init: plymouth-upstart-bridge main process ended, respawning
[    3.816408] init: plymouth-upstart-bridge main process (183) terminated with status 1
[    3.816428] init: plymouth-upstart-bridge main process ended, respawning
[    3.819737] init: plymouth-upstart-bridge main process (184) terminated with status 1
[    3.819753] init: plymouth-upstart-bridge main process ended, respawning
[    3.822392] init: plymouth-upstart-bridge main process (186) terminated with status 1
[    3.822407] init: plymouth-upstart-bridge main process ended, respawning
[    3.826166] init: plymouth-upstart-bridge main process (187) terminated with status 1
[    3.826182] init: plymouth-upstart-bridge main process ended, respawning
[    3.828592] init: plymouth-upstart-bridge main process (189) terminated with status 1
[    3.828606] init: plymouth-upstart-bridge main process ended, respawning
[    3.832307] init: plymouth-upstart-bridge main process (190) terminated with status 1
[    3.832323] init: plymouth-upstart-bridge main process ended, respawning
[    3.834875] init: plymouth-upstart-bridge main process (192) terminated with status 1
[    3.834888] init: plymouth-upstart-bridge respawning too fast, stopped
[    9.202275] Adding 20970492k swap on /dev/sda5.  Priority:-1 extents:1 across:20970492k FS
[    9.400169] systemd-udevd[293]: starting version 204
[    9.541776] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    9.767833] lp: driver loaded but no devices found
[    9.786934] ppdev: user-space parallel port driver
[    9.791414] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.813545] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.873269] acpi device:00: registered as cooling_device2
[    9.873395] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
[    9.874085] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
[    9.876958] hp_accel: laptop model unknown, using default axes configuration
[    9.886835] lis3lv02d: 8 bits 3DC sensor found
[    9.892436] wmi: Mapper loaded
[    9.893119] acpi device:0a: registered as cooling_device3
[    9.893467] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input13
[    9.893865] snd_hda_intel 0000:00:01.1: irq 48 for MSI/MSI-X
[    9.918634] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input14
[    9.923997] sound hdaudioC1D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[    9.924008] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    9.924011] sound hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[    9.924013] sound hdaudioC1D0:    mono: mono_out=0x0
[    9.924015] sound hdaudioC1D0:    inputs:
[    9.924018] sound hdaudioC1D0:      Internal Mic=0x11
[    9.924021] sound hdaudioC1D0:      Mic=0xc
[    9.927412] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input15
[    9.935148] cfg80211: Calling CRDA to update world regulatory domain
[    9.959482] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
[    9.959595] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input17
[    9.991057] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B06 (\_SB_.PCI0.SMBS.SMBO) (20140424/utaddress-254)
[    9.991068] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.092049] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   10.092054] AMD IOMMUv2 functionality not available on this system
[   10.173046] ath: phy0: ASPM enabled: 0x42
[   10.173052] ath: EEPROM regdomain: 0x60
[   10.173055] ath: EEPROM indicates we should expect a direct regpair map
[   10.173058] ath: Country alpha2 being used: 00
[   10.173059] ath: Regpair used: 0x60
[   10.182736] kvm: Nested Virtualization enabled
[   10.182742] kvm: Nested Paging enabled
[   10.199184] Bluetooth: Core ver 2.19
[   10.199217] NET: Registered protocol family 31
[   10.199219] Bluetooth: HCI device and connection manager initialized
[   10.199228] Bluetooth: HCI socket layer initialized
[   10.199231] Bluetooth: L2CAP socket layer initialized
[   10.199243] Bluetooth: SCO socket layer initialized
[   10.205212] Bluetooth: RFCOMM TTY layer initialized
[   10.205225] Bluetooth: RFCOMM socket layer initialized
[   10.205233] Bluetooth: RFCOMM ver 1.11
[   10.209157] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.209670] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011360000, irq=19
[   10.216186] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.216190] Bluetooth: BNEP filters: protocol multicast
[   10.216200] Bluetooth: BNEP socket layer initialized
[   10.260372] audit: type=1400 audit(1437933953.293:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=505 comm="apparmor_parser"
[   10.260383] audit: type=1400 audit(1437933953.293:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=505 comm="apparmor_parser"
[   10.261030] audit: type=1400 audit(1437933953.293:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=505 comm="apparmor_parser"
[   10.263329] audit: type=1400 audit(1437933953.297:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
[   10.263342] audit: type=1400 audit(1437933953.297:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
[   10.263347] audit: type=1400 audit(1437933953.297:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[   10.263994] audit: type=1400 audit(1437933953.297:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
[   10.264002] audit: type=1400 audit(1437933953.297:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[   10.264346] audit: type=1400 audit(1437933953.297:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[   10.267788] usbcore: registered new interface driver btusb
[   10.361791] init: cups main process (550) killed by HUP signal
[   10.361806] init: cups main process ended, respawning
[   10.632452] init: failsafe main process (605) killed by TERM signal
[   10.683599] cfg80211: World regulatory domain updated:
[   10.683607] cfg80211:  DFS Master region: unset
[   10.683609] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.683613] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.683616] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.683619] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.683621] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.683623] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.768179] input: HP WMI hotkeys as /devices/virtual/input/input18
[   11.011267] media: Linux media interface: v0.10
[   11.016938] Linux video capture interface: v2.00
[   11.033081] audit: type=1400 audit(1437933954.065:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=760 comm="apparmor_parser"
[   11.033343] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (0461:4dc7)
[   11.119890] hp_wmi: Unknown event_id - 0 - 0x0
[   11.119949] pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   11.119964] pci 0000:00:14.4: PCI bridge to [bus 07]
[   11.307218] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input19
[   11.307366] usbcore: registered new interface driver uvcvideo
[   11.307368] USB Video Class driver (1.1.1)
[   11.494590] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.494596] Disabling lock debugging due to kernel taint
[   11.509331] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
[   11.550511] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7226 MBytes.
[   11.550675] <6>[fglrx]   vendor: 1002 device: 9649 revision: 0 count: 1
[   11.551014] <6>[fglrx]   vendor: 1002 device: 6760 revision: 0 count: 2
[   11.551344] <6>[fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   11.552014] <6>[fglrx] ioport: bar 4, base 0x6000, size: 0x100
[   11.552024] pci 0000:01:00.0: enabling device (0000 -> 0003)
[   11.552246] <6>[fglrx] Kernel PAT support is enabled
[   11.552281] <6>[fglrx] module loaded - fglrx 15.20.3 [Jun 22 2015] with 2 minors
[   12.285947] vboxdrv: Found 2 processor cores.
[   12.288216] vboxdrv: fAsync=0 offMin=0x4aa offMax=0x2275
[   12.288367] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   12.288369] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[   12.290952] r8169 0000:02:00.0 eth0: link down
[   12.291618] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.312799] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.322835] vboxpci: IOMMU not found (not registered)
[   13.268300] init: plymouth-splash main process (1161) terminated with status 1
[   13.389769] wlan0: authenticate with c8:3a:35:4d:4b:08
[   13.396041] wlan0: send auth to c8:3a:35:4d:4b:08 (try 1/3)
[   13.397785] wlan0: authenticated
[   13.398856] wlan0: associate with c8:3a:35:4d:4b:08 (try 1/3)
[   13.402743] wlan0: RX AssocResp from c8:3a:35:4d:4b:08 (capab=0x11 status=0 aid=2)
[   13.402838] wlan0: associated
[   13.402883] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.402935] cfg80211: Calling CRDA for country: CN
[   13.406461] ath: EEPROM regdomain: 0x809c
[   13.406467] ath: EEPROM indicates we should expect a country code
[   13.406469] ath: doing EEPROM country->regdmn map search
[   13.406470] ath: country maps to regdmn code: 0x52
[   13.406472] ath: Country alpha2 being used: CN
[   13.406474] ath: Regpair used: 0x52
[   13.406476] ath: regdomain 0x809c dynamically updated by country IE
[   13.406500] cfg80211: Regulatory domain changed to country: CN
[   13.406502] cfg80211:  DFS Master region: unset
[   13.406504] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.406507] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.406510] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[   13.406512] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[   13.406514] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
[   13.406516] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[   22.420326] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   22.420339] pci 0000:00:14.4: PCI bridge to [bus 07]
[   40.427257] audit_printk_skb: 150 callbacks suppressed
[   40.427263] audit: type=1400 audit(1437933983.975:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2351 comm="apparmor_parser"
[   40.427276] audit: type=1400 audit(1437933983.975:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2351 comm="apparmor_parser"
[   40.427828] audit: type=1400 audit(1437933983.975:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2351 comm="apparmor_parser"

```

What could've caused those lines?
```
[   22.420326] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment[   22.420339] pci 0000:00:14.4: PCI bridge to [bus 07]
[   40.427257] audit_printk_skb: 150 callbacks suppressed
[   40.427263] audit: type=1400 audit(1437933983.975:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2351 
```

I'm mainly worried that I misused the AMD vendor driver as I currently got 2 errors after loging. 

The info for the video is:

```
ivan@ivan-HP-ProBook-4535s:~$ sudo lshw | grep -A 11 display[sudo] password for ivan: 
Sorry, try again.
[sudo] password for ivan: 
        *-display
             description: VGA compatible controller
             product: Sumo [Radeon HD 6480G]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:18 memory:b0000000-bfffffff ioport:7000(size=256) memory:d8100000-d813ffff
--
           *-display
                description: VGA compatible controller
                product: Seymour [Radeon HD 6400M/7400M Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:19 memory:c0000000-cfffffff memory:d8000000-d801ffff ioport:6000(size=256) memory:d8020000-d803ffff
ivan@ivan-HP-ProBook-4535s:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6480G]
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
ivan@ivan-HP-ProBook-4535s:~$ dkms status
fglrx-core, 15.200, 3.16.0-44-generic, x86_64: installed
virtualbox, 4.3.10, 3.16.0-44-generic, x86_64: installed

```

From what I see here the fglrx is installed, but how to see if it's working correctly?

This is the syslog for the current run:

```
Jul 26 20:48:11 ivan-HP-ProBook-4535s wpa_supplicant[1081]: wlan0: CTRL-EVENT-SCAN-STARTED Jul 26 20:50:18 ivan-HP-ProBook-4535s colord: device removed: xrandr-default
Jul 26 20:50:18 ivan-HP-ProBook-4535s colord: Profile removed: icc-8047dcbd0521d15201185b4fe16ea653
Jul 26 20:50:19 ivan-HP-ProBook-4535s dbus[495]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 26 20:50:19 ivan-HP-ProBook-4535s dbus[495]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 26 20:50:19 ivan-HP-ProBook-4535s rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="640" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul 26 20:51:53 ivan-HP-ProBook-4535s rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="665" x-info="http://www.rsyslog.com"] start
Jul 26 20:51:53 ivan-HP-ProBook-4535s rsyslogd: rsyslogd's groupid changed to 104
Jul 26 20:51:53 ivan-HP-ProBook-4535s rsyslogd: rsyslogd's userid changed to 101
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Linux version 3.16.0-44-generic (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #59~14.04.1-Ubuntu SMP Tue Jul 7 15:07:27 UTC 2015 (Ubuntu 3.16.0-44.59~14.04.1-generic 3.16.7-ckt14)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-44-generic root=UUID=06bbc19e-b72c-445e-851c-77c80ccf7f12 ro quiet splash nomodeset vt.handoff=7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] KERNEL supported cpus:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Intel GenuineIntel
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   AMD AuthenticAMD
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Centaur CentaurHauls
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008f08cfff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008f08d000-0x000000008f58cfff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008f58d000-0x000000008fbcefff] ACPI NVS
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbcf000-0x000000008fbfefff] ACPI data
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbff000-0x000000008fbfffff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024effffff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] SMBIOS 2.6 present.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] DMI: Hewlett-Packard HP ProBook 4535s/168B, BIOS 68CPC Ver. F.50 07/01/2014
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: No AGP bridge found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: last_pfn = 0x24f000 max_arch_pfn = 0x400000000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR default type: uncachable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   00000-9FFFF write-back
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   A0000-DFFFF uncachable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   E0000-FFFFF write-protect
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR variable ranges enabled:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   1 base 0080000000 mask FFF0000000 write-back
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   2 base 00FFE00000 mask FFFFE00000 write-protect
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   3 base 00FFE10000 mask FFFFFF0000 write-protect
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   4 disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   5 disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   6 disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   7 disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] TOM2: 000000024f000000 aka 9456M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: last_pfn = 0x8fc00 max_arch_pfn = 0x400000000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Using GB pages for direct mapping
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbd000, 0x01fbdfff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbe000, 0x01fbefff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbf000, 0x01fbffff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x24ee00000-0x24effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x24ee00000-0x24effffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fc0000, 0x01fc0fff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x24c000000-0x24edfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x24c000000-0x24edfffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x24bffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x200000000-0x23fffffff] page 1G
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x240000000-0x24bffffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x8f08cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x80000000-0x8effffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x8f000000-0x8f08cfff] page 4k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x8fbff000-0x8fbfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x8fbff000-0x8fbfffff] page 4k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fc1000, 0x01fc1fff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] RAMDISK: [mem 0x35ad4000-0x36d61fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: RSDP 0x00000000000F2F00 000014 (v00 HPQOEM)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: RSDT 0x000000008FBFE038 000044 (v01 HPQOEM SLIC-MPC 00000003      01000013)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: FACP 0x000000008FBFD000 000074 (v01 HPQOEM 168B     00000003 HP   00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20140424/tbfadt-649)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: DSDT 0x000000008FBD7000 0230B2 (v01 HPQOEM 168B     00000001 INTL 20060912)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: FACS 0x000000008FB8F000 000040
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: APIC 0x000000008FBFC000 000084 (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: MCFG 0x000000008FBFB000 00003C (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: HPET 0x000000008FBD4000 000038 (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD3000 00072C (v01 AMD    POWERNOW 00000001 AMD  00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD1000 00193D (v02 AMD    ALIB     00000001 MSFT 04000000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD0000 00078F (v01 HP     AMDSGTBL 00000001 INTL 20060912)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBCF000 000325 (v01 HP     HPZPODDT 00000001 INTL 20060912)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] No NUMA configuration found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x24effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   NODE_DATA [mem 0x24eff9000-0x24effdfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246e00000-ffff88024e5fffff] on node 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Zone ranges:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal   [mem 0x100000000-0x24effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Movable zone start for each node
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Early memory node ranges
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x00100000-0x8f08cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x8fbff000-0x8fbfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x100000000-0x24effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] On node 0 totalpages: 1957931
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 21 pages reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32 zone: 9091 pages used for memmap
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32 zone: 581774 pages, LIFO batch:31
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal zone: 21440 pages used for memmap
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal zone: 1372160 pages, LIFO batch:31
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] nr_irqs_gsi: 40
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8f08d000-0x8f58cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8f58d000-0x8fbcefff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8fbcf000-0x8fbfefff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8fc00000-0xdfffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfedfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffdfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: [mem 0x8fc00000-0xdfffffff] available for PCI devices
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88024ec00000 s81408 r8192 d20992 u524288
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] pcpu-alloc: s81408 r8192 d20992 u524288 alloc=1*2097152
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1927315
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Policy zone: Normal
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-44-generic root=UUID=06bbc19e-b72c-445e-851c-77c80ccf7f12 ro quiet splash nomodeset vt.handoff=7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: Checking aperture...
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: No AGP bridge found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Memory: 7606856K/7831724K available (7629K kernel code, 1131K rwdata, 3616K rodata, 1352K init, 1300K bss, 224868K reserved)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Hierarchical RCU implementation.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	Offload RCU callbacks from all CPUs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Console: colour dummy device 80x25
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] console [tty0] enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] allocated 31457280 bytes of page_cgroup
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] hpet clockevent registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] tsc: Detected 1896.422 MHz processor
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000051] Calibrating delay loop (skipped), value calculated using timer frequency.. 3792.84 BogoMIPS (lpj=7585688)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000056] pid_max: default: 32768 minimum: 301
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000065] ACPI: Core revision 20140424
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.013537] ACPI: All ACPI Tables successfully acquired
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.047861] Security Framework initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.047883] AppArmor: AppArmor initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.047885] Yama: becoming mindful.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.048662] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.051541] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.052786] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.052800] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053157] Initializing cgroup subsys memory
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053189] Initializing cgroup subsys devices
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053197] Initializing cgroup subsys freezer
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053201] Initializing cgroup subsys net_cls
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053207] Initializing cgroup subsys blkio
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053213] Initializing cgroup subsys perf_event
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053216] Initializing cgroup subsys net_prio
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053225] Initializing cgroup subsys hugetlb
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053253] tseg: 008fc00000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053256] CPU: Physical Processor ID: 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053257] CPU: Processor Core ID: 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053259] mce: CPU supports 6 MCE banks
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053271] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053271] Last level dTLB entries: 4KB 1024, 2MB 128, 4MB 64, 1GB 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053271] tlb_flushall_shift: 6
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053443] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.055063] ftrace: allocating 29259 entries in 115 pages
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.076667] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.116359] smpboot: CPU0: AMD A4-3305M APU with Radeon(tm) HD Graphics (fam: 12, model: 01, stepping: 00)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220987] Performance Events: AMD PMU driver.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220991] ... version:                0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220993] ... bit width:              48
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220994] ... generic registers:      4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220996] ... value mask:             0000ffffffffffff
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220997] ... max period:             00007fffffffffff
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220998] ... fixed-purpose events:   0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.221000] ... event mask:             000000000000000f
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.223297] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.223411] x86: Booting SMP configuration:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.223413] .... node  #0, CPUs:      #1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.236554] x86: Booted up 1 node, 2 CPUs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.236557] smpboot: Total of 2 processors activated (7585.68 BogoMIPS)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.237312] devtmpfs: initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242986] evm: security.selinux
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242989] evm: security.SMACK64
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242990] evm: security.SMACK64EXEC
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242992] evm: security.SMACK64TRANSMUTE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242993] evm: security.SMACK64MMAP
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242994] evm: security.ima
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242995] evm: security.capability
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.243154] PM: Registering ACPI NVS region [mem 0x8f58d000-0x8fbcefff] (6561792 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.244694] pinctrl core: initialized pinctrl subsystem
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.244826] regulator-dummy: no parameters
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.244909] RTC time: 20:51:43, date: 07/26/15
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.244983] NET: Registered protocol family 16
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245215] cpuidle: using governor ladder
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245218] cpuidle: using governor menu
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245434] ACPI: bus type PCI registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245437] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245590] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245594] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246174] PCI: Using configuration type 1 for base access
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246491] mtrr: your CPUs had inconsistent fixed MTRR settings
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246493] mtrr: your CPUs had inconsistent variable MTRR settings
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246494] mtrr: probably your BIOS does not setup all CPUs.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246495] mtrr: corrected configuration.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.250354] ACPI: Added _OSI(Module Device)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.250359] ACPI: Added _OSI(Processor Device)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.250361] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.250363] ACPI: Added _OSI(Processor Aggregator Device)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437278] ACPI: Interpreter enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437297] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437303] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437320] ACPI: (supports S0 S3 S4 S5)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437321] ACPI: Using IOAPIC for interrupt routing
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437554] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.440139] ACPI: Power Resource [APPR] (off)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.445946] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.445954] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446134] acpi PNP0A08:00: _OSC: platform does not support [PCIeCapability]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446247] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446250] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446252] acpi PNP0A08:00: _OSC: platform willing to grant [PCIeHotplug PME AER]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446254] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446382] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cf1ff])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446386] acpi PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000d3fff] (conflicts with Adapter ROM [mem 0x000cf800-0x000d07ff])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446640] PCI host bridge to bus 0000:00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446644] pci_bus 0000:00: root bus resource [bus 00-ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446647] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446649] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446652] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446655] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446657] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446660] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446662] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446665] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446667] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446670] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446672] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446675] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446677] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446680] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446682] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xdfffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446685] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfffdffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446695] pci 0000:00:00.0: [1022:1705] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446805] pci 0000:00:01.0: [1002:9649] type 00 class 0x030000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446818] pci 0000:00:01.0: reg 0x10: [mem 0xb0000000-0xbfffffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446826] pci 0000:00:01.0: reg 0x14: [io  0x7000-0x70ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446833] pci 0000:00:01.0: reg 0x18: [mem 0xd8100000-0xd813ffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446883] pci 0000:00:01.0: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446948] pci 0000:00:01.1: [1002:1714] type 00 class 0x040300
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446958] pci 0000:00:01.1: reg 0x10: [mem 0xd8144000-0xd8147fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447013] pci 0000:00:01.1: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447125] pci 0000:00:03.0: [1022:1708] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447185] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447259] pci 0000:00:04.0: [1022:1709] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447319] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447357] pci 0000:00:04.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447397] pci 0000:00:05.0: [1022:170a] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447456] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447493] pci 0000:00:05.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447583] pci 0000:00:07.0: [1022:170c] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447647] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447696] pci 0000:00:07.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447817] pci 0000:00:10.0: [1022:7812] type 00 class 0x0c0330
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447841] pci 0000:00:10.0: reg 0x10: [mem 0xd8148000-0xd8149fff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447951] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447997] pci 0000:00:10.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448097] pci 0000:00:10.1: [1022:7812] type 00 class 0x0c0330
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448122] pci 0000:00:10.1: reg 0x10: [mem 0xd814a000-0xd814bfff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448240] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448285] pci 0000:00:10.1: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448384] pci 0000:00:11.0: [1022:7801] type 00 class 0x010601
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448405] pci 0000:00:11.0: reg 0x10: [io  0x7118-0x711f]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448416] pci 0000:00:11.0: reg 0x14: [io  0x7124-0x7127]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448426] pci 0000:00:11.0: reg 0x18: [io  0x7110-0x7117]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448437] pci 0000:00:11.0: reg 0x1c: [io  0x7120-0x7123]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448447] pci 0000:00:11.0: reg 0x20: [io  0x7100-0x710f]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448458] pci 0000:00:11.0: reg 0x24: [mem 0xd8151000-0xd81517ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448614] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448629] pci 0000:00:12.0: reg 0x10: [mem 0xd8150000-0xd8150fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448733] pci 0000:00:12.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448778] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448799] pci 0000:00:12.2: reg 0x10: [mem 0xd814f000-0xd814f0ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448894] pci 0000:00:12.2: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448896] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448938] pci 0000:00:12.2: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449043] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449058] pci 0000:00:13.0: reg 0x10: [mem 0xd814e000-0xd814efff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449158] pci 0000:00:13.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449260] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449283] pci 0000:00:13.2: reg 0x10: [mem 0xd814d000-0xd814d0ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449378] pci 0000:00:13.2: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449380] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449426] pci 0000:00:13.2: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449527] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449709] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449732] pci 0000:00:14.2: reg 0x10: [mem 0xd8140000-0xd8143fff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449805] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450006] pci 0000:00:14.2: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450089] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450266] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450405] pci 0000:00:14.5: [1022:7809] type 00 class 0x0c0310
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450424] pci 0000:00:14.5: reg 0x10: [mem 0xd814c000-0xd814cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450603] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450704] pci 0000:00:15.0: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450745] pci 0000:00:15.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450851] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450950] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451043] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451138] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451236] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451311] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451386] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451462] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451676] pci 0000:01:00.0: [1002:6760] type 00 class 0x030000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451694] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451707] pci 0000:01:00.0: reg 0x18: [mem 0xd8000000-0xd801ffff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451714] pci 0000:01:00.0: reg 0x20: [io  0x6000-0x60ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451728] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451776] pci 0000:01:00.0: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457198] pci 0000:00:03.0: PCI bridge to [bus 01]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457218] pci 0000:00:03.0:   bridge window [io  0x6000-0x6fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457228] pci 0000:00:03.0:   bridge window [mem 0xd8000000-0xd80fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457239] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457391] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457411] pci 0000:02:00.0: reg 0x10: [io  0x5000-0x50ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457436] pci 0000:02:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457452] pci 0000:02:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457533] pci 0000:02:00.0: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457535] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457569] pci 0000:02:00.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465202] pci 0000:00:04.0: PCI bridge to [bus 02]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465222] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465231] pci 0000:00:04.0:   bridge window [mem 0xd7000000-0xd7ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465243] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465418] pci 0000:03:00.0: [197b:2392] type 00 class 0x088000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465441] pci 0000:03:00.0: reg 0x10: [mem 0xd6003000-0xd60030ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465507] pci 0000:03:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465645] pci 0000:03:00.2: [197b:2391] type 00 class 0x080501
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465665] pci 0000:03:00.2: reg 0x10: [mem 0xd6002000-0xd60020ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465850] pci 0000:03:00.3: [197b:2393] type 00 class 0x088000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465870] pci 0000:03:00.3: reg 0x10: [mem 0xd6001000-0xd60010ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473220] pci 0000:00:05.0: PCI bridge to [bus 03]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473241] pci 0000:00:05.0:   bridge window [io  0x4000-0x4fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473247] pci 0000:00:05.0:   bridge window [mem 0xd6000000-0xd6ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473253] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473395] pci 0000:04:00.0: [168c:002b] type 00 class 0x028000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473420] pci 0000:04:00.0: reg 0x10: [mem 0xd5000000-0xd500ffff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473530] pci 0000:04:00.0: supports D1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473532] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481202] pci 0000:00:07.0: PCI bridge to [bus 04-06]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481223] pci 0000:00:07.0:   bridge window [io  0x3000-0x3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481232] pci 0000:00:07.0:   bridge window [mem 0xd5000000-0xd5ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481244] pci 0000:00:07.0:   bridge window [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481450] pci 0000:00:14.4: PCI bridge to [bus 07] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481461] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481463] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481465] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481467] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481469] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481478] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481480] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481482] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481484] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481486] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481488] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481489] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481491] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481493] pci 0000:00:14.4:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481495] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xdfffffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481497] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfffdffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481674] acpiphp: Slot [1] registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481702] pci 0000:00:15.0: PCI bridge to [bus 08]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481709] pci 0000:00:15.0:   bridge window [io  0x2000-0x2fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481713] pci 0000:00:15.0:   bridge window [mem 0xd4000000-0xd4ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481720] pci 0000:00:15.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.482807] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.482880] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.482953] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483025] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483083] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483129] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483175] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483220] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483341] ACPI: Enabled 5 GPEs in block 00 to 1F
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483393] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483690] vgaarb: setting as boot device: PCI:0000:00:01.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483695] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483707] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483710] vgaarb: loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483712] vgaarb: bridge control possible 0000:01:00.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483713] vgaarb: no bridge control possible 0000:00:01.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484012] SCSI subsystem initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484090] libata version 3.00 loaded.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484116] ACPI: bus type USB registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484138] usbcore: registered new interface driver usbfs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484147] usbcore: registered new interface driver hub
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484334] usbcore: registered new device driver usb
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484670] PCI: Using ACPI for IRQ routing
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494109] PCI: pci_cache_line_size set to 64 bytes
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494216] Expanded resource reserved due to conflict with PCI Bus 0000:00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494218] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494221] e820: reserve RAM buffer [mem 0x8f08d000-0x8fffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494224] e820: reserve RAM buffer [mem 0x8fc00000-0x8fffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494226] e820: reserve RAM buffer [mem 0x24f000000-0x24fffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494387] NetLabel: Initializing
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494389] NetLabel:  domain hash size = 128
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494390] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494404] NetLabel:  unlabeled traffic allowed by default
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494658] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494664] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.496821] Switched to clocksource hpet
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.503818] AppArmor: AppArmor Filesystem Enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.503862] pnp: PnP ACPI init
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.503883] ACPI: bus type PNP registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504007] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504010] system 00:00: [mem 0xfeb00000-0xfeb00fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504015] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504017] system 00:00: [mem 0xfec10000-0xfec10fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504020] system 00:00: [mem 0xfed61000-0xfed61fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504022] system 00:00: [mem 0xfed80000-0xfed80fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504024] system 00:00: [mem 0xfed81000-0xfed81fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504026] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504030] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504263] system 00:01: [io  0x0400-0x04cf] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504265] system 00:01: [io  0x04d0-0x04d1] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504267] system 00:01: [io  0x04d6] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504270] system 00:01: [io  0x0680-0x06ff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504272] system 00:01: [io  0x077a] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504274] system 00:01: [io  0x0c00-0x0c01] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504276] system 00:01: [io  0x0c14] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504278] system 00:01: [io  0x0c50-0x0c52] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504279] system 00:01: [io  0x0c6c] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504281] system 00:01: [io  0x0c6f] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504283] system 00:01: [io  0x0cd0-0x0cdb] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504285] system 00:01: [io  0x0220-0x0227] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504287] system 00:01: [io  0x0260-0x0273] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504289] system 00:01: [io  0x0800] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504291] system 00:01: [io  0x0804] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504293] system 00:01: [io  0x087f] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504295] system 00:01: [io  0x0cdc-0x0cdf] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504298] system 00:01: [io  0x0b00-0x0b0f] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504300] system 00:01: [io  0x0b20-0x0b3f] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504302] system 00:01: [io  0x0200-0x027f] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504304] system 00:01: [io  0x0840-0x0847] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504307] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504398] system 00:02: [mem 0x00000000-0x0009ffff] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504402] system 00:02: [mem 0x00100000-0xafffffff] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504405] system 00:02: [mem 0xffe00000-0xffffffff] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504408] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504520] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504644] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504685] pnp 00:05: Plug and Play ACPI device, IDs SYN0189 SYN0100 SYN0002 PNP0f13 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.505086] pnp: PnP ACPI: found 6 devices
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.505087] ACPI: bus type PNP unregistered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514688] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514694] pci 0000:03:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514790] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8020000-0xd803ffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514793] pci 0000:00:03.0: PCI bridge to [bus 01]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514796] pci 0000:00:03.0:   bridge window [io  0x6000-0x6fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514800] pci 0000:00:03.0:   bridge window [mem 0xd8000000-0xd80fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514804] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514811] pci 0000:00:04.0: PCI bridge to [bus 02]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514815] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514819] pci 0000:00:04.0:   bridge window [mem 0xd7000000-0xd7ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514823] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514830] pci 0000:03:00.0: BAR 6: assigned [mem 0xd6010000-0xd601ffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514833] pci 0000:00:05.0: PCI bridge to [bus 03]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514836] pci 0000:00:05.0:   bridge window [io  0x4000-0x4fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514840] pci 0000:00:05.0:   bridge window [mem 0xd6000000-0xd6ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514844] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514850] pci 0000:00:07.0: PCI bridge to [bus 04-06]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514853] pci 0000:00:07.0:   bridge window [io  0x3000-0x3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514857] pci 0000:00:07.0:   bridge window [mem 0xd5000000-0xd5ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514861] pci 0000:00:07.0:   bridge window [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514866] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514928] pci 0000:00:15.0: PCI bridge to [bus 08]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514931] pci 0000:00:15.0:   bridge window [io  0x2000-0x2fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514937] pci 0000:00:15.0:   bridge window [mem 0xd4000000-0xd4ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514942] pci 0000:00:15.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514950] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514953] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514955] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514958] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514960] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514962] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514965] pci_bus 0000:00: resource 10 [mem 0x000d4000-0x000d7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514967] pci_bus 0000:00: resource 11 [mem 0x000d8000-0x000dbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514969] pci_bus 0000:00: resource 12 [mem 0x000dc000-0x000dffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514972] pci_bus 0000:00: resource 13 [mem 0x000e0000-0x000e3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514974] pci_bus 0000:00: resource 14 [mem 0x000e4000-0x000e7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514977] pci_bus 0000:00: resource 15 [mem 0x000e8000-0x000ebfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514979] pci_bus 0000:00: resource 16 [mem 0x000ec000-0x000effff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514981] pci_bus 0000:00: resource 17 [mem 0x000f0000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514984] pci_bus 0000:00: resource 18 [mem 0xb0000000-0xdfffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514986] pci_bus 0000:00: resource 19 [mem 0xf0000000-0xfffdffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514989] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514991] pci_bus 0000:01: resource 1 [mem 0xd8000000-0xd80fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514994] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514997] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514999] pci_bus 0000:02: resource 1 [mem 0xd7000000-0xd7ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515001] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515004] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515006] pci_bus 0000:03: resource 1 [mem 0xd6000000-0xd6ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515009] pci_bus 0000:03: resource 2 [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515011] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515014] pci_bus 0000:04: resource 1 [mem 0xd5000000-0xd5ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515016] pci_bus 0000:04: resource 2 [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515019] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515022] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515024] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515026] pci_bus 0000:07: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515029] pci_bus 0000:07: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515031] pci_bus 0000:07: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515034] pci_bus 0000:07: resource 10 [mem 0x000d4000-0x000d7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515036] pci_bus 0000:07: resource 11 [mem 0x000d8000-0x000dbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515039] pci_bus 0000:07: resource 12 [mem 0x000dc000-0x000dffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515041] pci_bus 0000:07: resource 13 [mem 0x000e0000-0x000e3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515043] pci_bus 0000:07: resource 14 [mem 0x000e4000-0x000e7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515046] pci_bus 0000:07: resource 15 [mem 0x000e8000-0x000ebfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515048] pci_bus 0000:07: resource 16 [mem 0x000ec000-0x000effff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515050] pci_bus 0000:07: resource 17 [mem 0x000f0000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515053] pci_bus 0000:07: resource 18 [mem 0xb0000000-0xdfffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515055] pci_bus 0000:07: resource 19 [mem 0xf0000000-0xfffdffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515058] pci_bus 0000:08: resource 0 [io  0x2000-0x2fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515060] pci_bus 0000:08: resource 1 [mem 0xd4000000-0xd4ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515063] pci_bus 0000:08: resource 2 [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515104] NET: Registered protocol family 2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515358] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515582] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515948] TCP: Hash tables configured (established 65536 bind 65536)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515997] TCP: reno registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516013] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516083] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516216] NET: Registered protocol family 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516238] pci 0000:00:01.0: Video device with shadowed ROM
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516302] pci 0000:00:10.0: enabling device (0000 -> 0002)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.637753] PCI: CLS mismatch (64 != 32), using 64 bytes
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.693403] Trying to unpack rootfs image as initramfs...
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071321] Freeing initrd memory: 19000K (ffff880035ad4000 - ffff880036d62000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071359] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071362] software IO TLB [mem 0x8b08d000-0x8f08d000] (64MB) mapped at [ffff88008b08d000-ffff88008f08cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071668] microcode: CPU0: patch_level=0x03000027
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071678] microcode: CPU1: patch_level=0x03000027
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071822] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071835] LVT offset 0 assigned for vector 0x400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071859] perf: AMD IBS detected (0x000000ff)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071907] Scanning for low memory corruption every 60 seconds
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072279] futex hash table entries: 1024 (order: 4, 65536 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072299] Initialise system trusted keyring
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072322] audit: initializing netlink subsys (disabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072342] audit: type=2000 audit(1437943903.932:1): initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072856] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.074590] zpool: loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.074593] zbud: loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.074919] VFS: Disk quotas dquot_6.5.2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.074971] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.075648] fuse init (API version 7.23)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.075814] msgmni has been set to 14894
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.075888] Key type big_key registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076652] Key type asymmetric registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076657] Asymmetric key parser 'x509' registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076707] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076803] io scheduler noop registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076806] io scheduler deadline registered (default)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076858] io scheduler cfq registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078279] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078298] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078359] vesafb: mode is 1366x768x32, linelength=5504, pages=0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078361] vesafb: scrolling: redraw
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078363] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078667] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90010f00000, using 4160k, total 4160k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078999] Console: switching to colour frame buffer device 170x48
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079022] fb0: VESA VGA frame buffer device
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079395] ACPI: AC Adapter [AC] (on-line)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079674] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079679] ACPI: Sleep Button [SLPB]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079730] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079801] ACPI: Lid Switch [LID]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079852] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079855] ACPI: Power Button [PWRF]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.080013] ACPI: acpi_idle registered with cpuidle
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.109997] thermal LNXTHERM:00: registered as thermal_zone0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.110003] ACPI: Thermal Zone [CPUZ] (71 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.133863] thermal LNXTHERM:01: registered as thermal_zone1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.133868] ACPI: Thermal Zone [GFXZ] (57 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.148659] thermal LNXTHERM:02: registered as thermal_zone2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.148664] ACPI: Thermal Zone [EXTZ] (43 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.163591] thermal LNXTHERM:03: registered as thermal_zone3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.163596] ACPI: Thermal Zone [LOCZ] (54 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.178519] thermal LNXTHERM:04: registered as thermal_zone4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.178524] ACPI: Thermal Zone [BATZ] (30 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.178584] GHES: HEST is not enabled!
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.179037] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.182101] Linux agpgart interface v0.103
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.184758] brd: module loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186114] loop: module loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186402] libphy: Fixed MDIO Bus: probed
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186405] tun: Universal TUN/TAP device driver, 1.6
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186406] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186485] PPP generic driver version 2.4.2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186595] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186602] ehci-pci: EHCI PCI platform driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186971] QUIRK: Enable AMD PLL fix
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187007] ehci-pci 0000:00:12.2: EHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187014] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187020] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187033] ehci-pci 0000:00:12.2: debug port 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187082] ehci-pci 0000:00:12.2: irq 17, io mem 0xd814f000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197001] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197165] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197167] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197170] usb usb1: Product: EHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197171] usb usb1: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197173] usb usb1: SerialNumber: 0000:00:12.2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197469] hub 1-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197475] hub 1-0:1.0: 5 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198042] ehci-pci 0000:00:13.2: EHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198048] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198053] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198065] ehci-pci 0000:00:13.2: debug port 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198098] ehci-pci 0000:00:13.2: irq 17, io mem 0xd814d000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209001] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209128] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209130] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209133] usb usb2: Product: EHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209134] usb usb2: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209136] usb usb2: SerialNumber: 0000:00:13.2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209385] hub 2-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209392] hub 2-0:1.0: 5 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209721] ehci-platform: EHCI generic platform driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209738] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209745] ohci-pci: OHCI PCI platform driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.210022] ohci-pci 0000:00:12.0: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.210028] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.210062] ohci-pci 0000:00:12.0: irq 18, io mem 0xd8150000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.223415] ACPI: Battery Slot [BAT0] (battery present)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269052] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269054] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269056] usb usb3: Product: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269058] usb usb3: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269059] usb usb3: SerialNumber: 0000:00:12.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269440] hub 3-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269499] hub 3-0:1.0: 5 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269998] ohci-pci 0000:00:13.0: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.270006] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.270040] ohci-pci 0000:00:13.0: irq 18, io mem 0xd814e000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329265] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329270] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329272] usb usb4: Product: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329274] usb usb4: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329276] usb usb4: SerialNumber: 0000:00:13.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329674] hub 4-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329735] hub 4-0:1.0: 5 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.330192] ohci-pci 0000:00:14.5: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.330199] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.330231] ohci-pci 0000:00:14.5: irq 18, io mem 0xd814c000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389267] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389272] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389274] usb usb5: Product: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389276] usb usb5: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389277] usb usb5: SerialNumber: 0000:00:14.5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389675] hub 5-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389734] hub 5-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389911] ohci-platform: OHCI generic platform driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389929] uhci_hcd: USB Universal Host Controller Interface driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390213] xhci_hcd 0000:00:10.0: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390221] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390440] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390444] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390447] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390539] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390541] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390543] usb usb6: Product: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390545] usb usb6: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390546] usb usb6: SerialNumber: 0000:00:10.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390889] hub 6-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390947] hub 6-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.391142] xhci_hcd 0000:00:10.0: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.391146] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393863] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393865] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393867] usb usb7: Product: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393869] usb usb7: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393870] usb usb7: SerialNumber: 0000:00:10.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394082] hub 7-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394139] hub 7-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394629] xhci_hcd 0000:00:10.1: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394636] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394858] xhci_hcd 0000:00:10.1: irq 43 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394861] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394864] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394951] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394953] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394955] usb usb8: Product: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394957] usb usb8: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394959] usb usb8: SerialNumber: 0000:00:10.1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.395296] hub 8-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.395354] hub 8-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.395549] xhci_hcd 0000:00:10.1: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.395554] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398274] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398276] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398279] usb usb9: Product: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398281] usb usb9: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398283] usb usb9: SerialNumber: 0000:00:10.1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398567] hub 9-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398627] hub 9-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398851] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.401268] i8042: Detected active multiplexing controller, rev 1.1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402420] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402425] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402460] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402489] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402510] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402995] mousedev: PS/2 mouse device common for all mice
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403410] rtc_cmos 00:03: RTC can wake from S4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403546] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403577] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403657] device-mapper: uevent: version 1.0.3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403766] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403789] ledtrig-cpu: registered to indicate activity on CPUs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403889] TCP: cubic registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.404006] NET: Registered protocol family 10
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.404332] NET: Registered protocol family 17
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.404356] Key type dns_resolver registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.404859] Loading compiled-in X.509 certificates
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.406000] Loaded X.509 cert 'Magrathea: Glacier signing key: 4b6de31c0185e45a0c0d73ca36f8fa02edc6253a'
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.406017] registered taskstats version 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.408609] Key type trusted registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.413393] Key type encrypted registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.413408] AppArmor: AppArmor sha1 policy hashing enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.413412] ima: No TPM chip found, activating TPM-bypass!
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.413446] evm: HMAC attrs: 0x1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414024]   Magic number: 7:422:903
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414038] usb usb2-port4: hash matches
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414179] rtc_cmos 00:03: setting system clock to 2015-07-26 20:51:44 UTC (1437943904)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414384] acpi-cpufreq: overriding BIOS provided _PSD data
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414484] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414485] EDD information not available.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414558] PM: Hibernation image not present or could not be loaded.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.416194] Freeing unused kernel memory: 1352K (ffffffff81d1c000 - ffffffff81e6e000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.416198] Write protecting the kernel read-only data: 12288k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.418271] Freeing unused kernel memory: 552K (ffff880001776000 - ffff880001800000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.419980] Freeing unused kernel memory: 480K (ffff880001b88000 - ffff880001c00000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.427704] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.439467] systemd-udevd[103]: starting version 204
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.468125] sdhci: Secure Digital Host Controller Interface driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.468129] sdhci: Copyright(c) Pierre Ossman
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471379] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471394] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471687] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471842] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2392] (rev 30)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471910] r8169 0000:02:00.0 eth0: RTL8168e/8111e at 0xffffc9000003a000, e4:11:5b:40:3b:c6, XID 0c200000 IRQ 46
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471912] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.472005] mmc0: no vqmmc regulator found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.472007] mmc0: no vmmc regulator found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.475687] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.475718] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 30)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.475883] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.484362] ahci 0000:00:11.0: version 3.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.484698] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.484756] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.484761] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.486294] scsi0 : ahci
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.486468] scsi1 : ahci
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.486577] ata1: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151100 irq 47
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.486580] ata2: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151180 irq 47
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.509064] usb 1-5: new high-speed USB device number 2 using ehci-pci
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.689999] usb 1-5: New USB device found, idVendor=0461, idProduct=4dc7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.690011] usb 1-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.690018] usb 1-5: Product: HP HD Webcam [Fixed]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.690023] usb 1-5: Manufacturer: Primax Electronics Ltd.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.690027] usb 1-5: SerialNumber: PMX02
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.977137] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.977197] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.978035] ata1.00: ATA-8: TOSHIBA MK6476GSX, GS001C, max UDMA/100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.978040] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.979023] ata1.00: configured for UDMA/100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.979497] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6476GS 1C   PQ: 0 ANSI: 5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.979937] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.979977] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.980047] sd 0:0:0:0: [sda] Write Protect is off
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.980053] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.980073] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.983114] ata2.00: ATAPI: hp       DVDRAM GT50N, MP00, max UDMA/100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.988620] ata2.00: configured for UDMA/100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.994211] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT50N     MP00 PQ: 0 ANSI: 5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.014164] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.014175] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.014366] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.014429] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.039093]  sda: sda1 sda2 sda3 sda4 < sda5 >
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.039808] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.069129] tsc: Refined TSC clocksource calibration: 1896.550 MHz
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.229423] usb 4-5: new full-speed USB device number 2 using ohci-pci
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.389480] usb 4-5: New USB device found, idVendor=0cf3, idProduct=3005
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.389485] usb 4-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.402110] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..4876]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.478410] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x640000/0xa0400, board id: 1397, fw id: 780218
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.485932] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.526780] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.069684] Switched to clocksource tsc
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.155940] random: init urandom read with 105 bits of entropy available
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.641401] random: nonblocking pool is initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.714282] init: plymouth-upstart-bridge main process (164) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.714299] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.717777] init: plymouth-upstart-bridge main process (178) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.717790] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.720152] init: plymouth-upstart-bridge main process (180) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.720164] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.723461] init: plymouth-upstart-bridge main process (181) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.723474] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.725866] init: plymouth-upstart-bridge main process (183) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.725880] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.729155] init: plymouth-upstart-bridge main process (184) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.729168] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.731653] init: plymouth-upstart-bridge main process (186) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.731670] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.734916] init: plymouth-upstart-bridge main process (187) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.734933] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.737669] init: plymouth-upstart-bridge main process (189) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.737681] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.740903] init: plymouth-upstart-bridge main process (190) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.740919] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.743207] init: plymouth-upstart-bridge main process (192) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.743218] init: plymouth-upstart-bridge respawning too fast, stopped
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.123721] Adding 20970492k swap on /dev/sda5.  Priority:-1 extents:1 across:20970492k FS
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.309165] systemd-udevd[292]: starting version 204
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.511447] lp: driver loaded but no devices found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.522256] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.532983] ppdev: user-space parallel port driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.542317] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.597707] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.597712] AMD IOMMUv2 functionality not available on this system
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.607875] acpi device:00: registered as cooling_device2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.608032] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.608262] hp_accel: laptop model unknown, using default axes configuration
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.608827] lis3lv02d: 8 bits 3DC sensor found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.618645] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.619478] acpi device:0a: registered as cooling_device3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.619629] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input13
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.633438] wmi: Mapper loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.647251] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input14
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.672303] cfg80211: Calling CRDA to update world regulatory domain
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.738476] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B06 (\_SB_.PCI0.SMBS.SMBO) (20140424/utaddress-254)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.738487] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.770488] snd_hda_intel 0000:00:01.1: irq 48 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793515] ath: phy0: ASPM enabled: 0x42
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793521] ath: EEPROM regdomain: 0x60
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793523] ath: EEPROM indicates we should expect a direct regpair map
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793526] ath: Country alpha2 being used: 00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793528] ath: Regpair used: 0x60
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.801655] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input15
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804318] sound hdaudioC1D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804325] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804328] sound hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804331] sound hdaudioC1D0:    mono: mono_out=0x0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804333] sound hdaudioC1D0:    inputs:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804336] sound hdaudioC1D0:      Internal Mic=0x11
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804338] sound hdaudioC1D0:      Mic=0xc
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.806686] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.807570] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90010ea0000, irq=19
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.839329] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.839427] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input17
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886139] Bluetooth: Core ver 2.19
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886212] NET: Registered protocol family 31
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886214] Bluetooth: HCI device and connection manager initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886223] Bluetooth: HCI socket layer initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886226] Bluetooth: L2CAP socket layer initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886242] Bluetooth: SCO socket layer initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.920396] kvm: Nested Virtualization enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.920402] kvm: Nested Paging enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.928453] usbcore: registered new interface driver btusb
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026002] audit: type=1400 audit(1437933113.105:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026014] audit: type=1400 audit(1437933113.105:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026019] audit: type=1400 audit(1437933113.105:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026726] audit: type=1400 audit(1437933113.109:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026734] audit: type=1400 audit(1437933113.109:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.027086] audit: type=1400 audit(1437933113.109:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.027373] audit: type=1400 audit(1437933113.109:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=452 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.027388] audit: type=1400 audit(1437933113.109:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.027395] audit: type=1400 audit(1437933113.109:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.028102] audit: type=1400 audit(1437933113.109:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.031461] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.338572] input: HP WMI hotkeys as /devices/virtual/input/input18
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.382577] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.382583] Disabling lock debugging due to kernel taint
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.397199] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416105] cfg80211: World regulatory domain updated:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416112] cfg80211:  DFS Master region: unset
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416114] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416117] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416119] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416120] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416122] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416124] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.418340] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7226 MBytes.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.418525] <6>[fglrx]   vendor: 1002 device: 9649 revision: 0 count: 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.418782] <6>[fglrx]   vendor: 1002 device: 6760 revision: 0 count: 2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.419036] <6>[fglrx] ioport: bar 1, base 0x7000, size: 0x100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.464783] media: Linux media interface: v0.10
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.470210] Linux video capture interface: v2.00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.482959] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (0461:4dc7)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.491185] <6>[fglrx] ioport: bar 4, base 0x6000, size: 0x100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.491199] pci 0000:01:00.0: enabling device (0000 -> 0003)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.519303] <6>[fglrx] Kernel PAT support is enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.519337] <6>[fglrx] module loaded - fglrx 15.20.3 [Jun 22 2015] with 2 minors
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.663145] init: failsafe main process (623) killed by TERM signal
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.755841] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input19
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.756068] usbcore: registered new interface driver uvcvideo
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.756072] USB Video Class driver (1.1.1)
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   10.918400] Bluetooth: RFCOMM TTY layer initialized
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   10.918416] Bluetooth: RFCOMM socket layer initialized
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   10.918426] Bluetooth: RFCOMM ver 1.11
Jul 26 20:51:54 ivan-HP-ProBook-4535s rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.034808] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.034821] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.078772] hp_wmi: Unknown event_id - 0 - 0x0
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.078829] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.078843] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Bluetooth daemon 4.101
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Starting SDP server
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: DIS cannot start: GATT is disabled
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init deviceinfo plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init proximity plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init time plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init alert plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init thermometer plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init gatt_example plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Bluetooth Management interface initialized
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.220375] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.220380] Bluetooth: BNEP filters: protocol multicast
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.220388] Bluetooth: BNEP socket layer initialized
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.377490] init: cups main process (685) killed by HUP signal
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.377503] init: cups main process ended, respawning
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Successfully dropped root privileges.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: avahi-daemon 0.6.31 starting up.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Successfully called chroot().
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Successfully dropped remaining capabilities.
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Adapter /org/bluez/697/hci0 has been enabled
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: No service file found in /etc/avahi/services.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Network interface enumeration completed.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Server startup complete. Host name is ivan-HP-ProBook-4535s.local. Local service cookie is 2001102376.
Jul 26 20:51:54 ivan-HP-ProBook-4535s ModemManager[673]: <info>  ModemManager (version 1.0.0) starting...
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager (version 0.9.8.8) is starting...
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WEXT support is enabled
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> DNS: loaded plugin dnsmasq
Jul 26 20:51:54 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul 26 20:51:54 ivan-HP-ProBook-4535s polkitd[811]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jul 26 20:51:54 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: init!
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: update_system_hostname
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:       interface-parser: parsing file /etc/network/interfaces
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:       interface-parser: finished parsing file /etc/network/interfaces
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPluginIfupdown: management mode: unmanaged
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0)
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: end _init.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: init!
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: end _init.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Loaded plugin (null): (null)
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    Ifupdown: get unmanaged devices count: 0
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: (27176720) ... get_connections.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: (27176720) ... get_connections (managed=false): return empty list.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    keyfile: parsing Ivan Mihaylov ... 
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]:    keyfile:     read connection 'Ivan Mihaylov'
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: (1610629408) ... get_connections.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: (1610629408) connections count: 0
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]:    Ifupdown: get unmanaged devices count: 0
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/ieee80211/phy0/rfkill0) (driver ath9k)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/platform/hp-wmi/rfkill/rfkill2) (platform driver hp-wmi)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Networking is enabled by state file
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> failed to allocate link cache: (-12) Object not found
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): carrier is OFF
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): bringing up device.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): preparing device.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.290411] r8169 0000:02:00.0 eth0: link down
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.292810] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): using nl80211 for WiFi device control
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): driver supports Access Point (AP) mode
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): bringing up device.
Jul 26 20:51:55 ivan-HP-ProBook-4535s anacron[952]: Anacron 2.3 started on 2015-07-26
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): preparing device.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul 26 20:51:55 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.315313] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> urfkill disappeared from the bus
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> ModemManager available in the bus
Jul 26 20:51:55 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> wpa_supplicant started
Jul 26 20:51:55 ivan-HP-ProBook-4535s wpa_supplicant[977]: Successfully initialized wpa_supplicant
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0) supports 4 scan SSIDs
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> Trying to remove a non-existant call id.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: starting -> ready
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0) supports 4 scan SSIDs
Jul 26 20:51:55 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:51:55 ivan-HP-ProBook-4535s acpid: starting up with netlink and the input layer
Jul 26 20:51:55 ivan-HP-ProBook-4535s cron[910]: (CRON) INFO (pidfile fd = 3)
Jul 26 20:51:55 ivan-HP-ProBook-4535s cron[1035]: (CRON) STARTUP (fork ok)
Jul 26 20:51:55 ivan-HP-ProBook-4535s cron[1035]: (CRON) INFO (Running @reboot jobs)
Jul 26 20:51:55 ivan-HP-ProBook-4535s ntpdate[1038]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jul 26 20:51:55 ivan-HP-ProBook-4535s ntpdate[1038]: no servers can be used, exiting
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.651831] vboxdrv: Found 2 processor cores.
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.653615] vboxdrv: fAsync=0 offMin=0x3cc offMax=0xf2a
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.653753] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.653755] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.675219] vboxpci: IOMMU not found (not registered)
Jul 26 20:51:55 ivan-HP-ProBook-4535s anacron[952]: Normal exit (0 jobs run)
Jul 26 20:51:55 ivan-HP-ProBook-4535s acpid: 11 rules loaded
Jul 26 20:51:55 ivan-HP-ProBook-4535s acpid: waiting for events: event logging is off
Jul 26 20:51:56 ivan-HP-ProBook-4535s kernel: [   13.194482] init: plymouth-splash main process (1164) terminated with status 1
Jul 26 20:51:56 ivan-HP-ProBook-4535s whoopsie[946]: whoopsie 0.2.24.6 starting up.
Jul 26 20:51:56 ivan-HP-ProBook-4535s whoopsie[946]: Using lock path: /var/lock/whoopsie/lock
Jul 26 20:51:56 ivan-HP-ProBook-4535s whoopsie[1185]: offline
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Auto-activating connection 'Ivan Mihaylov'.
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) starting connection 'Ivan Mihaylov'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now CONNECTING
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless): connection 'Ivan Mihaylov' has security, and secrets exist.  No new secrets needed.
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'ssid' value 'Ivan Mihaylov'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'scan_ssid' value '1'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'psk' value '<omitted>'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: set interface ap_scan to 1
Jul 26 20:51:57 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul 26 20:51:57 ivan-HP-ProBook-4535s accounts-daemon[1224]: started daemon version 0.6.35
Jul 26 20:51:57 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul 26 20:51:57 ivan-HP-ProBook-4535s ModemManager[673]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0': not supported by any plugin
Jul 26 20:51:57 ivan-HP-ProBook-4535s ModemManager[673]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0': not supported by any plugin
Jul 26 20:51:56 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:51:57 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: SME: Trying to authenticate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.347338] wlan0: authenticate with c8:3a:35:4d:4b:08
Jul 26 20:51:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jul 26 20:51:57 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Trying to associate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.359660] wlan0: send auth to c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.361680] wlan0: authenticated
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.362801] wlan0: associate with c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.366683] wlan0: RX AssocResp from c8:3a:35:4d:4b:08 (capab=0x11 status=0 aid=1)
Jul 26 20:51:57 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Associated with c8:3a:35:4d:4b:08
Jul 26 20:51:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.366823] wlan0: associated
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.366837] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.367624] cfg80211: Calling CRDA for country: CN
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370556] ath: EEPROM regdomain: 0x809c
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370563] ath: EEPROM indicates we should expect a country code
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370565] ath: doing EEPROM country->regdmn map search
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370566] ath: country maps to regdmn code: 0x52
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370568] ath: Country alpha2 being used: CN
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370570] ath: Regpair used: 0x52
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370592] ath: regdomain 0x809c dynamically updated by country IE
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370615] cfg80211: Regulatory domain changed to country: CN
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370616] cfg80211:  DFS Master region: unset
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370618] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370621] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370623] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370626] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370628] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370630] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 26 20:51:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associated -> group handshake
Jul 26 20:51:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:51:59 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv6 for mDNS.
Jul 26 20:51:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fe80::9eb7:dff:fe7f:c344 on wlan0.*.
Jul 26 20:52:00 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul 26 20:52:00 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul 26 20:52:00 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul 26 20:52:00 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully called chroot.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully dropped privileges.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully limited resources.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Running.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Canary thread running.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 1392 of process 1392 (n/a) owned by '112' high priority at nice level -11.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 1 threads of 1 processes of 1 users.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Watchdog thread running.
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: WPA: Key negotiation completed with c8:3a:35:4d:4b:08 [PTK=CCMP GTK=CCMP]
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-CONNECTED - Connection to c8:3a:35:4d:4b:08 completed [id=0 id_str=]
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: SME: Trying to authenticate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.601027] wlan0: deauthenticating from c8:3a:35:4d:4b:08 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.611105] cfg80211: Calling CRDA to update world regulatory domain
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614395] cfg80211: World regulatory domain updated:
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614402] cfg80211:  DFS Master region: unset
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614404] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614407] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614410] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614413] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614415] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614417] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.619190] wlan0: authenticate with c8:3a:35:4d:4b:08
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-DISCONNECTED bssid=c8:3a:35:4d:4b:08 reason=2 locally_generated=1
Jul 26 20:52:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: group handshake -> authenticating
Jul 26 20:52:00 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> Connection disconnected (reason -2)
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Trying to associate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.631224] wlan0: send auth to c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.632915] wlan0: authenticated
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.635178] wlan0: associate with c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 20:52:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.639031] wlan0: RX AssocResp from c8:3a:35:4d:4b:08 (capab=0x11 status=0 aid=1)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.639075] wlan0: associated
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.639186] cfg80211: Calling CRDA for country: CN
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Associated with c8:3a:35:4d:4b:08
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642829] ath: EEPROM regdomain: 0x809c
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642835] ath: EEPROM indicates we should expect a country code
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642837] ath: doing EEPROM country->regdmn map search
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642839] ath: country maps to regdmn code: 0x52
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642841] ath: Country alpha2 being used: CN
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642843] ath: Regpair used: 0x52
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642845] ath: regdomain 0x809c dynamically updated by country IE
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642869] cfg80211: Regulatory domain changed to country: CN
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642871] cfg80211:  DFS Master region: unset
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642873] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642876] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642879] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642881] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642883] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642885] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 1491 of process 1392 (n/a) owned by '112' RT at priority 5.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 2 threads of 1 processes of 1 users.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 1492 of process 1392 (n/a) owned by '112' RT at priority 5.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 3 threads of 1 processes of 1 users.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 1493 of process 1392 (n/a) owned by '112' RT at priority 5.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 4 threads of 1 processes of 1 users.
Jul 26 20:52:01 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/HFPAG
Jul 26 20:52:01 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/HFPHS
Jul 26 20:52:01 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Jul 26 20:52:01 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSink
Jul 26 20:52:01 ivan-HP-ProBook-4535s anacron[1497]: Anacron 2.3 started on 2015-07-26
Jul 26 20:52:01 ivan-HP-ProBook-4535s anacron[1497]: Normal exit (0 jobs run)
Jul 26 20:52:01 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 26 20:52:01 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associated -> group handshake
Jul 26 20:52:01 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: WPA: Key negotiation completed with c8:3a:35:4d:4b:08 [PTK=CCMP GTK=CCMP]
Jul 26 20:52:01 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-CONNECTED - Connection to c8:3a:35:4d:4b:08 completed [id=0 id_str=]
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: group handshake -> completed
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Ivan Mihaylov'.
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> dhclient started with pid 1590
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Withdrawing address record for fe80::9eb7:dff:fe7f:c344 on wlan0.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: All rights reserved.
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: 
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Listening on LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Sending on   LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Sending on   Socket/fallback
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 255.255.255.255 port 67 (xid=0x1e77f6d0)
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: bound to 192.168.0.102 -- renewal in 37486 seconds.
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   address 192.168.0.102
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   prefix 24 (255.255.255.0)
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   gateway 192.168.0.1
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   nameserver '192.168.1.1'
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv4 for mDNS.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for 192.168.0.102 on wlan0.IPv4.
Jul 26 20:52:01 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Using config file /etc/colord.conf
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Using mapping database file /var/lib/colord/mapping.db
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Using device database file /var/lib/colord/storage.db
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: loaded plugin libcd_plugin_scanner.so
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: loaded plugin libcd_plugin_camera.so
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Daemon ready for requests
Jul 26 20:52:01 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Device added: xrandr-default
Jul 26 20:52:02 ivan-HP-ProBook-4535s colord: Profile added: icc-7a9564ffe8e4686f7064491b7f3c6153
Jul 26 20:52:02 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:52:02 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv6 for mDNS.
Jul 26 20:52:02 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fe80::9eb7:dff:fe7f:c344 on wlan0.*.
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Policy set 'Ivan Mihaylov' (wlan0) as default for IPv4 routing and DNS.
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> DNS: starting dnsmasq...
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> dnsmasq not available on the bus, can't update servers.
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <error> [1437933122.636839] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> DNS: plugin dnsmasq update failed
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: started, version 2.68 cache disabled
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: DBus support enabled: connected to system bus
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: warning: no upstream servers configured
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) successful, device activated.
Jul 26 20:52:02 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> dnsmasq appeared on DBus: :1.46
Jul 26 20:52:02 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: setting upstream servers from DBus
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: using nameserver 192.168.1.1#53
Jul 26 20:52:03 ivan-HP-ProBook-4535s whoopsie[1185]: message repeated 3 times: [ offline]
Jul 26 20:52:03 ivan-HP-ProBook-4535s whoopsie[1185]: online
Jul 26 20:52:05 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WiFi hardware radio set enabled
Jul 26 20:52:05 ivan-HP-ProBook-4535s kernel: [   22.300022] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 20:52:05 ivan-HP-ProBook-4535s kernel: [   22.300036] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 20:52:05 ivan-HP-ProBook-4535s colord: device removed: xrandr-default
Jul 26 20:52:05 ivan-HP-ProBook-4535s colord: Profile removed: icc-7a9564ffe8e4686f7064491b7f3c6153
Jul 26 20:52:09 ivan-HP-ProBook-4535s ntpdate[1755]: adjust time server 91.189.94.4 offset 0.346865 sec
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 2146 of process 2146 (n/a) owned by '1000' high priority at nice level -11.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 5 threads of 2 processes of 2 users.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 2147 of process 2146 (n/a) owned by '1000' RT at priority 5.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 6 threads of 2 processes of 2 users.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 2148 of process 2146 (n/a) owned by '1000' RT at priority 5.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 7 threads of 2 processes of 2 users.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 2149 of process 2146 (n/a) owned by '1000' RT at priority 5.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 8 threads of 2 processes of 2 users.
Jul 26 20:52:09 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPAG
Jul 26 20:52:09 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPHS
Jul 26 20:52:09 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSource
Jul 26 20:52:09 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSink
Jul 26 20:52:09 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Jul 26 20:52:10 ivan-HP-ProBook-4535s colord: Device added: xrandr-default
Jul 26 20:52:10 ivan-HP-ProBook-4535s colord: Profile added: icc-8047dcbd0521d15201185b4fe16ea653
Jul 26 20:52:10 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.locale1'
Jul 26 20:52:13 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jul 26 20:52:13 ivan-HP-ProBook-4535s udisksd[2291]: udisks daemon version 2.1.3 starting
Jul 26 20:52:13 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jul 26 20:52:13 ivan-HP-ProBook-4535s udisksd[2291]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jul 26 20:52:19 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:52:22 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 26 20:52:22 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 26 20:52:22 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 26 20:52:22 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 26 20:52:24 ivan-HP-ProBook-4535s kernel: [   40.969782] audit_printk_skb: 168 callbacks suppressed
Jul 26 20:52:24 ivan-HP-ProBook-4535s kernel: [   40.969791] audit: type=1400 audit(1437933144.052:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2407 comm="apparmor_parser"
Jul 26 20:52:24 ivan-HP-ProBook-4535s kernel: [   40.969802] audit: type=1400 audit(1437933144.052:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2407 comm="apparmor_parser"
Jul 26 20:52:24 ivan-HP-ProBook-4535s kernel: [   40.970316] audit: type=1400 audit(1437933144.052:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2407 comm="apparmor_parser"
Jul 26 20:52:25 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/HFPAG
Jul 26 20:52:25 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/HFPHS
Jul 26 20:52:25 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Jul 26 20:52:25 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/A2DPSink
Jul 26 20:52:42 ivan-HP-ProBook-4535s gnome-session[2048]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Jul 26 20:54:07 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Jul 26 20:55:57 ivan-HP-ProBook-4535s dnsmasq[1655]: nameserver 192.168.1.1 refused to do a recursive query
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): disconnecting for new activation request.
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: activated -> disconnected (reason 'none') [100 30 0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): deactivating device (reason 'none') [0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1590
Jul 26 20:56:49 ivan-HP-ProBook-4535s avahi-daemon[772]: Withdrawing address record for 192.168.0.102 on wlan0.
Jul 26 20:56:49 ivan-HP-ProBook-4535s avahi-daemon[772]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Jul 26 20:56:49 ivan-HP-ProBook-4535s avahi-daemon[772]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.378298] wlan0: deauthenticating from c8:3a:35:4d:4b:08 by local choice (Reason: 3=DEAUTH_LEAVING)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> DNS: plugin dnsmasq update failed
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Removing DNS information from /sbin/resolvconf
Jul 26 20:56:49 ivan-HP-ProBook-4535s dnsmasq[1655]: setting upstream servers from DBus
Jul 26 20:55:28 ivan-HP-ProBook-4535s wpa_supplicant[1016]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jul 26 20:56:49 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-DISCONNECTED bssid=c8:3a:35:4d:4b:08 reason=3 locally_generated=1
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.392107] cfg80211: Calling CRDA to update world regulatory domain
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397142] cfg80211: World regulatory domain updated:
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397151] cfg80211:  DFS Master region: unset
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397154] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397160] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397164] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397180] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397184] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397187] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now DISCONNECTED
Jul 26 20:56:49 ivan-HP-ProBook-4535s whoopsie[1185]: offline
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) starting connection 'Sinjo13'
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now CONNECTING
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 20:56:49 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> Connection disconnected (reason -3)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> Connection disconnected (reason -3)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 20:56:49 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless): access point 'Sinjo13' has security, but secrets are required.
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 20:56:49 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 20:56:50 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jul 26 20:56:50 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless): connection 'Sinjo13' has security, and secrets exist.  No new secrets needed.
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'ssid' value 'Sinjo13'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'scan_ssid' value '1'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'psk' value '<omitted>'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: set interface ap_scan to 1
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 26 20:56:57 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:56:58 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: SME: Trying to authenticate with ec:cb:30:46:f3:2c (SSID='Sinjo13' freq=2442 MHz)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.229503] wlan0: authenticate with ec:cb:30:46:f3:2c
Jul 26 20:56:58 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Trying to associate with ec:cb:30:46:f3:2c (SSID='Sinjo13' freq=2442 MHz)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.236681] wlan0: send auth to ec:cb:30:46:f3:2c (try 1/3)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.238328] wlan0: authenticated
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.238558] ath9k 0000:04:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.238562] ath9k 0000:04:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.238826] wlan0: associate with ec:cb:30:46:f3:2c (try 1/3)
Jul 26 20:56:58 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 26 20:56:58 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Associated with ec:cb:30:46:f3:2c
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.242098] wlan0: RX AssocResp from ec:cb:30:46:f3:2c (capab=0x431 status=0 aid=3)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.242160] wlan0: associated
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.242236] cfg80211: Calling CRDA for country: BG
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245943] ath: EEPROM regdomain: 0x8064
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245948] ath: EEPROM indicates we should expect a country code
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245950] ath: doing EEPROM country->regdmn map search
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245952] ath: country maps to regdmn code: 0x34
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245954] ath: Country alpha2 being used: BG
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245956] ath: Regpair used: 0x34
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245958] ath: regdomain 0x8064 dynamically updated by country IE
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245981] cfg80211: Regulatory domain changed to country: BG
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245983] cfg80211:  DFS Master region: unset
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245985] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245988] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245990] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2300 mBm), (N/A)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245993] cfg80211:   (5250000 KHz - 5290000 KHz @ 40000 KHz), (N/A, 2300 mBm), (0 s)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245995] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 3000 mBm), (0 s)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245997] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul 26 20:56:58 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: authenticating -> associated
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jul 26 20:56:59 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: WPA: Key negotiation completed with ec:cb:30:46:f3:2c [PTK=CCMP GTK=TKIP]
Jul 26 20:56:59 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-CONNECTED - Connection to ec:cb:30:46:f3:2c completed [id=0 id_str=]
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Sinjo13'.
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> dhclient started with pid 2829
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Withdrawing address record for fe80::9eb7:dff:fe7f:c344 on wlan0.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: All rights reserved.
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: 
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Listening on LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Sending on   LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Sending on   Socket/fallback
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x79f03e08)
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: DHCPREQUEST of 192.168.1.4 on wlan0 to 255.255.255.255 port 67 (xid=0x83ef079)
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: DHCPOFFER of 192.168.1.4 from 192.168.1.1
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: DHCPACK of 192.168.1.4 from 192.168.1.1
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: bound to 192.168.1.4 -- renewal in 37384 seconds.
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   address 192.168.1.4
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   prefix 24 (255.255.255.0)
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   gateway 192.168.1.1
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   nameserver '192.168.1.1'
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: nm_ip4_config_add_nameserver: assertion 'nameserver > 0' failed
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   nameserver '0.0.0.0'
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   domain name 'vivacom-adsl'
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.4.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv4 for mDNS.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for 192.168.1.4 on wlan0.IPv4.
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Policy set 'Sinjo13' (wlan0) as default for IPv4 routing and DNS.
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 20:57:00 ivan-HP-ProBook-4535s dnsmasq[1655]: setting upstream servers from DBus
Jul 26 20:57:00 ivan-HP-ProBook-4535s dnsmasq[1655]: using nameserver 192.168.1.1#53
Jul 26 20:57:00 ivan-HP-ProBook-4535s dnsmasq[1655]: nameserver 192.168.1.1 refused to do a recursive query
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) successful, device activated.
Jul 26 20:57:00 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 20:57:00 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 20:57:00 ivan-HP-ProBook-4535s ntpdate[2920]: Can't find host ntp.ubuntu.com: No address associated with hostname (-5)
Jul 26 20:57:00 ivan-HP-ProBook-4535s ntpdate[2920]: no servers can be used, exiting
Jul 26 20:57:00 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:57:00 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv6 for mDNS.
Jul 26 20:57:00 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fe80::9eb7:dff:fe7f:c344 on wlan0.*.
Jul 26 20:57:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) scheduled...
Jul 26 20:57:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) started...
Jul 26 20:57:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:57:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv6 with address fdec:cb30:46f3:2400:696b:e408:aed7:86c0.
Jul 26 20:57:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fdec:cb30:46f3:2400:696b:e408:aed7:86c0 on wlan0.*.
Jul 26 20:57:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Withdrawing address record for fe80::9eb7:dff:fe7f:c344 on wlan0.
Jul 26 20:57:02 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fdec:cb30:46f3:2400:9eb7:dff:fe7f:c344 on wlan0.*.
Jul 26 20:57:02 ivan-HP-ProBook-4535s NetworkManager[804]: <error> [1437933422.981247] [nm-system.c:1266] nm_system_replace_default_ip6_route(): (wlan0): failed to set IPv6 default route: -7
Jul 26 20:57:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Policy set 'Sinjo13' (wlan0) as default for IPv6 routing and DNS.
Jul 26 20:57:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) complete.
Jul 26 20:57:16 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 21:00:27 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Jul 26 21:04:15 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 26 21:04:15 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 26 21:04:15 ivan-HP-ProBook-4535s rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="665" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul 26 21:05:53 ivan-HP-ProBook-4535s rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="595" x-info="http://www.rsyslog.com"] start
Jul 26 21:05:53 ivan-HP-ProBook-4535s rsyslogd: rsyslogd's groupid changed to 104
Jul 26 21:05:53 ivan-HP-ProBook-4535s rsyslogd: rsyslogd's userid changed to 101
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Linux version 3.16.0-44-generic (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #59~14.04.1-Ubuntu SMP Tue Jul 7 15:07:27 UTC 2015 (Ubuntu 3.16.0-44.59~14.04.1-generic 3.16.7-ckt14)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-44-generic root=UUID=06bbc19e-b72c-445e-851c-77c80ccf7f12 ro quiet splash nomodeset pci=pcie_mode_safe vt.handoff=7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] KERNEL supported cpus:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Intel GenuineIntel
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   AMD AuthenticAMD
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Centaur CentaurHauls
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008f08cfff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008f08d000-0x000000008f58cfff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008f58d000-0x000000008fbcefff] ACPI NVS
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbcf000-0x000000008fbfefff] ACPI data
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbff000-0x000000008fbfffff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024effffff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PCI: Unknown option `pcie_mode_safe'
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] SMBIOS 2.6 present.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] DMI: Hewlett-Packard HP ProBook 4535s/168B, BIOS 68CPC Ver. F.50 07/01/2014
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: No AGP bridge found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: last_pfn = 0x24f000 max_arch_pfn = 0x400000000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR default type: uncachable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   00000-9FFFF write-back
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   A0000-DFFFF uncachable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   E0000-FFFFF write-protect
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR variable ranges enabled:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   1 base 0080000000 mask FFF0000000 write-back
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   2 base 00FFE00000 mask FFFFE00000 write-protect
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   3 base 00FFE10000 mask FFFFFF0000 write-protect
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   4 disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   5 disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   6 disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   7 disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] TOM2: 000000024f000000 aka 9456M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: last_pfn = 0x8fc00 max_arch_pfn = 0x400000000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Using GB pages for direct mapping
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbd000, 0x01fbdfff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbe000, 0x01fbefff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbf000, 0x01fbffff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x24ee00000-0x24effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x24ee00000-0x24effffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fc0000, 0x01fc0fff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x24c000000-0x24edfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x24c000000-0x24edfffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x24bffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x200000000-0x23fffffff] page 1G
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x240000000-0x24bffffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x8f08cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x80000000-0x8effffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x8f000000-0x8f08cfff] page 4k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x8fbff000-0x8fbfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x8fbff000-0x8fbfffff] page 4k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fc1000, 0x01fc1fff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] RAMDISK: [mem 0x35ad4000-0x36d61fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: RSDP 0x00000000000F2F00 000014 (v00 HPQOEM)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: RSDT 0x000000008FBFE038 000044 (v01 HPQOEM SLIC-MPC 00000003      01000013)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: FACP 0x000000008FBFD000 000074 (v01 HPQOEM 168B     00000003 HP   00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20140424/tbfadt-649)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: DSDT 0x000000008FBD7000 0230B2 (v01 HPQOEM 168B     00000001 INTL 20060912)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: FACS 0x000000008FB8F000 000040
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: APIC 0x000000008FBFC000 000084 (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: MCFG 0x000000008FBFB000 00003C (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: HPET 0x000000008FBD4000 000038 (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD3000 00072C (v01 AMD    POWERNOW 00000001 AMD  00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD1000 00193D (v02 AMD    ALIB     00000001 MSFT 04000000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD0000 00078F (v01 HP     AMDSGTBL 00000001 INTL 20060912)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBCF000 000325 (v01 HP     HPZPODDT 00000001 INTL 20060912)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] No NUMA configuration found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x24effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   NODE_DATA [mem 0x24eff9000-0x24effdfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246e00000-ffff88024e5fffff] on node 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Zone ranges:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal   [mem 0x100000000-0x24effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Movable zone start for each node
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Early memory node ranges
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x00100000-0x8f08cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x8fbff000-0x8fbfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x100000000-0x24effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] On node 0 totalpages: 1957931
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 21 pages reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32 zone: 9091 pages used for memmap
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32 zone: 581774 pages, LIFO batch:31
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal zone: 21440 pages used for memmap
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal zone: 1372160 pages, LIFO batch:31
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] nr_irqs_gsi: 40
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8f08d000-0x8f58cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8f58d000-0x8fbcefff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8fbcf000-0x8fbfefff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8fc00000-0xdfffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfedfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffdfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: [mem 0x8fc00000-0xdfffffff] available for PCI devices
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88024ec00000 s81408 r8192 d20992 u524288
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] pcpu-alloc: s81408 r8192 d20992 u524288 alloc=1*2097152
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1927315
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Policy zone: Normal
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-44-generic root=UUID=06bbc19e-b72c-445e-851c-77c80ccf7f12 ro quiet splash nomodeset pci=pcie_mode_safe vt.handoff=7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: Checking aperture...
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: No AGP bridge found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Memory: 7606856K/7831724K available (7629K kernel code, 1131K rwdata, 3616K rodata, 1352K init, 1300K bss, 224868K reserved)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Hierarchical RCU implementation.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	Offload RCU callbacks from all CPUs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Console: colour dummy device 80x25
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] console [tty0] enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] allocated 31457280 bytes of page_cgroup
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] hpet clockevent registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] tsc: Detected 1896.380 MHz processor
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000050] Calibrating delay loop (skipped), value calculated using timer frequency.. 3792.76 BogoMIPS (lpj=7585520)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000054] pid_max: default: 32768 minimum: 301
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000063] ACPI: Core revision 20140424
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.014999] ACPI: All ACPI Tables successfully acquired
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.049285] Security Framework initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.049307] AppArmor: AppArmor initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.049308] Yama: becoming mindful.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.050087] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.052955] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054199] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054213] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054552] Initializing cgroup subsys memory
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054584] Initializing cgroup subsys devices
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054593] Initializing cgroup subsys freezer
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054597] Initializing cgroup subsys net_cls
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054603] Initializing cgroup subsys blkio
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054609] Initializing cgroup subsys perf_event
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054611] Initializing cgroup subsys net_prio
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054620] Initializing cgroup subsys hugetlb
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054649] tseg: 008fc00000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054653] CPU: Physical Processor ID: 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054654] CPU: Processor Core ID: 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054656] mce: CPU supports 6 MCE banks
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054668] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054668] Last level dTLB entries: 4KB 1024, 2MB 128, 4MB 64, 1GB 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054668] tlb_flushall_shift: 6
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054840] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.056459] ftrace: allocating 29259 entries in 115 pages
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.078055] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.117747] smpboot: CPU0: AMD A4-3305M APU with Radeon(tm) HD Graphics (fam: 12, model: 01, stepping: 00)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224770] Performance Events: AMD PMU driver.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224775] ... version:                0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224776] ... bit width:              48
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224778] ... generic registers:      4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224779] ... value mask:             0000ffffffffffff
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224780] ... max period:             00007fffffffffff
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224782] ... fixed-purpose events:   0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224783] ... event mask:             000000000000000f
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.227078] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.227194] x86: Booting SMP configuration:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.227197] .... node  #0, CPUs:      #1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.240339] x86: Booted up 1 node, 2 CPUs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.240341] smpboot: Total of 2 processors activated (7585.52 BogoMIPS)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.241085] devtmpfs: initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246762] evm: security.selinux
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246765] evm: security.SMACK64
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246766] evm: security.SMACK64EXEC
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246767] evm: security.SMACK64TRANSMUTE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246769] evm: security.SMACK64MMAP
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246770] evm: security.ima
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246771] evm: security.capability
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246934] PM: Registering ACPI NVS region [mem 0x8f58d000-0x8fbcefff] (6561792 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.248482] pinctrl core: initialized pinctrl subsystem
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.248611] regulator-dummy: no parameters
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.248694] RTC time: 21:05:43, date: 07/26/15
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.248766] NET: Registered protocol family 16
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249000] cpuidle: using governor ladder
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249004] cpuidle: using governor menu
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249223] ACPI: bus type PCI registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249225] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249380] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249383] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249962] PCI: Using configuration type 1 for base access
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.250286] mtrr: your CPUs had inconsistent fixed MTRR settings
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.250288] mtrr: your CPUs had inconsistent variable MTRR settings
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.250289] mtrr: probably your BIOS does not setup all CPUs.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.250290] mtrr: corrected configuration.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.254054] ACPI: Added _OSI(Module Device)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.254058] ACPI: Added _OSI(Processor Device)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.254060] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.254062] ACPI: Added _OSI(Processor Aggregator Device)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441061] ACPI: Interpreter enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441080] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441085] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441102] ACPI: (supports S0 S3 S4 S5)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441104] ACPI: Using IOAPIC for interrupt routing
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441335] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.444428] ACPI: Power Resource [APPR] (off)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451100] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451110] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451330] acpi PNP0A08:00: _OSC: platform does not support [PCIeCapability]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451463] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451467] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451470] acpi PNP0A08:00: _OSC: platform willing to grant [PCIeHotplug PME AER]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451473] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451629] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cf1ff])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451633] acpi PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000d3fff] (conflicts with Adapter ROM [mem 0x000cf800-0x000d07ff])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451886] PCI host bridge to bus 0000:00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451890] pci_bus 0000:00: root bus resource [bus 00-ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451892] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451895] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451898] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451900] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451903] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451905] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451908] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451911] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451913] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451916] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451918] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451921] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451923] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451926] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451928] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xdfffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451931] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfffdffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451941] pci 0000:00:00.0: [1022:1705] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452051] pci 0000:00:01.0: [1002:9649] type 00 class 0x030000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452065] pci 0000:00:01.0: reg 0x10: [mem 0xb0000000-0xbfffffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452072] pci 0000:00:01.0: reg 0x14: [io  0x7000-0x70ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452080] pci 0000:00:01.0: reg 0x18: [mem 0xd8100000-0xd813ffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452130] pci 0000:00:01.0: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452212] pci 0000:00:01.1: [1002:1714] type 00 class 0x040300
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452223] pci 0000:00:01.1: reg 0x10: [mem 0xd8144000-0xd8147fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452282] pci 0000:00:01.1: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452410] pci 0000:00:03.0: [1022:1708] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452475] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452569] pci 0000:00:04.0: [1022:1709] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452633] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452680] pci 0000:00:04.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452731] pci 0000:00:05.0: [1022:170a] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452806] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452852] pci 0000:00:05.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452952] pci 0000:00:07.0: [1022:170c] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453015] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453064] pci 0000:00:07.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453186] pci 0000:00:10.0: [1022:7812] type 00 class 0x0c0330
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453211] pci 0000:00:10.0: reg 0x10: [mem 0xd8148000-0xd8149fff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453319] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453373] pci 0000:00:10.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453483] pci 0000:00:10.1: [1022:7812] type 00 class 0x0c0330
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453510] pci 0000:00:10.1: reg 0x10: [mem 0xd814a000-0xd814bfff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453632] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453686] pci 0000:00:10.1: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453796] pci 0000:00:11.0: [1022:7801] type 00 class 0x010601
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453818] pci 0000:00:11.0: reg 0x10: [io  0x7118-0x711f]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453829] pci 0000:00:11.0: reg 0x14: [io  0x7124-0x7127]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453841] pci 0000:00:11.0: reg 0x18: [io  0x7110-0x7117]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453852] pci 0000:00:11.0: reg 0x1c: [io  0x7120-0x7123]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453864] pci 0000:00:11.0: reg 0x20: [io  0x7100-0x710f]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453875] pci 0000:00:11.0: reg 0x24: [mem 0xd8151000-0xd81517ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454050] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454066] pci 0000:00:12.0: reg 0x10: [mem 0xd8150000-0xd8150fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454231] pci 0000:00:12.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454332] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454355] pci 0000:00:12.2: reg 0x10: [mem 0xd814f000-0xd814f0ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454450] pci 0000:00:12.2: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454452] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454497] pci 0000:00:12.2: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454596] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454612] pci 0000:00:13.0: reg 0x10: [mem 0xd814e000-0xd814efff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454773] pci 0000:00:13.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454875] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454897] pci 0000:00:13.2: reg 0x10: [mem 0xd814d000-0xd814d0ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454992] pci 0000:00:13.2: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454994] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455040] pci 0000:00:13.2: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455141] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455337] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455362] pci 0000:00:14.2: reg 0x10: [mem 0xd8140000-0xd8143fff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455438] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455722] pci 0000:00:14.2: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455815] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456010] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456167] pci 0000:00:14.5: [1022:7809] type 00 class 0x0c0310
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456183] pci 0000:00:14.5: reg 0x10: [mem 0xd814c000-0xd814cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456374] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456476] pci 0000:00:15.0: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456527] pci 0000:00:15.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456633] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456731] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456831] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456925] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457028] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457119] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457212] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457304] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457550] pci 0000:01:00.0: [1002:6760] type 00 class 0x030000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457570] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457583] pci 0000:01:00.0: reg 0x18: [mem 0xd8000000-0xd801ffff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457591] pci 0000:01:00.0: reg 0x20: [io  0x6000-0x60ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457606] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457656] pci 0000:01:00.0: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.464983] pci 0000:00:03.0: PCI bridge to [bus 01]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465003] pci 0000:00:03.0:   bridge window [io  0x6000-0x6fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465013] pci 0000:00:03.0:   bridge window [mem 0xd8000000-0xd80fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465025] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465175] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465195] pci 0000:02:00.0: reg 0x10: [io  0x5000-0x50ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465220] pci 0000:02:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465236] pci 0000:02:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465318] pci 0000:02:00.0: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465320] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465354] pci 0000:02:00.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.472985] pci 0000:00:04.0: PCI bridge to [bus 02]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473006] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473015] pci 0000:00:04.0:   bridge window [mem 0xd7000000-0xd7ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473027] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473200] pci 0000:03:00.0: [197b:2392] type 00 class 0x088000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473224] pci 0000:03:00.0: reg 0x10: [mem 0xd6003000-0xd60030ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473290] pci 0000:03:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473428] pci 0000:03:00.2: [197b:2391] type 00 class 0x080501
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473448] pci 0000:03:00.2: reg 0x10: [mem 0xd6002000-0xd60020ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473632] pci 0000:03:00.3: [197b:2393] type 00 class 0x088000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473652] pci 0000:03:00.3: reg 0x10: [mem 0xd6001000-0xd60010ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481003] pci 0000:00:05.0: PCI bridge to [bus 03]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481023] pci 0000:00:05.0:   bridge window [io  0x4000-0x4fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481031] pci 0000:00:05.0:   bridge window [mem 0xd6000000-0xd6ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481037] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481178] pci 0000:04:00.0: [168c:002b] type 00 class 0x028000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481203] pci 0000:04:00.0: reg 0x10: [mem 0xd5000000-0xd500ffff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481313] pci 0000:04:00.0: supports D1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481315] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.488985] pci 0000:00:07.0: PCI bridge to [bus 04-06]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489005] pci 0000:00:07.0:   bridge window [io  0x3000-0x3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489015] pci 0000:00:07.0:   bridge window [mem 0xd5000000-0xd5ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489027] pci 0000:00:07.0:   bridge window [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489235] pci 0000:00:14.4: PCI bridge to [bus 07] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489246] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489247] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489249] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489251] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489254] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489262] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489264] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489266] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489268] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489270] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489272] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489273] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489275] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489277] pci 0000:00:14.4:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489279] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xdfffffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489281] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfffdffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489459] acpiphp: Slot [1] registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489487] pci 0000:00:15.0: PCI bridge to [bus 08]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489493] pci 0000:00:15.0:   bridge window [io  0x2000-0x2fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489498] pci 0000:00:15.0:   bridge window [mem 0xd4000000-0xd4ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489504] pci 0000:00:15.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490591] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490663] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490735] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490808] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490866] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490911] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490957] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491002] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491123] ACPI: Enabled 5 GPEs in block 00 to 1F
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491180] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491494] vgaarb: setting as boot device: PCI:0000:00:01.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491501] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491514] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491517] vgaarb: loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491519] vgaarb: bridge control possible 0000:01:00.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491521] vgaarb: no bridge control possible 0000:00:01.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491895] SCSI subsystem initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492018] libata version 3.00 loaded.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492056] ACPI: bus type USB registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492082] usbcore: registered new interface driver usbfs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492094] usbcore: registered new interface driver hub
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492280] usbcore: registered new device driver usb
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492629] PCI: Using ACPI for IRQ routing
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502212] PCI: pci_cache_line_size set to 64 bytes
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502312] Expanded resource reserved due to conflict with PCI Bus 0000:00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502314] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502316] e820: reserve RAM buffer [mem 0x8f08d000-0x8fffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502318] e820: reserve RAM buffer [mem 0x8fc00000-0x8fffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502319] e820: reserve RAM buffer [mem 0x24f000000-0x24fffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502461] NetLabel: Initializing
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502463] NetLabel:  domain hash size = 128
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502464] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502478] NetLabel:  unlabeled traffic allowed by default
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502756] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502764] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.504911] Switched to clocksource hpet
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512475] AppArmor: AppArmor Filesystem Enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512524] pnp: PnP ACPI init
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512549] ACPI: bus type PNP registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512693] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512697] system 00:00: [mem 0xfeb00000-0xfeb00fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512704] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512707] system 00:00: [mem 0xfec10000-0xfec10fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512710] system 00:00: [mem 0xfed61000-0xfed61fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512713] system 00:00: [mem 0xfed80000-0xfed80fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512716] system 00:00: [mem 0xfed81000-0xfed81fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512719] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512724] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513073] system 00:01: [io  0x0400-0x04cf] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513077] system 00:01: [io  0x04d0-0x04d1] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513079] system 00:01: [io  0x04d6] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513082] system 00:01: [io  0x0680-0x06ff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513084] system 00:01: [io  0x077a] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513087] system 00:01: [io  0x0c00-0x0c01] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513090] system 00:01: [io  0x0c14] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513092] system 00:01: [io  0x0c50-0x0c52] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513095] system 00:01: [io  0x0c6c] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513097] system 00:01: [io  0x0c6f] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513100] system 00:01: [io  0x0cd0-0x0cdb] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513103] system 00:01: [io  0x0220-0x0227] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513105] system 00:01: [io  0x0260-0x0273] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513108] system 00:01: [io  0x0800] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513110] system 00:01: [io  0x0804] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513113] system 00:01: [io  0x087f] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513116] system 00:01: [io  0x0cdc-0x0cdf] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513118] system 00:01: [io  0x0b00-0x0b0f] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513121] system 00:01: [io  0x0b20-0x0b3f] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513124] system 00:01: [io  0x0200-0x027f] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513127] system 00:01: [io  0x0840-0x0847] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513130] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513225] system 00:02: [mem 0x00000000-0x0009ffff] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513228] system 00:02: [mem 0x00100000-0xafffffff] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513231] system 00:02: [mem 0xffe00000-0xffffffff] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513234] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513346] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513470] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513511] pnp 00:05: Plug and Play ACPI device, IDs SYN0189 SYN0100 SYN0002 PNP0f13 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513944] pnp: PnP ACPI: found 6 devices
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513946] ACPI: bus type PNP unregistered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523718] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523725] pci 0000:03:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523826] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8020000-0xd803ffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523830] pci 0000:00:03.0: PCI bridge to [bus 01]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523834] pci 0000:00:03.0:   bridge window [io  0x6000-0x6fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523839] pci 0000:00:03.0:   bridge window [mem 0xd8000000-0xd80fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523843] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523848] pci 0000:00:04.0: PCI bridge to [bus 02]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523851] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523856] pci 0000:00:04.0:   bridge window [mem 0xd7000000-0xd7ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523860] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523867] pci 0000:03:00.0: BAR 6: assigned [mem 0xd6010000-0xd601ffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523869] pci 0000:00:05.0: PCI bridge to [bus 03]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523873] pci 0000:00:05.0:   bridge window [io  0x4000-0x4fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523877] pci 0000:00:05.0:   bridge window [mem 0xd6000000-0xd6ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523881] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523887] pci 0000:00:07.0: PCI bridge to [bus 04-06]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523889] pci 0000:00:07.0:   bridge window [io  0x3000-0x3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523894] pci 0000:00:07.0:   bridge window [mem 0xd5000000-0xd5ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523898] pci 0000:00:07.0:   bridge window [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523903] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523964] pci 0000:00:15.0: PCI bridge to [bus 08]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523968] pci 0000:00:15.0:   bridge window [io  0x2000-0x2fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523973] pci 0000:00:15.0:   bridge window [mem 0xd4000000-0xd4ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523978] pci 0000:00:15.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523986] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523988] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523991] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523994] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523996] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523998] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524001] pci_bus 0000:00: resource 10 [mem 0x000d4000-0x000d7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524003] pci_bus 0000:00: resource 11 [mem 0x000d8000-0x000dbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524005] pci_bus 0000:00: resource 12 [mem 0x000dc000-0x000dffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524008] pci_bus 0000:00: resource 13 [mem 0x000e0000-0x000e3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524010] pci_bus 0000:00: resource 14 [mem 0x000e4000-0x000e7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524013] pci_bus 0000:00: resource 15 [mem 0x000e8000-0x000ebfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524015] pci_bus 0000:00: resource 16 [mem 0x000ec000-0x000effff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524017] pci_bus 0000:00: resource 17 [mem 0x000f0000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524020] pci_bus 0000:00: resource 18 [mem 0xb0000000-0xdfffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524022] pci_bus 0000:00: resource 19 [mem 0xf0000000-0xfffdffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524025] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524027] pci_bus 0000:01: resource 1 [mem 0xd8000000-0xd80fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524030] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524032] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524035] pci_bus 0000:02: resource 1 [mem 0xd7000000-0xd7ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524037] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524040] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524042] pci_bus 0000:03: resource 1 [mem 0xd6000000-0xd6ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524045] pci_bus 0000:03: resource 2 [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524047] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524050] pci_bus 0000:04: resource 1 [mem 0xd5000000-0xd5ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524052] pci_bus 0000:04: resource 2 [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524055] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524057] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524060] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524062] pci_bus 0000:07: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524065] pci_bus 0000:07: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524067] pci_bus 0000:07: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524070] pci_bus 0000:07: resource 10 [mem 0x000d4000-0x000d7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524072] pci_bus 0000:07: resource 11 [mem 0x000d8000-0x000dbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524075] pci_bus 0000:07: resource 12 [mem 0x000dc000-0x000dffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524077] pci_bus 0000:07: resource 13 [mem 0x000e0000-0x000e3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524079] pci_bus 0000:07: resource 14 [mem 0x000e4000-0x000e7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524082] pci_bus 0000:07: resource 15 [mem 0x000e8000-0x000ebfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524084] pci_bus 0000:07: resource 16 [mem 0x000ec000-0x000effff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524086] pci_bus 0000:07: resource 17 [mem 0x000f0000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524089] pci_bus 0000:07: resource 18 [mem 0xb0000000-0xdfffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524091] pci_bus 0000:07: resource 19 [mem 0xf0000000-0xfffdffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524094] pci_bus 0000:08: resource 0 [io  0x2000-0x2fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524096] pci_bus 0000:08: resource 1 [mem 0xd4000000-0xd4ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524099] pci_bus 0000:08: resource 2 [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524139] NET: Registered protocol family 2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524409] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524682] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525090] TCP: Hash tables configured (established 65536 bind 65536)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525139] TCP: reno registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525156] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525225] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525362] NET: Registered protocol family 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525386] pci 0000:00:01.0: Video device with shadowed ROM
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525454] pci 0000:00:10.0: enabling device (0000 -> 0002)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.637840] PCI: CLS mismatch (64 != 32), using 64 bytes
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.693487] Trying to unpack rootfs image as initramfs...
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.114976] Freeing initrd memory: 19000K (ffff880035ad4000 - ffff880036d62000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115037] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115041] software IO TLB [mem 0x8b08d000-0x8f08d000] (64MB) mapped at [ffff88008b08d000-ffff88008f08cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115373] microcode: CPU0: patch_level=0x03000027
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115383] microcode: CPU1: patch_level=0x03000027
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115525] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115539] LVT offset 0 assigned for vector 0x400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115563] perf: AMD IBS detected (0x000000ff)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115609] Scanning for low memory corruption every 60 seconds
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116031] futex hash table entries: 1024 (order: 4, 65536 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116054] Initialise system trusted keyring
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116082] audit: initializing netlink subsys (disabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116105] audit: type=2000 audit(1437944743.972:1): initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116689] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.118836] zpool: loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.118840] zbud: loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.119247] VFS: Disk quotas dquot_6.5.2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.119314] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.120170] fuse init (API version 7.23)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.120365] msgmni has been set to 14894
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.120457] Key type big_key registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121159] Key type asymmetric registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121166] Asymmetric key parser 'x509' registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121241] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121339] io scheduler noop registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121343] io scheduler deadline registered (default)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121414] io scheduler cfq registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.122913] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.122936] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123015] vesafb: mode is 1366x768x32, linelength=5504, pages=0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123016] vesafb: scrolling: redraw
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123019] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123350] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90010f00000, using 4160k, total 4160k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123685] Console: switching to colour frame buffer device 170x48
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123713] fb0: VESA VGA frame buffer device
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124146] ACPI: AC Adapter [AC] (on-line)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124458] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124463] ACPI: Sleep Button [SLPB]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124514] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124586] ACPI: Lid Switch [LID]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124636] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124639] ACPI: Power Button [PWRF]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124798] ACPI: acpi_idle registered with cpuidle
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.154579] thermal LNXTHERM:00: registered as thermal_zone0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.154585] ACPI: Thermal Zone [CPUZ] (65 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.178447] thermal LNXTHERM:01: registered as thermal_zone1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.178453] ACPI: Thermal Zone [GFXZ] (57 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.193333] thermal LNXTHERM:02: registered as thermal_zone2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.193339] ACPI: Thermal Zone [EXTZ] (44 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.208271] thermal LNXTHERM:03: registered as thermal_zone3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.208277] ACPI: Thermal Zone [LOCZ] (54 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.223238] thermal LNXTHERM:04: registered as thermal_zone4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.223244] ACPI: Thermal Zone [BATZ] (31 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.223317] GHES: HEST is not enabled!
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.223834] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.227570] Linux agpgart interface v0.103
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.230332] brd: module loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.231848] loop: module loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232163] libphy: Fixed MDIO Bus: probed
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232167] tun: Universal TUN/TAP device driver, 1.6
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232169] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232282] PPP generic driver version 2.4.2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232391] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232398] ehci-pci: EHCI PCI platform driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232763] QUIRK: Enable AMD PLL fix
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232799] ehci-pci 0000:00:12.2: EHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232807] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232813] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232826] ehci-pci 0000:00:12.2: debug port 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232877] ehci-pci 0000:00:12.2: irq 17, io mem 0xd814f000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241108] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241226] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241230] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241232] usb usb1: Product: EHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241235] usb usb1: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241237] usb usb1: SerialNumber: 0000:00:12.2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241512] hub 1-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241520] hub 1-0:1.0: 5 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242172] ehci-pci 0000:00:13.2: EHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242180] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242186] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242201] ehci-pci 0000:00:13.2: debug port 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242239] ehci-pci 0000:00:13.2: irq 17, io mem 0xd814d000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253093] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253208] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253211] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253214] usb usb2: Product: EHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253216] usb usb2: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253218] usb usb2: SerialNumber: 0000:00:13.2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253537] hub 2-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253545] hub 2-0:1.0: 5 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253952] ehci-platform: EHCI generic platform driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253972] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253979] ohci-pci: OHCI PCI platform driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.254342] ohci-pci 0000:00:12.0: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.254350] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.254387] ohci-pci 0000:00:12.0: irq 18, io mem 0xd8150000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.270170] ACPI: Battery Slot [BAT0] (battery present)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313162] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313166] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313168] usb usb3: Product: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313171] usb usb3: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313173] usb usb3: SerialNumber: 0000:00:12.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313582] hub 3-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313644] hub 3-0:1.0: 5 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.314173] ohci-pci 0000:00:13.0: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.314182] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.314216] ohci-pci 0000:00:13.0: irq 18, io mem 0xd814e000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373317] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373323] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373326] usb usb4: Product: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373328] usb usb4: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373330] usb usb4: SerialNumber: 0000:00:13.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373733] hub 4-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373793] hub 4-0:1.0: 5 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.374327] ohci-pci 0000:00:14.5: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.374335] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.374368] ohci-pci 0000:00:14.5: irq 18, io mem 0xd814c000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433226] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433231] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433233] usb usb5: Product: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433235] usb usb5: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433236] usb usb5: SerialNumber: 0000:00:14.5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433637] hub 5-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433697] hub 5-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433908] ohci-platform: OHCI generic platform driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433929] uhci_hcd: USB Universal Host Controller Interface driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434267] xhci_hcd 0000:00:10.0: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434277] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434504] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434508] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434512] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434617] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434619] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434622] usb usb6: Product: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434624] usb usb6: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434627] usb usb6: SerialNumber: 0000:00:10.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.435014] hub 6-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.435074] hub 6-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.435261] xhci_hcd 0000:00:10.0: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.435267] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437918] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437921] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437923] usb usb7: Product: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437926] usb usb7: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437928] usb usb7: SerialNumber: 0000:00:10.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438173] hub 7-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438222] hub 7-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438705] xhci_hcd 0000:00:10.1: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438713] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438941] xhci_hcd 0000:00:10.1: irq 43 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438946] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438950] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439052] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439054] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439057] usb usb8: Product: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439059] usb usb8: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439061] usb usb8: SerialNumber: 0000:00:10.1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439389] hub 8-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439448] hub 8-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439650] xhci_hcd 0000:00:10.1: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439656] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442344] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442347] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442348] usb usb9: Product: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442350] usb usb9: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442352] usb usb9: SerialNumber: 0000:00:10.1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442611] hub 9-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442670] hub 9-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442917] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.445277] i8042: Detected active multiplexing controller, rev 1.1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446422] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446427] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446460] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446488] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446515] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447082] mousedev: PS/2 mouse device common for all mice
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447506] rtc_cmos 00:03: RTC can wake from S4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447645] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447680] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447779] device-mapper: uevent: version 1.0.3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447895] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447922] ledtrig-cpu: registered to indicate activity on CPUs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.448047] TCP: cubic registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.448197] NET: Registered protocol family 10
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.448560] NET: Registered protocol family 17
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.448584] Key type dns_resolver registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.449189] Loading compiled-in X.509 certificates
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.450604] Loaded X.509 cert 'Magrathea: Glacier signing key: 4b6de31c0185e45a0c0d73ca36f8fa02edc6253a'
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.450623] registered taskstats version 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.453622] Key type trusted registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459083] Key type encrypted registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459097] AppArmor: AppArmor sha1 policy hashing enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459101] ima: No TPM chip found, activating TPM-bypass!
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459136] evm: HMAC attrs: 0x1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459726]   Magic number: 7:701:96
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459881] rtc_cmos 00:03: setting system clock to 2015-07-26 21:05:44 UTC (1437944744)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.460097] acpi-cpufreq: overriding BIOS provided _PSD data
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.460252] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.460253] EDD information not available.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.460344] PM: Hibernation image not present or could not be loaded.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.462585] Freeing unused kernel memory: 1352K (ffffffff81d1c000 - ffffffff81e6e000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.462589] Write protecting the kernel read-only data: 12288k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.464849] Freeing unused kernel memory: 552K (ffff880001776000 - ffff880001800000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.466735] Freeing unused kernel memory: 480K (ffff880001b88000 - ffff880001c00000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.471790] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.490379] systemd-udevd[103]: starting version 204
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516021] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516037] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516288] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516507] r8169 0000:02:00.0 eth0: RTL8168e/8111e at 0xffffc9000003a000, e4:11:5b:40:3b:c6, XID 0c200000 IRQ 46
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516510] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.524036] sdhci: Secure Digital Host Controller Interface driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.524040] sdhci: Copyright(c) Pierre Ossman
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.526871] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2392] (rev 30)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.527840] mmc0: no vqmmc regulator found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.527844] mmc0: no vmmc regulator found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.528059] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.528083] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 30)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.528196] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.555029] ahci 0000:00:11.0: version 3.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556000] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556064] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556069] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556611] scsi0 : ahci
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556743] scsi1 : ahci
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556855] ata1: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151100 irq 47
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556858] ata2: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151180 irq 47
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.557095] usb 1-5: new high-speed USB device number 2 using ehci-pci
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742168] usb 1-5: New USB device found, idVendor=0461, idProduct=4dc7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742180] usb 1-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742187] usb 1-5: Product: HP HD Webcam [Fixed]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742192] usb 1-5: Manufacturer: Primax Electronics Ltd.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742196] usb 1-5: SerialNumber: PMX02
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.045198] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.045237] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.046163] ata1.00: ATA-8: TOSHIBA MK6476GSX, GS001C, max UDMA/100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.046171] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.046878] ata1.00: configured for UDMA/100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047341] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6476GS 1C   PQ: 0 ANSI: 5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047747] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047792] sd 0:0:0:0: [sda] Write Protect is off
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047813] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047823] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.049400] ata2.00: ATAPI: hp       DVDRAM GT50N, MP00, max UDMA/100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.053671] ata2.00: configured for UDMA/100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.058160] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT50N     MP00 PQ: 0 ANSI: 5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.077929] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.077939] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.078260] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.078343] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.106385]  sda: sda1 sda2 sda3 sda4 < sda5 >
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.107239] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.113300] tsc: Refined TSC clocksource calibration: 1896.551 MHz
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.269231] usb 4-5: new full-speed USB device number 2 using ohci-pci
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.419325] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..4876]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.430431] usb 4-5: New USB device found, idVendor=0cf3, idProduct=3005
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.430437] usb 4-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.494488] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x640000/0xa0400, board id: 1397, fw id: 780218
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.543485] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.553163] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.113758] Switched to clocksource tsc
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.235298] random: init urandom read with 111 bits of entropy available
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.459277] random: nonblocking pool is initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.803888] init: plymouth-upstart-bridge main process (164) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.803904] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.807426] init: plymouth-upstart-bridge main process (178) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.807442] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.810148] init: plymouth-upstart-bridge main process (180) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.810168] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.813743] init: plymouth-upstart-bridge main process (181) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.813760] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.816408] init: plymouth-upstart-bridge main process (183) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.816428] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.819737] init: plymouth-upstart-bridge main process (184) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.819753] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.822392] init: plymouth-upstart-bridge main process (186) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.822407] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.826166] init: plymouth-upstart-bridge main process (187) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.826182] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.828592] init: plymouth-upstart-bridge main process (189) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.828606] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.832307] init: plymouth-upstart-bridge main process (190) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.832323] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.834875] init: plymouth-upstart-bridge main process (192) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.834888] init: plymouth-upstart-bridge respawning too fast, stopped
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.202275] Adding 20970492k swap on /dev/sda5.  Priority:-1 extents:1 across:20970492k FS
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.400169] systemd-udevd[293]: starting version 204
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.541776] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.767833] lp: driver loaded but no devices found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.786934] ppdev: user-space parallel port driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.791414] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.813545] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.873269] acpi device:00: registered as cooling_device2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.873395] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.874085] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.876958] hp_accel: laptop model unknown, using default axes configuration
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.886835] lis3lv02d: 8 bits 3DC sensor found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.892436] wmi: Mapper loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.893119] acpi device:0a: registered as cooling_device3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.893467] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input13
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.893865] snd_hda_intel 0000:00:01.1: irq 48 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.918634] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input14
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.923997] sound hdaudioC1D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924008] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924011] sound hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924013] sound hdaudioC1D0:    mono: mono_out=0x0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924015] sound hdaudioC1D0:    inputs:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924018] sound hdaudioC1D0:      Internal Mic=0x11
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924021] sound hdaudioC1D0:      Mic=0xc
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.927412] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input15
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.935148] cfg80211: Calling CRDA to update world regulatory domain
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.959482] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.959595] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input17
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.991057] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B06 (\_SB_.PCI0.SMBS.SMBO) (20140424/utaddress-254)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.991068] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.092049] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.092054] AMD IOMMUv2 functionality not available on this system
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173046] ath: phy0: ASPM enabled: 0x42
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173052] ath: EEPROM regdomain: 0x60
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173055] ath: EEPROM indicates we should expect a direct regpair map
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173058] ath: Country alpha2 being used: 00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173059] ath: Regpair used: 0x60
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.182736] kvm: Nested Virtualization enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.182742] kvm: Nested Paging enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199184] Bluetooth: Core ver 2.19
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199217] NET: Registered protocol family 31
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199219] Bluetooth: HCI device and connection manager initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199228] Bluetooth: HCI socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199231] Bluetooth: L2CAP socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199243] Bluetooth: SCO socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.205212] Bluetooth: RFCOMM TTY layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.205225] Bluetooth: RFCOMM socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.205233] Bluetooth: RFCOMM ver 1.11
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.209157] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.209670] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011360000, irq=19
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.216186] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.216190] Bluetooth: BNEP filters: protocol multicast
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.216200] Bluetooth: BNEP socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.260372] audit: type=1400 audit(1437933953.293:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=505 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.260383] audit: type=1400 audit(1437933953.293:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=505 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.261030] audit: type=1400 audit(1437933953.293:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=505 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.263329] audit: type=1400 audit(1437933953.297:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.263342] audit: type=1400 audit(1437933953.297:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.263347] audit: type=1400 audit(1437933953.297:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.263994] audit: type=1400 audit(1437933953.297:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.264002] audit: type=1400 audit(1437933953.297:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.264346] audit: type=1400 audit(1437933953.297:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.267788] usbcore: registered new interface driver btusb
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.361791] init: cups main process (550) killed by HUP signal
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.361806] init: cups main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s failsafe: Failsafe of 120 seconds reached.
Jul 26 21:05:53 ivan-HP-ProBook-4535s rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.632452] init: failsafe main process (605) killed by TERM signal
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683599] cfg80211: World regulatory domain updated:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683607] cfg80211:  DFS Master region: unset
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683609] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683613] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683616] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683619] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683621] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683623] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.768179] input: HP WMI hotkeys as /devices/virtual/input/input18
Jul 26 21:05:53 ivan-HP-ProBook-4535s bluetoothd[499]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Jul 26 21:05:53 ivan-HP-ProBook-4535s bluetoothd[499]: Adapter /org/bluez/499/hci0 has been enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-5"
Jul 26 21:05:53 ivan-HP-ProBook-4535s mtp-probe: bus: 1, device: 2 was not an MTP device
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.011267] media: Linux media interface: v0.10
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.016938] Linux video capture interface: v2.00
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.033081] audit: type=1400 audit(1437933954.065:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=760 comm="apparmor_parser"
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.033343] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (0461:4dc7)
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.119890] hp_wmi: Unknown event_id - 0 - 0x0
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.119949] pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.119964] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.307218] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input19
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.307366] usbcore: registered new interface driver uvcvideo
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.307368] USB Video Class driver (1.1.1)
Jul 26 21:05:54 ivan-HP-ProBook-4535s ModemManager[674]: <info>  ModemManager (version 1.0.0) starting...
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.494590] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.494596] Disabling lock debugging due to kernel taint
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.509331] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.550511] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7226 MBytes.
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.550675] <6>[fglrx]   vendor: 1002 device: 9649 revision: 0 count: 1
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.551014] <6>[fglrx]   vendor: 1002 device: 6760 revision: 0 count: 2
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.551344] <6>[fglrx] ioport: bar 1, base 0x7000, size: 0x100
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.552014] <6>[fglrx] ioport: bar 4, base 0x6000, size: 0x100
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.552024] pci 0000:01:00.0: enabling device (0000 -> 0003)
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.552246] <6>[fglrx] Kernel PAT support is enabled
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.552281] <6>[fglrx] module loaded - fglrx 15.20.3 [Jun 22 2015] with 2 minors
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> NetworkManager (version 0.9.8.8) is starting...
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WEXT support is enabled
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> DNS: loaded plugin dnsmasq
Jul 26 21:05:54 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul 26 21:05:54 ivan-HP-ProBook-4535s polkitd[835]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jul 26 21:05:54 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: init!
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: update_system_hostname
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:       interface-parser: parsing file /etc/network/interfaces
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:       interface-parser: finished parsing file /etc/network/interfaces
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPluginIfupdown: management mode: unmanaged
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: end _init.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: init!
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: end _init.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Loaded plugin (null): (null)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    Ifupdown: get unmanaged devices count: 0
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: (27823888) ... get_connections.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: (27823888) ... get_connections (managed=false): return empty list.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    keyfile: parsing Ivan Mihaylov ... 
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    keyfile:     read connection 'Ivan Mihaylov'
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    keyfile: parsing Sinjo13 ... 
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    keyfile:     read connection 'Sinjo13'
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: (27630416) ... get_connections.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: (27630416) connections count: 0
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    Ifupdown: get unmanaged devices count: 0
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/ieee80211/phy0/rfkill0) (driver ath9k)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/platform/hp-wmi/rfkill/rfkill2) (platform driver hp-wmi)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Networking is enabled by state file
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> failed to allocate link cache: (-12) Object not found
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): carrier is OFF
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): bringing up device.
Jul 26 21:05:55 ivan-HP-ProBook-4535s anacron[931]: Anacron 2.3 started on 2015-07-26
Jul 26 21:05:55 ivan-HP-ProBook-4535s anacron[931]: Normal exit (0 jobs run)
Jul 26 21:05:55 ivan-HP-ProBook-4535s acpid: starting up with netlink and the input layer
Jul 26 21:05:55 ivan-HP-ProBook-4535s ntpdate[1005]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jul 26 21:05:55 ivan-HP-ProBook-4535s ntpdate[1005]: no servers can be used, exiting
Jul 26 21:05:55 ivan-HP-ProBook-4535s cron[890]: (CRON) INFO (pidfile fd = 3)
Jul 26 21:05:55 ivan-HP-ProBook-4535s cron[1026]: (CRON) STARTUP (fork ok)
Jul 26 21:05:55 ivan-HP-ProBook-4535s acpid: 11 rules loaded
Jul 26 21:05:55 ivan-HP-ProBook-4535s acpid: waiting for events: event logging is off
Jul 26 21:05:55 ivan-HP-ProBook-4535s cron[1026]: (CRON) INFO (Running @reboot jobs)
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.285947] vboxdrv: Found 2 processor cores.
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.288216] vboxdrv: fAsync=0 offMin=0x4aa offMax=0x2275
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.288367] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.288369] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.290952] r8169 0000:02:00.0 eth0: link down
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.291618] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): preparing device.
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): using nl80211 for WiFi device control
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): driver supports Access Point (AP) mode
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): bringing up device.
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): preparing device.
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.312799] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 26 21:05:55 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> urfkill disappeared from the bus
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.322835] vboxpci: IOMMU not found (not registered)
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> ModemManager available in the bus
Jul 26 21:05:55 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> wpa_supplicant started
Jul 26 21:05:55 ivan-HP-ProBook-4535s wpa_supplicant[1055]: Successfully initialized wpa_supplicant
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0) supports 4 scan SSIDs
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> Trying to remove a non-existant call id.
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: starting -> ready
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0) supports 4 scan SSIDs
Jul 26 21:05:55 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: Reject scan trigger since one is already pending
Jul 26 21:05:55 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 21:05:56 ivan-HP-ProBook-4535s whoopsie[927]: whoopsie 0.2.24.6 starting up.
Jul 26 21:05:56 ivan-HP-ProBook-4535s whoopsie[927]: Using lock path: /var/lock/whoopsie/lock
Jul 26 21:05:56 ivan-HP-ProBook-4535s whoopsie[1138]: offline
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.268300] init: plymouth-splash main process (1161) terminated with status 1
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Auto-activating connection 'Ivan Mihaylov'.
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) starting connection 'Ivan Mihaylov'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> NetworkManager state is now CONNECTING
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0/wireless): connection 'Ivan Mihaylov' has security, and secrets exist.  No new secrets needed.
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'ssid' value 'Ivan Mihaylov'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'scan_ssid' value '1'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'psk' value '<omitted>'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: set interface ap_scan to 1
Jul 26 21:05:56 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: SME: Trying to authenticate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.389769] wlan0: authenticate with c8:3a:35:4d:4b:08
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jul 26 21:05:56 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: Trying to associate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.396041] wlan0: send auth to c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.397785] wlan0: authenticated
Jul 26 21:05:56 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: Associated with c8:3a:35:4d:4b:08
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.398856] wlan0: associate with c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.402743] wlan0: RX AssocResp from c8:3a:35:4d:4b:08 (capab=0x11 status=0 aid=2)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.402838] wlan0: associated
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.402883] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.402935] cfg80211: Calling CRDA for country: CN
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: authenticating -> associated
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406461] ath: EEPROM regdomain: 0x809c
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406467] ath: EEPROM indicates we should expect a country code
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406469] ath: doing EEPROM country->regdmn map search
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406470] ath: country maps to regdmn code: 0x52
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406472] ath: Country alpha2 being used: CN
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406474] ath: Regpair used: 0x52
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406476] ath: regdomain 0x809c dynamically updated by country IE
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406500] cfg80211: Regulatory domain changed to country: CN
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406502] cfg80211:  DFS Master region: unset
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406504] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406507] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406510] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406512] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406514] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406516] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul 26 21:05:57 ivan-HP-ProBook-4535s accounts-daemon[1218]: started daemon version 0.6.35
Jul 26 21:05:57 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul 26 21:05:57 ivan-HP-ProBook-4535s ModemManager[674]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0': not supported by any plugin
Jul 26 21:05:57 ivan-HP-ProBook-4535s ModemManager[674]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0': not supported by any plugin
Jul 26 21:05:57 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: associated -> group handshake
Jul 26 21:06:00 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul 26 21:06:00 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul 26 21:06:00 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: WPA: Key negotiation completed with c8:3a:35:4d:4b:08 [PTK=CCMP GTK=CCMP]
Jul 26 21:06:00 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: CTRL-EVENT-CONNECTED - Connection to c8:3a:35:4d:4b:08 completed [id=0 id_str=]
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: group handshake -> completed
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Ivan Mihaylov'.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> dhclient started with pid 1375
Jul 26 21:06:00 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jul 26 21:06:00 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: All rights reserved.
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: 
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully called chroot.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully dropped privileges.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully limited resources.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Running.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 1378 of process 1378 (n/a) owned by '112' high priority at nice level -11.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 1 threads of 1 processes of 1 users.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Watchdog thread running.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Canary thread running.
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Listening on LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Sending on   LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Sending on   Socket/fallback
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 255.255.255.255 port 67 (xid=0x2e3e2690)
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: bound to 192.168.0.102 -- renewal in 34908 seconds.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info>   address 192.168.0.102
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info>   prefix 24 (255.255.255.0)
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info>   gateway 192.168.0.1
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info>   nameserver '192.168.1.1'
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 1453 of process 1378 (n/a) owned by '112' RT at priority 5.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 2 threads of 1 processes of 1 users.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 1471 of process 1378 (n/a) owned by '112' RT at priority 5.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 3 threads of 1 processes of 1 users.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 1472 of process 1378 (n/a) owned by '112' RT at priority 5.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 4 threads of 1 processes of 1 users.
Jul 26 21:06:00 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/HFPAG
Jul 26 21:06:00 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/HFPHS
Jul 26 21:06:00 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/A2DPSource
Jul 26 21:06:00 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/A2DPSink
Jul 26 21:06:01 ivan-HP-ProBook-4535s anacron[1490]: Anacron 2.3 started on 2015-07-26
Jul 26 21:06:01 ivan-HP-ProBook-4535s anacron[1490]: Normal exit (0 jobs run)
Jul 26 21:06:01 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 26 21:06:01 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 26 21:06:01 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Using config file /etc/colord.conf
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Using mapping database file /var/lib/colord/mapping.db
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Using device database file /var/lib/colord/storage.db
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: loaded plugin libcd_plugin_scanner.so
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: loaded plugin libcd_plugin_camera.so
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Daemon ready for requests
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 26 21:06:01 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Policy set 'Ivan Mihaylov' (wlan0) as default for IPv4 routing and DNS.
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> DNS: starting dnsmasq...
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> dnsmasq not available on the bus, can't update servers.
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <error> [1437933961.699190] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> DNS: plugin dnsmasq update failed
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Jul 26 21:06:01 ivan-HP-ProBook-4535s dnsmasq[1633]: started, version 2.68 cache disabled
Jul 26 21:06:01 ivan-HP-ProBook-4535s dnsmasq[1633]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jul 26 21:06:01 ivan-HP-ProBook-4535s dnsmasq[1633]: DBus support enabled: connected to system bus
Jul 26 21:06:01 ivan-HP-ProBook-4535s dnsmasq[1633]: warning: no upstream servers configured
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Device added: xrandr-default
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-7a9564ffe8e4686f7064491b7f3c6153
Jul 26 21:06:02 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) successful, device activated.
Jul 26 21:06:02 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 21:06:02 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> dnsmasq appeared on DBus: :1.43
Jul 26 21:06:02 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 21:06:02 ivan-HP-ProBook-4535s dnsmasq[1633]: setting upstream servers from DBus
Jul 26 21:06:02 ivan-HP-ProBook-4535s dnsmasq[1633]: using nameserver 192.168.1.1#53
Jul 26 21:06:02 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 21:06:02 ivan-HP-ProBook-4535s whoopsie[1138]: message repeated 3 times: [ offline]
Jul 26 21:06:02 ivan-HP-ProBook-4535s whoopsie[1138]: online
Jul 26 21:06:05 ivan-HP-ProBook-4535s colord: device removed: xrandr-default
Jul 26 21:06:05 ivan-HP-ProBook-4535s colord: Profile removed: icc-7a9564ffe8e4686f7064491b7f3c6153
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WiFi hardware radio set enabled
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.sleep-wake: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s kernel: [   22.420326] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 21:06:05 ivan-HP-ProBook-4535s kernel: [   22.420339] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 21:06:09 ivan-HP-ProBook-4535s ntpdate[1766]: step time server 91.189.89.199 offset 0.514630 sec
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 2065 of process 2065 (n/a) owned by '1000' high priority at nice level -11.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 5 threads of 2 processes of 2 users.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 2069 of process 2065 (n/a) owned by '1000' RT at priority 5.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 6 threads of 2 processes of 2 users.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 2072 of process 2065 (n/a) owned by '1000' RT at priority 5.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 7 threads of 2 processes of 2 users.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 2073 of process 2065 (n/a) owned by '1000' RT at priority 5.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 8 threads of 2 processes of 2 users.
Jul 26 21:06:09 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/HFPAG
Jul 26 21:06:09 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/HFPHS
Jul 26 21:06:09 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/A2DPSource
Jul 26 21:06:09 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/A2DPSink
Jul 26 21:06:09 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Jul 26 21:06:09 ivan-HP-ProBook-4535s colord: Device added: xrandr-default
Jul 26 21:06:09 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.locale1'
Jul 26 21:06:10 ivan-HP-ProBook-4535s colord: Profile added: icc-8047dcbd0521d15201185b4fe16ea653
Jul 26 21:06:12 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jul 26 21:06:13 ivan-HP-ProBook-4535s udisksd[2221]: udisks daemon version 2.1.3 starting
Jul 26 21:06:13 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jul 26 21:06:13 ivan-HP-ProBook-4535s udisksd[2221]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jul 26 21:06:19 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 21:06:21 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 26 21:06:21 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 26 21:06:21 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 26 21:06:21 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 26 21:06:23 ivan-HP-ProBook-4535s kernel: [   40.427257] audit_printk_skb: 150 callbacks suppressed
Jul 26 21:06:23 ivan-HP-ProBook-4535s kernel: [   40.427263] audit: type=1400 audit(1437933983.975:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2351 comm="apparmor_parser"
Jul 26 21:06:23 ivan-HP-ProBook-4535s kernel: [   40.427276] audit: type=1400 audit(1437933983.975:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2351 comm="apparmor_parser"
Jul 26 21:06:23 ivan-HP-ProBook-4535s kernel: [   40.427828] audit: type=1400 audit(1437933983.975:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2351 comm="apparmor_parser"
Jul 26 21:06:25 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/HFPAG
Jul 26 21:06:25 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/HFPHS
Jul 26 21:06:25 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/A2DPSource
Jul 26 21:06:25 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/A2DPSink
Jul 26 21:06:42 ivan-HP-ProBook-4535s gnome-session[1995]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Jul 26 21:11:14 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Jul 26 21:17:01 ivan-HP-ProBook-4535s CRON[2709]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 26 21:21:45 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jul 26 21:21:45 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

From what I understand there is some issue with the signature of the flgrx, but is this a critical issue? Also what are those bogus alignments? 

And last but not least - is there something more to worry about from what could be seen from the logs?

Sorry for the stupid questions and thank you for spending your time with my issues... 

Regards,
Ivan

---

### Post by Ivan_Mihaylov on 2015-07-26
> **oldfred said:**
> I do not know AMD.
But you had another longer time stamp gap. And it had this suggestion, have you tried it?
22.368420 use pci=pcie_bus_safe

That would be a boot option that you add likenomodeset on linux line in grub menu. Test just by booting and editing grub. That is a one time change but if it works then it can be made permanent.

If you only have Ubuntu and do not get grub menu hold shift key from BIOS until menu appears.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Generally best to not download drivers directly from vendor. Ubuntu repository has drivers, but often not most current. But most current driver usually only needed for very new systems. And for those very new systems other users create ppa's with updated drivers that will work.
Driver has to be re-integrated into every kernel you get. If from repository that is automatic. If downloaded from vendor you have to do that before rebooting after a new kernel is downloaded.

I have not followed AMD, as I have nVidia, but it is important to have the correct version driver to match your card/chip. And versions vary a lot.

#To see video:

sudo lshw | grep -A 11 display
lspci | grep VGA

#What is installed
dkms status

I used the pci mode suggestion and the nomodest. The boot results are:

```
[    1.123685] Console: switching to colour frame buffer device 170x48[    1.123713] fb0: VESA VGA frame buffer device
[    1.124146] ACPI: AC Adapter [AC] (on-line)
[    1.124458] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    1.124463] ACPI: Sleep Button [SLPB]
[    1.124514] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    1.124586] ACPI: Lid Switch [LID]
[    1.124636] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.124639] ACPI: Power Button [PWRF]
[    1.124798] ACPI: acpi_idle registered with cpuidle
[    1.154579] thermal LNXTHERM:00: registered as thermal_zone0
[    1.154585] ACPI: Thermal Zone [CPUZ] (65 C)
[    1.178447] thermal LNXTHERM:01: registered as thermal_zone1
[    1.178453] ACPI: Thermal Zone [GFXZ] (57 C)
[    1.193333] thermal LNXTHERM:02: registered as thermal_zone2
[    1.193339] ACPI: Thermal Zone [EXTZ] (44 C)
[    1.208271] thermal LNXTHERM:03: registered as thermal_zone3
[    1.208277] ACPI: Thermal Zone [LOCZ] (54 C)
[    1.223238] thermal LNXTHERM:04: registered as thermal_zone4
[    1.223244] ACPI: Thermal Zone [BATZ] (31 C)
[    1.223317] GHES: HEST is not enabled!
[    1.223834] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.227570] Linux agpgart interface v0.103
[    1.230332] brd: module loaded
[    1.231848] loop: module loaded
[    1.232163] libphy: Fixed MDIO Bus: probed
[    1.232167] tun: Universal TUN/TAP device driver, 1.6
[    1.232169] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.232282] PPP generic driver version 2.4.2
[    1.232391] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.232398] ehci-pci: EHCI PCI platform driver
[    1.232763] QUIRK: Enable AMD PLL fix
[    1.232799] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.232807] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.232813] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.232826] ehci-pci 0000:00:12.2: debug port 1
[    1.232877] ehci-pci 0000:00:12.2: irq 17, io mem 0xd814f000
[    1.241108] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.241226] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.241230] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.241232] usb usb1: Product: EHCI Host Controller
[    1.241235] usb usb1: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
[    1.241237] usb usb1: SerialNumber: 0000:00:12.2
[    1.241512] hub 1-0:1.0: USB hub found
[    1.241520] hub 1-0:1.0: 5 ports detected
[    1.242172] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.242180] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.242186] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.242201] ehci-pci 0000:00:13.2: debug port 1
[    1.242239] ehci-pci 0000:00:13.2: irq 17, io mem 0xd814d000
[    1.253093] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.253208] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.253211] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.253214] usb usb2: Product: EHCI Host Controller
[    1.253216] usb usb2: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
[    1.253218] usb usb2: SerialNumber: 0000:00:13.2
[    1.253537] hub 2-0:1.0: USB hub found
[    1.253545] hub 2-0:1.0: 5 ports detected
[    1.253952] ehci-platform: EHCI generic platform driver
[    1.253972] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.253979] ohci-pci: OHCI PCI platform driver
[    1.254342] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.254350] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.254387] ohci-pci 0000:00:12.0: irq 18, io mem 0xd8150000
[    1.270170] ACPI: Battery Slot [BAT0] (battery present)
[    1.313162] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.313166] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.313168] usb usb3: Product: OHCI PCI host controller
[    1.313171] usb usb3: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
[    1.313173] usb usb3: SerialNumber: 0000:00:12.0
[    1.313582] hub 3-0:1.0: USB hub found
[    1.313644] hub 3-0:1.0: 5 ports detected
[    1.314173] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.314182] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.314216] ohci-pci 0000:00:13.0: irq 18, io mem 0xd814e000
[    1.373317] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.373323] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.373326] usb usb4: Product: OHCI PCI host controller
[    1.373328] usb usb4: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
[    1.373330] usb usb4: SerialNumber: 0000:00:13.0
[    1.373733] hub 4-0:1.0: USB hub found
[    1.373793] hub 4-0:1.0: 5 ports detected
[    1.374327] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.374335] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 5
[    1.374368] ohci-pci 0000:00:14.5: irq 18, io mem 0xd814c000
[    1.433226] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.433231] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.433233] usb usb5: Product: OHCI PCI host controller
[    1.433235] usb usb5: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
[    1.433236] usb usb5: SerialNumber: 0000:00:14.5
[    1.433637] hub 5-0:1.0: USB hub found
[    1.433697] hub 5-0:1.0: 2 ports detected
[    1.433908] ohci-platform: OHCI generic platform driver
[    1.433929] uhci_hcd: USB Universal Host Controller Interface driver
[    1.434267] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.434277] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.434504] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
[    1.434508] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
[    1.434512] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    1.434617] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    1.434619] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.434622] usb usb6: Product: xHCI Host Controller
[    1.434624] usb usb6: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.434627] usb usb6: SerialNumber: 0000:00:10.0
[    1.435014] hub 6-0:1.0: USB hub found
[    1.435074] hub 6-0:1.0: 2 ports detected
[    1.435261] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.435267] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    1.437918] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
[    1.437921] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.437923] usb usb7: Product: xHCI Host Controller
[    1.437926] usb usb7: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.437928] usb usb7: SerialNumber: 0000:00:10.0
[    1.438173] hub 7-0:1.0: USB hub found
[    1.438222] hub 7-0:1.0: 2 ports detected
[    1.438705] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.438713] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    1.438941] xhci_hcd 0000:00:10.1: irq 43 for MSI/MSI-X
[    1.438946] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
[    1.438950] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
[    1.439052] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.439054] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.439057] usb usb8: Product: xHCI Host Controller
[    1.439059] usb usb8: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.439061] usb usb8: SerialNumber: 0000:00:10.1
[    1.439389] hub 8-0:1.0: USB hub found
[    1.439448] hub 8-0:1.0: 2 ports detected
[    1.439650] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.439656] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
[    1.442344] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.442347] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.442348] usb usb9: Product: xHCI Host Controller
[    1.442350] usb usb9: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
[    1.442352] usb usb9: SerialNumber: 0000:00:10.1
[    1.442611] hub 9-0:1.0: USB hub found
[    1.442670] hub 9-0:1.0: 2 ports detected
[    1.442917] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.445277] i8042: Detected active multiplexing controller, rev 1.1
[    1.446422] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.446427] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.446460] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.446488] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.446515] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.447082] mousedev: PS/2 mouse device common for all mice
[    1.447506] rtc_cmos 00:03: RTC can wake from S4
[    1.447645] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.447680] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.447779] device-mapper: uevent: version 1.0.3
[    1.447895] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.447922] ledtrig-cpu: registered to indicate activity on CPUs
[    1.448047] TCP: cubic registered
[    1.448197] NET: Registered protocol family 10
[    1.448560] NET: Registered protocol family 17
[    1.448584] Key type dns_resolver registered
[    1.449189] Loading compiled-in X.509 certificates
[    1.450604] Loaded X.509 cert 'Magrathea: Glacier signing key: 4b6de31c0185e45a0c0d73ca36f8fa02edc6253a'
[    1.450623] registered taskstats version 1
[    1.453622] Key type trusted registered
[    1.459083] Key type encrypted registered
[    1.459097] AppArmor: AppArmor sha1 policy hashing enabled
[    1.459101] ima: No TPM chip found, activating TPM-bypass!
[    1.459136] evm: HMAC attrs: 0x1
[    1.459726]   Magic number: 7:701:96
[    1.459881] rtc_cmos 00:03: setting system clock to 2015-07-26 21:05:44 UTC (1437944744)
[    1.460097] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.460252] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.460253] EDD information not available.
[    1.460344] PM: Hibernation image not present or could not be loaded.
[    1.462585] Freeing unused kernel memory: 1352K (ffffffff81d1c000 - ffffffff81e6e000)
[    1.462589] Write protecting the kernel read-only data: 12288k
[    1.464849] Freeing unused kernel memory: 552K (ffff880001776000 - ffff880001800000)
[    1.466735] Freeing unused kernel memory: 480K (ffff880001b88000 - ffff880001c00000)
[    1.471790] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.490379] systemd-udevd[103]: starting version 204
[    1.516021] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.516037] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.516288] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
[    1.516507] r8169 0000:02:00.0 eth0: RTL8168e/8111e at 0xffffc9000003a000, e4:11:5b:40:3b:c6, XID 0c200000 IRQ 46
[    1.516510] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.524036] sdhci: Secure Digital Host Controller Interface driver
[    1.524040] sdhci: Copyright(c) Pierre Ossman
[    1.526871] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2392] (rev 30)
[    1.527840] mmc0: no vqmmc regulator found
[    1.527844] mmc0: no vmmc regulator found
[    1.528059] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
[    1.528083] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 30)
[    1.528196] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
[    1.555029] ahci 0000:00:11.0: version 3.0
[    1.556000] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
[    1.556064] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.556069] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.556611] scsi0 : ahci
[    1.556743] scsi1 : ahci
[    1.556855] ata1: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151100 irq 47
[    1.556858] ata2: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151180 irq 47
[    1.557095] usb 1-5: new high-speed USB device number 2 using ehci-pci
[    1.742168] usb 1-5: New USB device found, idVendor=0461, idProduct=4dc7
[    1.742180] usb 1-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.742187] usb 1-5: Product: HP HD Webcam [Fixed]
[    1.742192] usb 1-5: Manufacturer: Primax Electronics Ltd.
[    1.742196] usb 1-5: SerialNumber: PMX02
[    2.045198] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.045237] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.046163] ata1.00: ATA-8: TOSHIBA MK6476GSX, GS001C, max UDMA/100
[    2.046171] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.046878] ata1.00: configured for UDMA/100
[    2.047341] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6476GS 1C   PQ: 0 ANSI: 5
[    2.047747] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    2.047792] sd 0:0:0:0: [sda] Write Protect is off
[    2.047794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.047813] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.047823] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.049400] ata2.00: ATAPI: hp       DVDRAM GT50N, MP00, max UDMA/100
[    2.053671] ata2.00: configured for UDMA/100
[    2.058160] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT50N     MP00 PQ: 0 ANSI: 5
[    2.077929] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.077939] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.078260] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.078343] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.106385]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.107239] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.113300] tsc: Refined TSC clocksource calibration: 1896.551 MHz
[    2.269231] usb 4-5: new full-speed USB device number 2 using ohci-pci
[    2.419325] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..4876]
[    2.430431] usb 4-5: New USB device found, idVendor=0cf3, idProduct=3005
[    2.430437] usb 4-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.494488] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x640000/0xa0400, board id: 1397, fw id: 780218
[    2.543485] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[    2.553163] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.113758] Switched to clocksource tsc
[    3.235298] random: init urandom read with 111 bits of entropy available
[    3.459277] random: nonblocking pool is initialized
[    3.803888] init: plymouth-upstart-bridge main process (164) terminated with status 1
[    3.803904] init: plymouth-upstart-bridge main process ended, respawning
[    3.807426] init: plymouth-upstart-bridge main process (178) terminated with status 1
[    3.807442] init: plymouth-upstart-bridge main process ended, respawning
[    3.810148] init: plymouth-upstart-bridge main process (180) terminated with status 1
[    3.810168] init: plymouth-upstart-bridge main process ended, respawning
[    3.813743] init: plymouth-upstart-bridge main process (181) terminated with status 1
[    3.813760] init: plymouth-upstart-bridge main process ended, respawning
[    3.816408] init: plymouth-upstart-bridge main process (183) terminated with status 1
[    3.816428] init: plymouth-upstart-bridge main process ended, respawning
[    3.819737] init: plymouth-upstart-bridge main process (184) terminated with status 1
[    3.819753] init: plymouth-upstart-bridge main process ended, respawning
[    3.822392] init: plymouth-upstart-bridge main process (186) terminated with status 1
[    3.822407] init: plymouth-upstart-bridge main process ended, respawning
[    3.826166] init: plymouth-upstart-bridge main process (187) terminated with status 1
[    3.826182] init: plymouth-upstart-bridge main process ended, respawning
[    3.828592] init: plymouth-upstart-bridge main process (189) terminated with status 1
[    3.828606] init: plymouth-upstart-bridge main process ended, respawning
[    3.832307] init: plymouth-upstart-bridge main process (190) terminated with status 1
[    3.832323] init: plymouth-upstart-bridge main process ended, respawning
[    3.834875] init: plymouth-upstart-bridge main process (192) terminated with status 1
[    3.834888] init: plymouth-upstart-bridge respawning too fast, stopped
[    9.202275] Adding 20970492k swap on /dev/sda5.  Priority:-1 extents:1 across:20970492k FS
[    9.400169] systemd-udevd[293]: starting version 204
[    9.541776] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    9.767833] lp: driver loaded but no devices found
[    9.786934] ppdev: user-space parallel port driver
[    9.791414] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.813545] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.873269] acpi device:00: registered as cooling_device2
[    9.873395] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
[    9.874085] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
[    9.876958] hp_accel: laptop model unknown, using default axes configuration
[    9.886835] lis3lv02d: 8 bits 3DC sensor found
[    9.892436] wmi: Mapper loaded
[    9.893119] acpi device:0a: registered as cooling_device3
[    9.893467] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input13
[    9.893865] snd_hda_intel 0000:00:01.1: irq 48 for MSI/MSI-X
[    9.918634] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input14
[    9.923997] sound hdaudioC1D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[    9.924008] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    9.924011] sound hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[    9.924013] sound hdaudioC1D0:    mono: mono_out=0x0
[    9.924015] sound hdaudioC1D0:    inputs:
[    9.924018] sound hdaudioC1D0:      Internal Mic=0x11
[    9.924021] sound hdaudioC1D0:      Mic=0xc
[    9.927412] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input15
[    9.935148] cfg80211: Calling CRDA to update world regulatory domain
[    9.959482] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
[    9.959595] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input17
[    9.991057] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B06 (\_SB_.PCI0.SMBS.SMBO) (20140424/utaddress-254)
[    9.991068] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.092049] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[   10.092054] AMD IOMMUv2 functionality not available on this system
[   10.173046] ath: phy0: ASPM enabled: 0x42
[   10.173052] ath: EEPROM regdomain: 0x60
[   10.173055] ath: EEPROM indicates we should expect a direct regpair map
[   10.173058] ath: Country alpha2 being used: 00
[   10.173059] ath: Regpair used: 0x60
[   10.182736] kvm: Nested Virtualization enabled
[   10.182742] kvm: Nested Paging enabled
[   10.199184] Bluetooth: Core ver 2.19
[   10.199217] NET: Registered protocol family 31
[   10.199219] Bluetooth: HCI device and connection manager initialized
[   10.199228] Bluetooth: HCI socket layer initialized
[   10.199231] Bluetooth: L2CAP socket layer initialized
[   10.199243] Bluetooth: SCO socket layer initialized
[   10.205212] Bluetooth: RFCOMM TTY layer initialized
[   10.205225] Bluetooth: RFCOMM socket layer initialized
[   10.205233] Bluetooth: RFCOMM ver 1.11
[   10.209157] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.209670] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011360000, irq=19
[   10.216186] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.216190] Bluetooth: BNEP filters: protocol multicast
[   10.216200] Bluetooth: BNEP socket layer initialized
[   10.260372] audit: type=1400 audit(1437933953.293:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=505 comm="apparmor_parser"
[   10.260383] audit: type=1400 audit(1437933953.293:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=505 comm="apparmor_parser"
[   10.261030] audit: type=1400 audit(1437933953.293:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=505 comm="apparmor_parser"
[   10.263329] audit: type=1400 audit(1437933953.297:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
[   10.263342] audit: type=1400 audit(1437933953.297:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
[   10.263347] audit: type=1400 audit(1437933953.297:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[   10.263994] audit: type=1400 audit(1437933953.297:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
[   10.264002] audit: type=1400 audit(1437933953.297:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[   10.264346] audit: type=1400 audit(1437933953.297:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[   10.267788] usbcore: registered new interface driver btusb
[   10.361791] init: cups main process (550) killed by HUP signal
[   10.361806] init: cups main process ended, respawning
[   10.632452] init: failsafe main process (605) killed by TERM signal
[   10.683599] cfg80211: World regulatory domain updated:
[   10.683607] cfg80211:  DFS Master region: unset
[   10.683609] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.683613] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.683616] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.683619] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.683621] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.683623] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   10.768179] input: HP WMI hotkeys as /devices/virtual/input/input18
[   11.011267] media: Linux media interface: v0.10
[   11.016938] Linux video capture interface: v2.00
[   11.033081] audit: type=1400 audit(1437933954.065:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=760 comm="apparmor_parser"
[   11.033343] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (0461:4dc7)
[   11.119890] hp_wmi: Unknown event_id - 0 - 0x0
[   11.119949] pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   11.119964] pci 0000:00:14.4: PCI bridge to [bus 07]
[   11.307218] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input19
[   11.307366] usbcore: registered new interface driver uvcvideo
[   11.307368] USB Video Class driver (1.1.1)
[   11.494590] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.494596] Disabling lock debugging due to kernel taint
[   11.509331] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
[   11.550511] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7226 MBytes.
[   11.550675] <6>[fglrx]   vendor: 1002 device: 9649 revision: 0 count: 1
[   11.551014] <6>[fglrx]   vendor: 1002 device: 6760 revision: 0 count: 2
[   11.551344] <6>[fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   11.552014] <6>[fglrx] ioport: bar 4, base 0x6000, size: 0x100
[   11.552024] pci 0000:01:00.0: enabling device (0000 -> 0003)
[   11.552246] <6>[fglrx] Kernel PAT support is enabled
[   11.552281] <6>[fglrx] module loaded - fglrx 15.20.3 [Jun 22 2015] with 2 minors
[   12.285947] vboxdrv: Found 2 processor cores.
[   12.288216] vboxdrv: fAsync=0 offMin=0x4aa offMax=0x2275
[   12.288367] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   12.288369] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[   12.290952] r8169 0000:02:00.0 eth0: link down
[   12.291618] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.312799] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.322835] vboxpci: IOMMU not found (not registered)
[   13.268300] init: plymouth-splash main process (1161) terminated with status 1
[   13.389769] wlan0: authenticate with c8:3a:35:4d:4b:08
[   13.396041] wlan0: send auth to c8:3a:35:4d:4b:08 (try 1/3)
[   13.397785] wlan0: authenticated
[   13.398856] wlan0: associate with c8:3a:35:4d:4b:08 (try 1/3)
[   13.402743] wlan0: RX AssocResp from c8:3a:35:4d:4b:08 (capab=0x11 status=0 aid=2)
[   13.402838] wlan0: associated
[   13.402883] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   13.402935] cfg80211: Calling CRDA for country: CN
[   13.406461] ath: EEPROM regdomain: 0x809c
[   13.406467] ath: EEPROM indicates we should expect a country code
[   13.406469] ath: doing EEPROM country->regdmn map search
[   13.406470] ath: country maps to regdmn code: 0x52
[   13.406472] ath: Country alpha2 being used: CN
[   13.406474] ath: Regpair used: 0x52
[   13.406476] ath: regdomain 0x809c dynamically updated by country IE
[   13.406500] cfg80211: Regulatory domain changed to country: CN
[   13.406502] cfg80211:  DFS Master region: unset
[   13.406504] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.406507] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.406510] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
[   13.406512] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[   13.406514] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
[   13.406516] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[   22.420326] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
[   22.420339] pci 0000:00:14.4: PCI bridge to [bus 07]
[   40.427257] audit_printk_skb: 150 callbacks suppressed
[   40.427263] audit: type=1400 audit(1437933983.975:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2351 comm="apparmor_parser"
[   40.427276] audit: type=1400 audit(1437933983.975:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2351 comm="apparmor_parser"
[   40.427828] audit: type=1400 audit(1437933983.975:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2351 comm="apparmor_parser"

```

What could've caused those lines?
```
[   22.420326] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment[   22.420339] pci 0000:00:14.4: PCI bridge to [bus 07]
[   40.427257] audit_printk_skb: 150 callbacks suppressed
[   40.427263] audit: type=1400 audit(1437933983.975:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2351 
```

I'm mainly worried that I misused the AMD vendor driver as I currently got 2 errors after loging. 

The info for the video is:

```
ivan@ivan-HP-ProBook-4535s:~$ sudo lshw | grep -A 11 display[sudo] password for ivan: 
Sorry, try again.
[sudo] password for ivan: 
        *-display
             description: VGA compatible controller
             product: Sumo [Radeon HD 6480G]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
             configuration: driver=fglrx_pci latency=0
             resources: irq:18 memory:b0000000-bfffffff ioport:7000(size=256) memory:d8100000-d813ffff
--
           *-display
                description: VGA compatible controller
                product: Seymour [Radeon HD 6400M/7400M Series]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:19 memory:c0000000-cfffffff memory:d8000000-d801ffff ioport:6000(size=256) memory:d8020000-d803ffff
ivan@ivan-HP-ProBook-4535s:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Sumo [Radeon HD 6480G]
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series]
ivan@ivan-HP-ProBook-4535s:~$ dkms status
fglrx-core, 15.200, 3.16.0-44-generic, x86_64: installed
virtualbox, 4.3.10, 3.16.0-44-generic, x86_64: installed

```

From what I see here the fglrx is installed, but how to see if it's working correctly?

This is the syslog for the current run:

```
Jul 26 20:48:11 ivan-HP-ProBook-4535s wpa_supplicant[1081]: wlan0: CTRL-EVENT-SCAN-STARTED Jul 26 20:50:18 ivan-HP-ProBook-4535s colord: device removed: xrandr-default
Jul 26 20:50:18 ivan-HP-ProBook-4535s colord: Profile removed: icc-8047dcbd0521d15201185b4fe16ea653
Jul 26 20:50:19 ivan-HP-ProBook-4535s dbus[495]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 26 20:50:19 ivan-HP-ProBook-4535s dbus[495]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 26 20:50:19 ivan-HP-ProBook-4535s rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="640" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul 26 20:51:53 ivan-HP-ProBook-4535s rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="665" x-info="http://www.rsyslog.com"] start
Jul 26 20:51:53 ivan-HP-ProBook-4535s rsyslogd: rsyslogd's groupid changed to 104
Jul 26 20:51:53 ivan-HP-ProBook-4535s rsyslogd: rsyslogd's userid changed to 101
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Linux version 3.16.0-44-generic (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #59~14.04.1-Ubuntu SMP Tue Jul 7 15:07:27 UTC 2015 (Ubuntu 3.16.0-44.59~14.04.1-generic 3.16.7-ckt14)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-44-generic root=UUID=06bbc19e-b72c-445e-851c-77c80ccf7f12 ro quiet splash nomodeset vt.handoff=7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] KERNEL supported cpus:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Intel GenuineIntel
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   AMD AuthenticAMD
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Centaur CentaurHauls
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008f08cfff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008f08d000-0x000000008f58cfff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008f58d000-0x000000008fbcefff] ACPI NVS
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbcf000-0x000000008fbfefff] ACPI data
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbff000-0x000000008fbfffff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024effffff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] SMBIOS 2.6 present.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] DMI: Hewlett-Packard HP ProBook 4535s/168B, BIOS 68CPC Ver. F.50 07/01/2014
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: No AGP bridge found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: last_pfn = 0x24f000 max_arch_pfn = 0x400000000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR default type: uncachable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   00000-9FFFF write-back
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   A0000-DFFFF uncachable
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   E0000-FFFFF write-protect
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR variable ranges enabled:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   1 base 0080000000 mask FFF0000000 write-back
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   2 base 00FFE00000 mask FFFFE00000 write-protect
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   3 base 00FFE10000 mask FFFFFF0000 write-protect
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   4 disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   5 disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   6 disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   7 disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] TOM2: 000000024f000000 aka 9456M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: last_pfn = 0x8fc00 max_arch_pfn = 0x400000000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Using GB pages for direct mapping
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbd000, 0x01fbdfff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbe000, 0x01fbefff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbf000, 0x01fbffff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x24ee00000-0x24effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x24ee00000-0x24effffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fc0000, 0x01fc0fff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x24c000000-0x24edfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x24c000000-0x24edfffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x24bffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x200000000-0x23fffffff] page 1G
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x240000000-0x24bffffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x8f08cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x80000000-0x8effffff] page 2M
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x8f000000-0x8f08cfff] page 4k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x8fbff000-0x8fbfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x8fbff000-0x8fbfffff] page 4k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fc1000, 0x01fc1fff] PGTABLE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] RAMDISK: [mem 0x35ad4000-0x36d61fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: RSDP 0x00000000000F2F00 000014 (v00 HPQOEM)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: RSDT 0x000000008FBFE038 000044 (v01 HPQOEM SLIC-MPC 00000003      01000013)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: FACP 0x000000008FBFD000 000074 (v01 HPQOEM 168B     00000003 HP   00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20140424/tbfadt-649)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: DSDT 0x000000008FBD7000 0230B2 (v01 HPQOEM 168B     00000001 INTL 20060912)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: FACS 0x000000008FB8F000 000040
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: APIC 0x000000008FBFC000 000084 (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: MCFG 0x000000008FBFB000 00003C (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: HPET 0x000000008FBD4000 000038 (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD3000 00072C (v01 AMD    POWERNOW 00000001 AMD  00000001)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD1000 00193D (v02 AMD    ALIB     00000001 MSFT 04000000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD0000 00078F (v01 HP     AMDSGTBL 00000001 INTL 20060912)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBCF000 000325 (v01 HP     HPZPODDT 00000001 INTL 20060912)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] No NUMA configuration found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x24effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   NODE_DATA [mem 0x24eff9000-0x24effdfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246e00000-ffff88024e5fffff] on node 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Zone ranges:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal   [mem 0x100000000-0x24effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Movable zone start for each node
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Early memory node ranges
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x00100000-0x8f08cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x8fbff000-0x8fbfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x100000000-0x24effffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] On node 0 totalpages: 1957931
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 21 pages reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32 zone: 9091 pages used for memmap
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32 zone: 581774 pages, LIFO batch:31
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal zone: 21440 pages used for memmap
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal zone: 1372160 pages, LIFO batch:31
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] nr_irqs_gsi: 40
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8f08d000-0x8f58cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8f58d000-0x8fbcefff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8fbcf000-0x8fbfefff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8fc00000-0xdfffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfedfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffdfffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: [mem 0x8fc00000-0xdfffffff] available for PCI devices
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88024ec00000 s81408 r8192 d20992 u524288
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] pcpu-alloc: s81408 r8192 d20992 u524288 alloc=1*2097152
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1927315
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Policy zone: Normal
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-44-generic root=UUID=06bbc19e-b72c-445e-851c-77c80ccf7f12 ro quiet splash nomodeset vt.handoff=7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: Checking aperture...
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: No AGP bridge found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Memory: 7606856K/7831724K available (7629K kernel code, 1131K rwdata, 3616K rodata, 1352K init, 1300K bss, 224868K reserved)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Hierarchical RCU implementation.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	Offload RCU callbacks from all CPUs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Console: colour dummy device 80x25
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] console [tty0] enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] allocated 31457280 bytes of page_cgroup
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] hpet clockevent registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000000] tsc: Detected 1896.422 MHz processor
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000051] Calibrating delay loop (skipped), value calculated using timer frequency.. 3792.84 BogoMIPS (lpj=7585688)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000056] pid_max: default: 32768 minimum: 301
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.000065] ACPI: Core revision 20140424
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.013537] ACPI: All ACPI Tables successfully acquired
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.047861] Security Framework initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.047883] AppArmor: AppArmor initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.047885] Yama: becoming mindful.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.048662] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.051541] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.052786] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.052800] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053157] Initializing cgroup subsys memory
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053189] Initializing cgroup subsys devices
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053197] Initializing cgroup subsys freezer
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053201] Initializing cgroup subsys net_cls
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053207] Initializing cgroup subsys blkio
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053213] Initializing cgroup subsys perf_event
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053216] Initializing cgroup subsys net_prio
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053225] Initializing cgroup subsys hugetlb
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053253] tseg: 008fc00000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053256] CPU: Physical Processor ID: 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053257] CPU: Processor Core ID: 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053259] mce: CPU supports 6 MCE banks
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053271] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053271] Last level dTLB entries: 4KB 1024, 2MB 128, 4MB 64, 1GB 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053271] tlb_flushall_shift: 6
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.053443] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.055063] ftrace: allocating 29259 entries in 115 pages
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.076667] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.116359] smpboot: CPU0: AMD A4-3305M APU with Radeon(tm) HD Graphics (fam: 12, model: 01, stepping: 00)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220987] Performance Events: AMD PMU driver.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220991] ... version:                0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220993] ... bit width:              48
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220994] ... generic registers:      4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220996] ... value mask:             0000ffffffffffff
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220997] ... max period:             00007fffffffffff
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.220998] ... fixed-purpose events:   0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.221000] ... event mask:             000000000000000f
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.223297] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.223411] x86: Booting SMP configuration:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.223413] .... node  #0, CPUs:      #1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.236554] x86: Booted up 1 node, 2 CPUs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.236557] smpboot: Total of 2 processors activated (7585.68 BogoMIPS)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.237312] devtmpfs: initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242986] evm: security.selinux
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242989] evm: security.SMACK64
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242990] evm: security.SMACK64EXEC
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242992] evm: security.SMACK64TRANSMUTE
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242993] evm: security.SMACK64MMAP
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242994] evm: security.ima
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.242995] evm: security.capability
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.243154] PM: Registering ACPI NVS region [mem 0x8f58d000-0x8fbcefff] (6561792 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.244694] pinctrl core: initialized pinctrl subsystem
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.244826] regulator-dummy: no parameters
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.244909] RTC time: 20:51:43, date: 07/26/15
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.244983] NET: Registered protocol family 16
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245215] cpuidle: using governor ladder
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245218] cpuidle: using governor menu
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245434] ACPI: bus type PCI registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245437] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245590] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.245594] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246174] PCI: Using configuration type 1 for base access
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246491] mtrr: your CPUs had inconsistent fixed MTRR settings
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246493] mtrr: your CPUs had inconsistent variable MTRR settings
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246494] mtrr: probably your BIOS does not setup all CPUs.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.246495] mtrr: corrected configuration.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.250354] ACPI: Added _OSI(Module Device)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.250359] ACPI: Added _OSI(Processor Device)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.250361] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.250363] ACPI: Added _OSI(Processor Aggregator Device)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437278] ACPI: Interpreter enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437297] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437303] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437320] ACPI: (supports S0 S3 S4 S5)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437321] ACPI: Using IOAPIC for interrupt routing
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.437554] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.440139] ACPI: Power Resource [APPR] (off)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.445946] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.445954] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446134] acpi PNP0A08:00: _OSC: platform does not support [PCIeCapability]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446247] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446250] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446252] acpi PNP0A08:00: _OSC: platform willing to grant [PCIeHotplug PME AER]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446254] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446382] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cf1ff])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446386] acpi PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000d3fff] (conflicts with Adapter ROM [mem 0x000cf800-0x000d07ff])
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446640] PCI host bridge to bus 0000:00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446644] pci_bus 0000:00: root bus resource [bus 00-ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446647] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446649] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446652] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446655] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446657] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446660] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446662] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446665] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446667] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446670] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446672] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446675] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446677] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446680] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446682] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xdfffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446685] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfffdffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446695] pci 0000:00:00.0: [1022:1705] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446805] pci 0000:00:01.0: [1002:9649] type 00 class 0x030000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446818] pci 0000:00:01.0: reg 0x10: [mem 0xb0000000-0xbfffffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446826] pci 0000:00:01.0: reg 0x14: [io  0x7000-0x70ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446833] pci 0000:00:01.0: reg 0x18: [mem 0xd8100000-0xd813ffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446883] pci 0000:00:01.0: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446948] pci 0000:00:01.1: [1002:1714] type 00 class 0x040300
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.446958] pci 0000:00:01.1: reg 0x10: [mem 0xd8144000-0xd8147fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447013] pci 0000:00:01.1: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447125] pci 0000:00:03.0: [1022:1708] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447185] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447259] pci 0000:00:04.0: [1022:1709] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447319] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447357] pci 0000:00:04.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447397] pci 0000:00:05.0: [1022:170a] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447456] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447493] pci 0000:00:05.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447583] pci 0000:00:07.0: [1022:170c] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447647] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447696] pci 0000:00:07.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447817] pci 0000:00:10.0: [1022:7812] type 00 class 0x0c0330
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447841] pci 0000:00:10.0: reg 0x10: [mem 0xd8148000-0xd8149fff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447951] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.447997] pci 0000:00:10.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448097] pci 0000:00:10.1: [1022:7812] type 00 class 0x0c0330
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448122] pci 0000:00:10.1: reg 0x10: [mem 0xd814a000-0xd814bfff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448240] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448285] pci 0000:00:10.1: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448384] pci 0000:00:11.0: [1022:7801] type 00 class 0x010601
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448405] pci 0000:00:11.0: reg 0x10: [io  0x7118-0x711f]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448416] pci 0000:00:11.0: reg 0x14: [io  0x7124-0x7127]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448426] pci 0000:00:11.0: reg 0x18: [io  0x7110-0x7117]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448437] pci 0000:00:11.0: reg 0x1c: [io  0x7120-0x7123]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448447] pci 0000:00:11.0: reg 0x20: [io  0x7100-0x710f]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448458] pci 0000:00:11.0: reg 0x24: [mem 0xd8151000-0xd81517ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448614] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448629] pci 0000:00:12.0: reg 0x10: [mem 0xd8150000-0xd8150fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448733] pci 0000:00:12.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448778] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448799] pci 0000:00:12.2: reg 0x10: [mem 0xd814f000-0xd814f0ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448894] pci 0000:00:12.2: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448896] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.448938] pci 0000:00:12.2: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449043] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449058] pci 0000:00:13.0: reg 0x10: [mem 0xd814e000-0xd814efff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449158] pci 0000:00:13.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449260] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449283] pci 0000:00:13.2: reg 0x10: [mem 0xd814d000-0xd814d0ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449378] pci 0000:00:13.2: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449380] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449426] pci 0000:00:13.2: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449527] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449709] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449732] pci 0000:00:14.2: reg 0x10: [mem 0xd8140000-0xd8143fff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.449805] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450006] pci 0000:00:14.2: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450089] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450266] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450405] pci 0000:00:14.5: [1022:7809] type 00 class 0x0c0310
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450424] pci 0000:00:14.5: reg 0x10: [mem 0xd814c000-0xd814cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450603] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450704] pci 0000:00:15.0: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450745] pci 0000:00:15.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450851] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.450950] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451043] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451138] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451236] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451311] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451386] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451462] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451676] pci 0000:01:00.0: [1002:6760] type 00 class 0x030000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451694] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451707] pci 0000:01:00.0: reg 0x18: [mem 0xd8000000-0xd801ffff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451714] pci 0000:01:00.0: reg 0x20: [io  0x6000-0x60ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451728] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.451776] pci 0000:01:00.0: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457198] pci 0000:00:03.0: PCI bridge to [bus 01]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457218] pci 0000:00:03.0:   bridge window [io  0x6000-0x6fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457228] pci 0000:00:03.0:   bridge window [mem 0xd8000000-0xd80fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457239] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457391] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457411] pci 0000:02:00.0: reg 0x10: [io  0x5000-0x50ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457436] pci 0000:02:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457452] pci 0000:02:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457533] pci 0000:02:00.0: supports D1 D2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457535] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.457569] pci 0000:02:00.0: System wakeup disabled by ACPI
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465202] pci 0000:00:04.0: PCI bridge to [bus 02]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465222] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465231] pci 0000:00:04.0:   bridge window [mem 0xd7000000-0xd7ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465243] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465418] pci 0000:03:00.0: [197b:2392] type 00 class 0x088000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465441] pci 0000:03:00.0: reg 0x10: [mem 0xd6003000-0xd60030ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465507] pci 0000:03:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465645] pci 0000:03:00.2: [197b:2391] type 00 class 0x080501
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465665] pci 0000:03:00.2: reg 0x10: [mem 0xd6002000-0xd60020ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465850] pci 0000:03:00.3: [197b:2393] type 00 class 0x088000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.465870] pci 0000:03:00.3: reg 0x10: [mem 0xd6001000-0xd60010ff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473220] pci 0000:00:05.0: PCI bridge to [bus 03]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473241] pci 0000:00:05.0:   bridge window [io  0x4000-0x4fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473247] pci 0000:00:05.0:   bridge window [mem 0xd6000000-0xd6ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473253] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473395] pci 0000:04:00.0: [168c:002b] type 00 class 0x028000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473420] pci 0000:04:00.0: reg 0x10: [mem 0xd5000000-0xd500ffff 64bit]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473530] pci 0000:04:00.0: supports D1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.473532] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481202] pci 0000:00:07.0: PCI bridge to [bus 04-06]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481223] pci 0000:00:07.0:   bridge window [io  0x3000-0x3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481232] pci 0000:00:07.0:   bridge window [mem 0xd5000000-0xd5ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481244] pci 0000:00:07.0:   bridge window [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481450] pci 0000:00:14.4: PCI bridge to [bus 07] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481461] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481463] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481465] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481467] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481469] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481478] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481480] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481482] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481484] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481486] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481488] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481489] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481491] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481493] pci 0000:00:14.4:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481495] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xdfffffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481497] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfffdffff] (subtractive decode)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481674] acpiphp: Slot [1] registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481702] pci 0000:00:15.0: PCI bridge to [bus 08]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481709] pci 0000:00:15.0:   bridge window [io  0x2000-0x2fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481713] pci 0000:00:15.0:   bridge window [mem 0xd4000000-0xd4ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.481720] pci 0000:00:15.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.482807] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.482880] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.482953] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483025] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483083] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483129] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483175] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483220] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483341] ACPI: Enabled 5 GPEs in block 00 to 1F
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483393] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483690] vgaarb: setting as boot device: PCI:0000:00:01.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483695] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483707] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483710] vgaarb: loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483712] vgaarb: bridge control possible 0000:01:00.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.483713] vgaarb: no bridge control possible 0000:00:01.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484012] SCSI subsystem initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484090] libata version 3.00 loaded.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484116] ACPI: bus type USB registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484138] usbcore: registered new interface driver usbfs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484147] usbcore: registered new interface driver hub
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484334] usbcore: registered new device driver usb
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.484670] PCI: Using ACPI for IRQ routing
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494109] PCI: pci_cache_line_size set to 64 bytes
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494216] Expanded resource reserved due to conflict with PCI Bus 0000:00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494218] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494221] e820: reserve RAM buffer [mem 0x8f08d000-0x8fffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494224] e820: reserve RAM buffer [mem 0x8fc00000-0x8fffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494226] e820: reserve RAM buffer [mem 0x24f000000-0x24fffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494387] NetLabel: Initializing
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494389] NetLabel:  domain hash size = 128
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494390] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494404] NetLabel:  unlabeled traffic allowed by default
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494658] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.494664] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.496821] Switched to clocksource hpet
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.503818] AppArmor: AppArmor Filesystem Enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.503862] pnp: PnP ACPI init
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.503883] ACPI: bus type PNP registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504007] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504010] system 00:00: [mem 0xfeb00000-0xfeb00fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504015] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504017] system 00:00: [mem 0xfec10000-0xfec10fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504020] system 00:00: [mem 0xfed61000-0xfed61fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504022] system 00:00: [mem 0xfed80000-0xfed80fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504024] system 00:00: [mem 0xfed81000-0xfed81fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504026] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504030] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504263] system 00:01: [io  0x0400-0x04cf] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504265] system 00:01: [io  0x04d0-0x04d1] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504267] system 00:01: [io  0x04d6] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504270] system 00:01: [io  0x0680-0x06ff] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504272] system 00:01: [io  0x077a] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504274] system 00:01: [io  0x0c00-0x0c01] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504276] system 00:01: [io  0x0c14] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504278] system 00:01: [io  0x0c50-0x0c52] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504279] system 00:01: [io  0x0c6c] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504281] system 00:01: [io  0x0c6f] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504283] system 00:01: [io  0x0cd0-0x0cdb] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504285] system 00:01: [io  0x0220-0x0227] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504287] system 00:01: [io  0x0260-0x0273] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504289] system 00:01: [io  0x0800] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504291] system 00:01: [io  0x0804] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504293] system 00:01: [io  0x087f] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504295] system 00:01: [io  0x0cdc-0x0cdf] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504298] system 00:01: [io  0x0b00-0x0b0f] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504300] system 00:01: [io  0x0b20-0x0b3f] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504302] system 00:01: [io  0x0200-0x027f] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504304] system 00:01: [io  0x0840-0x0847] has been reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504307] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504398] system 00:02: [mem 0x00000000-0x0009ffff] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504402] system 00:02: [mem 0x00100000-0xafffffff] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504405] system 00:02: [mem 0xffe00000-0xffffffff] could not be reserved
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504408] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504520] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504644] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.504685] pnp 00:05: Plug and Play ACPI device, IDs SYN0189 SYN0100 SYN0002 PNP0f13 (active)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.505086] pnp: PnP ACPI: found 6 devices
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.505087] ACPI: bus type PNP unregistered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514688] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514694] pci 0000:03:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514790] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8020000-0xd803ffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514793] pci 0000:00:03.0: PCI bridge to [bus 01]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514796] pci 0000:00:03.0:   bridge window [io  0x6000-0x6fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514800] pci 0000:00:03.0:   bridge window [mem 0xd8000000-0xd80fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514804] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514811] pci 0000:00:04.0: PCI bridge to [bus 02]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514815] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514819] pci 0000:00:04.0:   bridge window [mem 0xd7000000-0xd7ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514823] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514830] pci 0000:03:00.0: BAR 6: assigned [mem 0xd6010000-0xd601ffff pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514833] pci 0000:00:05.0: PCI bridge to [bus 03]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514836] pci 0000:00:05.0:   bridge window [io  0x4000-0x4fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514840] pci 0000:00:05.0:   bridge window [mem 0xd6000000-0xd6ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514844] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514850] pci 0000:00:07.0: PCI bridge to [bus 04-06]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514853] pci 0000:00:07.0:   bridge window [io  0x3000-0x3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514857] pci 0000:00:07.0:   bridge window [mem 0xd5000000-0xd5ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514861] pci 0000:00:07.0:   bridge window [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514866] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514928] pci 0000:00:15.0: PCI bridge to [bus 08]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514931] pci 0000:00:15.0:   bridge window [io  0x2000-0x2fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514937] pci 0000:00:15.0:   bridge window [mem 0xd4000000-0xd4ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514942] pci 0000:00:15.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514950] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514953] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514955] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514958] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514960] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514962] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514965] pci_bus 0000:00: resource 10 [mem 0x000d4000-0x000d7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514967] pci_bus 0000:00: resource 11 [mem 0x000d8000-0x000dbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514969] pci_bus 0000:00: resource 12 [mem 0x000dc000-0x000dffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514972] pci_bus 0000:00: resource 13 [mem 0x000e0000-0x000e3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514974] pci_bus 0000:00: resource 14 [mem 0x000e4000-0x000e7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514977] pci_bus 0000:00: resource 15 [mem 0x000e8000-0x000ebfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514979] pci_bus 0000:00: resource 16 [mem 0x000ec000-0x000effff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514981] pci_bus 0000:00: resource 17 [mem 0x000f0000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514984] pci_bus 0000:00: resource 18 [mem 0xb0000000-0xdfffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514986] pci_bus 0000:00: resource 19 [mem 0xf0000000-0xfffdffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514989] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514991] pci_bus 0000:01: resource 1 [mem 0xd8000000-0xd80fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514994] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514997] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.514999] pci_bus 0000:02: resource 1 [mem 0xd7000000-0xd7ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515001] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515004] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515006] pci_bus 0000:03: resource 1 [mem 0xd6000000-0xd6ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515009] pci_bus 0000:03: resource 2 [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515011] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515014] pci_bus 0000:04: resource 1 [mem 0xd5000000-0xd5ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515016] pci_bus 0000:04: resource 2 [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515019] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515022] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515024] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515026] pci_bus 0000:07: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515029] pci_bus 0000:07: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515031] pci_bus 0000:07: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515034] pci_bus 0000:07: resource 10 [mem 0x000d4000-0x000d7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515036] pci_bus 0000:07: resource 11 [mem 0x000d8000-0x000dbfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515039] pci_bus 0000:07: resource 12 [mem 0x000dc000-0x000dffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515041] pci_bus 0000:07: resource 13 [mem 0x000e0000-0x000e3fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515043] pci_bus 0000:07: resource 14 [mem 0x000e4000-0x000e7fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515046] pci_bus 0000:07: resource 15 [mem 0x000e8000-0x000ebfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515048] pci_bus 0000:07: resource 16 [mem 0x000ec000-0x000effff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515050] pci_bus 0000:07: resource 17 [mem 0x000f0000-0x000fffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515053] pci_bus 0000:07: resource 18 [mem 0xb0000000-0xdfffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515055] pci_bus 0000:07: resource 19 [mem 0xf0000000-0xfffdffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515058] pci_bus 0000:08: resource 0 [io  0x2000-0x2fff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515060] pci_bus 0000:08: resource 1 [mem 0xd4000000-0xd4ffffff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515063] pci_bus 0000:08: resource 2 [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515104] NET: Registered protocol family 2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515358] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515582] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515948] TCP: Hash tables configured (established 65536 bind 65536)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.515997] TCP: reno registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516013] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516083] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516216] NET: Registered protocol family 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516238] pci 0000:00:01.0: Video device with shadowed ROM
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.516302] pci 0000:00:10.0: enabling device (0000 -> 0002)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.637753] PCI: CLS mismatch (64 != 32), using 64 bytes
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    0.693403] Trying to unpack rootfs image as initramfs...
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071321] Freeing initrd memory: 19000K (ffff880035ad4000 - ffff880036d62000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071359] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071362] software IO TLB [mem 0x8b08d000-0x8f08d000] (64MB) mapped at [ffff88008b08d000-ffff88008f08cfff]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071668] microcode: CPU0: patch_level=0x03000027
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071678] microcode: CPU1: patch_level=0x03000027
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071822] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071835] LVT offset 0 assigned for vector 0x400
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071859] perf: AMD IBS detected (0x000000ff)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.071907] Scanning for low memory corruption every 60 seconds
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072279] futex hash table entries: 1024 (order: 4, 65536 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072299] Initialise system trusted keyring
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072322] audit: initializing netlink subsys (disabled)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072342] audit: type=2000 audit(1437943903.932:1): initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.072856] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.074590] zpool: loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.074593] zbud: loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.074919] VFS: Disk quotas dquot_6.5.2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.074971] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.075648] fuse init (API version 7.23)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.075814] msgmni has been set to 14894
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.075888] Key type big_key registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076652] Key type asymmetric registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076657] Asymmetric key parser 'x509' registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076707] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076803] io scheduler noop registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076806] io scheduler deadline registered (default)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.076858] io scheduler cfq registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078279] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078298] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078359] vesafb: mode is 1366x768x32, linelength=5504, pages=0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078361] vesafb: scrolling: redraw
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078363] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078667] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90010f00000, using 4160k, total 4160k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.078999] Console: switching to colour frame buffer device 170x48
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079022] fb0: VESA VGA frame buffer device
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079395] ACPI: AC Adapter [AC] (on-line)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079674] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079679] ACPI: Sleep Button [SLPB]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079730] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079801] ACPI: Lid Switch [LID]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079852] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.079855] ACPI: Power Button [PWRF]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.080013] ACPI: acpi_idle registered with cpuidle
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.109997] thermal LNXTHERM:00: registered as thermal_zone0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.110003] ACPI: Thermal Zone [CPUZ] (71 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.133863] thermal LNXTHERM:01: registered as thermal_zone1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.133868] ACPI: Thermal Zone [GFXZ] (57 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.148659] thermal LNXTHERM:02: registered as thermal_zone2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.148664] ACPI: Thermal Zone [EXTZ] (43 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.163591] thermal LNXTHERM:03: registered as thermal_zone3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.163596] ACPI: Thermal Zone [LOCZ] (54 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.178519] thermal LNXTHERM:04: registered as thermal_zone4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.178524] ACPI: Thermal Zone [BATZ] (30 C)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.178584] GHES: HEST is not enabled!
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.179037] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.182101] Linux agpgart interface v0.103
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.184758] brd: module loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186114] loop: module loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186402] libphy: Fixed MDIO Bus: probed
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186405] tun: Universal TUN/TAP device driver, 1.6
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186406] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186485] PPP generic driver version 2.4.2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186595] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186602] ehci-pci: EHCI PCI platform driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.186971] QUIRK: Enable AMD PLL fix
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187007] ehci-pci 0000:00:12.2: EHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187014] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187020] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187033] ehci-pci 0000:00:12.2: debug port 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.187082] ehci-pci 0000:00:12.2: irq 17, io mem 0xd814f000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197001] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197165] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197167] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197170] usb usb1: Product: EHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197171] usb usb1: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197173] usb usb1: SerialNumber: 0000:00:12.2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197469] hub 1-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.197475] hub 1-0:1.0: 5 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198042] ehci-pci 0000:00:13.2: EHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198048] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198053] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198065] ehci-pci 0000:00:13.2: debug port 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.198098] ehci-pci 0000:00:13.2: irq 17, io mem 0xd814d000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209001] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209128] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209130] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209133] usb usb2: Product: EHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209134] usb usb2: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209136] usb usb2: SerialNumber: 0000:00:13.2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209385] hub 2-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209392] hub 2-0:1.0: 5 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209721] ehci-platform: EHCI generic platform driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209738] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.209745] ohci-pci: OHCI PCI platform driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.210022] ohci-pci 0000:00:12.0: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.210028] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.210062] ohci-pci 0000:00:12.0: irq 18, io mem 0xd8150000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.223415] ACPI: Battery Slot [BAT0] (battery present)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269052] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269054] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269056] usb usb3: Product: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269058] usb usb3: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269059] usb usb3: SerialNumber: 0000:00:12.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269440] hub 3-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269499] hub 3-0:1.0: 5 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.269998] ohci-pci 0000:00:13.0: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.270006] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.270040] ohci-pci 0000:00:13.0: irq 18, io mem 0xd814e000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329265] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329270] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329272] usb usb4: Product: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329274] usb usb4: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329276] usb usb4: SerialNumber: 0000:00:13.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329674] hub 4-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.329735] hub 4-0:1.0: 5 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.330192] ohci-pci 0000:00:14.5: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.330199] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.330231] ohci-pci 0000:00:14.5: irq 18, io mem 0xd814c000
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389267] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389272] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389274] usb usb5: Product: OHCI PCI host controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389276] usb usb5: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389277] usb usb5: SerialNumber: 0000:00:14.5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389675] hub 5-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389734] hub 5-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389911] ohci-platform: OHCI generic platform driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.389929] uhci_hcd: USB Universal Host Controller Interface driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390213] xhci_hcd 0000:00:10.0: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390221] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390440] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390444] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390447] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390539] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390541] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390543] usb usb6: Product: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390545] usb usb6: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390546] usb usb6: SerialNumber: 0000:00:10.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390889] hub 6-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.390947] hub 6-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.391142] xhci_hcd 0000:00:10.0: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.391146] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393863] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393865] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393867] usb usb7: Product: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393869] usb usb7: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.393870] usb usb7: SerialNumber: 0000:00:10.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394082] hub 7-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394139] hub 7-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394629] xhci_hcd 0000:00:10.1: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394636] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394858] xhci_hcd 0000:00:10.1: irq 43 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394861] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394864] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394951] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394953] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394955] usb usb8: Product: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394957] usb usb8: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.394959] usb usb8: SerialNumber: 0000:00:10.1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.395296] hub 8-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.395354] hub 8-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.395549] xhci_hcd 0000:00:10.1: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.395554] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398274] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398276] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398279] usb usb9: Product: xHCI Host Controller
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398281] usb usb9: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398283] usb usb9: SerialNumber: 0000:00:10.1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398567] hub 9-0:1.0: USB hub found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398627] hub 9-0:1.0: 2 ports detected
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.398851] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.401268] i8042: Detected active multiplexing controller, rev 1.1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402420] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402425] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402460] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402489] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402510] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.402995] mousedev: PS/2 mouse device common for all mice
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403410] rtc_cmos 00:03: RTC can wake from S4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403546] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403577] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403657] device-mapper: uevent: version 1.0.3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403766] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403789] ledtrig-cpu: registered to indicate activity on CPUs
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.403889] TCP: cubic registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.404006] NET: Registered protocol family 10
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.404332] NET: Registered protocol family 17
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.404356] Key type dns_resolver registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.404859] Loading compiled-in X.509 certificates
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.406000] Loaded X.509 cert 'Magrathea: Glacier signing key: 4b6de31c0185e45a0c0d73ca36f8fa02edc6253a'
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.406017] registered taskstats version 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.408609] Key type trusted registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.413393] Key type encrypted registered
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.413408] AppArmor: AppArmor sha1 policy hashing enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.413412] ima: No TPM chip found, activating TPM-bypass!
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.413446] evm: HMAC attrs: 0x1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414024]   Magic number: 7:422:903
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414038] usb usb2-port4: hash matches
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414179] rtc_cmos 00:03: setting system clock to 2015-07-26 20:51:44 UTC (1437943904)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414384] acpi-cpufreq: overriding BIOS provided _PSD data
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414484] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414485] EDD information not available.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.414558] PM: Hibernation image not present or could not be loaded.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.416194] Freeing unused kernel memory: 1352K (ffffffff81d1c000 - ffffffff81e6e000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.416198] Write protecting the kernel read-only data: 12288k
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.418271] Freeing unused kernel memory: 552K (ffff880001776000 - ffff880001800000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.419980] Freeing unused kernel memory: 480K (ffff880001b88000 - ffff880001c00000)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.427704] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.439467] systemd-udevd[103]: starting version 204
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.468125] sdhci: Secure Digital Host Controller Interface driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.468129] sdhci: Copyright(c) Pierre Ossman
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471379] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471394] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471687] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471842] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2392] (rev 30)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471910] r8169 0000:02:00.0 eth0: RTL8168e/8111e at 0xffffc9000003a000, e4:11:5b:40:3b:c6, XID 0c200000 IRQ 46
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.471912] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.472005] mmc0: no vqmmc regulator found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.472007] mmc0: no vmmc regulator found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.475687] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.475718] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 30)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.475883] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.484362] ahci 0000:00:11.0: version 3.0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.484698] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.484756] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.484761] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.486294] scsi0 : ahci
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.486468] scsi1 : ahci
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.486577] ata1: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151100 irq 47
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.486580] ata2: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151180 irq 47
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.509064] usb 1-5: new high-speed USB device number 2 using ehci-pci
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.689999] usb 1-5: New USB device found, idVendor=0461, idProduct=4dc7
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.690011] usb 1-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.690018] usb 1-5: Product: HP HD Webcam [Fixed]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.690023] usb 1-5: Manufacturer: Primax Electronics Ltd.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.690027] usb 1-5: SerialNumber: PMX02
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.977137] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.977197] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.978035] ata1.00: ATA-8: TOSHIBA MK6476GSX, GS001C, max UDMA/100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.978040] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.979023] ata1.00: configured for UDMA/100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.979497] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6476GS 1C   PQ: 0 ANSI: 5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.979937] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.979977] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.980047] sd 0:0:0:0: [sda] Write Protect is off
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.980053] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.980073] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.983114] ata2.00: ATAPI: hp       DVDRAM GT50N, MP00, max UDMA/100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.988620] ata2.00: configured for UDMA/100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    1.994211] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT50N     MP00 PQ: 0 ANSI: 5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.014164] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.014175] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.014366] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.014429] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.039093]  sda: sda1 sda2 sda3 sda4 < sda5 >
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.039808] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.069129] tsc: Refined TSC clocksource calibration: 1896.550 MHz
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.229423] usb 4-5: new full-speed USB device number 2 using ohci-pci
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.389480] usb 4-5: New USB device found, idVendor=0cf3, idProduct=3005
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.389485] usb 4-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.402110] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..4876]
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.478410] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x640000/0xa0400, board id: 1397, fw id: 780218
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.485932] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    2.526780] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.069684] Switched to clocksource tsc
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.155940] random: init urandom read with 105 bits of entropy available
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.641401] random: nonblocking pool is initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.714282] init: plymouth-upstart-bridge main process (164) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.714299] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.717777] init: plymouth-upstart-bridge main process (178) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.717790] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.720152] init: plymouth-upstart-bridge main process (180) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.720164] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.723461] init: plymouth-upstart-bridge main process (181) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.723474] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.725866] init: plymouth-upstart-bridge main process (183) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.725880] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.729155] init: plymouth-upstart-bridge main process (184) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.729168] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.731653] init: plymouth-upstart-bridge main process (186) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.731670] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.734916] init: plymouth-upstart-bridge main process (187) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.734933] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.737669] init: plymouth-upstart-bridge main process (189) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.737681] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.740903] init: plymouth-upstart-bridge main process (190) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.740919] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.743207] init: plymouth-upstart-bridge main process (192) terminated with status 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    3.743218] init: plymouth-upstart-bridge respawning too fast, stopped
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.123721] Adding 20970492k swap on /dev/sda5.  Priority:-1 extents:1 across:20970492k FS
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.309165] systemd-udevd[292]: starting version 204
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.511447] lp: driver loaded but no devices found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.522256] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.532983] ppdev: user-space parallel port driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.542317] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.597707] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.597712] AMD IOMMUv2 functionality not available on this system
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.607875] acpi device:00: registered as cooling_device2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.608032] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.608262] hp_accel: laptop model unknown, using default axes configuration
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.608827] lis3lv02d: 8 bits 3DC sensor found
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.618645] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.619478] acpi device:0a: registered as cooling_device3
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.619629] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input13
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.633438] wmi: Mapper loaded
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.647251] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input14
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.672303] cfg80211: Calling CRDA to update world regulatory domain
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.738476] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B06 (\_SB_.PCI0.SMBS.SMBO) (20140424/utaddress-254)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.738487] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.770488] snd_hda_intel 0000:00:01.1: irq 48 for MSI/MSI-X
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793515] ath: phy0: ASPM enabled: 0x42
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793521] ath: EEPROM regdomain: 0x60
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793523] ath: EEPROM indicates we should expect a direct regpair map
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793526] ath: Country alpha2 being used: 00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.793528] ath: Regpair used: 0x60
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.801655] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input15
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804318] sound hdaudioC1D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804325] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804328] sound hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804331] sound hdaudioC1D0:    mono: mono_out=0x0
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804333] sound hdaudioC1D0:    inputs:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804336] sound hdaudioC1D0:      Internal Mic=0x11
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.804338] sound hdaudioC1D0:      Mic=0xc
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.806686] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.807570] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90010ea0000, irq=19
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.839329] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.839427] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input17
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886139] Bluetooth: Core ver 2.19
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886212] NET: Registered protocol family 31
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886214] Bluetooth: HCI device and connection manager initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886223] Bluetooth: HCI socket layer initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886226] Bluetooth: L2CAP socket layer initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.886242] Bluetooth: SCO socket layer initialized
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.920396] kvm: Nested Virtualization enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.920402] kvm: Nested Paging enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [    9.928453] usbcore: registered new interface driver btusb
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026002] audit: type=1400 audit(1437933113.105:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026014] audit: type=1400 audit(1437933113.105:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026019] audit: type=1400 audit(1437933113.105:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026726] audit: type=1400 audit(1437933113.109:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.026734] audit: type=1400 audit(1437933113.109:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.027086] audit: type=1400 audit(1437933113.109:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=382 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.027373] audit: type=1400 audit(1437933113.109:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=452 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.027388] audit: type=1400 audit(1437933113.109:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.027395] audit: type=1400 audit(1437933113.109:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.028102] audit: type=1400 audit(1437933113.109:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.031461] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.338572] input: HP WMI hotkeys as /devices/virtual/input/input18
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.382577] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.382583] Disabling lock debugging due to kernel taint
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.397199] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416105] cfg80211: World regulatory domain updated:
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416112] cfg80211:  DFS Master region: unset
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416114] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416117] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416119] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416120] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416122] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.416124] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.418340] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7226 MBytes.
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.418525] <6>[fglrx]   vendor: 1002 device: 9649 revision: 0 count: 1
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.418782] <6>[fglrx]   vendor: 1002 device: 6760 revision: 0 count: 2
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.419036] <6>[fglrx] ioport: bar 1, base 0x7000, size: 0x100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.464783] media: Linux media interface: v0.10
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.470210] Linux video capture interface: v2.00
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.482959] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (0461:4dc7)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.491185] <6>[fglrx] ioport: bar 4, base 0x6000, size: 0x100
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.491199] pci 0000:01:00.0: enabling device (0000 -> 0003)
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.519303] <6>[fglrx] Kernel PAT support is enabled
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.519337] <6>[fglrx] module loaded - fglrx 15.20.3 [Jun 22 2015] with 2 minors
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.663145] init: failsafe main process (623) killed by TERM signal
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.755841] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input19
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.756068] usbcore: registered new interface driver uvcvideo
Jul 26 20:51:53 ivan-HP-ProBook-4535s kernel: [   10.756072] USB Video Class driver (1.1.1)
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   10.918400] Bluetooth: RFCOMM TTY layer initialized
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   10.918416] Bluetooth: RFCOMM socket layer initialized
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   10.918426] Bluetooth: RFCOMM ver 1.11
Jul 26 20:51:54 ivan-HP-ProBook-4535s rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.034808] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.034821] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.078772] hp_wmi: Unknown event_id - 0 - 0x0
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.078829] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.078843] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Bluetooth daemon 4.101
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Starting SDP server
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: DIS cannot start: GATT is disabled
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init deviceinfo plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init proximity plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init time plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init alert plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init thermometer plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Failed to init gatt_example plugin
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Bluetooth Management interface initialized
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.220375] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.220380] Bluetooth: BNEP filters: protocol multicast
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.220388] Bluetooth: BNEP socket layer initialized
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.377490] init: cups main process (685) killed by HUP signal
Jul 26 20:51:54 ivan-HP-ProBook-4535s kernel: [   11.377503] init: cups main process ended, respawning
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Found user 'avahi' (UID 111) and group 'avahi' (GID 117).
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Successfully dropped root privileges.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: avahi-daemon 0.6.31 starting up.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Successfully called chroot().
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Successfully dropped remaining capabilities.
Jul 26 20:51:54 ivan-HP-ProBook-4535s bluetoothd[697]: Adapter /org/bluez/697/hci0 has been enabled
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: No service file found in /etc/avahi/services.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Network interface enumeration completed.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jul 26 20:51:54 ivan-HP-ProBook-4535s avahi-daemon[772]: Server startup complete. Host name is ivan-HP-ProBook-4535s.local. Local service cookie is 2001102376.
Jul 26 20:51:54 ivan-HP-ProBook-4535s ModemManager[673]: <info>  ModemManager (version 1.0.0) starting...
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager (version 0.9.8.8) is starting...
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WEXT support is enabled
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> DNS: loaded plugin dnsmasq
Jul 26 20:51:54 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul 26 20:51:54 ivan-HP-ProBook-4535s polkitd[811]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jul 26 20:51:54 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: init!
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: update_system_hostname
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:       interface-parser: parsing file /etc/network/interfaces
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:       interface-parser: finished parsing file /etc/network/interfaces
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPluginIfupdown: management mode: unmanaged
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0)
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: end _init.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: init!
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: end _init.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Loaded plugin (null): (null)
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    Ifupdown: get unmanaged devices count: 0
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: (27176720) ... get_connections.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ifupdown: (27176720) ... get_connections (managed=false): return empty list.
Jul 26 20:51:54 ivan-HP-ProBook-4535s NetworkManager[804]:    keyfile: parsing Ivan Mihaylov ... 
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]:    keyfile:     read connection 'Ivan Mihaylov'
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: (1610629408) ... get_connections.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]:    SCPlugin-Ofono: (1610629408) connections count: 0
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]:    Ifupdown: get unmanaged devices count: 0
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/ieee80211/phy0/rfkill0) (driver ath9k)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/platform/hp-wmi/rfkill/rfkill2) (platform driver hp-wmi)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Networking is enabled by state file
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> failed to allocate link cache: (-12) Object not found
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): carrier is OFF
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): bringing up device.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): preparing device.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.290411] r8169 0000:02:00.0 eth0: link down
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.292810] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): using nl80211 for WiFi device control
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): driver supports Access Point (AP) mode
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): bringing up device.
Jul 26 20:51:55 ivan-HP-ProBook-4535s anacron[952]: Anacron 2.3 started on 2015-07-26
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): preparing device.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul 26 20:51:55 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.315313] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> urfkill disappeared from the bus
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> ModemManager available in the bus
Jul 26 20:51:55 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> wpa_supplicant started
Jul 26 20:51:55 ivan-HP-ProBook-4535s wpa_supplicant[977]: Successfully initialized wpa_supplicant
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0) supports 4 scan SSIDs
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> Trying to remove a non-existant call id.
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: starting -> ready
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jul 26 20:51:55 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0) supports 4 scan SSIDs
Jul 26 20:51:55 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:51:55 ivan-HP-ProBook-4535s acpid: starting up with netlink and the input layer
Jul 26 20:51:55 ivan-HP-ProBook-4535s cron[910]: (CRON) INFO (pidfile fd = 3)
Jul 26 20:51:55 ivan-HP-ProBook-4535s cron[1035]: (CRON) STARTUP (fork ok)
Jul 26 20:51:55 ivan-HP-ProBook-4535s cron[1035]: (CRON) INFO (Running @reboot jobs)
Jul 26 20:51:55 ivan-HP-ProBook-4535s ntpdate[1038]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jul 26 20:51:55 ivan-HP-ProBook-4535s ntpdate[1038]: no servers can be used, exiting
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.651831] vboxdrv: Found 2 processor cores.
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.653615] vboxdrv: fAsync=0 offMin=0x3cc offMax=0xf2a
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.653753] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.653755] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
Jul 26 20:51:55 ivan-HP-ProBook-4535s kernel: [   12.675219] vboxpci: IOMMU not found (not registered)
Jul 26 20:51:55 ivan-HP-ProBook-4535s anacron[952]: Normal exit (0 jobs run)
Jul 26 20:51:55 ivan-HP-ProBook-4535s acpid: 11 rules loaded
Jul 26 20:51:55 ivan-HP-ProBook-4535s acpid: waiting for events: event logging is off
Jul 26 20:51:56 ivan-HP-ProBook-4535s kernel: [   13.194482] init: plymouth-splash main process (1164) terminated with status 1
Jul 26 20:51:56 ivan-HP-ProBook-4535s whoopsie[946]: whoopsie 0.2.24.6 starting up.
Jul 26 20:51:56 ivan-HP-ProBook-4535s whoopsie[946]: Using lock path: /var/lock/whoopsie/lock
Jul 26 20:51:56 ivan-HP-ProBook-4535s whoopsie[1185]: offline
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Auto-activating connection 'Ivan Mihaylov'.
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) starting connection 'Ivan Mihaylov'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now CONNECTING
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless): connection 'Ivan Mihaylov' has security, and secrets exist.  No new secrets needed.
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'ssid' value 'Ivan Mihaylov'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'scan_ssid' value '1'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'psk' value '<omitted>'
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jul 26 20:51:56 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: set interface ap_scan to 1
Jul 26 20:51:57 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul 26 20:51:57 ivan-HP-ProBook-4535s accounts-daemon[1224]: started daemon version 0.6.35
Jul 26 20:51:57 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul 26 20:51:57 ivan-HP-ProBook-4535s ModemManager[673]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0': not supported by any plugin
Jul 26 20:51:57 ivan-HP-ProBook-4535s ModemManager[673]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0': not supported by any plugin
Jul 26 20:51:56 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:51:57 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: SME: Trying to authenticate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.347338] wlan0: authenticate with c8:3a:35:4d:4b:08
Jul 26 20:51:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jul 26 20:51:57 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Trying to associate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.359660] wlan0: send auth to c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.361680] wlan0: authenticated
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.362801] wlan0: associate with c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.366683] wlan0: RX AssocResp from c8:3a:35:4d:4b:08 (capab=0x11 status=0 aid=1)
Jul 26 20:51:57 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Associated with c8:3a:35:4d:4b:08
Jul 26 20:51:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.366823] wlan0: associated
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.366837] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.367624] cfg80211: Calling CRDA for country: CN
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370556] ath: EEPROM regdomain: 0x809c
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370563] ath: EEPROM indicates we should expect a country code
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370565] ath: doing EEPROM country->regdmn map search
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370566] ath: country maps to regdmn code: 0x52
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370568] ath: Country alpha2 being used: CN
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370570] ath: Regpair used: 0x52
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370592] ath: regdomain 0x809c dynamically updated by country IE
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370615] cfg80211: Regulatory domain changed to country: CN
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370616] cfg80211:  DFS Master region: unset
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370618] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370621] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370623] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370626] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370628] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s kernel: [   14.370630] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 20:51:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 26 20:51:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associated -> group handshake
Jul 26 20:51:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:51:59 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv6 for mDNS.
Jul 26 20:51:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fe80::9eb7:dff:fe7f:c344 on wlan0.*.
Jul 26 20:52:00 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul 26 20:52:00 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul 26 20:52:00 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul 26 20:52:00 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully called chroot.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully dropped privileges.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully limited resources.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Running.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Canary thread running.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 1392 of process 1392 (n/a) owned by '112' high priority at nice level -11.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 1 threads of 1 processes of 1 users.
Jul 26 20:52:00 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Watchdog thread running.
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: WPA: Key negotiation completed with c8:3a:35:4d:4b:08 [PTK=CCMP GTK=CCMP]
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-CONNECTED - Connection to c8:3a:35:4d:4b:08 completed [id=0 id_str=]
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: SME: Trying to authenticate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.601027] wlan0: deauthenticating from c8:3a:35:4d:4b:08 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.611105] cfg80211: Calling CRDA to update world regulatory domain
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614395] cfg80211: World regulatory domain updated:
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614402] cfg80211:  DFS Master region: unset
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614404] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614407] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614410] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614413] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614415] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.614417] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.619190] wlan0: authenticate with c8:3a:35:4d:4b:08
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-DISCONNECTED bssid=c8:3a:35:4d:4b:08 reason=2 locally_generated=1
Jul 26 20:52:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: group handshake -> authenticating
Jul 26 20:52:00 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> Connection disconnected (reason -2)
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Trying to associate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.631224] wlan0: send auth to c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.632915] wlan0: authenticated
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.635178] wlan0: associate with c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 20:52:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.639031] wlan0: RX AssocResp from c8:3a:35:4d:4b:08 (capab=0x11 status=0 aid=1)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.639075] wlan0: associated
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.639186] cfg80211: Calling CRDA for country: CN
Jul 26 20:52:00 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Associated with c8:3a:35:4d:4b:08
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642829] ath: EEPROM regdomain: 0x809c
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642835] ath: EEPROM indicates we should expect a country code
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642837] ath: doing EEPROM country->regdmn map search
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642839] ath: country maps to regdmn code: 0x52
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642841] ath: Country alpha2 being used: CN
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642843] ath: Regpair used: 0x52
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642845] ath: regdomain 0x809c dynamically updated by country IE
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642869] cfg80211: Regulatory domain changed to country: CN
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642871] cfg80211:  DFS Master region: unset
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642873] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642876] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642879] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642881] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642883] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s kernel: [   17.642885] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 20:52:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associating -> associated
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 1491 of process 1392 (n/a) owned by '112' RT at priority 5.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 2 threads of 1 processes of 1 users.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 1492 of process 1392 (n/a) owned by '112' RT at priority 5.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 3 threads of 1 processes of 1 users.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 1493 of process 1392 (n/a) owned by '112' RT at priority 5.
Jul 26 20:52:01 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 4 threads of 1 processes of 1 users.
Jul 26 20:52:01 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/HFPAG
Jul 26 20:52:01 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/HFPHS
Jul 26 20:52:01 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Jul 26 20:52:01 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.33 path=/MediaEndpoint/A2DPSink
Jul 26 20:52:01 ivan-HP-ProBook-4535s anacron[1497]: Anacron 2.3 started on 2015-07-26
Jul 26 20:52:01 ivan-HP-ProBook-4535s anacron[1497]: Normal exit (0 jobs run)
Jul 26 20:52:01 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 26 20:52:01 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associated -> group handshake
Jul 26 20:52:01 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: WPA: Key negotiation completed with c8:3a:35:4d:4b:08 [PTK=CCMP GTK=CCMP]
Jul 26 20:52:01 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-CONNECTED - Connection to c8:3a:35:4d:4b:08 completed [id=0 id_str=]
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: group handshake -> completed
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Ivan Mihaylov'.
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> dhclient started with pid 1590
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Withdrawing address record for fe80::9eb7:dff:fe7f:c344 on wlan0.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: All rights reserved.
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: 
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Listening on LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Sending on   LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: Sending on   Socket/fallback
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 255.255.255.255 port 67 (xid=0x1e77f6d0)
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Jul 26 20:52:01 ivan-HP-ProBook-4535s dhclient: bound to 192.168.0.102 -- renewal in 37486 seconds.
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   address 192.168.0.102
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   prefix 24 (255.255.255.0)
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   gateway 192.168.0.1
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   nameserver '192.168.1.1'
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 26 20:52:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv4 for mDNS.
Jul 26 20:52:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for 192.168.0.102 on wlan0.IPv4.
Jul 26 20:52:01 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Using config file /etc/colord.conf
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Using mapping database file /var/lib/colord/mapping.db
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Using device database file /var/lib/colord/storage.db
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: loaded plugin libcd_plugin_scanner.so
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: loaded plugin libcd_plugin_camera.so
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Daemon ready for requests
Jul 26 20:52:01 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Jul 26 20:52:01 ivan-HP-ProBook-4535s colord: Device added: xrandr-default
Jul 26 20:52:02 ivan-HP-ProBook-4535s colord: Profile added: icc-7a9564ffe8e4686f7064491b7f3c6153
Jul 26 20:52:02 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:52:02 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv6 for mDNS.
Jul 26 20:52:02 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fe80::9eb7:dff:fe7f:c344 on wlan0.*.
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Policy set 'Ivan Mihaylov' (wlan0) as default for IPv4 routing and DNS.
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> DNS: starting dnsmasq...
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> dnsmasq not available on the bus, can't update servers.
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <error> [1437933122.636839] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> DNS: plugin dnsmasq update failed
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: started, version 2.68 cache disabled
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: DBus support enabled: connected to system bus
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: warning: no upstream servers configured
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) successful, device activated.
Jul 26 20:52:02 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> dnsmasq appeared on DBus: :1.46
Jul 26 20:52:02 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 20:52:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: setting upstream servers from DBus
Jul 26 20:52:02 ivan-HP-ProBook-4535s dnsmasq[1655]: using nameserver 192.168.1.1#53
Jul 26 20:52:03 ivan-HP-ProBook-4535s whoopsie[1185]: message repeated 3 times: [ offline]
Jul 26 20:52:03 ivan-HP-ProBook-4535s whoopsie[1185]: online
Jul 26 20:52:05 ivan-HP-ProBook-4535s NetworkManager[804]: <info> WiFi hardware radio set enabled
Jul 26 20:52:05 ivan-HP-ProBook-4535s kernel: [   22.300022] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 20:52:05 ivan-HP-ProBook-4535s kernel: [   22.300036] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 20:52:05 ivan-HP-ProBook-4535s colord: device removed: xrandr-default
Jul 26 20:52:05 ivan-HP-ProBook-4535s colord: Profile removed: icc-7a9564ffe8e4686f7064491b7f3c6153
Jul 26 20:52:09 ivan-HP-ProBook-4535s ntpdate[1755]: adjust time server 91.189.94.4 offset 0.346865 sec
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 2146 of process 2146 (n/a) owned by '1000' high priority at nice level -11.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 5 threads of 2 processes of 2 users.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 2147 of process 2146 (n/a) owned by '1000' RT at priority 5.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 6 threads of 2 processes of 2 users.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 2148 of process 2146 (n/a) owned by '1000' RT at priority 5.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 7 threads of 2 processes of 2 users.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Successfully made thread 2149 of process 2146 (n/a) owned by '1000' RT at priority 5.
Jul 26 20:52:09 ivan-HP-ProBook-4535s rtkit-daemon[1394]: Supervising 8 threads of 2 processes of 2 users.
Jul 26 20:52:09 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPAG
Jul 26 20:52:09 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/HFPHS
Jul 26 20:52:09 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSource
Jul 26 20:52:09 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint registered: sender=:1.67 path=/MediaEndpoint/A2DPSink
Jul 26 20:52:09 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Jul 26 20:52:10 ivan-HP-ProBook-4535s colord: Device added: xrandr-default
Jul 26 20:52:10 ivan-HP-ProBook-4535s colord: Profile added: icc-8047dcbd0521d15201185b4fe16ea653
Jul 26 20:52:10 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.locale1'
Jul 26 20:52:13 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jul 26 20:52:13 ivan-HP-ProBook-4535s udisksd[2291]: udisks daemon version 2.1.3 starting
Jul 26 20:52:13 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jul 26 20:52:13 ivan-HP-ProBook-4535s udisksd[2291]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jul 26 20:52:19 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:52:22 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 26 20:52:22 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 26 20:52:22 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 26 20:52:22 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 26 20:52:24 ivan-HP-ProBook-4535s kernel: [   40.969782] audit_printk_skb: 168 callbacks suppressed
Jul 26 20:52:24 ivan-HP-ProBook-4535s kernel: [   40.969791] audit: type=1400 audit(1437933144.052:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2407 comm="apparmor_parser"
Jul 26 20:52:24 ivan-HP-ProBook-4535s kernel: [   40.969802] audit: type=1400 audit(1437933144.052:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2407 comm="apparmor_parser"
Jul 26 20:52:24 ivan-HP-ProBook-4535s kernel: [   40.970316] audit: type=1400 audit(1437933144.052:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2407 comm="apparmor_parser"
Jul 26 20:52:25 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/HFPAG
Jul 26 20:52:25 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/HFPHS
Jul 26 20:52:25 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/A2DPSource
Jul 26 20:52:25 ivan-HP-ProBook-4535s bluetoothd[697]: Endpoint unregistered: sender=:1.33 path=/MediaEndpoint/A2DPSink
Jul 26 20:52:42 ivan-HP-ProBook-4535s gnome-session[2048]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Jul 26 20:54:07 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Jul 26 20:55:57 ivan-HP-ProBook-4535s dnsmasq[1655]: nameserver 192.168.1.1 refused to do a recursive query
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): disconnecting for new activation request.
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: activated -> disconnected (reason 'none') [100 30 0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): deactivating device (reason 'none') [0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1590
Jul 26 20:56:49 ivan-HP-ProBook-4535s avahi-daemon[772]: Withdrawing address record for 192.168.0.102 on wlan0.
Jul 26 20:56:49 ivan-HP-ProBook-4535s avahi-daemon[772]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Jul 26 20:56:49 ivan-HP-ProBook-4535s avahi-daemon[772]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.378298] wlan0: deauthenticating from c8:3a:35:4d:4b:08 by local choice (Reason: 3=DEAUTH_LEAVING)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> DNS: plugin dnsmasq update failed
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Removing DNS information from /sbin/resolvconf
Jul 26 20:56:49 ivan-HP-ProBook-4535s dnsmasq[1655]: setting upstream servers from DBus
Jul 26 20:55:28 ivan-HP-ProBook-4535s wpa_supplicant[1016]: message repeated 3 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jul 26 20:56:49 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-DISCONNECTED bssid=c8:3a:35:4d:4b:08 reason=3 locally_generated=1
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.392107] cfg80211: Calling CRDA to update world regulatory domain
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397142] cfg80211: World regulatory domain updated:
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397151] cfg80211:  DFS Master region: unset
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397154] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397160] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397164] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397180] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397184] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s kernel: [  306.397187] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now DISCONNECTED
Jul 26 20:56:49 ivan-HP-ProBook-4535s whoopsie[1185]: offline
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) starting connection 'Sinjo13'
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now CONNECTING
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 20:56:49 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> Connection disconnected (reason -3)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> Connection disconnected (reason -3)
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 20:56:49 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless): access point 'Sinjo13' has security, but secrets are required.
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jul 26 20:56:49 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 20:56:49 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 20:56:50 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jul 26 20:56:50 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: get_secret_flags: assertion 'is_secret_prop (setting, secret_name, error)' failed
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless): connection 'Sinjo13' has security, and secrets exist.  No new secrets needed.
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'ssid' value 'Sinjo13'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'scan_ssid' value '1'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: added 'psk' value '<omitted>'
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Config: set interface ap_scan to 1
Jul 26 20:56:57 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jul 26 20:56:57 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 20:56:58 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: SME: Trying to authenticate with ec:cb:30:46:f3:2c (SSID='Sinjo13' freq=2442 MHz)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.229503] wlan0: authenticate with ec:cb:30:46:f3:2c
Jul 26 20:56:58 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Trying to associate with ec:cb:30:46:f3:2c (SSID='Sinjo13' freq=2442 MHz)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.236681] wlan0: send auth to ec:cb:30:46:f3:2c (try 1/3)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.238328] wlan0: authenticated
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.238558] ath9k 0000:04:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.238562] ath9k 0000:04:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.238826] wlan0: associate with ec:cb:30:46:f3:2c (try 1/3)
Jul 26 20:56:58 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jul 26 20:56:58 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: Associated with ec:cb:30:46:f3:2c
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.242098] wlan0: RX AssocResp from ec:cb:30:46:f3:2c (capab=0x431 status=0 aid=3)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.242160] wlan0: associated
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.242236] cfg80211: Calling CRDA for country: BG
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245943] ath: EEPROM regdomain: 0x8064
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245948] ath: EEPROM indicates we should expect a country code
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245950] ath: doing EEPROM country->regdmn map search
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245952] ath: country maps to regdmn code: 0x34
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245954] ath: Country alpha2 being used: BG
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245956] ath: Regpair used: 0x34
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245958] ath: regdomain 0x8064 dynamically updated by country IE
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245981] cfg80211: Regulatory domain changed to country: BG
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245983] cfg80211:  DFS Master region: unset
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245985] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245988] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245990] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2300 mBm), (N/A)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245993] cfg80211:   (5250000 KHz - 5290000 KHz @ 40000 KHz), (N/A, 2300 mBm), (0 s)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245995] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 3000 mBm), (0 s)
Jul 26 20:56:58 ivan-HP-ProBook-4535s kernel: [  315.245997] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
Jul 26 20:56:58 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: authenticating -> associated
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jul 26 20:56:59 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: WPA: Key negotiation completed with ec:cb:30:46:f3:2c [PTK=CCMP GTK=TKIP]
Jul 26 20:56:59 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-CONNECTED - Connection to ec:cb:30:46:f3:2c completed [id=0 id_str=]
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Sinjo13'.
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> dhclient started with pid 2829
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Withdrawing address record for fe80::9eb7:dff:fe7f:c344 on wlan0.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: All rights reserved.
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: 
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Listening on LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Sending on   LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: Sending on   Socket/fallback
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x79f03e08)
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: DHCPREQUEST of 192.168.1.4 on wlan0 to 255.255.255.255 port 67 (xid=0x83ef079)
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: DHCPOFFER of 192.168.1.4 from 192.168.1.1
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: DHCPACK of 192.168.1.4 from 192.168.1.1
Jul 26 20:56:59 ivan-HP-ProBook-4535s dhclient: bound to 192.168.1.4 -- renewal in 37384 seconds.
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   address 192.168.1.4
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   prefix 24 (255.255.255.0)
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   gateway 192.168.1.1
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   nameserver '192.168.1.1'
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: nm_ip4_config_add_nameserver: assertion 'nameserver > 0' failed
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   nameserver '0.0.0.0'
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info>   domain name 'vivacom-adsl'
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 26 20:56:59 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.4.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv4 for mDNS.
Jul 26 20:56:59 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for 192.168.1.4 on wlan0.IPv4.
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Policy set 'Sinjo13' (wlan0) as default for IPv4 routing and DNS.
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 20:57:00 ivan-HP-ProBook-4535s dnsmasq[1655]: setting upstream servers from DBus
Jul 26 20:57:00 ivan-HP-ProBook-4535s dnsmasq[1655]: using nameserver 192.168.1.1#53
Jul 26 20:57:00 ivan-HP-ProBook-4535s dnsmasq[1655]: nameserver 192.168.1.1 refused to do a recursive query
Jul 26 20:57:00 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) successful, device activated.
Jul 26 20:57:00 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 20:57:00 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 20:57:00 ivan-HP-ProBook-4535s ntpdate[2920]: Can't find host ntp.ubuntu.com: No address associated with hostname (-5)
Jul 26 20:57:00 ivan-HP-ProBook-4535s ntpdate[2920]: no servers can be used, exiting
Jul 26 20:57:00 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:57:00 ivan-HP-ProBook-4535s avahi-daemon[772]: New relevant interface wlan0.IPv6 for mDNS.
Jul 26 20:57:00 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fe80::9eb7:dff:fe7f:c344 on wlan0.*.
Jul 26 20:57:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) scheduled...
Jul 26 20:57:01 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) started...
Jul 26 20:57:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::9eb7:dff:fe7f:c344.
Jul 26 20:57:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Joining mDNS multicast group on interface wlan0.IPv6 with address fdec:cb30:46f3:2400:696b:e408:aed7:86c0.
Jul 26 20:57:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fdec:cb30:46f3:2400:696b:e408:aed7:86c0 on wlan0.*.
Jul 26 20:57:01 ivan-HP-ProBook-4535s avahi-daemon[772]: Withdrawing address record for fe80::9eb7:dff:fe7f:c344 on wlan0.
Jul 26 20:57:02 ivan-HP-ProBook-4535s avahi-daemon[772]: Registering new address record for fdec:cb30:46f3:2400:9eb7:dff:fe7f:c344 on wlan0.*.
Jul 26 20:57:02 ivan-HP-ProBook-4535s NetworkManager[804]: <error> [1437933422.981247] [nm-system.c:1266] nm_system_replace_default_ip6_route(): (wlan0): failed to set IPv6 default route: -7
Jul 26 20:57:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Policy set 'Sinjo13' (wlan0) as default for IPv6 routing and DNS.
Jul 26 20:57:02 ivan-HP-ProBook-4535s NetworkManager[804]: <info> Activation (wlan0) Stage 5 of 5 (IPv6 Commit) complete.
Jul 26 20:57:16 ivan-HP-ProBook-4535s wpa_supplicant[1016]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 21:00:27 ivan-HP-ProBook-4535s NetworkManager[804]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Jul 26 21:04:15 ivan-HP-ProBook-4535s dbus[646]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 26 21:04:15 ivan-HP-ProBook-4535s dbus[646]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 26 21:04:15 ivan-HP-ProBook-4535s rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="665" x-info="http://www.rsyslog.com"] exiting on signal 15.
Jul 26 21:05:53 ivan-HP-ProBook-4535s rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="595" x-info="http://www.rsyslog.com"] start
Jul 26 21:05:53 ivan-HP-ProBook-4535s rsyslogd: rsyslogd's groupid changed to 104
Jul 26 21:05:53 ivan-HP-ProBook-4535s rsyslogd: rsyslogd's userid changed to 101
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Linux version 3.16.0-44-generic (buildd@orlo) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #59~14.04.1-Ubuntu SMP Tue Jul 7 15:07:27 UTC 2015 (Ubuntu 3.16.0-44.59~14.04.1-generic 3.16.7-ckt14)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-44-generic root=UUID=06bbc19e-b72c-445e-851c-77c80ccf7f12 ro quiet splash nomodeset pci=pcie_mode_safe vt.handoff=7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] KERNEL supported cpus:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Intel GenuineIntel
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   AMD AuthenticAMD
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Centaur CentaurHauls
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000008f08cfff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008f08d000-0x000000008f58cfff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008f58d000-0x000000008fbcefff] ACPI NVS
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbcf000-0x000000008fbfefff] ACPI data
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x000000008fbff000-0x000000008fbfffff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024effffff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PCI: Unknown option `pcie_mode_safe'
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] SMBIOS 2.6 present.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] DMI: Hewlett-Packard HP ProBook 4535s/168B, BIOS 68CPC Ver. F.50 07/01/2014
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: No AGP bridge found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: last_pfn = 0x24f000 max_arch_pfn = 0x400000000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR default type: uncachable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   00000-9FFFF write-back
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   A0000-DFFFF uncachable
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   E0000-FFFFF write-protect
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] MTRR variable ranges enabled:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   1 base 0080000000 mask FFF0000000 write-back
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   2 base 00FFE00000 mask FFFFE00000 write-protect
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   3 base 00FFE10000 mask FFFFFF0000 write-protect
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   4 disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   5 disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   6 disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   7 disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] TOM2: 000000024f000000 aka 9456M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: last_pfn = 0x8fc00 max_arch_pfn = 0x400000000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Using GB pages for direct mapping
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbd000, 0x01fbdfff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbe000, 0x01fbefff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fbf000, 0x01fbffff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x24ee00000-0x24effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x24ee00000-0x24effffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fc0000, 0x01fc0fff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x24c000000-0x24edfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x24c000000-0x24edfffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x200000000-0x24bffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x200000000-0x23fffffff] page 1G
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x240000000-0x24bffffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0x8f08cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x80000000-0x8effffff] page 2M
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x8f000000-0x8f08cfff] page 4k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x8fbff000-0x8fbfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x8fbff000-0x8fbfffff] page 4k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] BRK [0x01fc1000, 0x01fc1fff] PGTABLE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] RAMDISK: [mem 0x35ad4000-0x36d61fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: RSDP 0x00000000000F2F00 000014 (v00 HPQOEM)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: RSDT 0x000000008FBFE038 000044 (v01 HPQOEM SLIC-MPC 00000003      01000013)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: FACP 0x000000008FBFD000 000074 (v01 HPQOEM 168B     00000003 HP   00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20140424/tbfadt-649)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: DSDT 0x000000008FBD7000 0230B2 (v01 HPQOEM 168B     00000001 INTL 20060912)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: FACS 0x000000008FB8F000 000040
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: APIC 0x000000008FBFC000 000084 (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: MCFG 0x000000008FBFB000 00003C (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: HPET 0x000000008FBD4000 000038 (v01 HPQOEM 168B     00000001 HP   00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD3000 00072C (v01 AMD    POWERNOW 00000001 AMD  00000001)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD1000 00193D (v02 AMD    ALIB     00000001 MSFT 04000000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBD0000 00078F (v01 HP     AMDSGTBL 00000001 INTL 20060912)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: SSDT 0x000000008FBCF000 000325 (v01 HP     HPZPODDT 00000001 INTL 20060912)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] No NUMA configuration found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000024effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x24effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   NODE_DATA [mem 0x24eff9000-0x24effdfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]  [ffffea0000000000-ffffea00093fffff] PMD -> [ffff880246e00000-ffff88024e5fffff] on node 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Zone ranges:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal   [mem 0x100000000-0x24effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Movable zone start for each node
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Early memory node ranges
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x00100000-0x8f08cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x8fbff000-0x8fbfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   node   0: [mem 0x100000000-0x24effffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] On node 0 totalpages: 1957931
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 21 pages reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA zone: 3997 pages, LIFO batch:0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32 zone: 9091 pages used for memmap
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   DMA32 zone: 581774 pages, LIFO batch:31
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal zone: 21440 pages used for memmap
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000]   Normal zone: 1372160 pages, LIFO batch:31
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] ACPI: HPET id: 0x43538301 base: 0xfed00000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] smpboot: Allowing 4 CPUs, 2 hotplug CPUs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] nr_irqs_gsi: 40
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8f08d000-0x8f58cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8f58d000-0x8fbcefff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8fbcf000-0x8fbfefff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0x8fc00000-0xdfffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfebfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfedfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffdfffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PM: Registered nosave memory: [mem 0xffe00000-0xffffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] e820: [mem 0x8fc00000-0xdfffffff] available for PCI devices
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88024ec00000 s81408 r8192 d20992 u524288
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] pcpu-alloc: s81408 r8192 d20992 u524288 alloc=1*2097152
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1927315
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Policy zone: Normal
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-44-generic root=UUID=06bbc19e-b72c-445e-851c-77c80ccf7f12 ro quiet splash nomodeset pci=pcie_mode_safe vt.handoff=7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: Checking aperture...
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] AGP: No AGP bridge found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Memory: 7606856K/7831724K available (7629K kernel code, 1131K rwdata, 3616K rodata, 1352K init, 1300K bss, 224868K reserved)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Hierarchical RCU implementation.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	Offload RCU callbacks from all CPUs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] 	Offload RCU callbacks from CPUs: 0-3.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] vt handoff: transparent VT on vt#7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] Console: colour dummy device 80x25
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] console [tty0] enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] allocated 31457280 bytes of page_cgroup
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] hpet clockevent registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000000] tsc: Detected 1896.380 MHz processor
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000050] Calibrating delay loop (skipped), value calculated using timer frequency.. 3792.76 BogoMIPS (lpj=7585520)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000054] pid_max: default: 32768 minimum: 301
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.000063] ACPI: Core revision 20140424
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.014999] ACPI: All ACPI Tables successfully acquired
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.049285] Security Framework initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.049307] AppArmor: AppArmor initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.049308] Yama: becoming mindful.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.050087] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.052955] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054199] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054213] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054552] Initializing cgroup subsys memory
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054584] Initializing cgroup subsys devices
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054593] Initializing cgroup subsys freezer
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054597] Initializing cgroup subsys net_cls
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054603] Initializing cgroup subsys blkio
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054609] Initializing cgroup subsys perf_event
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054611] Initializing cgroup subsys net_prio
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054620] Initializing cgroup subsys hugetlb
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054649] tseg: 008fc00000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054653] CPU: Physical Processor ID: 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054654] CPU: Processor Core ID: 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054656] mce: CPU supports 6 MCE banks
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054668] Last level iTLB entries: 4KB 512, 2MB 16, 4MB 8
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054668] Last level dTLB entries: 4KB 1024, 2MB 128, 4MB 64, 1GB 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054668] tlb_flushall_shift: 6
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.054840] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.056459] ftrace: allocating 29259 entries in 115 pages
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.078055] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.117747] smpboot: CPU0: AMD A4-3305M APU with Radeon(tm) HD Graphics (fam: 12, model: 01, stepping: 00)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224770] Performance Events: AMD PMU driver.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224775] ... version:                0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224776] ... bit width:              48
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224778] ... generic registers:      4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224779] ... value mask:             0000ffffffffffff
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224780] ... max period:             00007fffffffffff
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224782] ... fixed-purpose events:   0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.224783] ... event mask:             000000000000000f
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.227078] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.227194] x86: Booting SMP configuration:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.227197] .... node  #0, CPUs:      #1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.240339] x86: Booted up 1 node, 2 CPUs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.240341] smpboot: Total of 2 processors activated (7585.52 BogoMIPS)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.241085] devtmpfs: initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246762] evm: security.selinux
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246765] evm: security.SMACK64
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246766] evm: security.SMACK64EXEC
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246767] evm: security.SMACK64TRANSMUTE
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246769] evm: security.SMACK64MMAP
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246770] evm: security.ima
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246771] evm: security.capability
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.246934] PM: Registering ACPI NVS region [mem 0x8f58d000-0x8fbcefff] (6561792 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.248482] pinctrl core: initialized pinctrl subsystem
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.248611] regulator-dummy: no parameters
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.248694] RTC time: 21:05:43, date: 07/26/15
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.248766] NET: Registered protocol family 16
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249000] cpuidle: using governor ladder
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249004] cpuidle: using governor menu
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249223] ACPI: bus type PCI registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249225] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249380] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249383] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.249962] PCI: Using configuration type 1 for base access
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.250286] mtrr: your CPUs had inconsistent fixed MTRR settings
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.250288] mtrr: your CPUs had inconsistent variable MTRR settings
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.250289] mtrr: probably your BIOS does not setup all CPUs.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.250290] mtrr: corrected configuration.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.254054] ACPI: Added _OSI(Module Device)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.254058] ACPI: Added _OSI(Processor Device)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.254060] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.254062] ACPI: Added _OSI(Processor Aggregator Device)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441061] ACPI: Interpreter enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441080] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441085] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441102] ACPI: (supports S0 S3 S4 S5)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441104] ACPI: Using IOAPIC for interrupt routing
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.441335] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.444428] ACPI: Power Resource [APPR] (off)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451100] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451110] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451330] acpi PNP0A08:00: _OSC: platform does not support [PCIeCapability]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451463] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451467] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451470] acpi PNP0A08:00: _OSC: platform willing to grant [PCIeHotplug PME AER]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451473] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451629] acpi PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cf1ff])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451633] acpi PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000d3fff] (conflicts with Adapter ROM [mem 0x000cf800-0x000d07ff])
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451886] PCI host bridge to bus 0000:00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451890] pci_bus 0000:00: root bus resource [bus 00-ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451892] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451895] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451898] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451900] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451903] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451905] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451908] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451911] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451913] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451916] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451918] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451921] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451923] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451926] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451928] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xdfffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451931] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfffdffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.451941] pci 0000:00:00.0: [1022:1705] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452051] pci 0000:00:01.0: [1002:9649] type 00 class 0x030000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452065] pci 0000:00:01.0: reg 0x10: [mem 0xb0000000-0xbfffffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452072] pci 0000:00:01.0: reg 0x14: [io  0x7000-0x70ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452080] pci 0000:00:01.0: reg 0x18: [mem 0xd8100000-0xd813ffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452130] pci 0000:00:01.0: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452212] pci 0000:00:01.1: [1002:1714] type 00 class 0x040300
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452223] pci 0000:00:01.1: reg 0x10: [mem 0xd8144000-0xd8147fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452282] pci 0000:00:01.1: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452410] pci 0000:00:03.0: [1022:1708] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452475] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452569] pci 0000:00:04.0: [1022:1709] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452633] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452680] pci 0000:00:04.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452731] pci 0000:00:05.0: [1022:170a] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452806] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452852] pci 0000:00:05.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.452952] pci 0000:00:07.0: [1022:170c] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453015] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453064] pci 0000:00:07.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453186] pci 0000:00:10.0: [1022:7812] type 00 class 0x0c0330
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453211] pci 0000:00:10.0: reg 0x10: [mem 0xd8148000-0xd8149fff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453319] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453373] pci 0000:00:10.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453483] pci 0000:00:10.1: [1022:7812] type 00 class 0x0c0330
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453510] pci 0000:00:10.1: reg 0x10: [mem 0xd814a000-0xd814bfff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453632] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453686] pci 0000:00:10.1: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453796] pci 0000:00:11.0: [1022:7801] type 00 class 0x010601
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453818] pci 0000:00:11.0: reg 0x10: [io  0x7118-0x711f]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453829] pci 0000:00:11.0: reg 0x14: [io  0x7124-0x7127]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453841] pci 0000:00:11.0: reg 0x18: [io  0x7110-0x7117]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453852] pci 0000:00:11.0: reg 0x1c: [io  0x7120-0x7123]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453864] pci 0000:00:11.0: reg 0x20: [io  0x7100-0x710f]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.453875] pci 0000:00:11.0: reg 0x24: [mem 0xd8151000-0xd81517ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454050] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454066] pci 0000:00:12.0: reg 0x10: [mem 0xd8150000-0xd8150fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454231] pci 0000:00:12.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454332] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454355] pci 0000:00:12.2: reg 0x10: [mem 0xd814f000-0xd814f0ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454450] pci 0000:00:12.2: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454452] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454497] pci 0000:00:12.2: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454596] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454612] pci 0000:00:13.0: reg 0x10: [mem 0xd814e000-0xd814efff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454773] pci 0000:00:13.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454875] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454897] pci 0000:00:13.2: reg 0x10: [mem 0xd814d000-0xd814d0ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454992] pci 0000:00:13.2: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.454994] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455040] pci 0000:00:13.2: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455141] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455337] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455362] pci 0000:00:14.2: reg 0x10: [mem 0xd8140000-0xd8143fff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455438] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455722] pci 0000:00:14.2: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.455815] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456010] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456167] pci 0000:00:14.5: [1022:7809] type 00 class 0x0c0310
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456183] pci 0000:00:14.5: reg 0x10: [mem 0xd814c000-0xd814cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456374] pci 0000:00:15.0: [1022:43a0] type 01 class 0x060400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456476] pci 0000:00:15.0: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456527] pci 0000:00:15.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456633] pci 0000:00:18.0: [1022:1700] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456731] pci 0000:00:18.1: [1022:1701] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456831] pci 0000:00:18.2: [1022:1702] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.456925] pci 0000:00:18.3: [1022:1703] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457028] pci 0000:00:18.4: [1022:1704] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457119] pci 0000:00:18.5: [1022:1718] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457212] pci 0000:00:18.6: [1022:1716] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457304] pci 0000:00:18.7: [1022:1719] type 00 class 0x060000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457550] pci 0000:01:00.0: [1002:6760] type 00 class 0x030000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457570] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457583] pci 0000:01:00.0: reg 0x18: [mem 0xd8000000-0xd801ffff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457591] pci 0000:01:00.0: reg 0x20: [io  0x6000-0x60ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457606] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.457656] pci 0000:01:00.0: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.464983] pci 0000:00:03.0: PCI bridge to [bus 01]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465003] pci 0000:00:03.0:   bridge window [io  0x6000-0x6fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465013] pci 0000:00:03.0:   bridge window [mem 0xd8000000-0xd80fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465025] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465175] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465195] pci 0000:02:00.0: reg 0x10: [io  0x5000-0x50ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465220] pci 0000:02:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465236] pci 0000:02:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465318] pci 0000:02:00.0: supports D1 D2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465320] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.465354] pci 0000:02:00.0: System wakeup disabled by ACPI
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.472985] pci 0000:00:04.0: PCI bridge to [bus 02]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473006] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473015] pci 0000:00:04.0:   bridge window [mem 0xd7000000-0xd7ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473027] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473200] pci 0000:03:00.0: [197b:2392] type 00 class 0x088000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473224] pci 0000:03:00.0: reg 0x10: [mem 0xd6003000-0xd60030ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473290] pci 0000:03:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473428] pci 0000:03:00.2: [197b:2391] type 00 class 0x080501
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473448] pci 0000:03:00.2: reg 0x10: [mem 0xd6002000-0xd60020ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473632] pci 0000:03:00.3: [197b:2393] type 00 class 0x088000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.473652] pci 0000:03:00.3: reg 0x10: [mem 0xd6001000-0xd60010ff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481003] pci 0000:00:05.0: PCI bridge to [bus 03]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481023] pci 0000:00:05.0:   bridge window [io  0x4000-0x4fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481031] pci 0000:00:05.0:   bridge window [mem 0xd6000000-0xd6ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481037] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481178] pci 0000:04:00.0: [168c:002b] type 00 class 0x028000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481203] pci 0000:04:00.0: reg 0x10: [mem 0xd5000000-0xd500ffff 64bit]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481313] pci 0000:04:00.0: supports D1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.481315] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.488985] pci 0000:00:07.0: PCI bridge to [bus 04-06]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489005] pci 0000:00:07.0:   bridge window [io  0x3000-0x3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489015] pci 0000:00:07.0:   bridge window [mem 0xd5000000-0xd5ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489027] pci 0000:00:07.0:   bridge window [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489235] pci 0000:00:14.4: PCI bridge to [bus 07] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489246] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489247] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489249] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489251] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489254] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489262] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489264] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489266] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489268] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489270] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489272] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489273] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489275] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489277] pci 0000:00:14.4:   bridge window [mem 0x000f0000-0x000fffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489279] pci 0000:00:14.4:   bridge window [mem 0xb0000000-0xdfffffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489281] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfffdffff] (subtractive decode)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489459] acpiphp: Slot [1] registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489487] pci 0000:00:15.0: PCI bridge to [bus 08]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489493] pci 0000:00:15.0:   bridge window [io  0x2000-0x2fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489498] pci 0000:00:15.0:   bridge window [mem 0xd4000000-0xd4ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.489504] pci 0000:00:15.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490591] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490663] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490735] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490808] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490866] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490911] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.490957] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491002] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491123] ACPI: Enabled 5 GPEs in block 00 to 1F
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491180] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491494] vgaarb: setting as boot device: PCI:0000:00:01.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491501] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491514] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491517] vgaarb: loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491519] vgaarb: bridge control possible 0000:01:00.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491521] vgaarb: no bridge control possible 0000:00:01.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.491895] SCSI subsystem initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492018] libata version 3.00 loaded.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492056] ACPI: bus type USB registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492082] usbcore: registered new interface driver usbfs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492094] usbcore: registered new interface driver hub
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492280] usbcore: registered new device driver usb
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.492629] PCI: Using ACPI for IRQ routing
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502212] PCI: pci_cache_line_size set to 64 bytes
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502312] Expanded resource reserved due to conflict with PCI Bus 0000:00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502314] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502316] e820: reserve RAM buffer [mem 0x8f08d000-0x8fffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502318] e820: reserve RAM buffer [mem 0x8fc00000-0x8fffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502319] e820: reserve RAM buffer [mem 0x24f000000-0x24fffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502461] NetLabel: Initializing
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502463] NetLabel:  domain hash size = 128
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502464] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502478] NetLabel:  unlabeled traffic allowed by default
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502756] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.502764] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.504911] Switched to clocksource hpet
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512475] AppArmor: AppArmor Filesystem Enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512524] pnp: PnP ACPI init
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512549] ACPI: bus type PNP registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512693] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512697] system 00:00: [mem 0xfeb00000-0xfeb00fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512704] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512707] system 00:00: [mem 0xfec10000-0xfec10fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512710] system 00:00: [mem 0xfed61000-0xfed61fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512713] system 00:00: [mem 0xfed80000-0xfed80fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512716] system 00:00: [mem 0xfed81000-0xfed81fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512719] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.512724] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513073] system 00:01: [io  0x0400-0x04cf] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513077] system 00:01: [io  0x04d0-0x04d1] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513079] system 00:01: [io  0x04d6] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513082] system 00:01: [io  0x0680-0x06ff] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513084] system 00:01: [io  0x077a] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513087] system 00:01: [io  0x0c00-0x0c01] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513090] system 00:01: [io  0x0c14] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513092] system 00:01: [io  0x0c50-0x0c52] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513095] system 00:01: [io  0x0c6c] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513097] system 00:01: [io  0x0c6f] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513100] system 00:01: [io  0x0cd0-0x0cdb] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513103] system 00:01: [io  0x0220-0x0227] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513105] system 00:01: [io  0x0260-0x0273] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513108] system 00:01: [io  0x0800] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513110] system 00:01: [io  0x0804] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513113] system 00:01: [io  0x087f] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513116] system 00:01: [io  0x0cdc-0x0cdf] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513118] system 00:01: [io  0x0b00-0x0b0f] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513121] system 00:01: [io  0x0b20-0x0b3f] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513124] system 00:01: [io  0x0200-0x027f] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513127] system 00:01: [io  0x0840-0x0847] has been reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513130] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513225] system 00:02: [mem 0x00000000-0x0009ffff] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513228] system 00:02: [mem 0x00100000-0xafffffff] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513231] system 00:02: [mem 0xffe00000-0xffffffff] could not be reserved
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513234] system 00:02: Plug and Play ACPI device, IDs PNP0c01 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513346] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513470] pnp 00:04: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513511] pnp 00:05: Plug and Play ACPI device, IDs SYN0189 SYN0100 SYN0002 PNP0f13 (active)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513944] pnp: PnP ACPI: found 6 devices
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.513946] ACPI: bus type PNP unregistered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523718] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: no compatible bridge window
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523725] pci 0000:03:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523826] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8020000-0xd803ffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523830] pci 0000:00:03.0: PCI bridge to [bus 01]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523834] pci 0000:00:03.0:   bridge window [io  0x6000-0x6fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523839] pci 0000:00:03.0:   bridge window [mem 0xd8000000-0xd80fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523843] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523848] pci 0000:00:04.0: PCI bridge to [bus 02]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523851] pci 0000:00:04.0:   bridge window [io  0x5000-0x5fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523856] pci 0000:00:04.0:   bridge window [mem 0xd7000000-0xd7ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523860] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523867] pci 0000:03:00.0: BAR 6: assigned [mem 0xd6010000-0xd601ffff pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523869] pci 0000:00:05.0: PCI bridge to [bus 03]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523873] pci 0000:00:05.0:   bridge window [io  0x4000-0x4fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523877] pci 0000:00:05.0:   bridge window [mem 0xd6000000-0xd6ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523881] pci 0000:00:05.0:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523887] pci 0000:00:07.0: PCI bridge to [bus 04-06]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523889] pci 0000:00:07.0:   bridge window [io  0x3000-0x3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523894] pci 0000:00:07.0:   bridge window [mem 0xd5000000-0xd5ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523898] pci 0000:00:07.0:   bridge window [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523903] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523964] pci 0000:00:15.0: PCI bridge to [bus 08]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523968] pci 0000:00:15.0:   bridge window [io  0x2000-0x2fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523973] pci 0000:00:15.0:   bridge window [mem 0xd4000000-0xd4ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523978] pci 0000:00:15.0:   bridge window [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523986] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523988] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523991] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523994] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523996] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.523998] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524001] pci_bus 0000:00: resource 10 [mem 0x000d4000-0x000d7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524003] pci_bus 0000:00: resource 11 [mem 0x000d8000-0x000dbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524005] pci_bus 0000:00: resource 12 [mem 0x000dc000-0x000dffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524008] pci_bus 0000:00: resource 13 [mem 0x000e0000-0x000e3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524010] pci_bus 0000:00: resource 14 [mem 0x000e4000-0x000e7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524013] pci_bus 0000:00: resource 15 [mem 0x000e8000-0x000ebfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524015] pci_bus 0000:00: resource 16 [mem 0x000ec000-0x000effff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524017] pci_bus 0000:00: resource 17 [mem 0x000f0000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524020] pci_bus 0000:00: resource 18 [mem 0xb0000000-0xdfffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524022] pci_bus 0000:00: resource 19 [mem 0xf0000000-0xfffdffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524025] pci_bus 0000:01: resource 0 [io  0x6000-0x6fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524027] pci_bus 0000:01: resource 1 [mem 0xd8000000-0xd80fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524030] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524032] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524035] pci_bus 0000:02: resource 1 [mem 0xd7000000-0xd7ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524037] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524040] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524042] pci_bus 0000:03: resource 1 [mem 0xd6000000-0xd6ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524045] pci_bus 0000:03: resource 2 [mem 0xd1000000-0xd1ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524047] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524050] pci_bus 0000:04: resource 1 [mem 0xd5000000-0xd5ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524052] pci_bus 0000:04: resource 2 [mem 0xd2000000-0xd2ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524055] pci_bus 0000:07: resource 4 [io  0x0000-0x0cf7]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524057] pci_bus 0000:07: resource 5 [io  0x0d00-0xffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524060] pci_bus 0000:07: resource 6 [mem 0x000a0000-0x000bffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524062] pci_bus 0000:07: resource 7 [mem 0x000c0000-0x000c3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524065] pci_bus 0000:07: resource 8 [mem 0x000c4000-0x000c7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524067] pci_bus 0000:07: resource 9 [mem 0x000c8000-0x000cbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524070] pci_bus 0000:07: resource 10 [mem 0x000d4000-0x000d7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524072] pci_bus 0000:07: resource 11 [mem 0x000d8000-0x000dbfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524075] pci_bus 0000:07: resource 12 [mem 0x000dc000-0x000dffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524077] pci_bus 0000:07: resource 13 [mem 0x000e0000-0x000e3fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524079] pci_bus 0000:07: resource 14 [mem 0x000e4000-0x000e7fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524082] pci_bus 0000:07: resource 15 [mem 0x000e8000-0x000ebfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524084] pci_bus 0000:07: resource 16 [mem 0x000ec000-0x000effff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524086] pci_bus 0000:07: resource 17 [mem 0x000f0000-0x000fffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524089] pci_bus 0000:07: resource 18 [mem 0xb0000000-0xdfffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524091] pci_bus 0000:07: resource 19 [mem 0xf0000000-0xfffdffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524094] pci_bus 0000:08: resource 0 [io  0x2000-0x2fff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524096] pci_bus 0000:08: resource 1 [mem 0xd4000000-0xd4ffffff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524099] pci_bus 0000:08: resource 2 [mem 0xd3000000-0xd3ffffff 64bit pref]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524139] NET: Registered protocol family 2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524409] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.524682] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525090] TCP: Hash tables configured (established 65536 bind 65536)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525139] TCP: reno registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525156] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525225] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525362] NET: Registered protocol family 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525386] pci 0000:00:01.0: Video device with shadowed ROM
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.525454] pci 0000:00:10.0: enabling device (0000 -> 0002)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.637840] PCI: CLS mismatch (64 != 32), using 64 bytes
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    0.693487] Trying to unpack rootfs image as initramfs...
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.114976] Freeing initrd memory: 19000K (ffff880035ad4000 - ffff880036d62000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115037] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115041] software IO TLB [mem 0x8b08d000-0x8f08d000] (64MB) mapped at [ffff88008b08d000-ffff88008f08cfff]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115373] microcode: CPU0: patch_level=0x03000027
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115383] microcode: CPU1: patch_level=0x03000027
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115525] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115539] LVT offset 0 assigned for vector 0x400
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115563] perf: AMD IBS detected (0x000000ff)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.115609] Scanning for low memory corruption every 60 seconds
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116031] futex hash table entries: 1024 (order: 4, 65536 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116054] Initialise system trusted keyring
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116082] audit: initializing netlink subsys (disabled)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116105] audit: type=2000 audit(1437944743.972:1): initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.116689] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.118836] zpool: loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.118840] zbud: loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.119247] VFS: Disk quotas dquot_6.5.2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.119314] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.120170] fuse init (API version 7.23)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.120365] msgmni has been set to 14894
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.120457] Key type big_key registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121159] Key type asymmetric registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121166] Asymmetric key parser 'x509' registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121241] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121339] io scheduler noop registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121343] io scheduler deadline registered (default)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.121414] io scheduler cfq registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.122913] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.122936] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123015] vesafb: mode is 1366x768x32, linelength=5504, pages=0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123016] vesafb: scrolling: redraw
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123019] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123350] vesafb: framebuffer at 0xb0000000, mapped to 0xffffc90010f00000, using 4160k, total 4160k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123685] Console: switching to colour frame buffer device 170x48
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.123713] fb0: VESA VGA frame buffer device
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124146] ACPI: AC Adapter [AC] (on-line)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124458] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124463] ACPI: Sleep Button [SLPB]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124514] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124586] ACPI: Lid Switch [LID]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124636] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124639] ACPI: Power Button [PWRF]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.124798] ACPI: acpi_idle registered with cpuidle
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.154579] thermal LNXTHERM:00: registered as thermal_zone0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.154585] ACPI: Thermal Zone [CPUZ] (65 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.178447] thermal LNXTHERM:01: registered as thermal_zone1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.178453] ACPI: Thermal Zone [GFXZ] (57 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.193333] thermal LNXTHERM:02: registered as thermal_zone2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.193339] ACPI: Thermal Zone [EXTZ] (44 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.208271] thermal LNXTHERM:03: registered as thermal_zone3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.208277] ACPI: Thermal Zone [LOCZ] (54 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.223238] thermal LNXTHERM:04: registered as thermal_zone4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.223244] ACPI: Thermal Zone [BATZ] (31 C)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.223317] GHES: HEST is not enabled!
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.223834] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.227570] Linux agpgart interface v0.103
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.230332] brd: module loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.231848] loop: module loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232163] libphy: Fixed MDIO Bus: probed
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232167] tun: Universal TUN/TAP device driver, 1.6
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232169] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232282] PPP generic driver version 2.4.2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232391] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232398] ehci-pci: EHCI PCI platform driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232763] QUIRK: Enable AMD PLL fix
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232799] ehci-pci 0000:00:12.2: EHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232807] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232813] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232826] ehci-pci 0000:00:12.2: debug port 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.232877] ehci-pci 0000:00:12.2: irq 17, io mem 0xd814f000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241108] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241226] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241230] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241232] usb usb1: Product: EHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241235] usb usb1: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241237] usb usb1: SerialNumber: 0000:00:12.2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241512] hub 1-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.241520] hub 1-0:1.0: 5 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242172] ehci-pci 0000:00:13.2: EHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242180] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242186] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242201] ehci-pci 0000:00:13.2: debug port 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.242239] ehci-pci 0000:00:13.2: irq 17, io mem 0xd814d000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253093] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253208] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253211] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253214] usb usb2: Product: EHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253216] usb usb2: Manufacturer: Linux 3.16.0-44-generic ehci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253218] usb usb2: SerialNumber: 0000:00:13.2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253537] hub 2-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253545] hub 2-0:1.0: 5 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253952] ehci-platform: EHCI generic platform driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253972] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.253979] ohci-pci: OHCI PCI platform driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.254342] ohci-pci 0000:00:12.0: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.254350] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.254387] ohci-pci 0000:00:12.0: irq 18, io mem 0xd8150000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.270170] ACPI: Battery Slot [BAT0] (battery present)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313162] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313166] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313168] usb usb3: Product: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313171] usb usb3: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313173] usb usb3: SerialNumber: 0000:00:12.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313582] hub 3-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.313644] hub 3-0:1.0: 5 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.314173] ohci-pci 0000:00:13.0: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.314182] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.314216] ohci-pci 0000:00:13.0: irq 18, io mem 0xd814e000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373317] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373323] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373326] usb usb4: Product: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373328] usb usb4: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373330] usb usb4: SerialNumber: 0000:00:13.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373733] hub 4-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.373793] hub 4-0:1.0: 5 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.374327] ohci-pci 0000:00:14.5: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.374335] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.374368] ohci-pci 0000:00:14.5: irq 18, io mem 0xd814c000
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433226] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433231] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433233] usb usb5: Product: OHCI PCI host controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433235] usb usb5: Manufacturer: Linux 3.16.0-44-generic ohci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433236] usb usb5: SerialNumber: 0000:00:14.5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433637] hub 5-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433697] hub 5-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433908] ohci-platform: OHCI generic platform driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.433929] uhci_hcd: USB Universal Host Controller Interface driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434267] xhci_hcd 0000:00:10.0: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434277] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434504] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434508] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434512] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434617] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434619] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434622] usb usb6: Product: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434624] usb usb6: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.434627] usb usb6: SerialNumber: 0000:00:10.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.435014] hub 6-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.435074] hub 6-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.435261] xhci_hcd 0000:00:10.0: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.435267] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437918] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437921] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437923] usb usb7: Product: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437926] usb usb7: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.437928] usb usb7: SerialNumber: 0000:00:10.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438173] hub 7-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438222] hub 7-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438705] xhci_hcd 0000:00:10.1: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438713] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438941] xhci_hcd 0000:00:10.1: irq 43 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438946] xhci_hcd 0000:00:10.1: irq 44 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.438950] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439052] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439054] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439057] usb usb8: Product: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439059] usb usb8: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439061] usb usb8: SerialNumber: 0000:00:10.1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439389] hub 8-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439448] hub 8-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439650] xhci_hcd 0000:00:10.1: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.439656] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 9
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442344] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442347] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442348] usb usb9: Product: xHCI Host Controller
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442350] usb usb9: Manufacturer: Linux 3.16.0-44-generic xhci_hcd
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442352] usb usb9: SerialNumber: 0000:00:10.1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442611] hub 9-0:1.0: USB hub found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442670] hub 9-0:1.0: 2 ports detected
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.442917] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.445277] i8042: Detected active multiplexing controller, rev 1.1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446422] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446427] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446460] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446488] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.446515] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447082] mousedev: PS/2 mouse device common for all mice
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447506] rtc_cmos 00:03: RTC can wake from S4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447645] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447680] rtc_cmos 00:03: alarms up to one month, 114 bytes nvram, hpet irqs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447779] device-mapper: uevent: version 1.0.3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447895] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.447922] ledtrig-cpu: registered to indicate activity on CPUs
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.448047] TCP: cubic registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.448197] NET: Registered protocol family 10
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.448560] NET: Registered protocol family 17
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.448584] Key type dns_resolver registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.449189] Loading compiled-in X.509 certificates
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.450604] Loaded X.509 cert 'Magrathea: Glacier signing key: 4b6de31c0185e45a0c0d73ca36f8fa02edc6253a'
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.450623] registered taskstats version 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.453622] Key type trusted registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459083] Key type encrypted registered
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459097] AppArmor: AppArmor sha1 policy hashing enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459101] ima: No TPM chip found, activating TPM-bypass!
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459136] evm: HMAC attrs: 0x1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459726]   Magic number: 7:701:96
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.459881] rtc_cmos 00:03: setting system clock to 2015-07-26 21:05:44 UTC (1437944744)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.460097] acpi-cpufreq: overriding BIOS provided _PSD data
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.460252] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.460253] EDD information not available.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.460344] PM: Hibernation image not present or could not be loaded.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.462585] Freeing unused kernel memory: 1352K (ffffffff81d1c000 - ffffffff81e6e000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.462589] Write protecting the kernel read-only data: 12288k
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.464849] Freeing unused kernel memory: 552K (ffff880001776000 - ffff880001800000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.466735] Freeing unused kernel memory: 480K (ffff880001b88000 - ffff880001c00000)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.471790] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.490379] systemd-udevd[103]: starting version 204
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516021] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516037] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516288] r8169 0000:02:00.0: irq 46 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516507] r8169 0000:02:00.0 eth0: RTL8168e/8111e at 0xffffc9000003a000, e4:11:5b:40:3b:c6, XID 0c200000 IRQ 46
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.516510] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.524036] sdhci: Secure Digital Host Controller Interface driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.524040] sdhci: Copyright(c) Pierre Ossman
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.526871] sdhci-pci 0000:03:00.0: SDHCI controller found [197b:2392] (rev 30)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.527840] mmc0: no vqmmc regulator found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.527844] mmc0: no vmmc regulator found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.528059] mmc0: SDHCI controller on PCI [0000:03:00.0] using DMA
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.528083] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 30)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.528196] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.555029] ahci 0000:00:11.0: version 3.0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556000] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556064] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556069] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556611] scsi0 : ahci
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556743] scsi1 : ahci
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556855] ata1: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151100 irq 47
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.556858] ata2: SATA max UDMA/133 abar m2048@0xd8151000 port 0xd8151180 irq 47
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.557095] usb 1-5: new high-speed USB device number 2 using ehci-pci
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742168] usb 1-5: New USB device found, idVendor=0461, idProduct=4dc7
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742180] usb 1-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742187] usb 1-5: Product: HP HD Webcam [Fixed]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742192] usb 1-5: Manufacturer: Primax Electronics Ltd.
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    1.742196] usb 1-5: SerialNumber: PMX02
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.045198] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.045237] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.046163] ata1.00: ATA-8: TOSHIBA MK6476GSX, GS001C, max UDMA/100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.046171] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.046878] ata1.00: configured for UDMA/100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047341] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6476GS 1C   PQ: 0 ANSI: 5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047747] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047792] sd 0:0:0:0: [sda] Write Protect is off
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047813] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.047823] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.049400] ata2.00: ATAPI: hp       DVDRAM GT50N, MP00, max UDMA/100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.053671] ata2.00: configured for UDMA/100
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.058160] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT50N     MP00 PQ: 0 ANSI: 5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.077929] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.077939] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.078260] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.078343] sr 1:0:0:0: Attached scsi generic sg1 type 5
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.106385]  sda: sda1 sda2 sda3 sda4 < sda5 >
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.107239] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.113300] tsc: Refined TSC clocksource calibration: 1896.551 MHz
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.269231] usb 4-5: new full-speed USB device number 2 using ohci-pci
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.419325] psmouse serio4: synaptics: queried max coordinates: x [..5756], y [..4876]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.430431] usb 4-5: New USB device found, idVendor=0cf3, idProduct=3005
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.430437] usb 4-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.494488] psmouse serio4: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x640000/0xa0400, board id: 1397, fw id: 780218
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.543485] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    2.553163] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.113758] Switched to clocksource tsc
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.235298] random: init urandom read with 111 bits of entropy available
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.459277] random: nonblocking pool is initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.803888] init: plymouth-upstart-bridge main process (164) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.803904] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.807426] init: plymouth-upstart-bridge main process (178) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.807442] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.810148] init: plymouth-upstart-bridge main process (180) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.810168] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.813743] init: plymouth-upstart-bridge main process (181) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.813760] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.816408] init: plymouth-upstart-bridge main process (183) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.816428] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.819737] init: plymouth-upstart-bridge main process (184) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.819753] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.822392] init: plymouth-upstart-bridge main process (186) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.822407] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.826166] init: plymouth-upstart-bridge main process (187) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.826182] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.828592] init: plymouth-upstart-bridge main process (189) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.828606] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.832307] init: plymouth-upstart-bridge main process (190) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.832323] init: plymouth-upstart-bridge main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.834875] init: plymouth-upstart-bridge main process (192) terminated with status 1
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    3.834888] init: plymouth-upstart-bridge respawning too fast, stopped
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.202275] Adding 20970492k swap on /dev/sda5.  Priority:-1 extents:1 across:20970492k FS
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.400169] systemd-udevd[293]: starting version 204
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.541776] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.767833] lp: driver loaded but no devices found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.786934] ppdev: user-space parallel port driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.791414] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.813545] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.873269] acpi device:00: registered as cooling_device2
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.873395] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.874085] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.876958] hp_accel: laptop model unknown, using default axes configuration
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.886835] lis3lv02d: 8 bits 3DC sensor found
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.892436] wmi: Mapper loaded
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.893119] acpi device:0a: registered as cooling_device3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.893467] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input13
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.893865] snd_hda_intel 0000:00:01.1: irq 48 for MSI/MSI-X
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.918634] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input14
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.923997] sound hdaudioC1D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924008] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924011] sound hdaudioC1D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924013] sound hdaudioC1D0:    mono: mono_out=0x0
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924015] sound hdaudioC1D0:    inputs:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924018] sound hdaudioC1D0:      Internal Mic=0x11
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.924021] sound hdaudioC1D0:      Mic=0xc
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.927412] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input15
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.935148] cfg80211: Calling CRDA to update world regulatory domain
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.959482] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input16
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.959595] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input17
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.991057] ACPI Warning: SystemIO range 0x0000000000000B00-0x0000000000000B07 conflicts with OpRegion 0x0000000000000B00-0x0000000000000B06 (\_SB_.PCI0.SMBS.SMBO) (20140424/utaddress-254)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [    9.991068] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.092049] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.092054] AMD IOMMUv2 functionality not available on this system
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173046] ath: phy0: ASPM enabled: 0x42
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173052] ath: EEPROM regdomain: 0x60
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173055] ath: EEPROM indicates we should expect a direct regpair map
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173058] ath: Country alpha2 being used: 00
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.173059] ath: Regpair used: 0x60
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.182736] kvm: Nested Virtualization enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.182742] kvm: Nested Paging enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199184] Bluetooth: Core ver 2.19
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199217] NET: Registered protocol family 31
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199219] Bluetooth: HCI device and connection manager initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199228] Bluetooth: HCI socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199231] Bluetooth: L2CAP socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.199243] Bluetooth: SCO socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.205212] Bluetooth: RFCOMM TTY layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.205225] Bluetooth: RFCOMM socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.205233] Bluetooth: RFCOMM ver 1.11
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.209157] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.209670] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xffffc90011360000, irq=19
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.216186] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.216190] Bluetooth: BNEP filters: protocol multicast
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.216200] Bluetooth: BNEP socket layer initialized
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.260372] audit: type=1400 audit(1437933953.293:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=505 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.260383] audit: type=1400 audit(1437933953.293:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=505 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.261030] audit: type=1400 audit(1437933953.293:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=505 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.263329] audit: type=1400 audit(1437933953.297:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.263342] audit: type=1400 audit(1437933953.297:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.263347] audit: type=1400 audit(1437933953.297:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.263994] audit: type=1400 audit(1437933953.297:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.264002] audit: type=1400 audit(1437933953.297:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.264346] audit: type=1400 audit(1437933953.297:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.267788] usbcore: registered new interface driver btusb
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.361791] init: cups main process (550) killed by HUP signal
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.361806] init: cups main process ended, respawning
Jul 26 21:05:53 ivan-HP-ProBook-4535s failsafe: Failsafe of 120 seconds reached.
Jul 26 21:05:53 ivan-HP-ProBook-4535s rsyslogd-2039: Could no open output pipe '/dev/xconsole': No such file or directory [try http://www.rsyslog.com/e/2039 ]
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.632452] init: failsafe main process (605) killed by TERM signal
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683599] cfg80211: World regulatory domain updated:
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683607] cfg80211:  DFS Master region: unset
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683609] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683613] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683616] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683619] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683621] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.683623] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
Jul 26 21:05:53 ivan-HP-ProBook-4535s kernel: [   10.768179] input: HP WMI hotkeys as /devices/virtual/input/input18
Jul 26 21:05:53 ivan-HP-ProBook-4535s bluetoothd[499]: hci0: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Jul 26 21:05:53 ivan-HP-ProBook-4535s bluetoothd[499]: Adapter /org/bluez/499/hci0 has been enabled
Jul 26 21:05:53 ivan-HP-ProBook-4535s mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-5"
Jul 26 21:05:53 ivan-HP-ProBook-4535s mtp-probe: bus: 1, device: 2 was not an MTP device
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.011267] media: Linux media interface: v0.10
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.016938] Linux video capture interface: v2.00
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.033081] audit: type=1400 audit(1437933954.065:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=760 comm="apparmor_parser"
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.033343] uvcvideo: Found UVC 1.00 device HP HD Webcam [Fixed] (0461:4dc7)
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.119890] hp_wmi: Unknown event_id - 0 - 0x0
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.119949] pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.119964] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.307218] input: HP HD Webcam [Fixed] as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input19
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.307366] usbcore: registered new interface driver uvcvideo
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.307368] USB Video Class driver (1.1.1)
Jul 26 21:05:54 ivan-HP-ProBook-4535s ModemManager[674]: <info>  ModemManager (version 1.0.0) starting...
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.494590] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.494596] Disabling lock debugging due to kernel taint
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.509331] fglrx: module verification failed: signature and/or  required key missing - tainting kernel
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.550511] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7226 MBytes.
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.550675] <6>[fglrx]   vendor: 1002 device: 9649 revision: 0 count: 1
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.551014] <6>[fglrx]   vendor: 1002 device: 6760 revision: 0 count: 2
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.551344] <6>[fglrx] ioport: bar 1, base 0x7000, size: 0x100
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.552014] <6>[fglrx] ioport: bar 4, base 0x6000, size: 0x100
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.552024] pci 0000:01:00.0: enabling device (0000 -> 0003)
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.552246] <6>[fglrx] Kernel PAT support is enabled
Jul 26 21:05:54 ivan-HP-ProBook-4535s kernel: [   11.552281] <6>[fglrx] module loaded - fglrx 15.20.3 [Jun 22 2015] with 2 minors
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> NetworkManager (version 0.9.8.8) is starting...
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WEXT support is enabled
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> DNS: loaded plugin dnsmasq
Jul 26 21:05:54 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Jul 26 21:05:54 ivan-HP-ProBook-4535s polkitd[835]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jul 26 21:05:54 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: init!
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: update_system_hostname
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:       interface-parser: parsing file /etc/network/interfaces
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:       interface-parser: finished parsing file /etc/network/interfaces
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPluginIfupdown: management mode: unmanaged
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/wlan0, iface: wlan0)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: end _init.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: init!
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: end _init.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Loaded plugin (null): (null)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    Ifupdown: get unmanaged devices count: 0
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: (27823888) ... get_connections.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ifupdown: (27823888) ... get_connections (managed=false): return empty list.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    keyfile: parsing Ivan Mihaylov ... 
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    keyfile:     read connection 'Ivan Mihaylov'
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    keyfile: parsing Sinjo13 ... 
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    keyfile:     read connection 'Sinjo13'
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: (27630416) ... get_connections.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    SCPlugin-Ofono: (27630416) connections count: 0
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]:    Ifupdown: get unmanaged devices count: 0
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0/ieee80211/phy0/rfkill0) (driver ath9k)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> rfkill2: found WiFi radio killswitch (at /sys/devices/platform/hp-wmi/rfkill/rfkill2) (platform driver hp-wmi)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WiFi enabled by radio killswitch; enabled by state file
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WWAN enabled by radio killswitch; enabled by state file
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Networking is enabled by state file
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> failed to allocate link cache: (-12) Object not found
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): carrier is OFF
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 26 21:05:54 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): bringing up device.
Jul 26 21:05:55 ivan-HP-ProBook-4535s anacron[931]: Anacron 2.3 started on 2015-07-26
Jul 26 21:05:55 ivan-HP-ProBook-4535s anacron[931]: Normal exit (0 jobs run)
Jul 26 21:05:55 ivan-HP-ProBook-4535s acpid: starting up with netlink and the input layer
Jul 26 21:05:55 ivan-HP-ProBook-4535s ntpdate[1005]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Jul 26 21:05:55 ivan-HP-ProBook-4535s ntpdate[1005]: no servers can be used, exiting
Jul 26 21:05:55 ivan-HP-ProBook-4535s cron[890]: (CRON) INFO (pidfile fd = 3)
Jul 26 21:05:55 ivan-HP-ProBook-4535s cron[1026]: (CRON) STARTUP (fork ok)
Jul 26 21:05:55 ivan-HP-ProBook-4535s acpid: 11 rules loaded
Jul 26 21:05:55 ivan-HP-ProBook-4535s acpid: waiting for events: event logging is off
Jul 26 21:05:55 ivan-HP-ProBook-4535s cron[1026]: (CRON) INFO (Running @reboot jobs)
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.285947] vboxdrv: Found 2 processor cores.
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.288216] vboxdrv: fAsync=0 offMin=0x4aa offMax=0x2275
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.288367] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.288369] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.290952] r8169 0000:02:00.0 eth0: link down
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.291618] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): preparing device.
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (eth0): deactivating device (reason 'managed') [2]
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): using nl80211 for WiFi device control
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): driver supports Access Point (AP) mode
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath9k' ifindex: 3)
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): bringing up device.
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): preparing device.
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.312799] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jul 26 21:05:55 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='fi.w1.wpa_supplicant1' (using servicehelper)
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> urfkill disappeared from the bus
Jul 26 21:05:55 ivan-HP-ProBook-4535s kernel: [   12.322835] vboxpci: IOMMU not found (not registered)
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> ModemManager available in the bus
Jul 26 21:05:55 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'fi.w1.wpa_supplicant1'
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> wpa_supplicant started
Jul 26 21:05:55 ivan-HP-ProBook-4535s wpa_supplicant[1055]: Successfully initialized wpa_supplicant
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0) supports 4 scan SSIDs
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> Trying to remove a non-existant call id.
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: starting -> ready
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: ready -> disconnected
Jul 26 21:05:55 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0) supports 4 scan SSIDs
Jul 26 21:05:55 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: Reject scan trigger since one is already pending
Jul 26 21:05:55 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 21:05:56 ivan-HP-ProBook-4535s whoopsie[927]: whoopsie 0.2.24.6 starting up.
Jul 26 21:05:56 ivan-HP-ProBook-4535s whoopsie[927]: Using lock path: /var/lock/whoopsie/lock
Jul 26 21:05:56 ivan-HP-ProBook-4535s whoopsie[1138]: offline
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.268300] init: plymouth-splash main process (1161) terminated with status 1
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Auto-activating connection 'Ivan Mihaylov'.
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) starting connection 'Ivan Mihaylov'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> NetworkManager state is now CONNECTING
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0/wireless): connection 'Ivan Mihaylov' has security, and secrets exist.  No new secrets needed.
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'ssid' value 'Ivan Mihaylov'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'scan_ssid' value '1'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'auth_alg' value 'OPEN'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: added 'psk' value '<omitted>'
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Config: set interface ap_scan to 1
Jul 26 21:05:56 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: SME: Trying to authenticate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.389769] wlan0: authenticate with c8:3a:35:4d:4b:08
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Jul 26 21:05:56 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: Trying to associate with c8:3a:35:4d:4b:08 (SSID='Ivan Mihaylov' freq=2432 MHz)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.396041] wlan0: send auth to c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.397785] wlan0: authenticated
Jul 26 21:05:56 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: Associated with c8:3a:35:4d:4b:08
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.398856] wlan0: associate with c8:3a:35:4d:4b:08 (try 1/3)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.402743] wlan0: RX AssocResp from c8:3a:35:4d:4b:08 (capab=0x11 status=0 aid=2)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.402838] wlan0: associated
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.402883] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.402935] cfg80211: Calling CRDA for country: CN
Jul 26 21:05:56 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: authenticating -> associated
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406461] ath: EEPROM regdomain: 0x809c
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406467] ath: EEPROM indicates we should expect a country code
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406469] ath: doing EEPROM country->regdmn map search
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406470] ath: country maps to regdmn code: 0x52
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406472] ath: Country alpha2 being used: CN
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406474] ath: Regpair used: 0x52
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406476] ath: regdomain 0x809c dynamically updated by country IE
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406500] cfg80211: Regulatory domain changed to country: CN
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406502] cfg80211:  DFS Master region: unset
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406504] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406507] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406510] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406512] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406514] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s kernel: [   13.406516] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
Jul 26 21:05:56 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Jul 26 21:05:57 ivan-HP-ProBook-4535s accounts-daemon[1218]: started daemon version 0.6.35
Jul 26 21:05:57 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.Accounts'
Jul 26 21:05:57 ivan-HP-ProBook-4535s ModemManager[674]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0': not supported by any plugin
Jul 26 21:05:57 ivan-HP-ProBook-4535s ModemManager[674]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:07.0/0000:04:00.0': not supported by any plugin
Jul 26 21:05:57 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: associated -> group handshake
Jul 26 21:06:00 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Jul 26 21:06:00 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.UPower'
Jul 26 21:06:00 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: WPA: Key negotiation completed with c8:3a:35:4d:4b:08 [PTK=CCMP GTK=CCMP]
Jul 26 21:06:00 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: CTRL-EVENT-CONNECTED - Connection to c8:3a:35:4d:4b:08 completed [id=0 id_str=]
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): supplicant interface state: group handshake -> completed
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Ivan Mihaylov'.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> dhclient started with pid 1375
Jul 26 21:06:00 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Internet Systems Consortium DHCP Client 4.2.4
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Copyright 2004-2012 Internet Systems Consortium.
Jul 26 21:06:00 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: All rights reserved.
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: 
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully called chroot.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully dropped privileges.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully limited resources.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Running.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 1378 of process 1378 (n/a) owned by '112' high priority at nice level -11.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 1 threads of 1 processes of 1 users.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Watchdog thread running.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Canary thread running.
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Listening on LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Sending on   LPF/wlan0/9c:b7:0d:7f:c3:44
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: Sending on   Socket/fallback
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 255.255.255.255 port 67 (xid=0x2e3e2690)
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
Jul 26 21:06:00 ivan-HP-ProBook-4535s dhclient: bound to 192.168.0.102 -- renewal in 34908 seconds.
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info>   address 192.168.0.102
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info>   prefix 24 (255.255.255.0)
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info>   gateway 192.168.0.1
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info>   nameserver '192.168.1.1'
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jul 26 21:06:00 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 1453 of process 1378 (n/a) owned by '112' RT at priority 5.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 2 threads of 1 processes of 1 users.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 1471 of process 1378 (n/a) owned by '112' RT at priority 5.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 3 threads of 1 processes of 1 users.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 1472 of process 1378 (n/a) owned by '112' RT at priority 5.
Jul 26 21:06:00 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 4 threads of 1 processes of 1 users.
Jul 26 21:06:00 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/HFPAG
Jul 26 21:06:00 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/HFPHS
Jul 26 21:06:00 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/A2DPSource
Jul 26 21:06:00 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.35 path=/MediaEndpoint/A2DPSink
Jul 26 21:06:01 ivan-HP-ProBook-4535s anacron[1490]: Anacron 2.3 started on 2015-07-26
Jul 26 21:06:01 ivan-HP-ProBook-4535s anacron[1490]: Normal exit (0 jobs run)
Jul 26 21:06:01 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jul 26 21:06:01 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.systemd1'
Jul 26 21:06:01 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Using config file /etc/colord.conf
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Using mapping database file /var/lib/colord/mapping.db
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Using device database file /var/lib/colord/storage.db
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: loaded plugin libcd_plugin_scanner.so
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: loaded plugin libcd_plugin_camera.so
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Daemon ready for requests
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Jul 26 21:06:01 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-526fbc9bdf0d7156c553998d47a3b5fc
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-fb0ac62618f016ed9b92ce239258efa8
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-d4a7a2bd8ddaacf10e275e3db31d72b8
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-f64a1f19ce07290b35a752b00217b684
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> NetworkManager state is now CONNECTED_GLOBAL
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Policy set 'Ivan Mihaylov' (wlan0) as default for IPv4 routing and DNS.
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> DNS: starting dnsmasq...
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-ea421e3a65cfa796e2732ce36086e327
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> dnsmasq not available on the bus, can't update servers.
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <error> [1437933961.699190] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> DNS: plugin dnsmasq update failed
Jul 26 21:06:01 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-3bd2261b1125a0fd9ebf827a2d1bed84
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-57f0d896250f6f98f77ca1b0d19019c0
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-d6490883a866e4059370e1de1d840283
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-0720e7cdbc792b77c0740c39f325ef9e
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-2f1f11ecd613fe5551420fcaf5b11ff8
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-a1d13bd5309e0f06ceda6f0d75367823
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-df7c0067b1eb9bcc9fc9b33bc3a797eb
Jul 26 21:06:01 ivan-HP-ProBook-4535s dnsmasq[1633]: started, version 2.68 cache disabled
Jul 26 21:06:01 ivan-HP-ProBook-4535s dnsmasq[1633]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Jul 26 21:06:01 ivan-HP-ProBook-4535s dnsmasq[1633]: DBus support enabled: connected to system bus
Jul 26 21:06:01 ivan-HP-ProBook-4535s dnsmasq[1633]: warning: no upstream servers configured
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Device added: xrandr-default
Jul 26 21:06:01 ivan-HP-ProBook-4535s colord: Profile added: icc-7a9564ffe8e4686f7064491b7f3c6153
Jul 26 21:06:02 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) successful, device activated.
Jul 26 21:06:02 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jul 26 21:06:02 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> dnsmasq appeared on DBus: :1.43
Jul 26 21:06:02 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Writing DNS information to /sbin/resolvconf
Jul 26 21:06:02 ivan-HP-ProBook-4535s dnsmasq[1633]: setting upstream servers from DBus
Jul 26 21:06:02 ivan-HP-ProBook-4535s dnsmasq[1633]: using nameserver 192.168.1.1#53
Jul 26 21:06:02 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jul 26 21:06:02 ivan-HP-ProBook-4535s whoopsie[1138]: message repeated 3 times: [ offline]
Jul 26 21:06:02 ivan-HP-ProBook-4535s whoopsie[1138]: online
Jul 26 21:06:05 ivan-HP-ProBook-4535s colord: device removed: xrandr-default
Jul 26 21:06:05 ivan-HP-ProBook-4535s colord: Profile removed: icc-7a9564ffe8e4686f7064491b7f3c6153
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <info> WiFi hardware radio set enabled
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.sleep-wake: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.32': no such name
Jul 26 21:06:05 ivan-HP-ProBook-4535s kernel: [   22.420326] fglrx_pci 0000:00:01.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Jul 26 21:06:05 ivan-HP-ProBook-4535s kernel: [   22.420339] pci 0000:00:14.4: PCI bridge to [bus 07]
Jul 26 21:06:09 ivan-HP-ProBook-4535s ntpdate[1766]: step time server 91.189.89.199 offset 0.514630 sec
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 2065 of process 2065 (n/a) owned by '1000' high priority at nice level -11.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 5 threads of 2 processes of 2 users.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 2069 of process 2065 (n/a) owned by '1000' RT at priority 5.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 6 threads of 2 processes of 2 users.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 2072 of process 2065 (n/a) owned by '1000' RT at priority 5.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 7 threads of 2 processes of 2 users.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Successfully made thread 2073 of process 2065 (n/a) owned by '1000' RT at priority 5.
Jul 26 21:06:09 ivan-HP-ProBook-4535s rtkit-daemon[1380]: Supervising 8 threads of 2 processes of 2 users.
Jul 26 21:06:09 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/HFPAG
Jul 26 21:06:09 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/HFPHS
Jul 26 21:06:09 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/A2DPSource
Jul 26 21:06:09 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint registered: sender=:1.66 path=/MediaEndpoint/A2DPSink
Jul 26 21:06:09 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Jul 26 21:06:09 ivan-HP-ProBook-4535s colord: Device added: xrandr-default
Jul 26 21:06:09 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.locale1'
Jul 26 21:06:10 ivan-HP-ProBook-4535s colord: Profile added: icc-8047dcbd0521d15201185b4fe16ea653
Jul 26 21:06:12 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Jul 26 21:06:13 ivan-HP-ProBook-4535s udisksd[2221]: udisks daemon version 2.1.3 starting
Jul 26 21:06:13 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Jul 26 21:06:13 ivan-HP-ProBook-4535s udisksd[2221]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Jul 26 21:06:19 ivan-HP-ProBook-4535s wpa_supplicant[1070]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jul 26 21:06:21 ivan-HP-ProBook-4535s NetworkManager[821]: <info> (wlan0): IP6 addrconf timed out or failed.
Jul 26 21:06:21 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jul 26 21:06:21 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jul 26 21:06:21 ivan-HP-ProBook-4535s NetworkManager[821]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jul 26 21:06:23 ivan-HP-ProBook-4535s kernel: [   40.427257] audit_printk_skb: 150 callbacks suppressed
Jul 26 21:06:23 ivan-HP-ProBook-4535s kernel: [   40.427263] audit: type=1400 audit(1437933983.975:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2351 comm="apparmor_parser"
Jul 26 21:06:23 ivan-HP-ProBook-4535s kernel: [   40.427276] audit: type=1400 audit(1437933983.975:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2351 comm="apparmor_parser"
Jul 26 21:06:23 ivan-HP-ProBook-4535s kernel: [   40.427828] audit: type=1400 audit(1437933983.975:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2351 comm="apparmor_parser"
Jul 26 21:06:25 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/HFPAG
Jul 26 21:06:25 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/HFPHS
Jul 26 21:06:25 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/A2DPSource
Jul 26 21:06:25 ivan-HP-ProBook-4535s bluetoothd[499]: Endpoint unregistered: sender=:1.35 path=/MediaEndpoint/A2DPSink
Jul 26 21:06:42 ivan-HP-ProBook-4535s gnome-session[1995]: GLib-CRITICAL: g_environ_setenv: assertion 'value != NULL' failed
Jul 26 21:11:14 ivan-HP-ProBook-4535s NetworkManager[821]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted
Jul 26 21:17:01 ivan-HP-ProBook-4535s CRON[2709]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 26 21:21:45 ivan-HP-ProBook-4535s dbus[408]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Jul 26 21:21:45 ivan-HP-ProBook-4535s dbus[408]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

From what I understand there is some issue with the signature of the flgrx, but is this a critical issue? Also what are those bogus alignments? 

And last but not least - is there something more to worry about from what could be seen from the logs?

Sorry for the stupid questions and thank you for spending your time with my issues... 

Regards,
Ivan

---

### Post by oldfred on 2015-07-26
Try with just the option, but not nomodeset.

Still seems like a video driver issue, and with two AMD video, how do you control which is used? 
I do not know about AMD much less dual AMD. 
Are they one video port or just two different ports to give different connections?

I found this in my notes from others, but do not know if even current now.
       Dell AMDIntel  dual video 
[URL="http://ubuntuforums.org/showthread.php?t=2240312"]http://ubuntuforums.org/showthread.php?t=2240312

[/URL]
 [URL="https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver"]https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver


[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2240312"]
[/URL]

---

### Post by Ivan_Mihaylov on 2015-07-28
At last I managed to clear the boot and performance issues. They were both graphic related... Actually I could've done something else too, but currently I can't recall it.

The things that i done:

1. I removed the current **fglrx**:

```
sudo apt-get remove --purge fglrx*
```

2. Rebooted

3. Installed all updates (from Terminal and from GUI)

```
sudo apt-get update
sudo apt-get upgrade
```

4. Installed the **generic linux headers**

```
sudo apt-get install linux-headers-generic
```

5. Installed the video driver and the hardware acceleration

```
sudo apt-get install fglrx xvba-va-driver libva-glx1 libva-egl1 vainfo
```

6. Generated new **xorg.conf** for both adapters

```
sudo amdconfig --adapter=all --initial
```

7. Rebooted to get changes up

Now the results of **fglrxinfo** and **vainfo** are:

[B]fglrxinfo:
[/B]```
display: :0  screen: 0OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 7400M Series
OpenGL version string: 4.4.13374 Compatibility Profile Context 15.20.1013

```

**vainfo**:
[/CODE]libva info: VA-API version 0.35.0libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_32
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.35 (libva 1.3.0)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
[/CODE]

I'm really proud of myself for solving this one and I hope my thread to help others too.
Thanks for all replies again!

Best regards,
Ivan

---

