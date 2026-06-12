---
title: "Mouse configured as keyboard"
date: 2015-04-25
forum: New to Ubuntu
---

### Post by lmerceron22 on 2015-04-25
Hello community,

I have a gaming Slider SX200 mouse that doesn't work on my Elementary OS Luna (Ubuntu 12.04 Precise) version.

Here is dmesg result :
```
[    3.596449] usb 2-1.4.1: Product: G110 G-keys
[    3.596450] usb 2-1.4.1: Manufacturer: LOGITECH
[    3.597130] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    3.597132] radeon 0000:01:00.0: registered panic notifier
[    3.597223] [drm] Initialized radeon 2.29.0 20080528 for 0000:01:00.0 on minor 0
[    3.601473] input: LOGITECH G110 G-keys as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.1/2-1.4.1:1.0/input/input7
[    3.601582] hid-generic 0003:046D:C22B.0002: input,hiddev0,hidraw1: USB HID v1.00 Keypad [LOGITECH G110 G-keys] on usb-0000:00:1d.0-1.4.1/input0
[    3.601623] usbhid 2-1.4.1:1.1: couldn't find an input interrupt endpoint
[    3.801702] usb 2-1.4.3: new low-speed USB device number 5 using ehci-pci
[    3.899364] usb 2-1.4.3: New USB device found, idVendor=046d, idProduct=c22a
[    3.899374] usb 2-1.4.3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    3.899380] usb 2-1.4.3: Product: Gaming Keyboard G110
[    3.903208] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.3/2-1.4.3:1.0/input/input8
[    3.903265] hid-generic 0003:046D:C22A.0003: input,hidraw2: USB HID v1.10 Keyboard [Gaming Keyboard G110] on usb-0000:00:1d.0-1.4.3/input0
[    3.909367] input: Gaming Keyboard G110 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4.3/2-1.4.3:1.1/input/input9
[    3.909452] hid-generic 0003:046D:C22A.0004: input,hiddev0,hidraw3: USB HID v1.10 Device [Gaming Keyboard G110] on usb-0000:00:1d.0-1.4.3/input1
[    4.795932] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    6.594850] init: ureadahead main process (426) terminated with status 5
[    7.824546] Adding 6270972k swap on /dev/sda6.  Priority:-1 extents:1 across:6270972k 
[    8.911722] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.353896] udevd[545]: starting version 175
[   10.830997] lp: driver loaded but no devices found
[   10.992144] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   12.343473] mei 0000:00:16.0: setting latency timer to 64
[   12.343538] mei 0000:00:16.0: irq 51 for MSI/MSI-X
[   12.563890] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[   12.563897] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.563901] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   12.563904] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.563905] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   12.563907] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.563908] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[   12.563911] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.563912] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   12.573871] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.262554] cfg80211: module has bad taint, not creating trace events
[   13.262766] cfg80211: Calling CRDA to update world regulatory domain
[   13.419997] device-mapper: multipath: version 1.6.0 loaded
[   13.427863] acer_wmi: Acer Laptop ACPI-WMI Extras
[   13.427876] acer_wmi: Function bitmap for Communication Button: 0x1
[   13.427879] acer_wmi: Brightness must be controlled by acpi video driver
[   13.428062] input: Acer WMI hotkeys as /devices/virtual/input/input10
[   13.428248] input: Acer BMA150 accelerometer as /devices/virtual/input/input11
[   13.698340] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x17
[   14.025577] microcode: CPU1 sig=0x206a7, pf=0x10, revision=0x17
[   14.026632] microcode: CPU2 sig=0x206a7, pf=0x10, revision=0x17
[   14.027624] microcode: CPU3 sig=0x206a7, pf=0x10, revision=0x17
[   14.028528] microcode: CPU4 sig=0x206a7, pf=0x10, revision=0x17
[   14.029417] microcode: CPU5 sig=0x206a7, pf=0x10, revision=0x17
[   14.030310] microcode: CPU6 sig=0x206a7, pf=0x10, revision=0x17
[   14.031197] microcode: CPU7 sig=0x206a7, pf=0x10, revision=0x17
[   14.032084] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   14.642406] kvm: module has bad taint, not creating trace events
[   14.710216] mac80211: module has bad taint, not creating trace events
[   15.047745] ath: phy0: ASPM enabled: 0x42
[   15.047748] ath: EEPROM regdomain: 0x65
[   15.047749] ath: EEPROM indicates we should expect a direct regpair map
[   15.047751] ath: Country alpha2 being used: 00
[   15.047752] ath: Regpair used: 0x65
[   15.211325] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   15.211530] ieee80211 phy0: Atheros AR9287 Rev:2 mem=0xffffc90010f60000, irq=17
[   15.273798] cfg80211: World regulatory domain updated:
[   15.273801] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.273803] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.273804] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.273806] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.273807] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.273808] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.379476] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   15.431687] psmouse serio1: elantech: Synaptics capabilities query result 0x68, 0x15, 0x0a.
[   15.457847] Linux video capture interface: v2.00
[   15.489972] snd_hda_codec: module has bad taint, not creating trace events
[   15.514340] snd_hda_intel: module has bad taint, not creating trace events
[   15.514478] snd_hda_intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[   15.554702] hda_codec: ALC269VB: SKU not ready 0x598301f0
[   15.559081] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   15.559144] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   15.559283] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   15.559341] snd_hda_intel 0000:01:00.1: irq 53 for MSI/MSI-X
[   15.625697] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   15.686855] type=1400 audit(1429932630.336:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=973 comm="apparmor_parser"
[   15.686864] type=1400 audit(1429932630.336:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1075 comm="apparmor_parser"
[   15.686919] type=1400 audit(1429932630.336:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=972 comm="apparmor_parser"
[   15.687181] type=1400 audit(1429932630.336:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=973 comm="apparmor_parser"
[   15.687190] type=1400 audit(1429932630.336:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1075 comm="apparmor_parser"
[   15.687245] type=1400 audit(1429932630.336:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=972 comm="apparmor_parser"
[   15.687365] type=1400 audit(1429932630.336:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=973 comm="apparmor_parser"
[   15.687375] type=1400 audit(1429932630.336:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1075 comm="apparmor_parser"
[   15.687429] type=1400 audit(1429932630.336:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=972 comm="apparmor_parser"
[   15.689075] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input15
[   15.781823] uvcvideo: Found UVC 1.00 device 1.3M HD WebCam (04fc:2801)
[   15.793578] type=1400 audit(1429932630.444:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=1096 comm="apparmor_parser"
[   15.798930] input: 1.3M HD WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input16
[   15.798997] usbcore: registered new interface driver uvcvideo
[   15.798999] USB Video Class driver (1.1.1)
[   16.869763] init: failsafe main process (1117) killed by TERM signal
[   18.239558] ppdev: user-space parallel port driver
[   18.900403] Bluetooth: Core ver 2.16
[   18.900417] NET: Registered protocol family 31
[   18.900419] Bluetooth: HCI device and connection manager initialized
[   18.900425] Bluetooth: HCI socket layer initialized
[   18.900427] Bluetooth: L2CAP socket layer initialized
[   18.900435] Bluetooth: SCO socket layer initialized
[   19.166907] Bluetooth: RFCOMM TTY layer initialized
[   19.166917] Bluetooth: RFCOMM socket layer initialized
[   19.166918] Bluetooth: RFCOMM ver 1.11
[   19.363954] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.363957] Bluetooth: BNEP filters: protocol multicast
[   19.363964] Bluetooth: BNEP socket layer initialized
[   22.617867] audit_printk_skb: 84 callbacks suppressed
[   22.617869] type=1400 audit(1429932637.268:40): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=1385 comm="apparmor_parser"
[   25.545909] atl1c 0000:02:00.0: irq 54 for MSI/MSI-X
[   25.567415] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.588343] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.628234] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.637296] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.662375] vboxdrv: Found 8 processor cores.
[   27.662644] vboxdrv: fAsync=0 offMin=0x160 offMax=0x1126
[   27.662692] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   27.662693] vboxdrv: Successfully loaded version 4.1.12_Ubuntu (interface 0x00190000).
[   27.884458] vboxpci: IOMMU not found (not registered)
[   28.685333] Bridge firewalling registered
[   28.835312] wlan0: authenticate with 56:01:70:a4:17:84
[   28.849595] wlan0: send auth to 56:01:70:a4:17:84 (try 1/3)
[   28.851581] wlan0: authenticated
[   28.853372] wlan0: associate with 56:01:70:a4:17:84 (try 1/3)
[   28.866176] wlan0: RX AssocResp from 56:01:70:a4:17:84 (capab=0x411 status=0 aid=1)
[   28.866250] wlan0: associated
[   28.866278] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.337895] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.865517] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   31.131964] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   34.434025] Ebtables v2.0 registered
[   35.205916] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   36.323444] cgroup: libvirtd (1499) created nested cgroup for controller "memory" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   36.323447] cgroup: "memory" requires setting use_hierarchy to 1 on the root.
[   36.323477] cgroup: libvirtd (1499) created nested cgroup for controller "devices" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   36.323512] cgroup: libvirtd (1499) created nested cgroup for controller "blkio" which has incomplete hierarchy support. Nested cgroups may change behavior in the future.
[   38.209073] aufs 3.x-rcN-20121112
[   38.553999] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready
[   41.666518] type=1400 audit(1429932656.324:41): apparmor="STATUS" operation="profile_replace" name="docker-default" pid=2379 comm="apparmor_parser"
[   42.753576] init: plymouth-stop pre-start process (2511) terminated with status 1
[   43.180033] hid-generic 0003:046D:C22B.0002: can't reset device, 0000:00:1d.0-1.4.1/input0, status -71
[   43.184101] usb 2-1.4: clear tt 1 (0040) error -71
[   43.195997] hid-generic 0003:046D:C22B.0002: can't reset device, 0000:00:1d.0-1.4.1/input0, status -71
[   43.196870] hid-generic 0003:046D:C22A.0003: can't reset device, 0000:00:1d.0-1.4.3/input0, status -71
[   43.199964] usb 2-1.4: clear tt 1 (0040) error -71
[   43.204247] hid-generic 0003:046D:C22B.0002: can't reset device, 0000:00:1d.0-1.4.1/input0, status -71
[   43.204260] usb 2-1.4: clear tt 3 (0050) error -71
[   43.208232] hid-generic 0003:046D:C22A.0004: can't reset device, 0000:00:1d.0-1.4.3/input1, status -71
[   43.208586] usb 2-1.4: clear tt 1 (0040) error -71
[   43.212839] usb 2-1.4: clear tt 3 (0050) error -71
[   43.219990] hid-generic 0003:046D:C22B.0002: can't reset device, 0000:00:1d.0-1.4.1/input0, status -71
[   43.222082] usb 2-1.4: USB disconnect, device number 3
[   43.222089] usb 2-1.4.1: USB disconnect, device number 4
[   43.224571] usb 2-1.4: clear tt 1 (0040) error -71
[   43.241123] usb 2-1.4.3: USB disconnect, device number 5
[   44.313231] usb 3-2: USB disconnect, device number 2
[   87.318745] type=1400 audit(1429932701.992:42): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1241 comm="cupsd" pid=1241 comm="cupsd" capability=36  capname="block_suspend"
[  100.822609] usb 2-1.2: new full-speed USB device number 6 using ehci-pci
[  100.922831] usb 2-1.2: New USB device found, idVendor=04d9, idProduct=a04a
[  100.922842] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  100.922848] usb 2-1.2: Product: USB Gaming Mouse
[  100.922853] usb 2-1.2: Manufacturer: Newman
[  100.926573] input: Newman USB Gaming Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input17
[  100.926726] hid-generic 0003:04D9:A04A.0005: input,hidraw0: USB HID v1.10 Keyboard [Newman USB Gaming Mouse] on usb-0000:00:1d.0-1.2/input0
[  100.933893] hid-generic 0003:04D9:A04A.0006: usage index exceeded
[  100.933897] hid-generic 0003:04D9:A04A.0006: item 0 2 2 2 parsing failed
[  100.933913] hid-generic: probe of 0003:04D9:A04A.0006 failed with error -22
[  129.521977] usb 2-1.2: USB disconnect, device number 6
[  244.280862] usb 2-1.2: new full-speed USB device number 7 using ehci-pci
[  244.381332] usb 2-1.2: New USB device found, idVendor=04d9, idProduct=a04a
[  244.381343] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  244.381349] usb 2-1.2: Product: USB Gaming Mouse
[  244.381355] usb 2-1.2: Manufacturer: Newman
[  244.385751] input: Newman USB Gaming Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input18
[  244.386162] hid-generic 0003:04D9:A04A.0007: input,hidraw0: USB HID v1.10 Keyboard [Newman USB Gaming Mouse] on usb-0000:00:1d.0-1.2/input0
[  244.393659] hid-generic 0003:04D9:A04A.0008: usage index exceeded
[  244.393671] hid-generic 0003:04D9:A04A.0008: item 0 2 2 2 parsing failed
[  244.393727] hid-generic: probe of 0003:04D9:A04A.0008 failed with error -22
[  538.213158] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  902.111209] usb 2-1.2: USB disconnect, device number 7
[ 1162.007446] usb 3-2: new full-speed USB device number 3 using xhci_hcd
[ 1162.100359] usb 3-2: New USB device found, idVendor=04d9, idProduct=a04a
[ 1162.100363] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1162.100365] usb 3-2: Product: USB Gaming Mouse
[ 1162.100367] usb 3-2: Manufacturer: Newman
[ 1162.127613] input: Newman USB Gaming Mouse as /devices/pci0000:00/0000:00:1c.3/0000:05:00.0/usb3/3-2/3-2:1.0/input/input19
[ 1162.127844] hid-generic 0003:04D9:A04A.0009: input,hidraw0: USB HID v1.10 Keyboard [Newman USB Gaming Mouse] on usb-0000:05:00.0-2/input0
[ 1162.180720] hid-generic 0003:04D9:A04A.000A: usage index exceeded
[ 1162.180724] hid-generic 0003:04D9:A04A.000A: item 0 2 2 2 parsing failed
[ 1162.180746] hid-generic: probe of 0003:04D9:A04A.000A failed with error -22

```

