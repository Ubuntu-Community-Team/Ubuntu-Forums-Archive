---
title: "ubuntu 12.10 problem"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by ken8 on 2013-03-27
Hi there,

I'm a new using ubuntu user! My trouble is :
- I were working with eclipse and then when I turn off wifi my OS has been crashed,  I found that I can't communicate with it so I restart my laptop (I use Acer asprire 4820 core i3 first generation) How can I fix this. I updated driver and it still there.
- After reset, my eclipse didn't work. It only shows white blank! I remove & reinstall it in Ubuntu Software Center. But nothing change... 
- I follow [https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL) but the terminal say: "bash: /user/share/mysql.jar: No such file or directory"
Please tell me what to do.
Thanks,

---

### Post by DuckHook on 2013-03-28
Removing packages through the software centre often leaves configuration files behind. When trying to do a fresh re-install, it is best to use the command line. Try:```
sudo apt-get purge eclipse-platform
```then```
sudo apt-get install eclipse-platform
```and see if this gets you further.

---

### Post by ken8 on 2013-03-28
@[**[COLOR=#000000]DuckHook[/COLOR]**]("http://ubuntuforums.org/member.php?u=1256508") 
Thanks for helping me. I did as you say but it same as always

---

### Post by ken8 on 2013-03-28
@[**[COLOR=#000000]DuckHook[/COLOR]**]("http://ubuntuforums.org/member.php?u=1256508") 
Thanks for helping me. I did as you say but it same as always

---

### Post by DuckHook on 2013-03-28
Your thread is marked "solved" so I am confused. Did it eventually get solved, with reboot, for example?

If not, then please try opening eclipse through the command line and post any error messages. Also, check dmesg and syslog immediately after trying to open. The logs are always the first place to look if encountering issues of this sort.

If solved, let me know and I will delete my thread subscription. I will also delete subscription if thread is dormant for more than 48 hrs.

---

### Post by ken8 on 2013-03-28
Well I dunno how to fix this so I marked "solved" I'll careful it next post.
I did dmesg and not found.I install syslog but stm crashed. This is my dmesg
[PHP]
[    2.949088] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5
[    2.949259] hid-generic 0003:1C4F:0003.0001: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:1d.0-1.2/input0
[    3.593555] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   21.719125] Adding 2047996k swap on /dev/sda1.  Priority:-1 extents:1 across:2047996k 
[   21.724468] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.779907] udevd[361]: starting version 175
[   21.843895] mei 0000:00:16.0: setting latency timer to 64
[   21.843978] mei 0000:00:16.0: irq 41 for MSI/MSI-X
[   21.844176] lp: driver loaded but no devices found
[   21.846460] bcma: Found chip with id 0xA8D9, rev 0x01 and package 0x0A
[   21.846492] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[   21.846527] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[   21.846588] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[   21.848622] mei 0000:00:16.0: wd: failed to find the client
[   21.851936] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   21.851946] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \_SB_.PCI0.TCOT 2 (20120320/utaddress-251)
[   21.851951] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \_SB_.PCI0.LPCB.TCOT 3 (20120320/utaddress-251)
[   21.851956] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   21.851958] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   21.851963] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   21.851967] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   21.851971] ACPI Warning: 0x00000500-0x0000057f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   21.851976] ACPI Warning: 0x00000500-0x0000057f SystemIO conflicts with Region \_SB_.PCI0.LPCB.EC0_.GPBD 2 (20120320/utaddress-251)
[   21.851979] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   21.851981] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   21.861117] [drm] Initialized drm 1.1.0 20060810
[   21.874234] intel ips 0000:00:1f.6: CPU TDP doesn't match expected value (found 25, expected 29)
[   21.874300] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled until i915 loads
[   21.876380] intel ips 0000:00:1f.6: IPS driver initialized, MCP temp limit 90
[   21.878539] i915 0000:00:02.0: setting latency timer to 64
[   21.879154] i915 0000:00:02.0: irq 42 for MSI/MSI-X
[   21.879165] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   21.879167] [drm] Driver supports precise vblank timestamp query.
[   21.879224] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   21.890603] bcma: Bus registered
[   21.896035] wmi: Mapper loaded
[   21.923485] type=1400 audit(1364525235.055:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=456 comm="apparmor_parser"
[   21.924088] type=1400 audit(1364525235.055:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=456 comm="apparmor_parser"
[   21.924475] type=1400 audit(1364525235.059:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=456 comm="apparmor_parser"
[   21.942267] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x2
[   21.987306] Linux video capture interface: v2.00
[   21.999713] uvcvideo: Found UVC 1.00 device 1.3M HD WebCam (064e:c21c)
[   22.017497] input: 1.3M HD WebCam as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input6
[   22.017680] usbcore: registered new interface driver uvcvideo
[   22.017683] USB Video Class driver (1.1.1)
[   22.029590] acer_wmi: Acer Laptop ACPI-WMI Extras
[   22.029609] acer_wmi: Function bitmap for Communication Button: 0x801
[   22.029728] acer_wmi: Brightness must be controlled by acpi video driver
[   22.030428] input: Acer WMI hotkeys as /devices/virtual/input/input7
[   22.030830] input: Acer BMA150 accelerometer as /devices/virtual/input/input8
[   22.034981] cfg80211: Calling CRDA to update world regulatory domain
[   22.046953] brcmsmac bcma0:0: mfg 4bf core 812 rev 23 class 0 irq 17
[   22.055680] cfg80211: World regulatory domain updated:
[   22.055685] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   22.055688] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.055690] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.055693] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   22.055695] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.055698] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.059804] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x2
[   22.063279] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x2
[   22.064816] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x2
[   22.066325] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   22.066329] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066332] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   22.066334] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066336] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   22.066339] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066341] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   22.066343] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066345] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   22.066347] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066349] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   22.066352] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066354] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   22.066356] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066358] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   22.066360] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066362] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   22.066364] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066366] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   22.066368] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066370] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   22.066372] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 1900 mBm)
[   22.066373] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   22.066375] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A mBi, 1900 mBm)
[   22.066377] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   22.066379] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (N/A mBi, 1900 mBm)
[   22.066381] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   22.066423] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   22.067163] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   22.073425] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   22.074397] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   22.453534] fbcon: inteldrmfb (fb0) is primary device
[   22.453642] Console: switching to colour frame buffer device 170x48
[   22.453685] fb0: inteldrmfb frame buffer device
[   22.453687] drm: registered panic notifier
[   22.454811] acpi device:01: registered as cooling_device4
[   22.454949] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.454995] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   22.455295] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   22.468155] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[   22.468257] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   22.524053] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   22.524163] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   22.524166] usb 2-1.5: new full-speed USB device number 4 using ehci_hcd
[   22.524251] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   22.584694] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   22.620550] usb 2-1.5: New USB device found, idVendor=0489, idProduct=e011
[   22.620559] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   22.620565] usb 2-1.5: Product: Acer Module
[   22.620570] usb 2-1.5: Manufacturer: Broadcom Corp
[   22.620575] usb 2-1.5: SerialNumber: 90004EA15C21
[   22.636278] Bluetooth: Core ver 2.16
[   22.636300] NET: Registered protocol family 31
[   22.636302] Bluetooth: HCI device and connection manager initialized
[   22.636304] Bluetooth: HCI socket layer initialized
[   22.636306] Bluetooth: L2CAP socket layer initialized
[   22.636310] Bluetooth: SCO socket layer initialized
[   22.636990] usbcore: registered new interface driver btusb
[   22.654119] psmouse serio2: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa44000/0xa0000
[   22.699564] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input13
[   23.668891] init: failsafe main process (915) killed by TERM signal
[   23.747542] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.747546] Bluetooth: BNEP filters: protocol multicast
[   23.752364] Bluetooth: RFCOMM TTY layer initialized
[   23.752371] Bluetooth: RFCOMM socket layer initialized
[   23.752373] Bluetooth: RFCOMM ver 1.11
[   23.778920] ppdev: user-space parallel port driver
[   23.813505] type=1400 audit(1364525236.947:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=992 comm="apparmor_parser"
[   23.814269] type=1400 audit(1364525236.947:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=992 comm="apparmor_parser"
[   23.836086] type=1400 audit(1364525236.971:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1025 comm="apparmor_parser"
[   23.836762] type=1400 audit(1364525236.971:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1025 comm="apparmor_parser"
[   23.837132] type=1400 audit(1364525236.971:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1025 comm="apparmor_parser"
[   23.838381] type=1400 audit(1364525236.971:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1022 comm="apparmor_parser"
[   23.838573] type=1400 audit(1364525236.971:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1023 comm="apparmor_parser"
[   23.861558] usb 2-1.5: USB disconnect, device number 4
[   23.911631] atl1c 0000:01:00.0: irq 44 for MSI/MSI-X
[   23.929310] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.935383] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.959957] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   23.959969] ieee80211 phy0: brcms_ops_config: change power-save mode: false (implement)
[   23.961150] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.963090] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.341728] vboxdrv: Found 4 processor cores.
[   24.341893] vboxdrv: fAsync=0 offMin=0x411 offMax=0x2ff4
[   24.342098] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.342100] vboxdrv: Successfully loaded version 4.1.18_Ubuntu (interface 0x00190000).
[   24.350465] vboxpci: IOMMU not found (not registered)
[   25.380021] init: plymouth-stop pre-start process (1503) terminated with status 1
[   25.751864] wlan0: authenticate with a0:f3:c1:cd:b1:28
[   25.752799] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[   25.754217] wlan0: authenticated
[   25.754917] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[   25.768756] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[   25.769241] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   25.769246] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   25.769248] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   25.769254] wlan0: associated
[   25.769395] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.074577] intel ips 0000:00:1f.6: i915 driver attached, reenabling gpu turbo
[   35.767182] wlan0: disassociating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[   35.775359] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   35.775369] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[   35.775372] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   35.775978] cfg80211: All devices are disconnected, going to restore regulatory settings
[   35.775982] cfg80211: Restoring regulatory settings
[   35.775987] cfg80211: Calling CRDA to update world regulatory domain
[   35.776295] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[   35.780111] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   35.780115] cfg80211: World regulatory domain updated:
[   35.780117] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   35.780118] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.780120] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   35.780122] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   35.780123] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   35.780124] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   37.639111] wlan0: authenticate with a0:f3:c1:cd:b1:28
[   37.640265] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[   37.641650] wlan0: authenticated
[   37.642383] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[   37.646285] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[   37.646941] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   37.646946] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   37.646948] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   37.646955] wlan0: associated
[   47.644582] wlan0: disassociating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[   47.650858] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   47.650872] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[   47.650878] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   47.651621] cfg80211: All devices are disconnected, going to restore regulatory settings
[   47.651625] cfg80211: Restoring regulatory settings
[   47.651630] cfg80211: Calling CRDA to update world regulatory domain
[   47.651921] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[   47.655867] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   47.655871] cfg80211: World regulatory domain updated:
[   47.655873] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   47.655875] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.655876] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   47.655878] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   47.655879] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   47.655881] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.514606] wlan0: authenticate with a0:f3:c1:cd:b1:28
[   49.516699] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[   49.519062] wlan0: authenticated
[   49.521888] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[   49.527557] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=12)
[   49.528171] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   49.528177] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   49.528180] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   49.528189] wlan0: associated
[   50.447278] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[   50.465562] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   50.465575] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[   50.465578] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   50.466939] cfg80211: All devices are disconnected, going to restore regulatory settings
[   50.466945] cfg80211: Restoring regulatory settings
[   50.466949] cfg80211: Calling CRDA to update world regulatory domain
[   50.470982] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   50.470987] cfg80211: World regulatory domain updated:
[   50.470989] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.470991] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.470992] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.470994] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   50.470995] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.470997] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   81.898270] wlan0: authenticate with a0:f3:c1:cd:b1:28
[   81.899434] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[   81.902522] wlan0: authenticated
[   81.905613] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[   81.911012] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=12)
[   81.911535] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   81.911540] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   81.911542] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   81.911549] wlan0: associated
[   91.909441] wlan0: disassociating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[   91.913977] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   91.913987] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[   91.913991] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   91.914917] cfg80211: All devices are disconnected, going to restore regulatory settings
[   91.914922] cfg80211: Restoring regulatory settings
[   91.914926] cfg80211: Calling CRDA to update world regulatory domain
[   91.915385] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[   91.921888] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   91.921896] cfg80211: World regulatory domain updated:
[   91.921900] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   91.921905] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   91.921909] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   91.921913] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   91.921917] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   91.921921] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.798099] wlan0: authenticate with a0:f3:c1:cd:b1:28
[   93.799033] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[   93.800432] wlan0: authenticated
[   93.801024] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[   93.804850] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[   93.805495] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   93.805506] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[   93.805511] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   93.805524] wlan0: associated
[  103.803574] wlan0: disassociating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  103.809461] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  103.809475] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  103.809480] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  103.810108] cfg80211: All devices are disconnected, going to restore regulatory settings
[  103.810120] cfg80211: Restoring regulatory settings
[  103.810127] cfg80211: Calling CRDA to update world regulatory domain
[  103.810862] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  103.819524] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  103.819534] cfg80211: World regulatory domain updated:
[  103.819537] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  103.819542] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  103.819547] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  103.819551] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  103.819555] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  103.819559] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  105.673362] wlan0: authenticate with a0:f3:c1:cd:b1:28
[  105.674498] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[  105.676504] wlan0: authenticated
[  105.680602] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[  105.688339] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[  105.689014] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  105.689020] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  105.689024] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  105.689030] wlan0: associated
[  106.426313] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  106.448688] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  106.448699] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  106.448702] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  106.450063] cfg80211: All devices are disconnected, going to restore regulatory settings
[  106.450068] cfg80211: Restoring regulatory settings
[  106.450072] cfg80211: Calling CRDA to update world regulatory domain
[  106.462036] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  106.462044] cfg80211: World regulatory domain updated:
[  106.462046] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  106.462049] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  106.462052] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  106.462055] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  106.462057] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  106.462059] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  111.903349] wlan0: authenticate with a0:f3:c1:cd:b1:28
[  111.904217] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[  111.905654] wlan0: authenticated
[  111.906165] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[  111.910237] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[  111.910778] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  111.910782] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  111.910784] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  111.910790] wlan0: associated
[  121.908500] wlan0: disassociating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  121.918590] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  121.918605] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  121.918610] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  121.919498] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  121.920653] cfg80211: All devices are disconnected, going to restore regulatory settings
[  121.920661] cfg80211: Restoring regulatory settings
[  121.920669] cfg80211: Calling CRDA to update world regulatory domain
[  121.930688] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  121.930697] cfg80211: World regulatory domain updated:
[  121.930700] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  121.930705] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  121.930710] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  121.930714] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  121.930718] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  121.930722] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  123.782160] wlan0: authenticate with a0:f3:c1:cd:b1:28
[  123.783498] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[  123.786300] wlan0: authenticated
[  123.789664] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[  123.798006] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=5)
[  123.798884] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  123.798898] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  123.798906] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  123.798923] wlan0: associated
[  133.796980] wlan0: disassociating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  133.829947] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  133.829964] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  133.829967] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  133.830855] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  133.831693] cfg80211: All devices are disconnected, going to restore regulatory settings
[  133.831699] cfg80211: Restoring regulatory settings
[  133.831704] cfg80211: Calling CRDA to update world regulatory domain
[  133.836576] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  133.836583] cfg80211: World regulatory domain updated:
[  133.836584] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  133.836587] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  133.836589] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  133.836591] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  133.836593] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  133.836595] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  135.693817] wlan0: authenticate with a0:f3:c1:cd:b1:28
[  135.694985] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[  135.698538] wlan0: authenticated
[  135.701135] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[  135.707881] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[  135.708433] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  135.708438] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  135.708441] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  135.708449] wlan0: associated
[  136.414265] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  136.436538] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  136.436550] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  136.436553] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  136.438051] cfg80211: All devices are disconnected, going to restore regulatory settings
[  136.438056] cfg80211: Restoring regulatory settings
[  136.438062] cfg80211: Calling CRDA to update world regulatory domain
[  136.442715] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  136.442720] cfg80211: World regulatory domain updated:
[  136.442722] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  136.442724] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  136.442725] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  136.442727] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  136.442728] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  136.442730] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  146.841484] wlan0: authenticate with a0:f3:c1:cd:b1:28
[  146.842738] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[  146.845130] wlan0: authenticated
[  146.848878] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[  146.853640] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[  146.854174] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  146.854178] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  146.854181] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  146.854188] wlan0: associated
[  154.188215] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  154.188367] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  156.851818] wlan0: disassociating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  156.861180] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  156.861189] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  156.861192] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  156.862057] cfg80211: All devices are disconnected, going to restore regulatory settings
[  156.862062] cfg80211: Restoring regulatory settings
[  156.862066] cfg80211: Calling CRDA to update world regulatory domain
[  156.862372] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  156.866153] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  156.866157] cfg80211: World regulatory domain updated:
[  156.866159] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  156.866161] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  156.866162] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  156.866164] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  156.866165] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  156.866167] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  158.724982] wlan0: authenticate with a0:f3:c1:cd:b1:28
[  158.726216] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[  158.727644] wlan0: authenticated
[  158.728357] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[  158.735126] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[  158.735724] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  158.735728] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  158.735730] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  158.735738] wlan0: associated
[  168.732709] wlan0: disassociating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  168.744639] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  168.744652] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  168.744654] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  168.746865] cfg80211: All devices are disconnected, going to restore regulatory settings
[  168.746870] cfg80211: Restoring regulatory settings
[  168.746876] cfg80211: Calling CRDA to update world regulatory domain
[  168.747250] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  168.751922] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  168.751928] cfg80211: World regulatory domain updated:
[  168.751930] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  168.751933] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  168.751936] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  168.751938] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  168.751940] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  168.751943] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  170.609259] wlan0: authenticate with a0:f3:c1:cd:b1:28
[  170.609934] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[  170.611405] wlan0: authenticated
[  170.612255] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[  170.617595] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=4)
[  170.618153] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  170.618159] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  170.618162] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  170.618171] wlan0: associated
[  171.401931] wlan0: deauthenticating from a0:f3:c1:cd:b1:28 by local choice (reason=3)
[  171.423742] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  171.423755] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 0 (implement)
[  171.423758] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  171.425112] cfg80211: All devices are disconnected, going to restore regulatory settings
[  171.425117] cfg80211: Restoring regulatory settings
[  171.425122] cfg80211: Calling CRDA to update world regulatory domain
[  171.432110] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  171.432119] cfg80211: World regulatory domain updated:
[  171.432122] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  171.432125] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  171.432127] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  171.432129] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  171.432131] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  171.432133] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  178.297565] wlan0: authenticate with a0:f3:c1:bf:11:48
[  178.300559] wlan0: direct probe to a0:f3:c1:bf:11:48 (try 1/3)
[  178.500834] wlan0: direct probe to a0:f3:c1:bf:11:48 (try 2/3)
[  178.704772] wlan0: direct probe to a0:f3:c1:bf:11:48 (try 3/3)
[  178.908695] wlan0: authentication with a0:f3:c1:bf:11:48 timed out
[  191.614156] wlan0: authenticate with a0:f3:c1:bf:11:48
[  191.616355] wlan0: direct probe to a0:f3:c1:bf:11:48 (try 1/3)
[  191.819789] wlan0: direct probe to a0:f3:c1:bf:11:48 (try 2/3)
[  192.023719] wlan0: direct probe to a0:f3:c1:bf:11:48 (try 3/3)
[  192.227644] wlan0: authentication with a0:f3:c1:bf:11:48 timed out
[  368.747933] wlan0: authenticate with a0:f3:c1:cd:b1:28
[  368.749752] wlan0: send auth to a0:f3:c1:cd:b1:28 (try 1/3)
[  368.753232] wlan0: authenticated
[  368.756592] wlan0: associate with a0:f3:c1:cd:b1:28 (try 1/3)
[  368.760289] wlan0: RX AssocResp from a0:f3:c1:cd:b1:28 (capab=0x431 status=0 aid=13)
[  368.761533] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[  368.761540] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  368.761543] ieee80211 phy0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  368.761550] wlan0: associated
[  369.239688] ieee80211 phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[  610.860345] ------------[ cut here ]------------
[  610.860383] WARNING: at /build/buildd/linux-3.5.0/drivers/net/wireless/brcm80211/brcmsmac/main.c:7953 brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]()
[  610.860387] Hardware name: Aspire 4820
[  610.860390] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) parport_pc ppdev rfcomm bnep binfmt_misc btusb bluetooth snd_hda_codec_hdmi snd_hda_codec_realtek coretemp kvm_intel kvm arc4 brcmsmac joydev mac80211 brcmutil acer_wmi sparse_keymap cfg80211 cordic uvcvideo videobuf2_core videodev videobuf2_vmalloc videobuf2_memops microcode snd_hda_intel snd_hda_codec snd_hwdep snd_pcm wmi snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq intel_ips snd_timer snd_seq_device mac_hid snd i915 drm_kms_helper drm i2c_algo_bit lpc_ich video bcma mei psmouse serio_raw lp soundcore parport snd_page_alloc hid_generic usbhid hid ahci libahci atl1c
[  610.860485] Pid: 194, comm: kworker/u:3 Tainted: G           O 3.5.0-26-generic #42-Ubuntu
[  610.860489] Call Trace:
[  610.860503]  [<c1044cc2>] warn_slowpath_common+0x72/0xa0
[  610.860526]  [<f8fbee3a>] ? brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[  610.860548]  [<f8fbee3a>] ? brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[  610.860556]  [<c1044d12>] warn_slowpath_null+0x22/0x30
[  610.860578]  [<f8fbee3a>] brcms_c_wait_for_tx_completion+0x8a/0xa0 [brcmsmac]
[  610.860593]  [<f8fb1550>] brcms_ops_flush+0x30/0x50 [brcmsmac]
[  610.860627]  [<f8f4699d>] ieee80211_scan_work+0x29d/0x4d0 [mac80211]
[  610.860635]  [<c106002f>] process_one_work+0x10f/0x380
[  610.860642]  [<c105e2e0>] ? need_to_create_worker+0x10/0x30
[  610.860671]  [<f8f46700>] ? ieee80211_run_deferred_scan+0x70/0x70 [mac80211]
[  610.860678]  [<c1061279>] worker_thread+0xf9/0x290
[  610.860686]  [<c1070e0e>] ? complete+0x4e/0x60
[  610.860692]  [<c1061180>] ? manage_workers.isra.25+0x1d0/0x1d0
[  610.860699]  [<c1065412>] kthread+0x72/0x80
[  610.860706]  [<c10653a0>] ? kthread_freezable_should_stop+0x60/0x60
[  610.860715]  [<c15cfdfe>] kernel_thread_helper+0x6/0x10
[  610.860720] ---[ end trace 168de194a9575cba ]---
[  610.884293] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 13
[  610.884466] ieee80211 phy0: brcms_c_ampdu_dotxstatus_complete: Pkt tx suppressed, illegal channel possibly 13
[ 2204.779012] show_signal_msg: 60 callbacks suppressed
[ 2204.779022] nautilus[2202]: segfault at 746e6f47 ip b6acd4ef sp bff42a30 error 6 in libglib-2.0.so.0.3400.1[b6a6a000+fa000]
[/PHP]

Plz help me find out those prolem!

---

### Post by ken8 on 2013-03-29
Oh, I fixed it!
Thanks so much DuckHook

---

### Post by DuckHook on 2013-03-29
Perhaps you can post a brief description of the fix here to help others. Truth be told, I don't think I helped you out very much because all I did was suggest that you read the logs. I don't know what you did to make *eclipse* work again.

Glad that you are computing again, though.

---

### Post by ken8 on 2013-03-30
First I did what you say, then I used bleachbit to swap all. I did install netbeans too but the same as eclipse.
I couldn't find any solution to fix it so I reinstalled ubuntu...  I'm so sorry but I had to use eclipse for job as soon as possible :(

---

### Post by DuckHook on 2013-03-30
Hardly any need to apologize. I'm just happy you are up and running again.

Good luck and Happy Ubuntuing!

---

