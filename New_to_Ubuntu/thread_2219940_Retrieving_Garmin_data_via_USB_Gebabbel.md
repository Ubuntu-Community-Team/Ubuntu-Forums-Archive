---
title: "Retrieving Garmin data via USB Gebabbel"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by jimbo6 on 2014-04-26
I've acquired a Garmin etrex visa HCX (usb) device which has some really interesting waypoints stored in it. I would like to retrieve the data (stored on the device itself, not on micro SD) via gebabbel so that I can use it on QGIS (and yes, I'm using the Garmin usb cable which is in excellent condition). I'm using Ubuntu 14.04 LTS.

I can view the waypoint data on the device and when I connect it to my computer, I activate the "connect as mass storage device" option in "interface". 

In Gebabbel, however, I encounter this error:
```
A problem was detected by gpsbabel.
No Garmin USB device seems to be connected to the computer.


The original error message reported by gpsbabel was:
Found no Garmin USB devices.

```

I receive the same result when I run gebabbel with sudo privileges.

With a Micro SD card inserted, I can browse the micro SD card's data only. There is no way I can think of to access the device's data itself.

dmesg output (only one usb device [the Garmin] connected): 

```
[    1.153959] ata1.00: supports DRM functions and may not be fully accessible
[    1.154067] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    1.154069] ata1.00: ATA-9: SAMSUNG MZ7TD256HAFV-000L7, DXT04L6Q, max UDMA/133
[    1.154070] ata1.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.154482] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.154485] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.154674] ata1.00: supports DRM functions and may not be fully accessible
[    1.154782] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    1.154854] ata1.00: configured for UDMA/133
[    1.157551] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.157553] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.157906] hub 1-1:1.0: USB hub found
[    1.158045] hub 1-1:1.0: 6 ports detected
[    1.161300] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG MZ7TD256 DXT0 PQ: 0 ANSI: 5
[    1.161393] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    1.161401] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.161443] sd 0:0:0:0: [sda] Write Protect is off
[    1.161446] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.161463] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.162334]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 > sda4
[    1.163117] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.269265] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.361560] firewire_core 0000:02:00.3: created device fw0: GUID 3c970eff835afdff, S400
[    1.401810] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.401816] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.402069] hub 2-1:1.0: USB hub found
[    1.402152] hub 2-1:1.0: 8 ports detected
[    1.441452] tsc: Refined TSC clocksource calibration: 2793.654 MHz
[    1.481508] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.490876] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.491672] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.491996] ata2.00: ATAPI: PLDS DVD-RW DS8A8SH, KU54, max UDMA/100
[    1.499563] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[    1.500358] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[    1.500672] ata2.00: configured for UDMA/100
[    1.513671] scsi 1:0:0:0: CD-ROM            PLDS     DVD-RW DS8A8SH   KU54 PQ: 0 ANSI: 5
[    1.517797] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.517803] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.517979] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.518041] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.569624] usb 3-1: new full-speed USB device number 2 using xhci_hcd
[    1.586424] usb 3-1: New USB device found, idVendor=091e, idProduct=0003
[    1.586430] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.657915] usb 1-1.2: new full-speed USB device number 3 using ehci-pci
[    1.753666] usb 1-1.2: New USB device found, idVendor=046d, idProduct=c52b
[    1.753672] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.753675] usb 1-1.2: Product: USB Receiver
[    1.753678] usb 1-1.2: Manufacturer: Logitech
[    1.756885] hidraw: raw HID events driver (C) Jiri Kosina
[    1.762607] usbcore: registered new interface driver usbhid
[    1.762609] usbhid: USB HID core driver
[    1.765180] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.2/input2
[    1.768846] input: Logitech Unifying Device. Wireless PID:1028 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.2/0003:046D:C52B.0003/input/input5
[    1.768951] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1028] on usb-0000:00:1a.0-1.2:1
[    1.826129] usb 1-1.4: new full-speed USB device number 4 using ehci-pci
[    1.837945] ata5: SATA link down (SStatus 0 SControl 300)
[    1.866747] EXT4-fs (sda6): mounting ext3 file system using the ext4 subsystem
[    1.867950] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    1.922368] usb 1-1.4: New USB device found, idVendor=0a5c, idProduct=21e6
[    1.922371] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.922372] usb 1-1.4: Product: BCM20702A0
[    1.922374] usb 1-1.4: Manufacturer: Broadcom Corp
[    1.922375] usb 1-1.4: SerialNumber: F4B7E2E6288F
[    1.941788] random: init urandom read with 71 bits of entropy available
[    1.963336] init: plymouth-upstart-bridge main process (193) terminated with status 1
[    1.963350] init: plymouth-upstart-bridge main process ended, respawning
[    1.969413] init: plymouth-upstart-bridge main process (203) terminated with status 1
[    1.969423] init: plymouth-upstart-bridge main process ended, respawning
[    1.972880] init: plymouth-upstart-bridge main process (206) terminated with status 1
[    1.972894] init: plymouth-upstart-bridge main process ended, respawning
[    1.975550] init: plymouth-upstart-bridge main process (209) terminated with status 1
[    1.975564] init: plymouth-upstart-bridge main process ended, respawning
[    1.994383] usb 1-1.6: new high-speed USB device number 5 using ehci-pci
[    2.067112] Adding 7944188k swap on /dev/sda7.  Priority:-1 extents:1 across:7944188k SSFS
[    2.071604] random: nonblocking pool is initialized
[    2.085286] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.094165] usb 1-1.6: New USB device found, idVendor=5986, idProduct=02d2
[    2.094169] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.094171] usb 1-1.6: Product: Integrated Camera
[    2.094173] usb 1-1.6: Manufacturer: Ricoh Company Ltd.
[    2.094870] usb 3-1: USB disconnect, device number 2
[    2.130157] systemd-udevd[325]: starting version 204
[    2.179212] lp: driver loaded but no devices found
[    2.192930] ppdev: user-space parallel port driver
[    2.195502] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    2.210233] wmi: Mapper loaded
[    2.229108] [drm] Initialized drm 1.1.0 20060810
[    2.268915] type=1400 audit(1398489297.006:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=402 comm="apparmor_parser"
[    2.268921] type=1400 audit(1398489297.006:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=402 comm="apparmor_parser"
[    2.268924] type=1400 audit(1398489297.006:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=402 comm="apparmor_parser"
[    2.269277] type=1400 audit(1398489297.006:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=402 comm="apparmor_parser"
[    2.269283] type=1400 audit(1398489297.006:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=402 comm="apparmor_parser"
[    2.269482] type=1400 audit(1398489297.006:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=402 comm="apparmor_parser"
[    2.271277] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[    2.272056] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20131115/nsarguments-95)
[    2.272380] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[    2.273089] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[    2.274545] pci 0000:01:00.0: optimus capabilities: enabled, status dynamic power, hda bios codec supported
[    2.274552] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG_.VID_ handle
[    2.274580] checking generic (e0000000 580000) vs hw (c0000000 10000000)
[    2.274582] checking generic (e0000000 580000) vs hw (d0000000 2000000)
[    2.274604] nouveau 0000:01:00.0: enabling device (0004 -> 0007)
[    2.279543] [drm] hdmi device  not found 1 0 1
[    2.279679] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x0e73c0a2
[    2.279681] nouveau  [  DEVICE][0000:01:00.0] Chipset: GK107 (NVE7)
[    2.279682] nouveau  [  DEVICE][0000:01:00.0] Family : NVE0
[    2.281070] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[    2.329269] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[    2.329271] nouveau  [   VBIOS][0000:01:00.0] checking PROM for image...
[    2.329344] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[    2.329346] nouveau  [   VBIOS][0000:01:00.0] checking ACPI for image...
[    2.340907] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \_SB_.PCI0.LPC_.PMIO 1 (20131115/utaddress-251)
[    2.340914] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.340918] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPC_.LPIO 1 (20131115/utaddress-251)
[    2.340922] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.340923] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.LPC_.LPIO 1 (20131115/utaddress-251)
[    2.340926] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.340928] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    2.342870] cfg80211: Calling CRDA to update world regulatory domain
[    2.370158] Non-volatile memory driver v1.3
[    2.373175] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[    2.373177] thinkpad_acpi: http://ibm-acpi.sf.net/
[    2.373178] thinkpad_acpi: ThinkPad BIOS G5ET90WW (2.50 ), EC unknown
[    2.373179] thinkpad_acpi: Lenovo ThinkPad W530, model 2436CTO
[    2.373712] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[    2.373818] thinkpad_acpi: radio switch found; radios are enabled
[    2.373922] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[    2.373924] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[    2.375628] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[    2.377252] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[    2.377346] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[    2.379069] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
[    2.395437] rtl8192ce: rtl8192ce: Power Save off (module option)
[    2.395444] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    2.405714] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    2.406021] rtlwifi: wireless switch is on
[    2.443708] Switched to clocksource tsc
[    2.448380] kvm: disabled by bios
[    2.660452] cfg80211: World regulatory domain updated:
[    2.660452] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    2.660454] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.660455] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.660456] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    2.660456] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.660457] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    2.741485] Bluetooth: Core ver 2.17
[    2.741549] NET: Registered protocol family 31
[    2.741552] Bluetooth: HCI device and connection manager initialized
[    2.741560] Bluetooth: HCI socket layer initialized
[    2.741563] Bluetooth: L2CAP socket layer initialized
[    2.741568] Bluetooth: SCO socket layer initialized
[    2.745557] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.745560] Bluetooth: BNEP filters: protocol multicast
[    2.745567] Bluetooth: BNEP socket layer initialized
[    2.747138] Bluetooth: RFCOMM TTY layer initialized
[    2.747147] Bluetooth: RFCOMM socket layer initialized
[    2.747152] Bluetooth: RFCOMM ver 1.11
[    2.796553] type=1400 audit(1398489297.532:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=676 comm="apparmor_parser"
[    2.796562] type=1400 audit(1398489297.532:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=676 comm="apparmor_parser"
[    2.796949] type=1400 audit(1398489297.532:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=676 comm="apparmor_parser"
[    2.859860] init: failsafe main process (629) killed by TERM signal
[    2.931413] init: cups main process (683) killed by HUP signal
[    2.931426] init: cups main process ended, respawning
[    3.072421] init: samba-ad-dc main process (838) terminated with status 1
[    3.167846] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd047b3/0xb40000/0xa0000, board id: 71, fw id: 920262
[    3.167851] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[    3.219099] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    3.226739] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    3.252195] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[    3.321264] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[    3.321370] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.321635] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.501938] init: gdm main process (978) killed by TERM signal
[    3.666317] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.666766] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    3.671397] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[    3.671401] nouveau  [   VBIOS][0000:01:00.0] using image from ACPI
[    3.671547] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    3.671550] nouveau  [   VBIOS][0000:01:00.0] version 80.07.33.00.09
[    3.671922] nouveau  [ DEVINIT][0000:01:00.0] adaptor not initialised
[    3.671924] nouveau  [   VBIOS][0000:01:00.0] running init tables
[    3.803360] postgres (1117): /proc/1117/oom_adj is deprecated, please use /proc/1117/oom_score_adj instead.
[    3.803969] usbcore: registered new interface driver btusb
[    3.804005] usb 1-1.4: Direct firmware load failed with error -2
[    3.804008] usb 1-1.4: Falling back to user helper
[    3.805464] Bluetooth: can't load firmware, may not work correctly
[    3.811422] Linux video capture interface: v2.00
[    3.817393] uvcvideo: Found UVC 1.00 device Integrated Camera (5986:02d2)
[    3.819656] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input9
[    3.819763] usbcore: registered new interface driver uvcvideo
[    3.819766] USB Video Class driver (1.1.1)
[    3.914166] nouveau 0000:01:00.0: irq 45 for MSI/MSI-X
[    3.914188] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[    3.914240] nouveau  [     PFB][0000:01:00.0] RAM type: DDR3
[    3.914241] nouveau  [     PFB][0000:01:00.0] RAM size: 2048 MiB
[    3.914243] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[    3.917821] nouveau  [    VOLT][0000:01:00.0] GPU voltage: 875000uv
[    3.945944] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[    3.945951] nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
[    3.945963] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[    3.945994] nouveau  [     CLK][0000:01:00.0] 07: core 270-405 MHz memory 405 MHz 
[    3.946017] nouveau  [     CLK][0000:01:00.0] 0f: core 270-850 MHz memory 900 MHz 
[    3.946211] nouveau  [     CLK][0000:01:00.0] --: core 405 MHz memory 324 MHz 
[    3.971916] [TTM] Zone  kernel: Available graphics memory: 3860154 kiB
[    3.971918] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    3.971919] [TTM] Initializing pool allocator
[    3.971925] [TTM] Initializing DMA pool allocator
[    3.971933] nouveau  [     DRM] VRAM: 2048 MiB
[    3.971934] nouveau  [     DRM] GART: 1048576 MiB
[    3.971937] nouveau  [     DRM] TMDS table version 2.0
[    3.971939] nouveau  [     DRM] DCB version 4.0
[    3.971940] nouveau  [     DRM] DCB outp 00: 01800f23 00010034
[    3.971942] nouveau  [     DRM] DCB outp 01: 02811f00 00000000
[    3.971943] nouveau  [     DRM] DCB outp 02: 02822fa6 0f420010
[    3.971944] nouveau  [     DRM] DCB outp 03: 02822f62 00020010
[    3.971946] nouveau  [     DRM] DCB outp 04: 04833fb6 0f220010
[    3.971947] nouveau  [     DRM] DCB outp 05: 04833f72 00020010
[    3.971948] nouveau  [     DRM] DCB outp 06: 08844fc6 0f220010
[    3.971949] nouveau  [     DRM] DCB outp 07: 08844f82 00020010
[    3.971950] nouveau  [     DRM] DCB conn 00: 00000040
[    3.971952] nouveau  [     DRM] DCB conn 01: 00000100
[    3.971953] nouveau  [     DRM] DCB conn 02: 00010246
[    3.971955] nouveau  [     DRM] DCB conn 03: 00020346
[    3.971956] nouveau  [     DRM] DCB conn 04: 01000446
[    3.973203] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.973204] [drm] No driver support for vblank timestamp query.
[    3.973206] nouveau  [     DRM] ACPI backlight interface available, not registering our own
[    3.982918] nouveau  [     DRM] MM: using COPY for buffer copies
[    4.184819] nouveau 0000:01:00.0: No connectors reported connected with modes
[    4.184823] [drm] Cannot find any crtc or sizes - going 1024x768
[    4.210303] nouveau  [     DRM] allocated 1024x768 fb: 0x80000, bo ffff880230e7e000
[    4.210481] nouveau 0000:01:00.0: fb1: nouveaufb frame buffer device
[    4.210495] nouveau 0000:01:00.0: registered panic notifier
[    4.210510] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 0
[    4.211204] [drm] Memory usable by graphics device = 2048M
[    4.211208] checking generic (e0000000 580000) vs hw (e0000000 10000000)
[    4.211209] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[    4.211238] Console: switching to colour dummy device 80x25
[    4.228208] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[    4.262999] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    4.263010] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    4.263011] [drm] Driver supports precise vblank timestamp query.
[    4.263136] vga_switcheroo: enabled
[    4.263179] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    4.263182] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=none
[    4.298798] init: kdm main process (1148) killed by TERM signal
[    4.357101] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    4.374063] fbcon: inteldrmfb (fb0) is primary device
[    5.142201] Console: switching to colour frame buffer device 200x56
[    5.144509] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    5.146336] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    5.151030] acpi device:01: registered as cooling_device5
[    5.151091] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input10
[    5.151219] ACPI: Video Device [VID1] (multi-head: yes  rom: yes  post: no)
[    5.151951] acpi device:0b: registered as cooling_device6
[    5.151998] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0a/LNXVIDEO:01/input/input11
[    5.152081] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[    5.155081] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    5.173165] SKU: Nid=0x1d sku_cfg=0x40138205
[    5.173168] SKU: port_connectivity=0x1
[    5.173169] SKU: enable_pcbeep=0x1
[    5.173170] SKU: check_sum=0x00000003
[    5.173171] SKU: customization=0x00000082
[    5.173172] SKU: external_amp=0x0
[    5.173173] SKU: platform_type=0x1
[    5.173174] SKU: swap=0x0
[    5.173175] SKU: override=0x1
[    5.173477] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    5.173479]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.173480]    hp_outs=2 (0x15/0x1b/0x0/0x0/0x0)
[    5.173481]    mono: mono_out=0x0
[    5.173482]    inputs:
[    5.173484]      Mic=0x18
[    5.173485]      Dock Mic=0x19
[    5.173486]      Internal Mic=0x12
[    5.173487] realtek: No valid SSID, checking pincfg 0x40138205 for NID 0x1d
[    5.173489] realtek: Enabling init ASM_ID=0x8205 CODEC_ID=10ec0269
[    5.181479] input: HDA Intel PCH Dock Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    5.182193] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    5.182292] input: HDA Intel PCH Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    5.182411] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    5.615044] wlan0: authenticate with 32:46:9a:ff:e2:ed
[    5.634948] wlan0: send auth to 32:46:9a:ff:e2:ed (try 1/3)
[    5.636390] wlan0: authenticated
[    5.638640] wlan0: associate with 32:46:9a:ff:e2:ed (try 1/3)
[    5.643301] wlan0: RX AssocResp from 32:46:9a:ff:e2:ed (capab=0x411 status=0 aid=2)
[    5.643414] wlan0: associated
[    5.643430] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    5.664588] wlan0: deauthenticating from 32:46:9a:ff:e2:ed by local choice (reason=2)
[    5.696935] cfg80211: Calling CRDA to update world regulatory domain
[    5.696964] wlan0: authenticate with 32:46:9a:ff:e2:ed
[    5.707097] wlan0: send auth to 32:46:9a:ff:e2:ed (try 1/3)
[    5.707190] cfg80211: World regulatory domain updated:
[    5.707192] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.707193] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.707194] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.707195] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.707196] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.707197] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.709805] wlan0: authenticated
[    5.710719] wlan0: associate with 32:46:9a:ff:e2:ed (try 1/3)
[    5.714484] wlan0: RX AssocResp from 32:46:9a:ff:e2:ed (capab=0x411 status=0 aid=2)
[    5.714598] wlan0: associated
[    5.775976] init: plymouth-upstart-bridge main process ended, respawning
[    5.782944] init: plymouth-upstart-bridge main process (1300) terminated with status 1
[    5.782957] init: plymouth-upstart-bridge main process ended, respawning
[    5.815130] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    6.493044] psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    7.362822] init: plymouth-stop pre-start process (1805) terminated with status 1
[    7.862404] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    8.059362] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
[   13.961030] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   13.961810] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   15.263217] thinkpad_acpi: EC reports that Thermal Table has changed
[   21.532290] thinkpad_acpi: EC reports that Thermal Table has changed
[   28.850216] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   28.850860] ACPI Warning: \_SB_.PCI0.PEG_.VID_._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[   30.157118] thinkpad_acpi: EC reports that Thermal Table has changed
[   32.912656] audit_printk_skb: 165 callbacks suppressed
[   32.912659] type=1400 audit(1398489327.599:66): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2592 comm="apparmor_parser"
[   32.912664] type=1400 audit(1398489327.599:67): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2592 comm="apparmor_parser"
[   32.912962] type=1400 audit(1398489327.599:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2592 comm="apparmor_parser"
[   35.994993] usb 4-1: new SuperSpeed USB device number 2 using xhci_hcd
[   36.011577] usb 4-1: New USB device found, idVendor=1058, idProduct=0740
[   36.011580] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[   36.011582] usb 4-1: Product: My Passport 0740
[   36.011583] usb 4-1: Manufacturer: Western Digital
[   36.011584] usb 4-1: SerialNumber: 57584C314135313337373336
[   36.524971] usb-storage 4-1:1.0: USB Mass Storage device detected
[   36.525016] scsi6 : usb-storage 4-1:1.0
[   36.525371] usbcore: registered new interface driver usb-storage
[   37.526409] scsi 6:0:0:0: Direct-Access     WD       My Passport 0740 1007 PQ: 0 ANSI: 6
[   37.526803] scsi 6:0:0:1: Enclosure         WD       SES Device       1007 PQ: 0 ANSI: 6
[   37.527039] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   37.527162] scsi 6:0:0:1: Attached scsi generic sg3 type 13
[   37.528619] sd 6:0:0:0: [sdb] Spinning up disk...
[   38.531041] .ready
[   41.786358] sd 6:0:0:0: [sdb] 976707584 512-byte logical blocks: (500 GB/465 GiB)
[   41.786839] sd 6:0:0:0: [sdb] Write Protect is off
[   41.786841] sd 6:0:0:0: [sdb] Mode Sense: 47 00 10 08
[   41.787207] sd 6:0:0:0: [sdb] No Caching mode page found
[   41.787209] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   41.788714] sd 6:0:0:0: [sdb] No Caching mode page found
[   41.788717] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   41.788838] ses 6:0:0:1: Attached Enclosure device
[   41.847691]  sdb: sdb1 sdb2
[   41.848786] sd 6:0:0:0: [sdb] No Caching mode page found
[   41.848789] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   41.848792] sd 6:0:0:0: [sdb] Attached SCSI disk
[   42.190559] usb 4-1: USB disconnect, device number 2
[   72.970543] scsi 6:0:0:0: [sdb] Unhandled error code
[   72.970560] scsi 6:0:0:0: [sdb]  
[   72.970564] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[   72.970567] scsi 6:0:0:0: [sdb] CDB: 
[   72.970570] Read(10): 28 00 00 00 08 28 00 00 08 00
[   72.970584] end_request: I/O error, dev sdb, sector 2088
[   72.970590] Buffer I/O error on device sdb1, logical block 256
[   72.970617] scsi 6:0:0:0: rejecting I/O to offline device
[   72.970624] scsi 6:0:0:0: [sdb] killing request
[   72.970649] scsi 6:0:0:0: [sdb] Unhandled error code
[   72.970652] scsi 6:0:0:0: [sdb]  
[   72.970654] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[   72.970657] scsi 6:0:0:0: [sdb] CDB: 
[   72.970659] Read(10): 28 00 00 06 48 28 00 00 08 00
[   72.970670] end_request: I/O error, dev sdb, sector 411688
[   72.970673] Buffer I/O error on device sdb2, logical block 256
[   74.712583] usb 3-1: new full-speed USB device number 3 using xhci_hcd
[   74.729487] usb 3-1: New USB device found, idVendor=091e, idProduct=0003
[   74.729494] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   81.344868] usb 3-1: USB disconnect, device number 3
[   82.033656] usb 3-1: new full-speed USB device number 4 using xhci_hcd
[   82.051069] usb 3-1: New USB device found, idVendor=091e, idProduct=22b6
[   82.051077] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=5
[   82.051081] usb 3-1: SerialNumber: 0000d590b373
[   82.051813] usb-storage 3-1:1.0: USB Mass Storage device detected
[   82.052042] scsi7 : usb-storage 3-1:1.0
[   83.051786] scsi 7:0:0:0: Direct-Access     Garmin   eTrexHCx microSD 1.00 PQ: 0 ANSI: 5
[   83.053700] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   83.054492] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  449.461789] usb 3-1: USB disconnect, device number 4
[  452.609051] usb 3-1: new full-speed USB device number 5 using xhci_hcd
[  452.626068] usb 3-1: New USB device found, idVendor=091e, idProduct=0003
[  452.626075] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  455.747459] usb 3-1: USB disconnect, device number 5
[  458.119873] usb 3-1: new full-speed USB device number 6 using xhci_hcd
[  458.136808] usb 3-1: New USB device found, idVendor=091e, idProduct=0003
[  458.136815] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[  469.962618] usb 3-1: USB disconnect, device number 6
[  470.647436] usb 3-1: new full-speed USB device number 7 using xhci_hcd
[  470.664602] usb 3-1: New USB device found, idVendor=091e, idProduct=22b6
[  470.664610] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=5
[  470.664613] usb 3-1: SerialNumber: 0000d590b373
[  470.665258] usb-storage 3-1:1.0: USB Mass Storage device detected
[  470.665373] scsi8 : usb-storage 3-1:1.0
[  471.665560] scsi 8:0:0:0: Direct-Access     Garmin   eTrexHCx microSD 1.00 PQ: 0 ANSI: 5
[  471.666211] sd 8:0:0:0: Attached scsi generic sg2 type 0
[  471.668285] sd 8:0:0:0: [sdb] Attached SCSI removable disk

```
I ran: rmmod garmin_usb 

and received: 
```
rmmod: ERROR: Module garmin_usb is not currently loaded

```

I have already gedited:/etc/udev/rules.d/51-garmin.rules
```

[COLOR=#000000][FONT=monospace]ATTRS{idVendor}=="091e", ATTRS{idProduct}=="0003", MODE="666"[/FONT][/COLOR]
```



I tried downloading data through gebabbel on Windows 7, however I am receiving a could not "init" the device error.


Any help would be greatly appreciated!

---

### Post by mike16 on 2015-03-31
I have the same problem.  Is there any news yet please?

---

### Post by Vladlenin5000 on 2015-03-31
Perhaps you need to check the permissions: [http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux](http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux)

---

