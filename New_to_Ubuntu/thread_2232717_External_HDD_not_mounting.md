---
title: "External HDD not mounting"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by chasdev on 2014-07-03
Hi,
I have a USB external HDD that won't mount (or even appear as a device) in Ubuntu 14.04. (It's a 2TB Samsung, NTFS). When I plug it in, the drive light comes on for maybe a minute, then goes out. Manual mounting doesn't help; fdisk and parted don't even see the drive.
I'd be grateful for any help!
Here's the information I've collected so far:

Output of lsb_release -a:
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


```

Output of dmesg | tail after connecting the drive:

```
 1999.133429] usb 3-4: new high-speed USB device number 8 using xhci_hcd
[ 1999.133518] usb 3-4: Device not responding to set address.
[ 1999.337576] usb 3-4: Device not responding to set address.
[ 1999.541589] usb 3-4: device not accepting address 8, error -71
[ 1999.837791] usb 3-4: new high-speed USB device number 10 using xhci_hcd
[ 1999.859140] usb 3-4: New USB device found, idVendor=04e8, idProduct=6014
[ 1999.859144] usb 3-4: New USB device strings: Mfr=1, Product=11, SerialNumber=3
[ 1999.859147] usb 3-4: Product: Samsung G3 Station
[ 1999.859149] usb 3-4: Manufacturer: JMicron
[ 1999.859151] usb 3-4: SerialNumber: 00000011E10EB
[ 1999.980609] usb-storage 3-4:1.0: USB Mass Storage device detected
[ 1999.980654] scsi6 : usb-storage 3-4:1.0
[ 1999.980718] usbcore: registered new interface driver usb-storage
[ 2000.071382] usb 3-4: USB disconnect, device number 10

```

Output of lsusb -v: (while the drive light is still on!)
```


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x8000 
  bcdDevice            0.05
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              12


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12


Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x8008 
  bcdDevice            0.05
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         3 
  bMaxPacketSize0         9
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0003 3.0 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           31
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
        bMaxBurst               0


Bus 003 Device 006: ID 8087:07dc Intel Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          224 Wireless
  bDeviceSubClass         1 Radio Frequency
  bDeviceProtocol         1 Bluetooth
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x07dc 
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          177
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0009  1x 9 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0011  1x 17 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0019  1x 25 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0021  1x 33 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       224 Wireless
      bInterfaceSubClass      1 Radio Frequency
      bInterfaceProtocol      1 Bluetooth
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0031  1x 49 bytes
        bInterval               1


Bus 003 Device 005: ID 06cb:0ac3 Synaptics, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x06cb Synaptics, Inc.
  idProduct          0x0ac3 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           41
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              144mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     572
         Report Descriptors: 
           ** UNAVAILABLE**
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1


Bus 003 Device 004: ID 0424:7500 Standard Microsystems Corp. LAN7500 Ethernet 10/100/1000 Adapter
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol       255 
  bMaxPacketSize0        64
  idVendor           0x0424 Standard Microsystems Corp.
  idProduct          0x7500 LAN7500 Ethernet 10/100/1000 Adapter
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               1


