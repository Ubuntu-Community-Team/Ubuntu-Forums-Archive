---
title: "Ubuntu – “Activation of network connection failed” wifi works but sometimes it stops"
date: 2022-08-29
forum: New to Ubuntu
---

### Post by master-55555 on 2022-08-29
[1661808781.2296] NetworkManager (version 1.22.10) is starting... (for the first time)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.2297] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 10-globally-managed-devices.conf, 20-connectivi>
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.2319] bus-manager: acquired D-Bus service "org.freedesktop.NetworkManager"
Avq 30 01:33:01 subhan-comp systemd[1]: Started Network Manager.
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.2387] manager[0x55ebbfa53030]: monitoring kernel firmware directory '/lib/firmware'.
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.2387] monitoring ifupdown state file '/run/network/ifstate'.
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3499] hostname: hostname: using hostnamed
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3499] hostname: hostname changed from (none) to "subhan-comp"
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3502] dns-mgr[0x55ebbfa39290]: init: dns=systemd-resolved rc-manager=symlink, plugin=systemd-resolved
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3510] rfkill0: found Wi-Fi radio killswitch (at /sys/devices/pci0000:00/0000:00:02.2/0000:03:00.0/ieee80211/phy0/rfkill0) (driver rtw_>
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3512] manager[0x55ebbfa53030]: rfkill: Wi-Fi hardware radio set enabled
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3512] manager[0x55ebbfa53030]: rfkill: WWAN hardware radio set enabled
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3589] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-adsl.so)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3605] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wifi.so)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3653] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-bluetooth.so)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3675] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-wwan.so)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3721] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-device-plugin-team.so)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3724] manager: rfkill: Wi-Fi enabled by radio killswitch; enabled by state file
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3725] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3726] manager: Networking is enabled by state file
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3727] dhcp-init: Using DHCP client 'internal'
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3788] settings: Loaded settings plugin: ifupdown ("/usr/lib/x86_64-linux-gnu/NetworkManager/1.22.10/libnm-settings-plugin-ifupdown.so")
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3788] settings: Loaded settings plugin: keyfile (internal)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3789] ifupdown: management mode: unmanaged
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <warn>  [1661808781.3793] ifupdown: interfaces file /etc/network/interfaces doesn't exist
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3991] device (lo): carrier: link connected
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.3993] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.4003] manager: (enp2s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.4008] device (wlp3s0): driver supports Access Point (AP) mode
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.4013] manager: (wlp3s0): new 802.11 Wi-Fi device (/org/freedesktop/NetworkManager/Devices/3)
Avq 30 01:33:01 subhan-comp NetworkManager[883]: <info>  [1661808781.4023] device (wlp3s0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Avq 30 01:33:02 subhan-comp NetworkManager[883]: <warn>  [1661808782.3484] Error: failed to open /run/network/ifstate
Avq 30 01:33:02 subhan-comp NetworkManager[883]: <info>  [1661808782.3584] modem-manager: ModemManager available
Avq 30 01:33:02 subhan-comp NetworkManager[883]: <info>  [1661808782.3587] supplicant: wpa_supplicant running
Avq 30 01:33:02 subhan-comp NetworkManager[883]: <info>  [1661808782.3588] device (wlp3s0): supplicant interface state: init -> starting
Avq 30 01:33:02 subhan-comp NetworkManager[883]: <info>  [1661808782.4270] sup-iface[0x55ebbfa61120,wlp3s0]: supports 4 scan SSIDs
Avq 30 01:33:02 subhan-comp NetworkManager[883]: <info>  [1661808782.4275] device (wlp3s0): supplicant interface state: starting -> ready
Avq 30 01:33:02 subhan-comp NetworkManager[883]: <info>  [1661808782.4275] device (wlp3s0): state change: unavailable -> disconnected (reason 'supplicant-available', sys-iface-state: 'managed')
Avq 30 01:33:06 subhan-comp NetworkManager[883]: <info>  [1661808786.5303] manager: startup complete
Avq 30 01:33:06 subhan-comp NetworkManager[883]: <info>  [1661808786.9251] manager: (br-1e89040960f2): new Bridge device (/org/freedesktop/NetworkManager/Devices/4)
Avq 30 01:33:06 subhan-comp NetworkManager[883]: <info>  [1661808786.9740] manager: (br-62b05783c88f): new Bridge device (/org/freedesktop/NetworkManager/Devices/5)
Avq 30 01:33:07 subhan-comp NetworkManager[883]: <info>  [1661808787.0033] manager: (br-73d3fbdf14aa): new Bridge device (/org/freedesktop/NetworkManager/Devices/6)
Avq 30 01:33:07 subhan-comp NetworkManager[883]: <info>  [1661808787.0333] manager: (br-84d990d5c139): new Bridge device (/org/freedesktop/NetworkManager/Devices/7)
Avq 30 01:33:07 subhan-comp NetworkManager[883]: <info>  [1661808787.0572] manager: (br-8aeca049bbe8): new Bridge device (/org/freedesktop/NetworkManager/Devices/8)
Avq 30 01:33:07 subhan-comp NetworkManager[883]: <info>  [1661808787.0766] manager: (br-bf66b1604eee): new Bridge device (/org/freedesktop/NetworkManager/Devices/9)
Avq 30 01:33:07 subhan-comp NetworkManager[883]: <info>  [1661808787.0988] manager: (br-b7f109fbdb17): new Bridge device (/org/freedesktop/NetworkManager/Devices/10)
Avq 30 01:33:07 subhan-comp NetworkManager[883]: <info>  [1661808787.1241] manager: (br-e79031311dbc): new Bridge device (/org/freedesktop/NetworkManager/Devices/11)
Avq 30 01:33:07 subhan-comp NetworkManager[883]: <info>  [1661808787.1492] manager: (br-ef3ed8ecda41): new Bridge device (/org/freedesktop/NetworkManager/Devices/12)

---

