---
title: "Bluetooth installed but won't start"
date: 2017-12-24
forum: New to Ubuntu
---

### Post by steve169 on 2017-12-24
I'm trying (and failing) to get Bluetooth running and connecting to a Bluetooth speaker.

I'm running Ubuntu 16.04 on a Dell Inspiron 660 desktop.

The speaker is an Anker SoundCore model A3102.

Synaptic shows that these are installed:

    blueman
    bluez
    bluez-dpg
    bluez-obexd
    bluez-tools
    gnome-bluetooth
    indicator-bluetooth
    libbluetooth3
    libbluetooth3-dbg
    libgnome-bluetooth13

With the speaker only a few inches from the computer and  router, I power up the speaker and set it to "pair."

I launch "Bluetooth Manager" and get this window:

[ATTACH=CONFIG]277926[/ATTACH]

I launch "Bluetooth" and get this window, in which all the settings are grayed and inoperable:

[ATTACH=CONFIG]277925[/ATTACH]

What am I doing wrong?

---

### Post by jeremy31 on 2017-12-24
Open a terminal and enter ```
lspci -nnk | grep -iA3 net; lsusb; dmesg | egrep -i 'blue|firm'
```
Post results

---

### Post by steve169 on 2017-12-24
Here is the result of the above command:

[INDENT]03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Dell Wireless 1506 WLAN Half Mini-Card [1028:0208]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Dell RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1028:0581]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 004: ID 413c:2111 Dell Computer Corp. 
Bus 002 Device 003: ID 1a7c:0191 Evoluent VerticalMouse 4
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0930:6544 Toshiba Corp. TransMemory-Mini / Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0c45:7603 Microdia 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/INDENT]

---

### Post by jeremy31 on 2017-12-24
I don't see a bluetooth device discovered on your computer.  I have the same wireless card with bluetooth, I think the model number is AR5B225, you might have the AR5B125(?) the one without bluetooth

---

### Post by steve169 on 2017-12-24
I will contact Dell and report back.

---