Bus 003 Device 007: ID 0bda:573c Realtek Semiconductor Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.01
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x0bda Realtek Semiconductor Corp.
  idProduct          0x573c 
  bcdDevice           39.02
  iManufacturer           3 
  iProduct                1 
  iSerial                 2 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          706
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    ** UNRECOGNIZED:  28 ff 42 49 53 54 00 01 06 06 10 00 00 00 00 00 01 07 f4 01 02 08 f4 01 03 09 f4 01 04 0a f4 01 05 0b f4 01 06 0c e8 03
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               5 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              5 
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength          107
        dwClockFrequency       15.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x0000000e
          Auto-Exposure Mode
          Auto-Exposure Priority
          Exposure Time (Absolute)
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 2
        bSourceID               1
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000157f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x 9
          None
          SECAM - 625/50
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               4
        iTerminal               0 
      VideoControl Interface Descriptor:
        bLength                27
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 4
        guidExtensionCode         {8ca72912-b447-9440-b0ce-db07386fb938}
        bNumControl             2
        bNrPins                 1
        baSourceID( 0)          7
        bControlSize            2
        bmControls( 0)       0x00
        bmControls( 1)       0x06
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                29
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 7
        guidExtensionCode         {c385b80f-c268-4745-90f7-8f47579d95fc}
        bNumControl             0
        bNrPins                 1
        baSourceID( 0)          2
        bControlSize            4
        bmControls( 0)       0x0f
        bmControls( 1)       0x00
        bmControls( 2)       0x00
        bmControls( 3)       0x00
        iExtension              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               6
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
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
        INTERFACE CLASS:  0f 24 01 02 f9 01 81 00 03 02 01 00 01 00 00
        INTERFACE CLASS:  1b 24 04 01 0b 59 55 59 32 00 00 10 00 80 00 00 aa 00 38 9b 71 10 01 00 00 00 00
        INTERFACE CLASS:  1e 24 05 01 00 80 02 e0 01 00 00 ca 08 00 00 ca 08 00 60 09 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 02 00 a0 00 78 00 00 a0 8c 00 00 a0 8c 00 00 96 00 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 03 00 b0 00 90 00 00 a0 b9 00 00 a0 b9 00 00 c6 00 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 04 00 40 01 b4 00 00 e0 a5 01 00 e0 a5 01 00 c2 01 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 05 00 40 01 f0 00 00 80 32 02 00 80 32 02 00 58 02 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 06 00 60 01 20 01 00 80 e6 02 00 80 e6 02 00 18 03 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 07 00 a8 01 f0 00 00 50 e9 02 00 50 e9 02 00 1b 03 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 08 00 80 02 68 01 00 80 97 06 00 80 97 06 00 08 07 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 09 00 50 03 e0 01 00 40 a5 0b 00 40 a5 0b 00 6c 0c 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 05 0a 00 00 05 d0 02 00 00 ca 08 00 00 ca 08 00 20 1c 00 40 42 0f 00 01 40 42 0f 00
        INTERFACE CLASS:  1e 24 05 0b 00 80 02 e0 01 00 00 ca 08 00 00 ca 08 00 60 09 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  0a 24 03 00 01 00 05 d0 02 00
        INTERFACE CLASS:  06 24 0d 01 01 04
        INTERFACE CLASS:  0b 24 06 02 03 01 01 00 00 00 00
        INTERFACE CLASS:  1e 24 07 01 00 00 05 d0 02 00 00 5e 1a 00 00 5e 1a 00 20 1c 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 07 02 00 c0 03 1c 02 00 e0 d4 0e 00 e0 d4 0e 00 d2 0f 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  1e 24 07 03 00 00 05 d0 02 00 00 5e 1a 00 00 5e 1a 00 20 1c 00 15 16 05 00 01 15 16 05 00
        INTERFACE CLASS:  0a 24 03 00 01 00 05 d0 02 00
        INTERFACE CLASS:  06 24 0d 01 01 04


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.13
  iManufacturer           3 
  iProduct                2 
  iSerial                 1 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Datae
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12




```

---

### Post by TheFu on 2014-07-03
Unplug all other USB devices and try again.
Try a different port.

Some HDDs just don't work with some USB hubs/ports. Did this ever work on this machine, with this port?  Basically, what has changed?

I have a 10.04 x64 machine with USB3 via add-in card that only does USB3 speeds with directly connected storage, never through a reputable USB3 hub. There is a firmware update available, but only from Windows and only over a USB3 port (which I don't have on the same computer).  The company offered to send a replacement, but returning it is a hassle. Someday I'll get to a friend's house with Windows AND USB3 to load the firmware ... it has been almost a year now.

**See update on next page!  My USB3 card and hub are working great now.** EHCI disabled.

---

### Post by chasdev on 2014-07-04
Thanks for these suggestions, I'll try them when I get a chance, and report back.
Yes, the drive did previously work on this machine and port. What changed was the drive fell off the tower case:frown: (about 2ft onto carpet). I'll be happy if I can just recover the data, even if the drive is toast...

---

### Post by Impavidus on 2014-07-04
Depending on the type of external drive (a box with an ordinary drive inside?) it may be a loose connector inside the external drive's outer casing. In this case it should be possible to open the outer casing and properly reconnect the drive. If your carpet is soft enough the drive itself should still work. If it happened whilst the drive was spinning there could be more damage.

---

### Post by TheFu on 2014-07-04
I had a 2 hr old HDD fall off the PCcase - I'd connected it temporarily via an external USB/SATA connector and laid it on top. It never worked again.  Fortunately, my CC had damage replacement if it happened in the 1st 90 days. They refunded the price immediately.

Hopefully, you can get a replacement under the CC replacement or you can pull the HDD out of the case and connect it internally. Worst case, your backup will have to do until a replacement drive is available.

---

