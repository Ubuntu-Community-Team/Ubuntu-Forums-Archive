---
title: "CLS USB Gamepad not working with Ubuntu 13.04"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by 7KpHN4w on 2013-09-03
Hello World!

I am an absolute beginner in linux and got problems with my gamepad.
I have two nearly equal gamepads, but just one is detected as a gamepad. My Windows detects both correctly.
Gamepad 1 works fine. Gamepad 2 doesn't work.
It does'nt create the /dev/input/js0 file.

I use Ubuntu 13.04 on my Acer C710 Chromebook.

Gamepad 1:
- Front: [http://u75.img-up.net/CSL_C180_Vb178.jpg](http://u75.img-up.net/CSL_C180_Vb178.jpg)
- Back: [http://s06.img-up.net/CSL_C180_Ve470.jpg](http://s06.img-up.net/CSL_C180_Ve470.jpg)
- lsusb: ID 0e8f:310d GreenAsia Inc.
- dmesg:[INDENT][ 1098.842465] usb 2-1.4: new full-speed USB device number 8 using ehci_hcd
    [ 1098.928385] usb 2-1.4: New USB device found, idVendor=0e8f, idProduct=310d
    [ 1098.928396] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
    [ 1098.928403] usb 2-1.4: Product: GAMEPAD 3 TURBO
    [ 1098.928408] usb 2-1.4: Manufacturer: SZMY-POWER CO.,LTD.
    [ 1098.930153] input: SZMY-POWER CO.,LTD. GAMEPAD 3 TURBO as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input15
    [ 1098.930556] generic-usb 0003:0E8F:310D.0006: input,hidraw0: USB HID v1.10 Gamepad [SZMY-POWER CO.,LTD. GAMEPAD 3 TURBO] on usb-0000:00:1d.0-1.4/input0[/INDENT]

Gamepad 2:
- Front: [http://h23.img-up.net/CSL_C180_V84f0.jpg](http://h23.img-up.net/CSL_C180_V84f0.jpg)
- Back: [http://n41.img-up.net/CSL_C180_V97d9.jpg](http://n41.img-up.net/CSL_C180_V97d9.jpg)
- lsusb: ID 0e8f:0003 GreenAsia Inc. MaxFire Blaze2
- dmesg:[INDENT][ 1139.854531] usb 2-1.4: new full-speed USB device number 9 using ehci_hcd
    [ 1139.940879] usb 2-1.4: New USB device found, idVendor=0e8f, idProduct=0003
    [ 1139.940890] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
    [ 1139.940897] usb 2-1.4: Product: 2In1 USB Joystick
    [ 1139.940902] usb 2-1.4: Manufacturer: MY-POWER CO.,LTD.[/INDENT]

How can I get my gamepad to work?

):P

---

### Post by 7KpHN4w on 2013-09-04
Nobody can help me? Do you need more information?

---

### Post by liankesm on 2013-10-23
i'm having the same problem

---

### Post by 7KpHN4w on 2013-12-23
I still have that problem. If nobody helps linux beginners, they will went back to windows...
Why aren't you helping us to get into linux?

---

