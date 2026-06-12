---
title: "Auto Enginuity OBDII Scan Tool"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by Ingeniator on 2013-05-26
Ok so trying to get this working on my 11.04 install. I'm using wine to run the software but I'm having trouble with the OBDII adapter(Proline VCI). I cleared the dmesg and ran the following.
Before Plugging in USB
```
******-MBP:~$ dmesg | tail
******-MBP:~$ lsusb
Bus 002 Device 004: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 002 Device 003: ID 05ac:8507 Apple, Inc. 
Bus 002 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 008: ID 05ac:8218 Apple, Inc. 
Bus 001 Device 005: ID 05ac:8403 Apple, Inc. 
Bus 001 Device 004: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

After plugging in USB
```
******-MBP:~$ dmesg | tail
[B][10501.046225] usb 1-1.4: new full speed USB device using ehci_hcd and address 20
[10501.439203] generic-usb 0003:1AA0:0008.0015: hiddev0,hidraw3: USB HID v1.00 Device [AutoEnginuity LLC ProLine VCI] on usb-0000:00:1a.7-1.4/input0[/B]
******-MBP:~$ lsusb
Bus 002 Device 004: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 002 Device 003: ID 05ac:8507 Apple, Inc. 
Bus 002 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 020: ID 1aa0:0008**  
Bus 001 Device 008: ID 05ac:8218 Apple, Inc. 
Bus 001 Device 005: ID 05ac:8403 Apple, Inc. 
Bus 001 Device 004: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Then lsusb -d -v 1aa0:0008 returns
```
******-MBP:~$ lsusb -v -d 1aa0:0008

Bus 001 Device 020: ID 1aa0:0008  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.01
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
[B]  idVendor           0x1aa0 
  idProduct          0x0008 [/B]
  bcdDevice            2.00
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
    iConfiguration          1 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
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
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)


```

So what I'm looking to do is get the device recognised by ubuntu so that the program can see it in wine. I think the problem may be with the device class but I'm out of my depth and could use some input.

Thanks

---

### Post by Ingeniator on 2013-05-28
No ideas? If someone can interpret why the default usb driver doesn't comunicate/find it. I can go from there.

---

