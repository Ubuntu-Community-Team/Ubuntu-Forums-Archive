---
title: "USB Bluetooth adapter shows up on lsusb but isn't detected by Blueman"
date: 2020-09-11
forum: New to Ubuntu
---

### Post by matthpmoreira on 2020-09-11
Hey guys. I've used Linux distros many times in the past, but I can never get the hang of it. I decided to try again yesterday, but I'm having issues with my Bluetooth adapter. At the time, I didn't have Bluetooth devices so I never had this problem. My WiFi adapter is working fine (even better than Windows). I've read a bunch of threads and executed many instructions unknown by me but this hasn't been solved. When I run lsusb this shows up:

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 001 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 003: ID 1a2c:2124 China Resource Semico Co., Ltd USB Keyboard
Bus 001 Device 002: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 005: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

You can see my USB Bluetooth adapter on Bus 001 Device 008. It says "Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)". However, when I run Bluetooth Manager by itself, it won't open. When I run Bluetooth Manager on a terminal (sudo blueman-manager), it shows this:

```
blueman-manager version 2.1.2 startingblueman-manager 19.02.53 ERROR    Manager:118 on_dbus_name_appeared: Default adapter not found, trying first available.
blueman-manager 19.02.53 ERROR    Manager:122 on_dbus_name_appeared: No adapter(s) found, exiting
```

As you can see, it's being detected by the computer but not by Blueman. I have no idea of what exactly is wrong and what I should do. Thanks for your time.

---

