---
title: "Can't copy some files from Nokia Lumia 710"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by Matt92HUN on 2013-09-24
First it didn't let me copy half of the pictures, now it says the phone is empty, whiles it isn't, I can still view the pictures on it.

---

### Post by peertje on 2013-09-25
Does it come up as a device on your desktop when you connect to it?

When you have it connected, what is the output of:
```
lsusb
```

Post the results here.

---

### Post by peertje on 2013-09-25
Does it come up as a device on your desktop when you connect to it?

When you have it connected, what is the output of:
```
lsusb
```

Post the results here.

---

### Post by Matt92HUN on 2013-09-28
Bus 003 Device 002: ID 0458:00f0 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 002: ID 0d8c:0103 C-Media Electronics, Inc. CM102-A+/102S+ Audio Controller
Bus 006 Device 002: ID 045e:04ec Microsoft Corp. Windows Phone (Zune)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by peertje on 2013-09-30
What's the output of
```
dmesg | tail
lsusb -v -d 045e:04ec
```
just after you connected your phone?

---

### Post by Matt92HUN on 2013-10-01
```
[ 1160.740018] usb 2-2: new high-speed USB device number 5 using ehci-pci
[ 1161.148016] usb 2-2: device not accepting address 5, error -71
[ 1161.148034] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1161.616018] usb 6-2: new full-speed USB device number 2 using uhci_hcd
[ 1162.043042] usb 6-2: not running at top speed; connect to a high speed hub
[ 1162.067040] usb 6-2: New USB device found, idVendor=045e, idProduct=04ec
[ 1162.067045] usb 6-2: New USB device strings: Mfr=0, Product=8, SerialNumber=9
[ 1162.067049] usb 6-2: Product: RM-803|NOKIA Lumia 710
[ 1162.067053] usb 6-2: SerialNumber: 99461300-b56a-0801-d579-3fd97732e2b2
[ 1163.011639] systemd-hostnamed[3169]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!

```
and
```
Bus 006 Device 002: ID 045e:04ec Microsoft Corp. Windows Phone (Zune)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x045e Microsoft Corp.
  idProduct          0x04ec Windows Phone (Zune)
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                8 RM-803|NOKIA Lumia 710
  iSerial                 9 99461300-b56a-0801-d579-3fd97732e2b2
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           62
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

---

