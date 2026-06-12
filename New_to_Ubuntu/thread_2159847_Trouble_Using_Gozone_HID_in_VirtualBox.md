---
title: "Trouble Using Gozone HID in VirtualBox"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by fgrinst on 2013-07-04
Hi all,

I'm trying to use a Virgin Healthmiles Gozone HID on my laptop running 12.0.4. There is no software for Ubuntu, so I installed Windows XP using VirtualBox.

Unfortunately, neither Ubuntu or XP recognize the HID when it is attached via USB cable. I can read USB flash drives in VirtualBox without any problems by creating a filter. I think I'm missing the drivers required to make let Ubuntu recognize the device, but I'm not sure. 

Here is the command line output for lsusb -v:

Bus 004 Device 005: ID 1125:2000  
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x1125 
  idProduct          0x2000 
  bcdDevice            0.5e
  iManufacturer           0 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               20mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      28
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1

Any help is greatly appreciated. Thanks!

---

