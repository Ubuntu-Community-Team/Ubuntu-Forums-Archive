---
title: "Bluetooth strange interferences - suddenly black screen - Lock"
date: 2016-09-10
forum: New to Ubuntu
---

### Post by wolf-zirbs on 2016-09-10
Hi this is my first post in the Forum, please apology my non native English.
i love Ubuntu in special way Ubuntu-Gnome and I am a happy User since 2012.
I really learned to appreciate the uncountable Help you get online and will like to pay back the many feedback I got all around in the Internet.

Ok, that was my short introduction, now to my first problem I search to find a solution if possible.

I am testing a Bluetooth Keyboard acquired shortly: **Inateck**

I managed to configure using  Blueman-applet so far.
But I have notice that from time to time when the Bluetooth-Keyboard goes in "Pause" i get suddenly a black screen
that goes to "Lock" even I have disabled with the "Settings" all feature about automatic "Lock" and so ons.

To get an approx diagnostic i edit her the result of "dmesg | egrep -i 'blue|firm'"

```
@debian:~$ dmesg | egrep -i 'blue|firm'
[    0.133111] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    1.418787] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x381f17)
[    8.010417] Bluetooth: Core ver 2.21
[    8.010430] Bluetooth: HCI device and connection manager initialized
[    8.010432] Bluetooth: HCI socket layer initialized
[    8.010434] Bluetooth: L2CAP socket layer initialized
[    8.010438] Bluetooth: SCO socket layer initialized
[    8.548529] Bluetooth: hci0: read Intel version: 3707100180012d0d00
[    8.731732] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7260-17.ucode failed with error -2
[    8.780488] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.1.2d.d.bseq
[    8.968535] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    8.985821] iwlwifi 0000:03:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[   20.038969] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.038971] Bluetooth: BNEP filters: protocol multicast
[   20.038975] Bluetooth: BNEP socket layer initialized
[   44.205964] Bluetooth: RFCOMM TTY layer initialized
[   44.205971] Bluetooth: RFCOMM socket layer initialized
[   44.205975] Bluetooth: RFCOMM ver 1.11
[   57.175561] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   57.175566] Bluetooth: HIDP socket layer initialized
[   57.176182] input: Inateck BK1003 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/bluetooth/hci0/hci0:256/0005:04E8:7021.0002/input/input20
[   57.176369] hid-generic 0005:04E8:7021.0002: input,hidraw1: BLUETOOTH HID v0.01 Keyboard [Inateck BK1003] on 7c:5c:f8:6f:14:f8
[ 1597.492870] input: Inateck BK1003 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/bluetooth/hci0/hci0:256/0005:04E8:7021.0003/input/input21
[ 1597.494038] hid-generic 0005:04E8:7021.0003: input,hidraw1: BLUETOOTH HID v0.01 Keyboard [Inateck BK1003] on 7c:5c:f8:6f:14:f8
[ 2279.255691] input: Inateck BK1003 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/bluetooth/hci0/hci0:256/0005:04E8:7021.0004/input/input22
[ 2279.256588] hid-generic 0005:04E8:7021.0004: input,hidraw1: BLUETOOTH HID v0.01 Keyboard [Inateck BK1003] on 7c:5c:f8:6f:14:f8
[ 2447.016065] input: Inateck BK1003 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/bluetooth/hci0/hci0:512/0005:04E8:7021.0005/input/input23
[ 2447.016272] hid-generic 0005:04E8:7021.0005: input,hidraw1: BLUETOOTH HID v0.01 Keyboard [Inateck BK1003] on 7c:5c:f8:6f:14:f8
```

I hope this may help. If not please not esitate to ask me to edit more info.

Thanks for your help.

---

### Post by ajgreeny on 2016-09-10
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

