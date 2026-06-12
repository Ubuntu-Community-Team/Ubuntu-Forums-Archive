---
title: "Bluetooth mouse and keyboard"
date: 2015-03-28
forum: New to Ubuntu
---

### Post by geoff20 on 2015-03-28
Hi,
Having problems with a blue tooth mouse and a blue tooth keyboard.
Intel NUC celeron Baytrail.
Its very difficult to get Ubuntu to recognise the mouse which makes it difficult to work the keyboard.
Both are recognised in the settings for blue tooth and both are indicated as locked but the mouse invariably does not work and I have to use a wireless mouse to reboot which sometimes fixes the problem.
The keyboard sometimes does not respond very quickly.
I have tried both on an Android box and they are recognised and work well.
Is it Ubuntu or the Intel NUC?
Geoff

---

### Post by Vladlenin5000 on 2015-03-28
It is probably the WiFi/Bluetooth driver.

---

### Post by geoff20 on 2015-03-28
Will give that a go

---

### Post by geoff20 on 2015-03-29
Checked drivers, appears they are all up to date.
Tried uninstalling and reinstalling, which worked for a while.Rebooting seems to fix the problem but only for a while.
Any other suggestions?

---

### Post by Vladlenin5000 on 2015-03-29
No, not really... Not without knowing the hardware we're talking about anyway... It really is of little to no importance the form factor or the CPU or... It boils down to the specific WiFi/Bluetooth card you have and the same issues are expected to happen in other platforms, namely notebooks, using the same card, regardless of the base hardware it sits on.

So, if you post info regarding that card, someone might be able to suggest something like staging drivers or whatever...

---

### Post by Geoffrey_Arndt on 2015-03-29
What version of Ubuntu?   Maybe this bluetooth transmitter will provide a solution? [http://www.amazon.com/Panda-Bluetooth-4-0-Nano-Adapter/dp/B00BCU4TZE/ref=sr_1_1?ie=UTF8&qid=1427683365&sr=8-1&keywords=panda+bluetooth+4.0+usb+nano+adapter](http://www.amazon.com/Panda-Bluetooth-4-0-Nano-Adapter/dp/B00BCU4TZE/ref=sr_1_1?ie=UTF8&qid=1427683365&sr=8-1&keywords=panda+bluetooth+4.0+usb+nano+adapter)

---

### Post by geoff20 on 2015-03-31
> **Vladlenin5000 said:**
> No, not really... Not without knowing the hardware we're talking about anyway... It really is of little to no importance the form factor or the CPU or... It boils down to the specific WiFi/Bluetooth card you have and the same issues are expected to happen in other platforms, namely notebooks, using the same card, regardless of the base hardware it sits on..
Sorry for delay , sorting out another problem.
Card details Intel Wireless N, 7260DN. WiFi 802.11bgn. Bluetooth 4.0.

---

### Post by geoff20 on 2015-03-31
> **Geoffrey_Arndt said:**
> What version of Ubuntu?   Maybe this bluetooth transmitter will provide a solution? [http://www.amazon.com/Panda-Bluetooth-4-0-Nano-Adapter/dp/B00BCU4TZE/ref=sr_1_1?ie=UTF8&qid=1427683365&sr=8-1&keywords=panda+bluetooth+4.0+usb+nano+adapter](http://www.amazon.com/Panda-Bluetooth-4-0-Nano-Adapter/dp/B00BCU4TZE/ref=sr_1_1?ie=UTF8&qid=1427683365&sr=8-1&keywords=panda+bluetooth+4.0+usb+nano+adapter)
One of the reason,s I choose a Bluetooth mouse and keyboard was to free up USB ports, but thanks for the suggestion,might have to go down that route.

---

### Post by sandyd on 2015-04-01
Can you post the output of
```

dpkg -l | grep linux-firmware
dmesg | grep -i Bluetooth

```

Thanks

---

### Post by geoff20 on 2015-04-01
2.950805] Bluetooth: Core ver 2.20
[    2.950848] Bluetooth: HCI device and connection manager initialized
[    2.950855] Bluetooth: HCI socket layer initialized
[    2.950860] Bluetooth: L2CAP socket layer initialized
[    2.950870] Bluetooth: SCO socket layer initialized
[    2.982737] Bluetooth: RFCOMM TTY layer initialized
[    2.982753] Bluetooth: RFCOMM socket layer initialized
[    2.982767] Bluetooth: RFCOMM ver 1.11
[    2.984732] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.984738] Bluetooth: BNEP filters: protocol multicast
[    2.984748] Bluetooth: BNEP socket layer initialized
[    3.473929] Bluetooth: hci0: read Intel version: 370710018002030d41
[    3.473935] Bluetooth: hci0: Intel device is already patched. patch num: 41
[    6.742623] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[    6.742638] Bluetooth: HIDP socket layer initialized
[    6.753231] input: Bluetooth Mouse as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/bluetooth/hci0/hci0:256/0005:099A:0500.0001/input/input12
[    6.753775] hid-generic 0005:099A:0500.0001: input,hidraw0: BLUETOOTH HID v1.1b Mouse [Bluetooth Mouse] on a0:a8:cd:07:11:f5
[  174.730163] input: Bluetooth 3.0  Keyboard as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/bluetooth/hci0/hci0:512/0005:099A:0500.0002/input/input13
[  174.731760] hid-generic 0005:099A:0500.0002: input,hidraw1: BLUETOOTH HID v1.1b Keyboard [Bluetooth 3.0

---

### Post by sandyd on 2015-04-02
Some have reported that installing the firmware helps on this card:
```

sudo apt-get install linux-firmware
```

---

### Post by geoff20 on 2015-04-02
With the earlier printout I missed the bit that said this was already installed and have checked that it is the newest version.
Thanks for all your help.
Its been fine so far but if I leave Ubuntu on for a few hours and don't use it the mouse becomes unresponsive but not the keyboard.
I suppose I could shut it down when I'm not using it.

---

### Post by trag on 2015-04-04
If you are using Logitech BT keyboard and mouse, install their BT unified driver

[FONT=Roboto Slab]sudo add-apt-repository ppa:daniel.pavel/solaar[/FONT]
[FONT=Roboto Slab]sudo apt-get update && sudo apt-get install solaar[/FONT]

[FONT=Roboto Slab]Those using GNOME Shell should swap the last command for:[/FONT]

[FONT=Roboto Slab]sudo apt-get update && sudo apt-get install solaar-gnome3

Good Luck
Tragic
[/FONT]

---

### Post by geoff20 on 2015-04-04
Using cheap Chinese ones.
I'm keeping my fingers crossed as the mouse has been fine recently.

---

### Post by Vladlenin5000 on 2015-04-04
> **geoff20 said:**
> Using cheap Chinese ones.
I'm keeping my fingers crossed as the mouse has been fine recently.

Those are often the best because they tend to be more generic.

---

