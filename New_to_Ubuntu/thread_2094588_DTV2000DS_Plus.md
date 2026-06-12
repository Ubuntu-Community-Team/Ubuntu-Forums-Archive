---
title: "DTV2000DS Plus"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by sparx66 on 2012-12-14
Hi there, this is my first attempt at using Ubuntu. (or Linux)
Seems pretty fun. 
MythTV has lots of cool features and I refuse to give up and go back to the dark side.(winXP)

The DTV2000DS Plus doesn't show up as an option when I select DVB DTV Capture Card V3.0. 

Any ideas how I get a driver?

Do I need to update the Kernal? 

I ran the update manager.

lsusb -v gives me:


Bus 003 Device 003: ID 0413:6f12 Leadtek Research, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0413 Leadtek Research, Inc.
  idProduct          0x6f12 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
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

---

