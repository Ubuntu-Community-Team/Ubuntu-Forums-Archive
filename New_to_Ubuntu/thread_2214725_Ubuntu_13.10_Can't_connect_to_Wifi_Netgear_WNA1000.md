---
title: "Ubuntu 13.10: Can't connect to Wifi: Netgear WNA1000M"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by jayden2 on 2014-04-02
I guess I'm using a very infamous Wi-fi Adapter because I've tried everything out on the internet and I guess its time to ask for individual help:
I can't seem to connect to my Wi-fi Network, I'm on a Desktop, With a Network Adapter, Network Adapter is: Netgear WNA1000M,
I know its not a distance problem or a hardware problem since I can connect to Wi-fi using Windows (I'm dual-booting Windows 8.1 and Ubuntu 13.10).
and I don't have any other Hotspots so I decided to connect to an Android Hotspot and it worked. I don't know whats wrong and I need help,
The only solution right now is to USB Tether my Wi-fi using my Samsung Phone to my Computer, and its not a solution I like, I would like to use Wireless.
Thanks.
**EDIT**

[LIST]
[*]There are no error messages, It keeps trying to connect and after two minutes I get a Wireless Network: Disconnected, Error
[*]dmesg output:
[/LIST]
```
[   10.015356] microcode: CPU1: new patch_level=0x01000083
[   10.015370] microcode: CPU2: patch_level=0x01000039
[   10.015380] microcode: CPU2: new patch_level=0x01000083
[   10.015516] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   10.201938] usb 2-3: New USB device found, idVendor=046d, idProduct=c52b
[   10.201946] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   10.201949] usb 2-3: Product: USB Receiver
[   10.201951] usb 2-3: Manufacturer: Logitech
[   10.517730] kvm: Nested Virtualization enabled
[   10.517740] kvm: Nested Paging enabled
[   11.070492] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   11.070504] hda_intel: Disabling MSI
[   11.070545] snd_hda_intel 0000:00:05.0: setting latency timer to 64
[   11.070549] hda-intel 0000:00:05.0: Disabling 64bit DMA
[   11.074515] hda-intel 0000:00:05.0: Enable delay in RIRB handling
[   11.818560] hda_codec: ALC1200: SKU not ready 0x411111f0
[   11.898489] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[   11.898496]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   11.898498]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   11.898500]    mono: mono_out=0x0
[   11.898501]    dig-out=0x11/0x0
[   11.898503]    inputs:
[   11.898505]      Front Mic=0x19
[   11.898507]      Rear Mic=0x18
[   11.898508]      Line=0x1c
[   11.898509]      Aux=0x1a
[   11.898513] realtek: No valid SSID, checking pincfg 0x411111f0 for NID 0x1d
[   11.898514] realtek: Enable default setup for auto mode as fallback
[   12.045982] cfg80211: Calling CRDA to update world regulatory domain
[   12.165349] hidraw: raw HID events driver (C) Jiri Kosina
[   12.284312] usbcore: registered new interface driver usbhid
[   12.284318] usbhid: USB HID core driver
[   12.319383] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:02.0-3/input2
[   12.324513] input: Logitech Unifying Device. Wireless PID:4009 as /devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3:1.2/0003:046D:C52B.0003/input/input3
[   12.324695] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:4009] on usb-0000:00:02.0-3:1
[   12.651027] rtl8192cu: Chip version 0x10
[   12.759674] rtl8192cu: MAC address: e0:46:9a:32:60:12
[   12.759682] rtl8192cu: Board Type 0
[   12.759917] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   12.759979] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[   12.760169] usbcore: registered new interface driver rtl8192cu
[   12.879925] type=1400 audit(1396462775.602:2): apparmor="STATUS" operation="profile_load" parent=448 profile="unconfined" name="/sbin/dhclient" pid=449 comm="apparmor_parser"
[   12.879937] type=1400 audit(1396462775.602:3): apparmor="STATUS" operation="profile_load" parent=448 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=449 comm="apparmor_parser"
[   12.879943] type=1400 audit(1396462775.602:4): apparmor="STATUS" operation="profile_load" parent=448 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=449 comm="apparmor_parser"
[   12.879970] type=1400 audit(1396462775.602:5): apparmor="STATUS" operation="profile_replace" parent=376 profile="unconfined" name="/sbin/dhclient" pid=383 comm="apparmor_parser"
[   12.879985] type=1400 audit(1396462775.602:6): apparmor="STATUS" operation="profile_replace" parent=376 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=383 comm="apparmor_parser"
[   12.879992] type=1400 audit(1396462775.602:7): apparmor="STATUS" operation="profile_replace" parent=376 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=383 comm="apparmor_parser"
[   12.880724] type=1400 audit(1396462775.602:8): apparmor="STATUS" operation="profile_replace" parent=448 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=449 comm="apparmor_parser"
[   12.880734] type=1400 audit(1396462775.602:9): apparmor="STATUS" operation="profile_replace" parent=448 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=449 comm="apparmor_parser"
[   12.880775] type=1400 audit(1396462775.602:10): apparmor="STATUS" operation="profile_replace" parent=376 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=383 comm="apparmor_parser"
[   12.880781] type=1400 audit(1396462775.602:11): apparmor="STATUS" operation="profile_replace" parent=376 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=383 comm="apparmor_parser"
[   12.923561] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.924158] rtlwifi: wireless switch is on
[   13.349526] cfg80211: World regulatory domain updated:
[   13.349534] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.349537] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.349540] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.349542] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.349543] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.349545] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.552319] nvidia: module license 'NVIDIA' taints kernel.
[   13.552327] Disabling lock debugging due to kernel taint
[   13.801071] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:05.0/sound/card0/input4
[   13.801204] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:05.0/sound/card0/input5
[   13.801308] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:05.0/sound/card0/input6
[   13.801408] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:05.0/sound/card0/input7
[   13.801501] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:05.0/sound/card0/input8
[   13.801597] input: HDA NVidia Line as /devices/pci0000:00/0000:00:05.0/sound/card0/input9
[   13.801692] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input10
[   13.801790] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:05.0/sound/card0/input11
[   13.802644] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
[   13.802668] nvidia 0000:00:0d.0: setting latency timer to 64
[   13.802674] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.802984] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.108  Wed Jul 31 19:35:17 PDT 2013
[   13.897636] init: failsafe main process (521) killed by TERM signal
[   15.887720] Bluetooth: Core ver 2.16
[   15.887799] NET: Registered protocol family 31
[   15.887802] Bluetooth: HCI device and connection manager initialized
[   15.887823] Bluetooth: HCI socket layer initialized
[   15.887826] Bluetooth: L2CAP socket layer initialized
[   15.887833] Bluetooth: SCO socket layer initialized
[   16.123616] Bluetooth: RFCOMM TTY layer initialized
[   16.123640] Bluetooth: RFCOMM socket layer initialized
[   16.123642] Bluetooth: RFCOMM ver 1.11
[   16.248006] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.248013] Bluetooth: BNEP filters: protocol multicast
[   16.248038] Bluetooth: BNEP socket layer initialized
[   16.265889] init: avahi-cups-reload main process (715) terminated with status 1
[   16.543251] ppdev: user-space parallel port driver
[   19.267116] init: udev-fallback-graphics main process (862) terminated with status 1
[   21.923211] rtl8192cu: MAC auto ON okay!
[   21.955936] rtl8192cu: Tx queue select: 0x05
[   22.318236] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.318917] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.324133] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
[   22.324180] forcedeth 0000:00:07.0 eth0: MSI enabled
[   22.324395] forcedeth 0000:00:07.0 eth0: no link during initialization
[   22.324836] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.325367] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  141.264639] wlan0: authenticate with c4:39:3a:15:63:88
[  141.290695] wlan0: send auth to c4:39:3a:15:63:88 (try 1/3)
[  141.310379] wlan0: authenticated
[  141.311341] wlan0: associate with c4:39:3a:15:63:88 (try 1/3)
[  141.341940] wlan0: RX AssocResp from c4:39:3a:15:63:88 (capab=0xc11 status=0 aid=5)
[  141.342103] wlan0: associated
[  141.343566] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  141.344148] cfg80211: Calling CRDA for country: US
[  141.350359] cfg80211: Regulatory domain changed to country: US
[  141.350365] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  141.350369] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  141.350371] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  141.350373] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  141.350375] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  141.350376] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  141.350378] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  141.350380] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  195.184578] wlan0: deauthenticating from c4:39:3a:15:63:88 by local choice (reason=3)
[  195.204481] cfg80211: Calling CRDA to update world regulatory domain
[  195.210009] cfg80211: World regulatory domain updated:
[  195.210017] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  195.210020] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  195.210022] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  195.210024] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  195.210026] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  195.210027] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  215.229015] usb 1-6: USB disconnect, device number 4
[  638.077096] rtl8192cu: MAC auto ON okay!
[  638.110688] rtl8192cu: Tx queue select: 0x05
[  638.477706] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  646.573786] wlan0: authenticate with c4:39:3a:15:63:88
[  646.598779] wlan0: send auth to c4:39:3a:15:63:88 (try 1/3)
[  646.617499] wlan0: authenticated
[  646.620877] wlan0: associate with c4:39:3a:15:63:88 (try 1/3)
[  646.632645] wlan0: RX AssocResp from c4:39:3a:15:63:88 (capab=0xc01 status=0 aid=2)
[  646.632753] wlan0: associated
[  646.633526] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  646.634083] cfg80211: Calling CRDA for country: US
[  646.643670] cfg80211: Regulatory domain changed to country: US
[  646.643681] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  646.643687] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  646.643691] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  646.643695] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  646.643698] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  646.643702] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  646.643705] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  646.643709] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  646.644019] show_signal_msg: 180 callbacks suppressed
[  646.644025] wpa_supplicant[989]: segfault at 200000008 ip 00000000004b1795 sp 00007fff3eaf63e0 error 4 in wpa_supplicant[400000+15f000]
[  649.311097] wlan0: deauthenticating from c4:39:3a:15:63:88 by local choice (reason=2)
[  649.340167] cfg80211: Calling CRDA to update world regulatory domain
[  649.349652] cfg80211: World regulatory domain updated:
[  649.349663] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  649.349669] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  649.349674] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  649.349678] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  649.349681] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  649.349685] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  650.147130] wlan0: authenticate with c4:39:3a:15:63:88
[  650.171451] wlan0: send auth to c4:39:3a:15:63:88 (try 1/3)
[  650.173091] wlan0: authenticated
[  650.173916] wlan0: associate with c4:39:3a:15:63:88 (try 1/3)
[  650.180969] wlan0: RX AssocResp from c4:39:3a:15:63:88 (capab=0xc01 status=0 aid=2)
[  650.181026] wlan0: associated
[  650.181227] cfg80211: Calling CRDA for country: US
[  650.188718] cfg80211: Regulatory domain changed to country: US
[  650.188728] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  650.188734] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  650.188738] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  650.188742] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  650.188746] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  650.188749] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  650.188753] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  650.188757] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  712.805160] wlan0: deauthenticating from c4:39:3a:15:63:88 by local choice (reason=3)
[  712.819958] cfg80211: Calling CRDA to update world regulatory domain
[  712.829068] cfg80211: World regulatory domain updated:
[  712.829079] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  712.829085] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  712.829090] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  712.829094] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  712.829097] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  712.829101] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  725.371621] usb 1-6: new high-speed USB device number 6 using ehci-pci
[  725.504965] usb 1-6: New USB device found, idVendor=04e8, idProduct=6865
[  725.504972] usb 1-6: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[  725.504977] usb 1-6: Product: SAMSUNG_Android_SPH-L710
[  725.504982] usb 1-6: Manufacturer: SAMSUNG
[  725.504985] usb 1-6: SerialNumber: 7a82037e
[  737.490716] usb 1-6: USB disconnect, device number 6
[  737.761358] usb 1-6: new high-speed USB device number 7 using ehci-pci
[  737.894839] usb 1-6: New USB device found, idVendor=04e8, idProduct=6863
[  737.894851] usb 1-6: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[  737.894857] usb 1-6: Product: SAMSUNG_Android_SPH-L710
[  737.894862] usb 1-6: Manufacturer: SAMSUNG
[  737.894866] usb 1-6: SerialNumber: 7a82037e
[  737.966008] usbcore: registered new interface driver cdc_ether
[  737.974913] rndis_host 1-6:1.0 usb0: register 'rndis_host' at usb-0000:00:02.1-6, RNDIS device, 02:04:56:5d:32:30
[  737.975001] usbcore: registered new interface driver rndis_host
[  873.870741] wlan0: authenticate with c4:39:3a:15:63:88
[  873.897613] wlan0: send auth to c4:39:3a:15:63:88 (try 1/3)
[  873.909169] wlan0: authenticated
[  873.910011] wlan0: associate with c4:39:3a:15:63:88 (try 1/3)
[  873.922705] wlan0: RX AssocResp from c4:39:3a:15:63:88 (capab=0xc01 status=0 aid=2)
[  873.922874] wlan0: associated
[  873.924285] cfg80211: Calling CRDA for country: US
[  873.943481] cfg80211: Regulatory domain changed to country: US
[  873.943489] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  873.943492] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  873.943495] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  873.943497] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  873.943498] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  873.943500] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  873.943502] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  873.943504] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[  919.672553] wlan0: deauthenticating from c4:39:3a:15:63:88 by local choice (reason=3)
[  919.689846] cfg80211: Calling CRDA to update world regulatory domain
[  919.703994] cfg80211: World regulatory domain updated:
[  919.704002] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  919.704005] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  919.704007] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  919.704009] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  919.704011] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  919.704013] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1245.421301] wlan0: authenticate with c4:39:3a:15:63:88
[ 1245.447720] wlan0: send auth to c4:39:3a:15:63:88 (try 1/3)
[ 1245.449655] wlan0: authenticated
[ 1245.452036] wlan0: associate with c4:39:3a:15:63:88 (try 1/3)
[ 1245.464247] wlan0: RX AssocResp from c4:39:3a:15:63:88 (capab=0xc01 status=0 aid=2)
[ 1245.464314] wlan0: associated
[ 1245.464643] cfg80211: Calling CRDA for country: US
[ 1245.473437] cfg80211: Regulatory domain changed to country: US
[ 1245.473445] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1245.473448] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1245.473451] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1245.473453] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1245.473454] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1245.473456] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1245.473458] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1245.473460] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[ 1269.634002] usb 1-6: USB disconnect, device number 7
[ 1269.636075] rndis_host 1-6:1.0 usb0: unregister 'rndis_host' usb-0000:00:02.1-6, RNDIS device
[ 1290.554058] wlan0: deauthenticating from c4:39:3a:15:63:88 by local choice (reason=3)
[ 1290.571246] cfg80211: Calling CRDA to update world regulatory domain
[ 1290.578585] cfg80211: World regulatory domain updated:
[ 1290.578594] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1290.578598] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1290.578600] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1290.578602] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1290.578604] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1290.578605] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1307.924514] wlan0: authenticate with 06:1d:d5:ff:10:20
[ 1307.956604] wlan0: direct probe to 06:1d:d5:ff:10:20 (try 1/3)
[ 1308.159420] wlan0: direct probe to 06:1d:d5:ff:10:20 (try 2/3)
[ 1308.363357] wlan0: direct probe to 06:1d:d5:ff:10:20 (try 3/3)
[ 1308.567359] wlan0: authentication with 06:1d:d5:ff:10:20 timed out
[ 1322.290815] usb 1-6: new high-speed USB device number 8 using ehci-pci
[ 1322.424250] usb 1-6: New USB device found, idVendor=04e8, idProduct=6865
[ 1322.424262] usb 1-6: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1322.424268] usb 1-6: Product: SAMSUNG_Android_SPH-L710
[ 1322.424273] usb 1-6: Manufacturer: SAMSUNG
[ 1322.424277] usb 1-6: SerialNumber: 7a82037e
[ 1396.352275] wlan0: authenticate with 34:23:ba:35:8f:7a
[ 1396.377484] wlan0: send auth to 34:23:ba:35:8f:7a (try 1/3)
[ 1396.381444] wlan0: authenticated
[ 1396.383326] wlan0: associate with 34:23:ba:35:8f:7a (try 1/3)
[ 1396.403089] wlan0: RX AssocResp from 34:23:ba:35:8f:7a (capab=0x401 status=0 aid=1)
[ 1396.403175] wlan0: associated
[ 1428.620766] wlan0: deauthenticating from 34:23:ba:35:8f:7a by local choice (reason=3)
[ 1428.635944] cfg80211: Calling CRDA to update world regulatory domain
[ 1428.642438] cfg80211: World regulatory domain updated:
[ 1428.642446] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1428.642448] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1428.642451] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1428.642453] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1428.642455] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1428.642456] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1430.471960] wlan0: authenticate with c4:39:3a:15:63:88
[ 1430.485934] wlan0: send auth to c4:39:3a:15:63:88 (try 1/3)
[ 1430.492432] wlan0: authenticated
[ 1430.495391] wlan0: associate with c4:39:3a:15:63:88 (try 1/3)
[ 1430.502970] wlan0: RX AssocResp from c4:39:3a:15:63:88 (capab=0xc01 status=0 aid=1)
[ 1430.503089] wlan0: associated
[ 1430.503423] cfg80211: Calling CRDA for country: US
[ 1430.511712] cfg80211: Regulatory domain changed to country: US
[ 1430.511727] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1430.511734] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1430.511738] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1430.511742] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1430.511746] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1430.511749] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1430.511753] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1430.511757] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[ 1476.441679] wlan0: deauthenticating from c4:39:3a:15:63:88 by local choice (reason=3)
[ 1476.455673] cfg80211: Calling CRDA to update world regulatory domain
[ 1476.465744] cfg80211: World regulatory domain updated:
[ 1476.465756] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1476.465761] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1476.465766] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1476.465770] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1476.465774] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1476.465777] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1496.175855] usb 1-6: USB disconnect, device number 8
[ 1496.476442] usb 1-6: new high-speed USB device number 9 using ehci-pci
[ 1496.609947] usb 1-6: New USB device found, idVendor=04e8, idProduct=6863
[ 1496.609959] usb 1-6: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1496.609965] usb 1-6: Product: SAMSUNG_Android_SPH-L710
[ 1496.609970] usb 1-6: Manufacturer: SAMSUNG
[ 1496.609974] usb 1-6: SerialNumber: 7a82037e
[ 1496.612834] rndis_host 1-6:1.0 usb0: register 'rndis_host' at usb-0000:00:02.1-6, RNDIS device, 02:04:56:5d:32:30
[ 1748.812978] usb 1-5: USB disconnect, device number 3
[ 1748.837498] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x0
[ 1748.837516] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x20004
[ 1748.837527] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x20000
[ 1748.837538] rtl_usb: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x83040000
[ 2996.422443] usb 1-5: new high-speed USB device number 10 using ehci-pci
[ 2996.556116] usb 1-5: New USB device found, idVendor=0846, idProduct=9041
[ 2996.556123] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2996.556129] usb 1-5: Product: 802.11n WLAN Adapter
[ 2996.556133] usb 1-5: Manufacturer: Realtek
[ 2996.556137] usb 1-5: SerialNumber: 00e04c000001
[ 2996.556984] rtl8192cu: Chip version 0x10
[ 2996.665773] rtl8192cu: MAC address: e0:46:9a:32:60:12
[ 2996.665779] rtl8192cu: Board Type 0
[ 2996.666017] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 2996.666097] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 2996.666570] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 2996.667782] rtlwifi: wireless switch is on
[ 2996.723342] rtl8192cu: MAC auto ON okay!
[ 2996.776310] rtl8192cu: Tx queue select: 0x05
[ 2997.151971] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2997.152724] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3028.736827] wlan0: authenticate with c4:39:3a:15:63:88
[ 3028.762330] wlan0: send auth to c4:39:3a:15:63:88 (try 1/3)
[ 3028.765942] wlan0: authenticated
[ 3028.768172] wlan0: associate with c4:39:3a:15:63:88 (try 1/3)
[ 3028.793369] wlan0: RX AssocResp from c4:39:3a:15:63:88 (capab=0xc01 status=0 aid=1)
[ 3028.793444] wlan0: associated
[ 3028.793639] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3028.795107] cfg80211: Calling CRDA for country: US
[ 3028.805585] cfg80211: Regulatory domain changed to country: US
[ 3028.805598] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3028.805603] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3028.805608] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 3028.805612] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3028.805615] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3028.805618] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3028.805622] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 3028.805625] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
```

[LIST]
[*]Iwconfig Output:
```
alan@alan-ubuntu:~$ iwconfig usb0 no wireless extensions.
eth0 no wireless extensions.
lo no wireless extensions.
wlan0 IEEE 802.11bgn ESSID:off/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr=2347 B Fragment thr:off Power Management:off

```
[*]Removed the password still the same issue.
[/LIST]

---

### Post by JeQhdMD on 2014-04-02
I don't have any experience with your particular adapter, but I've heard netgear can be problematic in Linux (unless you download and compile the drivers yourself).

I have 3 other usb wifi adapters that were all "plug & play" in ubuntu:

>  Panda Ultra wifi b/g/n 150
>  TP-Link TL-WN722N 
>  TP-Link TL-WN822N 

The TP Links use an atheros chipset which is recognized automatically by the Linux kernel, and the Panda module is pre-installed in Ubuntu since v12.04.  All available on Amazon (the Panda has best price, and has CONSIDERABLY better specs than the Netgear).

---

### Post by jayden2 on 2014-04-03
Alright, bought a new adapter and can't wait for it to be shipped :), Thank you.

---

### Post by efflandt on 2014-04-05
So you are able to get to your WiFi working for now using your tethered Samsung phone (without using mobile data)? That is something I did successfully as a test in Windows before, but had not tried it in Linux.

That actually works pretty easily (64-bit 12.04). I already had my Samsung S3 with its WiFi enabled connected to USB for charging. I disabled my WiFi connection in Ubuntu, enabled tethering on the phone, and that added a usb0 network device to Linux that automatically connected. So ifconfig showed usb0 as the only device (other than loopback) with an IP address and I know that is connected to my WiFi because I can access my DSL gateway config. Although, the phone apparently does NAT because the usb0 IP is a different private range than my LAN.

When I was looking for USB wireless for a Raspberry Pi computer on a board (special Debian wheezy for old ARM cpu) I went to Fry's and found a tiny one from Sabrent that said on the package that it worked with an older Linux kernel version and it worked out of the box.

---

