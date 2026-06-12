---
title: "Sandberg wifi adapter wont connect"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by GarethA on 2012-11-10
My new sandberg (realtek RTL8188CUS) wifi adapter wont connect to my network.
I've installed latest drivers.
This is the log output - can anyone tell me why it's not connecting?

```
Nov 10 10:46:26 peter-linux kernel: [ 1709.697410] usb 1-1.4: new high-speed USB device number 9 using ehci_hcd
Nov 10 10:46:26 peter-linux mtp-probe: checking bus 1, device 9: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4"
Nov 10 10:46:26 peter-linux kernel: [ 1709.874261] rtl8192cu: MAC address: 80:1f:02:5c:76:ee
Nov 10 10:46:26 peter-linux kernel: [ 1709.874268] rtl8192cu: Board Type 0
Nov 10 10:46:26 peter-linux mtp-probe: bus: 1, device: 9 was not an MTP device
Nov 10 10:46:26 peter-linux kernel: [ 1709.877135] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
Nov 10 10:46:26 peter-linux kernel: [ 1709.877142] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877146] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877149] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877152] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877155] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877158] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877160] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877163] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877166] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877169] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877171] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877174] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877177] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877180] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877183] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877186] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877188] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877191] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877194] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877197] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877200] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:26 peter-linux kernel: [ 1709.877203] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:26 peter-linux kernel: [ 1709.877206] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
Nov 10 10:46:26 peter-linux kernel: [ 1709.877208] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
Nov 10 10:46:26 peter-linux kernel: [ 1709.877211] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
Nov 10 10:46:26 peter-linux kernel: [ 1709.877273] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Nov 10 10:46:26 peter-linux kernel: [ 1709.877517] ieee80211 phy3: Selected rate control algorithm 'rtl_rc'
Nov 10 10:46:26 peter-linux NetworkManager[644]: <info> found WiFi radio killswitch rfkill3 (at /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/ieee80211/phy3/rfkill3) (driver (unknown))
Nov 10 10:46:26 peter-linux NetworkManager[644]: <info> (wlan0): using nl80211 for WiFi device control
Nov 10 10:46:26 peter-linux NetworkManager[644]: <warn> (wlan0): driver supports Access Point (AP) mode
Nov 10 10:46:26 peter-linux NetworkManager[644]: <info> (wlan0): new 802.11 WiFi device (driver: 'rtl8192cu' ifindex: 6)
Nov 10 10:46:26 peter-linux NetworkManager[644]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/4
Nov 10 10:46:26 peter-linux NetworkManager[644]: <info> (wlan0): now managed
Nov 10 10:46:26 peter-linux NetworkManager[644]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 10 10:46:26 peter-linux NetworkManager[644]: <info> (wlan0): bringing up device.
Nov 10 10:46:26 peter-linux kernel: [ 1709.899798] rtl8192cu: MAC auto ON okay!
Nov 10 10:46:26 peter-linux kernel: [ 1709.932433] rtl8192cu: Tx queue select: 0x05
Nov 10 10:46:26 peter-linux kernel: [ 1709.933198] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin
Nov 10 10:46:27 peter-linux NetworkManager[644]: <info> (wlan0): preparing device.
Nov 10 10:46:27 peter-linux NetworkManager[644]: <info> (wlan0): deactivating device (reason 'managed') [2]
Nov 10 10:46:27 peter-linux NetworkManager[644]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/net/wlan0, iface: wlan0)
Nov 10 10:46:27 peter-linux NetworkManager[644]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 10 10:46:27 peter-linux kernel: [ 1710.338452] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 10 10:46:27 peter-linux kernel: [ 1710.338675] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 10 10:46:27 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: starting -> ready
Nov 10 10:46:27 peter-linux NetworkManager[644]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Nov 10 10:46:27 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: ready -> inactive
Nov 10 10:46:27 peter-linux NetworkManager[644]: <warn> Trying to remove a non-existant call id.
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Auto-activating connection 'linux-final'.
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) starting connection 'linux-final'
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0/wireless): access point 'linux-final' has security, but secrets are required.
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0/wireless): connection 'linux-final' has security, and secrets exist.  No new secrets needed.
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Config: added 'ssid' value 'linux-final'
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Config: added 'scan_ssid' value '1'
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Config: added 'auth_alg' value 'OPEN'
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Config: added 'psk' value '<omitted>'
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> Config: set interface ap_scan to 1
Nov 10 10:46:28 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: inactive -> scanning
Nov 10 10:46:29 peter-linux wpa_supplicant[1706]: Trying to authenticate with 14:d6:4d:c5:ae:e2 (SSID='linux-final' freq=2457 MHz)
Nov 10 10:46:29 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Nov 10 10:46:29 peter-linux wpa_supplicant[1706]: Trying to associate with 14:d6:4d:c5:ae:e2 (SSID='linux-final' freq=2457 MHz)
Nov 10 10:46:29 peter-linux kernel: [ 1712.589652] wlan0: authenticate with 14:d6:4d:c5:ae:e2 (try 1)
Nov 10 10:46:29 peter-linux kernel: [ 1712.592113] wlan0: authenticated
Nov 10 10:46:29 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: authenticating -> associating
Nov 10 10:46:29 peter-linux kernel: [ 1712.614573] wlan0: associate with 14:d6:4d:c5:ae:e2 (try 1)
Nov 10 10:46:29 peter-linux kernel: [ 1712.620751] wlan0: RX AssocResp from 14:d6:4d:c5:ae:e2 (capab=0xc31 status=0 aid=2)
Nov 10 10:46:29 peter-linux kernel: [ 1712.620755] wlan0: associated
Nov 10 10:46:29 peter-linux wpa_supplicant[1706]: Associated with 14:d6:4d:c5:ae:e2
Nov 10 10:46:29 peter-linux kernel: [ 1712.633592] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 10 10:46:29 peter-linux kernel: [ 1712.634004] cfg80211: Calling CRDA for country: GB
Nov 10 10:46:29 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Nov 10 10:46:29 peter-linux kernel: [ 1712.638407] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638413] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638416] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638419] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638422] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638425] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638427] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638430] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638433] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638436] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638438] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638441] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638444] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638447] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638450] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638453] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638455] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638458] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638461] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638464] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638466] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638469] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638472] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638475] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638477] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:29 peter-linux kernel: [ 1712.638480] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638483] cfg80211: Disabling freq 2484 MHz
Nov 10 10:46:29 peter-linux kernel: [ 1712.638489] cfg80211: Regulatory domain changed to country: GB
Nov 10 10:46:29 peter-linux kernel: [ 1712.638491] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638494] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638496] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638499] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov 10 10:46:29 peter-linux kernel: [ 1712.638501] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Nov 10 10:46:39 peter-linux wpa_supplicant[1706]: Authentication with 14:d6:4d:c5:ae:e2 timed out.
Nov 10 10:46:39 peter-linux kernel: [ 1722.622313] wlan0: disassociating from 14:d6:4d:c5:ae:e2 by local choice (reason=3)
Nov 10 10:46:39 peter-linux wpa_supplicant[1706]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Nov 10 10:46:39 peter-linux wpa_supplicant[1706]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Nov 10 10:46:39 peter-linux kernel: [ 1722.636597] cfg80211: All devices are disconnected, going to restore regulatory settings
Nov 10 10:46:39 peter-linux kernel: [ 1722.636604] cfg80211: Restoring regulatory settings while preserving user preference for: GB
Nov 10 10:46:39 peter-linux kernel: [ 1722.636882] wlan0: deauthenticating from 14:d6:4d:c5:ae:e2 by local choice (reason=3)
Nov 10 10:46:39 peter-linux kernel: [ 1722.636970] cfg80211: Calling CRDA to update world regulatory domain
Nov 10 10:46:39 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Nov 10 10:46:39 peter-linux kernel: [ 1722.641382] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Nov 10 10:46:39 peter-linux kernel: [ 1722.641387] cfg80211: World regulatory domain updated:
Nov 10 10:46:39 peter-linux kernel: [ 1722.641389] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 10 10:46:39 peter-linux kernel: [ 1722.641393] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.641396] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.641399] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.641402] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.641405] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.641567] cfg80211: Calling CRDA for country: GB
Nov 10 10:46:39 peter-linux kernel: [ 1722.646696] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646702] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646705] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646708] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646710] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646714] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646716] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646719] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646722] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646725] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646727] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646730] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646733] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646736] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646739] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646742] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646744] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646747] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646750] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646753] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646755] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646758] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646761] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646764] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646767] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
Nov 10 10:46:39 peter-linux kernel: [ 1722.646770] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646772] cfg80211: Disabling freq 2484 MHz
Nov 10 10:46:39 peter-linux kernel: [ 1722.646776] cfg80211: Regulatory domain changed to country: GB
Nov 10 10:46:39 peter-linux kernel: [ 1722.646778] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646781] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646784] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646787] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Nov 10 10:46:39 peter-linux kernel: [ 1722.646789] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Nov 10 10:46:40 peter-linux wpa_supplicant[1706]: Trying to authenticate with 14:d6:4d:c5:ae:e2 (SSID='linux-final' freq=2457 MHz)
Nov 10 10:46:40 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: disconnected -> authenticating
Nov 10 10:46:40 peter-linux kernel: [ 1723.383975] wlan0: authenticate with 14:d6:4d:c5:ae:e2 (try 1)
Nov 10 10:46:40 peter-linux kernel: [ 1723.583303] wlan0: authenticate with 14:d6:4d:c5:ae:e2 (try 2)
Nov 10 10:46:40 peter-linux kernel: [ 1723.783045] wlan0: authenticate with 14:d6:4d:c5:ae:e2 (try 3)
Nov 10 10:46:40 peter-linux kernel: [ 1723.982788] wlan0: authentication with 14:d6:4d:c5:ae:e2 timed out
Nov 10 10:47:29 peter-linux NetworkManager[644]: <warn> Activation (wlan0/wireless): association took too long.
Nov 10 10:47:29 peter-linux NetworkManager[644]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Nov 10 10:47:29 peter-linux NetworkManager[644]: <warn> Activation (wlan0/wireless): asking for new secrets
Nov 10 10:47:29 peter-linux NetworkManager[644]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Nov 10 10:47:29 peter-linux NetworkManager[644]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Nov 10 10:47:42 peter-linux NetworkManager[644]: <warn> No agents were available for this request.
Nov 10 10:47:42 peter-linux NetworkManager[644]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Nov 10 10:47:42 peter-linux NetworkManager[644]: <warn> Activation (wlan0) failed for access point (linux-final)
Nov 10 10:47:42 peter-linux NetworkManager[644]: <info> Marking connection 'linux-final' invalid.
Nov 10 10:47:42 peter-linux NetworkManager[644]: <warn> Activation (wlan0) failed.
Nov 10 10:47:42 peter-linux NetworkManager[644]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 10 10:47:42 peter-linux NetworkManager[644]: <info> (wlan0): deactivating device (reason 'none') [0]
```

---

### Post by grahammechanical on 2012-11-10
You need to help us to help you but you do not even tell us which version of Ubuntu you are using. The best I can do is to give you this.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

My guess is that your router is called linux-final and the wireless adapter in the computer is not connecting to it because Network Manager has not been given the correct authorization passphrase.

With the latest version of Ubuntu it is best if we let the Network Manager do all the work and Additional Drivers install any needed drivers. 


Regards.

---

### Post by GarethA on 2012-11-10
Thanks.
Sorry yes, should hae given more info:
ubuntu 12.04 (and have also tried a couple of other distros with similar effect).
Yes you're correct the ssid of the wireless network is linux-final.
Thanks for the link to the guide I have been through that and am still stuck.
I have also tried removing security/passphrase from the network and it still wont connect.
I have another wireless network in the building which it wont connect to either.
Both wireless networks are used happily by a bunch of other devices.

---

