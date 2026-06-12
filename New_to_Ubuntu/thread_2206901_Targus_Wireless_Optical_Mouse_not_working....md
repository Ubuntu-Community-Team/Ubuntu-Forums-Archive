---
title: "Targus Wireless Optical Mouse not working..."
date: 2014-02-21
forum: New to Ubuntu
---

### Post by SWGraphics291 on 2014-02-21
I have been using my Targus mouse for a while now and I was'nt noticing any problems at all. But then today it suddenly went. I thought the battery was dead, which it was, so I got some new ones and put the in it. However, there was no difference.

I ran:
```
lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b209 Chicony Electronics Co., Ltd 
Bus 002 Device 012: ID 4168:1011 

```

and I think the mouse is Bus 002 Device 012: ID 4168:1011 because I ran lsusb without it plugged in and wallah, it disappeared.

I have also tried dmesg | tail -20:
```
dmesg | tail -20
[  569.106666] usb 2-1.1: New USB device found, idVendor=4168, idProduct=1011
[  569.106672] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  569.106675] usb 2-1.1: Product: Targus Wireless Optical Mouse
[  569.106679] usb 2-1.1: Manufacturer: reserved
[  569.109759] input: reserved Targus Wireless Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input15
[  569.110572] hid-generic 0003:4168:1011.0004: input,hiddev0,hidraw0: USB HID v1.11 Mouse [reserved Targus Wireless Optical Mouse] on usb-0000:00:1d.0-1.1/input0
[  575.297743] usb 2-1.1: USB disconnect, device number 7
[  671.954867] usbcore: deregistering interface driver usbhid
[  688.453018] usb 2-1.1: new full-speed USB device number 8 using ehci_hcd
[  688.548230] usb 2-1.1: New USB device found, idVendor=4168, idProduct=1011
[  688.548236] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  688.548240] usb 2-1.1: Product: Targus Wireless Optical Mouse
[  688.548243] usb 2-1.1: Manufacturer: reserved
[  688.565594] input: reserved Targus Wireless Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input16
[  688.566670] hid-generic 0003:4168:1011.0005: input,hiddev0,hidraw0: USB HID v1.11 Mouse [reserved Targus Wireless Optical Mouse] on usb-0000:00:1d.0-1.1/input0
[  688.567395] usbcore: registered new interface driver usbhid
[  688.567399] usbhid: USB HID core driver
[  739.430017] tg3 0000:01:00.0: eth0: Link is up at 100 Mbps, full duplex
[  739.430024] tg3 0000:01:00.0: eth0: Flow control is on for TX and on for RX
[  739.431122] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

And it's only this usb device that does'nt work, I have tried different ports. Please help...

---

### Post by SWGraphics291 on 2014-02-21
This should be in General Help, sorry.

---

