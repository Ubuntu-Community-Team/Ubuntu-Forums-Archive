---
title: "mouse recognized but not working"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by reeseslover531 on 2008-11-14
So I am using an x61 on Hardy and when I connect an internal mouse it seems to be recognized in dmesg.
```
[  417.353709] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  417.531106] usb 3-2: configuration #1 chosen from 1 choice
[  417.540964] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input28
[  417.589569] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[  417.595459] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.1/input/input29
[  417.646262] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2

``` 
but The mouse does nothing, I can still use the mouse built into the laptop, but the external one does not work.  Can anyone help me out?? thanks!

---

### Post by sharke on 2008-11-14
> **reeseslover531 said:**
> So I am using an x61 on Hardy and when I connect an internal mouse it seems to be recognized in dmesg.
```
[  417.353709] usb 3-2: new full speed USB device using uhci_hcd and address 2
[  417.531106] usb 3-2: configuration #1 chosen from 1 choice
[  417.540964] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input28
[  417.589569] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[  417.595459] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.1/input/input29
[  417.646262] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2

``` 
but The mouse does nothing, I can still use the mouse built into the laptop, but the external one does not work.  Can anyone help me out?? thanks!

I had same problem on my desktop comp fixed it by activating USB Legacy Support in the Bios.

Cheers
Sharke

---

