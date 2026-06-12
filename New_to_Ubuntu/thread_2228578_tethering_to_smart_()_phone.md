---
title: "tethering to smart (?) phone"
date: 2014-06-08
forum: New to Ubuntu
---

### Post by quailwoods on 2014-06-08
I'm trying to tether my phone to laptop with 12.04. Saw on a forum I should run dmesg to see if it recognized phone, and I got way more than I bargained for:

[   22.240196] cfg80211: Disabling freq 5580 MHz
[   22.240202] cfg80211: Disabling freq 5600 MHz
[   22.240213] cfg80211: Disabling freq 5620 MHz
[   22.240219] cfg80211: Disabling freq 5640 MHz
[   22.240225] cfg80211: Disabling freq 5660 MHz
[   22.240236] cfg80211: Disabling freq 5680 MHz
[   22.240242] cfg80211: Disabling freq 5700 MHz
[   22.240250] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   22.240259] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.240271] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   22.240280] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.240288] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   22.240312] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.240330] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   22.240350] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.240368] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   22.240391] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   22.240408] cfg80211: Disabling freq 5920 MHz
[   22.240414] cfg80211: Disabling freq 5940 MHz
[   22.240420] cfg80211: Disabling freq 5960 MHz
[   22.240427] cfg80211: Disabling freq 5980 MHz
[   22.240433] cfg80211: Disabling freq 6000 MHz
[   22.240439] cfg80211: Disabling freq 6020 MHz
[   22.240445] cfg80211: Disabling freq 6040 MHz
[   22.240451] cfg80211: Disabling freq 6060 MHz
[   22.240458] cfg80211: Disabling freq 6080 MHz
[   22.256929] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   22.258386] Linux video capture interface: v2.00
[   22.263810] uvcvideo: Found UVC 1.00 device Integrated Webcam (174f:1403)
[   22.272918] lib80211_crypt: registered algorithm 'TKIP'
[   22.296518] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input5
[   22.296782] usbcore: registered new interface driver uvcvideo
[   22.296790] USB Video Class driver (1.1.1)
[   22.415237] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   22.837464] microcode: CPU0 sig=0x106c2, pf=0x1, revision=0x211
[   23.093849] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   23.117826] compal_laptop: Identified laptop model 'Dell Mini 10'
[   23.127202] compal_laptop: Driver 0.2.7 successfully loaded
[   23.498835] fbcon: psbfb (fb0) is primary device
[   23.499213] Console: switching to colour frame buffer device 128x36
[   23.499308] fb0: psbfb frame buffer device
[   23.499315] drm: registered panic notifier
[   23.499567] gma500 0000:00:02.0: Backlight lvds set brightness 7a120000
[   23.499596] [drm] Initialized gma500 1.0.0 2011-06-06 for 0000:00:02.0 on minor 0
[   23.499942] ACPI Warning: 0x00001180-0x000011bf SystemIO conflicts with Region \GPI0 1 (20120320/utaddress-251)
[   23.499965] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   23.500261] lpc_sch: probe of 0000:00:1f.0 failed with error -16
[   23.665227] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   23.669211] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   23.672944] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   23.866208] init: failsafe main process (703) killed by TERM signal
[   24.025118] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020801)
[   24.099380] psmouse serio1: elantech: Synaptics capabilities query result 0x08, 0x13, 0x0d.
[   24.386977] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input9
[   24.422135] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   24.422152] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422163] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   24.422174] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422184] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   24.422194] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422204] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   24.422213] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422222] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   24.422232] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422241] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   24.422251] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422260] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   24.422270] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422280] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   24.422291] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422301] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   24.422311] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422321] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   24.422332] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422342] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   24.422352] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422362] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   24.422373] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.422383] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   24.422393] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.422403] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   24.422413] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.422421] cfg80211: Disabling freq 5170 MHz
[   24.422431] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   24.422441] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422450] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[   24.422461] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422471] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   24.422481] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422491] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[   24.422502] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422512] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   24.422522] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422532] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[   24.422543] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422553] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   24.422563] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422572] cfg80211: Disabling freq 5260 MHz
[   24.422580] cfg80211: Disabling freq 5280 MHz
[   24.422588] cfg80211: Disabling freq 5300 MHz
[   24.422595] cfg80211: Disabling freq 5320 MHz
[   24.422603] cfg80211: Disabling freq 5500 MHz
[   24.422610] cfg80211: Disabling freq 5520 MHz
[   24.422618] cfg80211: Disabling freq 5540 MHz
[   24.422625] cfg80211: Disabling freq 5560 MHz
[   24.422633] cfg80211: Disabling freq 5580 MHz
[   24.422640] cfg80211: Disabling freq 5600 MHz
[   24.422648] cfg80211: Disabling freq 5620 MHz
[   24.422655] cfg80211: Disabling freq 5640 MHz
[   24.422663] cfg80211: Disabling freq 5660 MHz
[   24.422670] cfg80211: Disabling freq 5680 MHz
[   24.422678] cfg80211: Disabling freq 5700 MHz
[   24.422688] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   24.422698] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422708] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   24.422717] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422726] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   24.422736] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422746] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   24.422756] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422766] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   24.422777] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422786] cfg80211: Disabling freq 5920 MHz
[   24.422794] cfg80211: Disabling freq 5940 MHz
[   24.422801] cfg80211: Disabling freq 5960 MHz
[   24.422809] cfg80211: Disabling freq 5980 MHz
[   24.422817] cfg80211: Disabling freq 6000 MHz
[   24.422824] cfg80211: Disabling freq 6020 MHz
[   24.422831] cfg80211: Disabling freq 6040 MHz
[   24.422838] cfg80211: Disabling freq 6060 MHz
[   24.422846] cfg80211: Disabling freq 6080 MHz
[   24.422865] cfg80211: World regulatory domain updated:
[   24.422873] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.422884] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422894] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.422905] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.422915] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.422925] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.514554] type=1400 audit(1402233760.843:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=812 comm="apparmor_parser"
[   24.527586] type=1400 audit(1402233760.855:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=811 comm="apparmor_parser"
[   24.528879] type=1400 audit(1402233760.859:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=812 comm="apparmor_parser"
[   24.529942] type=1400 audit(1402233760.859:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=812 comm="apparmor_parser"
[   24.534108] type=1400 audit(1402233760.863:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=811 comm="apparmor_parser"
[   25.145234] microcode: CPU1 sig=0x106c2, pf=0x1, revision=0x211
[   25.404757] r8169 0000:02:00.0: eth0: link down
[   25.405512] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.429306] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.676522] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   27.882452] init: anacron main process (929) killed by TERM signal
[   28.719773] init: plymouth-stop pre-start process (1154) terminated with status 1
[   54.817034] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   54.819418] sd 2:0:0:0: [sdb] Asking for cache data failed
[   54.819436] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  106.521848] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  106.525064] sd 2:0:0:0: [sdb] Asking for cache data failed
[  106.525082] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  158.243360] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  158.245728] sd 2:0:0:0: [sdb] Asking for cache data failed
[  158.245756] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  209.945523] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  209.947842] sd 2:0:0:0: [sdb] Asking for cache data failed
[  209.947861] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  261.667396] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  261.670289] sd 2:0:0:0: [sdb] Asking for cache data failed
[  261.670318] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  313.379057] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  313.382168] sd 2:0:0:0: [sdb] Asking for cache data failed
[  313.382193] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  342.734503] audit_printk_skb: 39 callbacks suppressed
[  342.734523] type=1400 audit(1402234079.066:25): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=589 comm="cupsd" pid=589 comm="cupsd" capability=36  capname="block_suspend"
[  365.091057] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  365.094291] sd 2:0:0:0: [sdb] Asking for cache data failed
[  365.094319] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  416.803195] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  416.808151] sd 2:0:0:0: [sdb] Asking for cache data failed
[  416.808178] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  468.514970] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  468.517836] sd 2:0:0:0: [sdb] Asking for cache data failed
[  468.517862] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  520.226987] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  520.232176] sd 2:0:0:0: [sdb] Asking for cache data failed
[  520.232205] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  571.939123] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  571.945497] sd 2:0:0:0: [sdb] Asking for cache data failed
[  571.945526] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  623.651391] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  623.653783] sd 2:0:0:0: [sdb] Asking for cache data failed
[  623.653810] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  675.362572] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  675.365588] sd 2:0:0:0: [sdb] Asking for cache data failed
[  675.365609] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  727.197051] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  727.199289] sd 2:0:0:0: [sdb] Asking for cache data failed
[  727.199306] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  778.823226] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  778.825687] sd 2:0:0:0: [sdb] Asking for cache data failed
[  778.825711] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  830.498897] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  830.501204] sd 2:0:0:0: [sdb] Asking for cache data failed
[  830.501231] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  882.211090] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  882.216723] sd 2:0:0:0: [sdb] Asking for cache data failed
[  882.216752] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  933.922988] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  933.928611] sd 2:0:0:0: [sdb] Asking for cache data failed
[  933.928640] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  985.635372] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  985.638255] sd 2:0:0:0: [sdb] Asking for cache data failed
[  985.638291] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1037.339005] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1037.345632] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1037.345661] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1089.061083] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1089.063481] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1089.063499] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1140.765447] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1140.768094] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1140.768113] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1183.289700] type=1400 audit(1402234919.620:26): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=589 comm="cupsd" pid=589 comm="cupsd" capability=36  capname="block_suspend"
[ 1192.479032] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1192.481789] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1192.481816] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1244.195422] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1244.198296] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1244.198326] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1295.907432] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1295.909809] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1295.909837] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1347.614817] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1347.620691] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1347.620719] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1399.331074] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1399.333472] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1399.333499] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1429.256131] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1429.256153] cfg80211: Restoring regulatory settings
[ 1429.256168] cfg80211: Calling CRDA to update world regulatory domain
[ 1429.543895] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.543907] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.543915] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.543922] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.543928] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.543934] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.543940] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.543947] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.543953] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.543960] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.543966] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.543972] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.543979] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.543985] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.543991] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.543998] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544065] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544075] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544092] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544116] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544138] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544157] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544176] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544195] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1429.544213] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544233] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1429.544245] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544253] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1429.544261] cfg80211: Disabling freq 5170 MHz
[ 1429.544268] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544277] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544286] cfg80211: Updating information on frequency 5190 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544294] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544303] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544312] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544322] cfg80211: Updating information on frequency 5210 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544332] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544341] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544352] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544362] cfg80211: Updating information on frequency 5230 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544372] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544381] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544390] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544397] cfg80211: Disabling freq 5260 MHz
[ 1429.544403] cfg80211: Disabling freq 5280 MHz
[ 1429.544409] cfg80211: Disabling freq 5300 MHz
[ 1429.544415] cfg80211: Disabling freq 5320 MHz
[ 1429.544422] cfg80211: Disabling freq 5500 MHz
[ 1429.544430] cfg80211: Disabling freq 5520 MHz
[ 1429.544438] cfg80211: Disabling freq 5540 MHz
[ 1429.544446] cfg80211: Disabling freq 5560 MHz
[ 1429.544453] cfg80211: Disabling freq 5580 MHz
[ 1429.544461] cfg80211: Disabling freq 5600 MHz
[ 1429.544468] cfg80211: Disabling freq 5620 MHz
[ 1429.544475] cfg80211: Disabling freq 5640 MHz
[ 1429.544482] cfg80211: Disabling freq 5660 MHz
[ 1429.544489] cfg80211: Disabling freq 5680 MHz
[ 1429.544495] cfg80211: Disabling freq 5700 MHz
[ 1429.544504] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544513] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544522] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544531] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544539] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544548] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544557] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544565] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544573] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[ 1429.544581] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544588] cfg80211: Disabling freq 5920 MHz
[ 1429.544595] cfg80211: Disabling freq 5940 MHz
[ 1429.544602] cfg80211: Disabling freq 5960 MHz
[ 1429.544610] cfg80211: Disabling freq 5980 MHz
[ 1429.544616] cfg80211: Disabling freq 6000 MHz
[ 1429.544624] cfg80211: Disabling freq 6020 MHz
[ 1429.544632] cfg80211: Disabling freq 6040 MHz
[ 1429.544640] cfg80211: Disabling freq 6060 MHz
[ 1429.544647] cfg80211: Disabling freq 6080 MHz
[ 1429.544667] cfg80211: World regulatory domain updated:
[ 1429.544676] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1429.544687] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544697] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1429.544707] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1429.544717] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1429.544728] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1451.041795] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1451.044097] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1451.044113] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1502.755011] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1502.761511] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1502.761540] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1554.465860] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1554.472245] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1554.472272] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1606.178694] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1606.181604] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1606.181625] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1657.887190] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1657.892166] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1657.892194] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1709.598236] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1709.600953] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1709.600981] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1761.305021] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1761.307286] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1761.307298] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1813.025065] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1813.027431] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1813.027446] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1864.739228] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1864.742350] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1864.742376] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1916.445184] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1916.447422] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1916.447440] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 1968.163001] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1968.168618] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 1968.168646] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2019.869109] sd 2:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2019.871334] sd 2:0:0:0: [sdb] Asking for cache data failed
[ 2019.871356] sd 2:0:0:0: [sdb] Assuming drive cache: write through


So what does it all mean, O Great and Powerful Oz?

---