And here is my Xorg.0.log :
```
[  1162.528] (II) config/udev: Adding input device Newman USB Gaming Mouse (/dev/input/event6)
[  1162.528] (**) Newman USB Gaming Mouse: Applying InputClass "evdev keyboard catchall"
[  1162.528] (II) Using input driver 'evdev' for 'Newman USB Gaming Mouse'
[  1162.528] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1162.528] (**) Newman USB Gaming Mouse: always reports core events
[  1162.528] (**) evdev: Newman USB Gaming Mouse: Device: "/dev/input/event6"
[  1162.529] (--) evdev: Newman USB Gaming Mouse: Vendor 0x4d9 Product 0xa04a
[  1162.529] (--) evdev: Newman USB Gaming Mouse: Found keys
[  1162.529] (II) evdev: Newman USB Gaming Mouse: Configuring as keyboard
[  1162.529] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.3/0000:05:00.0/usb3/3-2/3-2:1.0/input/input19/event6"
[  1162.529] (II) XINPUT: Adding extended input device "Newman USB Gaming Mouse" (type: KEYBOARD, id 11)
[  1162.529] (**) Option "xkb_rules" "evdev"
[  1162.529] (**) Option "xkb_model" "pc105"
[  1162.529] (**) Option "xkb_layout" "fr"
[  1162.529] (**) Option "xkb_variant" "latin9"

```

I already applied the solution other topic proposed which is modifying hid.h and recompiling the kernel. I have now :
```

#define HID_MAX_USAGES            36864
```

I would be thankful if you can help me.

Regards,

Spyrit

---

