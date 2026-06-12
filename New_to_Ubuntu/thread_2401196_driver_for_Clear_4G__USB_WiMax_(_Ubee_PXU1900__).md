---
title: "driver for Clear 4G  USB WiMax ( Ubee PXU1900  )"
date: 2018-09-14
forum: New to Ubuntu
---

### Post by salem1870 on 2018-09-14
Hi all I have this USB fro long time it's [Clear 4G usb stick]("http://i46.tinypic.com/1zdb51x.jpg") (its actually Ubee PXU1900 chip  )
this is output of lsusb 

```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 011: ID 0489:e016 Foxconn / Hon Hai Ubee PXU1900 WiMAX Adapter [Beceem BCSM250]
Bus 003 Device 007: ID 1c4f:0034 SiGma Micro 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I don't know about other countries but we still have (   WiMAX network running ) , 
and I already tried this stick on Windows with (our ISP connection software ) and it's works .
I tried to install Windows driver using ndiswrapper and ndiswrapper shows me it's installed 
```
bcmbusctr_64 : driver installed
    device (0489:E016) present

```
 
```
$ lsusb -vd 0489:e016


Bus 003 Device 011: ID 0489:e016 Foxconn / Hon Hai Ubee PXU1900 WiMAX Adapter [Beceem BCSM250]
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0489 Foxconn / Hon Hai
  idProduct          0xe016 Ubee PXU1900 WiMAX Adapter [Beceem BCSM250]
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          111
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           6
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           6
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               6

```

> dmesg -T
```
[Fri Sep 14 21:43:40 2018] intel_pstate: Turbo disabled by BIOS or unavailable on processor
[Fri Sep 14 21:43:51 2018] intel_pstate: Turbo disabled by BIOS or unavailable on processor
[Fri Sep 14 21:46:11 2018] intel_pstate: Turbo disabled by BIOS or unavailable on processor
[Fri Sep 14 21:52:45 2018] intel_pstate: Turbo disabled by BIOS or unavailable on processor
[Fri Sep 14 22:02:53 2018] usb 3-2: USB disconnect, device number 3
[Fri Sep 14 22:02:58 2018] usb 3-2: new high-speed USB device number 8 using xhci_hcd
[Fri Sep 14 22:02:58 2018] usb 3-2: New USB device found, idVendor=198f, idProduct=0210
[Fri Sep 14 22:02:58 2018] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[Fri Sep 14 22:02:58 2018] usb 3-2: Product: USBw25100
[Fri Sep 14 22:02:58 2018] usb 3-2: Manufacturer: Beceem Communications
[Fri Sep 14 22:02:58 2018] usb 3-2: SerialNumber: AAA99M25JQ
[Fri Sep 14 22:17:00 2018] usb 3-2: USB disconnect, device number 8
[Fri Sep 14 22:18:02 2018] usb 3-2: new full-speed USB device number 9 using xhci_hcd
[Fri Sep 14 22:18:03 2018] usb 3-2: new high-speed USB device number 10 using xhci_hcd
[Fri Sep 14 22:18:03 2018] usb 3-2: New USB device found, idVendor=198f, idProduct=0210
[Fri Sep 14 22:18:03 2018] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[Fri Sep 14 22:18:03 2018] usb 3-2: Product: USBw25100
[Fri Sep 14 22:18:03 2018] usb 3-2: Manufacturer: Beceem Communications
[Fri Sep 14 22:18:03 2018] usb 3-2: SerialNumber: AAA99M25JQ
[Fri Sep 14 22:49:47 2018] usb 3-2: USB disconnect, device number 10
[Fri Sep 14 22:51:08 2018] audit: type=1400 audit(1536958269.087:50): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/usr/local/lib/libpcre.so.3.13.2" pid=5306 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[Fri Sep 14 22:51:08 2018] audit: type=1400 audit(1536958269.123:51): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/usr/local/lib/libpcre.so.3.13.2" pid=5311 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[Fri Sep 14 22:51:36 2018] intel_pstate: Turbo disabled by BIOS or unavailable on processor
[Fri Sep 14 22:53:18 2018] usb 3-2: new high-speed USB device number 11 using xhci_hcd
[Fri Sep 14 22:53:18 2018] usb 3-2: New USB device found, idVendor=0489, idProduct=e016
[Fri Sep 14 22:53:18 2018] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[Fri Sep 14 22:53:18 2018] usb 3-2: Product: Clear 4G Mobile USB - PXU190
[Fri Sep 14 22:53:18 2018] usb 3-2: Manufacturer: Ubee Interactive
[Fri Sep 14 22:53:18 2018] usb 3-2: SerialNumber: USB_SN_1
[Fri Sep 14 23:18:15 2018] audit: type=1400 audit(1536959895.611:52): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/usr/local/lib/libpcre.so.3.13.2" pid=6084 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[Fri Sep 14 23:25:14 2018] intel_pstate: Turbo disabled by BIOS or unavailable on processor
[Fri Sep 14 23:38:28 2018] Bluetooth: hci0: last event is not cmd complete (0x0f)
[Fri Sep 14 23:41:02 2018] audit: type=1400 audit(1536961263.575:53): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/usr/local/lib/libpcre.so.3.13.2" pid=14176 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[Fri Sep 14 23:41:24 2018] Bluetooth: hci0: last event is not cmd complete (0x0f)
[Sat Sep 15 00:04:55 2018] audit: type=1400 audit(1536962696.215:54): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/usr/local/lib/libpcre.so.3.13.2" pid=14342 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[Sat Sep 15 00:28:37 2018] audit: type=1400 audit(1536964118.151:55): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/usr/local/lib/libpcre.so.3.13.2" pid=14496 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[Sat Sep 15 00:37:39 2018] usb 3-2: USB disconnect, device number 11
[Sat Sep 15 00:37:54 2018] usb 3-2: new high-speed USB device number 12 using xhci_hcd
[Sat Sep 15 00:37:54 2018] usb 3-2: New USB device found, idVendor=0489, idProduct=e016
[Sat Sep 15 00:37:54 2018] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[Sat Sep 15 00:37:54 2018] usb 3-2: Product: Clear 4G Mobile USB - PXU190
[Sat Sep 15 00:37:54 2018] usb 3-2: Manufacturer: Ubee Interactive
[Sat Sep 15 00:37:54 2018] usb 3-2: SerialNumber: USB_SN_1
[Sat Sep 15 00:37:54 2018] usb 3-2: USB disconnect, device number 12
[Sat Sep 15 00:37:55 2018] usb 3-2: new high-speed USB device number 13 using xhci_hcd
[Sat Sep 15 00:37:55 2018] usb 3-2: New USB device found, idVendor=0489, idProduct=e016
[Sat Sep 15 00:37:55 2018] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[Sat Sep 15 00:37:55 2018] usb 3-2: Product: Clear 4G Mobile USB - PXU190
[Sat Sep 15 00:37:55 2018] usb 3-2: Manufacturer: Ubee Interactive
[Sat Sep 15 00:37:55 2018] usb 3-2: SerialNumber: USB_SN_1
[Sat Sep 15 00:37:55 2018] intel_pstate: Turbo disabled by BIOS or unavailable on processor



```

---

