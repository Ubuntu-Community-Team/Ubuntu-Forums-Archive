---
title: "Bluetooth Randomly Disconnects When Not In Use Ubuntu 18.10"
date: 2018-11-26
forum: New to Ubuntu
---

### Post by aquaraider on 2018-11-26
I have a Bluetooth Headset (Sennheiser HD1 M2 AEBT) which works fine on windows and android but for some reason, it disconnects when not in use on Ubuntu 18.10. I have tried many solutions but none of which have worked to keep them connected. I do not use wifi and have it turned off in settings.  I have reinstalled Ubuntu 18.04 and it still seems to have issues. I upgraded bluez to 5.50 and updated the kernel to 4.19.5. Whenever it disconnects it is impossible to disconnect the headset in settings as well and when you turn off Bluetooth it will not turn back on. I have to restart my pc to fix it. 

**`**[COLOR=#000000][FONT=&amp]**lspci -nnk | grep -iA2 net`**
[/FONT][/COLOR]
03:00.0 Network controller [0280]: Intel Corporation Wireless 8265 / 8275 [8086:24fd] (rev 78)
	Subsystem: Intel Corporation Wireless 8265 / 8275 [8086:1010]
	Kernel driver in use: iwlwifi
--
05:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 10)
	Subsystem: Gigabyte Technology Co., Ltd Killer E220x Gigabit Ethernet Controller [1458:e000]
	Kernel driver in use: alx
	Kernel modules: alx

**`****systemctl**** status ****bluetooth****`**

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2018-11-27 10:12:18 EST; 4h 42min ago
     Docs: man:bluetoothd(8)
 Main PID: 1018 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1018 /usr/lib/bluetooth/bluetoothd


Nov 27 10:12:18 aquaraider-gaming systemd[1]: Starting Bluetooth service...
Nov 27 10:12:18 aquaraider-gaming bluetoothd[1018]: Bluetooth daemon 5.50
Nov 27 10:12:18 aquaraider-gaming systemd[1]: Started Bluetooth service.
Nov 27 10:12:18 aquaraider-gaming bluetoothd[1018]: Starting SDP server
Nov 27 10:12:18 aquaraider-gaming bluetoothd[1018]: Bluetooth management interface 1.14 initialized
Nov 27 10:12:27 aquaraider-gaming bluetoothd[1018]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/A2DPSource
Nov 27 10:12:27 aquaraider-gaming bluetoothd[1018]: Endpoint registered: sender=:1.47 path=/MediaEndpoint/A2DPSink
Nov 27 10:13:45 aquaraider-gaming bluetoothd[1018]: /org/bluez/hci0/dev_00_1B_66_81_EC_A5/fd0: fd(37) ready
Nov 27 11:50:45 aquaraider-gaming bluetoothd[1018]: Start: Connection timed out (110)
Nov 27 11:50:47 aquaraider-gaming bluetoothd[1018]: Abort: Connection timed out (110)

---

### Post by aquaraider on 2018-11-29
Solved with [https://bbs.archlinux.org/viewtopic.php?id=236479](https://bbs.archlinux.org/viewtopic.php?id=236479)

---

