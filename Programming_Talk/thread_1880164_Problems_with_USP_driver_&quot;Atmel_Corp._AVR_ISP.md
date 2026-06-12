---
title: "Problems with USP driver &quot;Atmel Corp. AVR ISP mkII&quot;"
date: 2011-11-13
forum: Programming Talk
---

### Post by ritchie-w on 2011-11-13
Hello,

I have a problem with the driver USB driver "Atmel Corp. AVR ISP mkII".

When is connect the programmer, I will have the following usb device availiable.

> 
Bus 002 Device 008: ID 03eb:2104 Atmel Corp. AVR ISP mkII


But after access this device once, via "avrdude" or a VMWare system using the AVR Studio, the driver is gone. I tried this with the kUbuntu 32Bit/64bit Version.

Any help for me ?

R.

---

### Post by ritchie-w on 2011-12-05
Hi,

does somebody may know, what this means, because this messages where log in the system log during trying to connect to the USB programmer.

```

05.12.2011 22:17:14	XXX	kernel	[ 2706.061782] usb 2-1.2: new full speed USB device number 9 using ehci_hcd
05.12.2011 22:17:29	XXX	kernel	[ 2721.090828] usb 2-1.2: device descriptor read/64, error -110
05.12.2011 22:17:44	XXX	kernel	[ 2736.223606] usb 2-1.2: device descriptor read/64, error -110
05.12.2011 22:17:44	XXX	kernel	[ 2736.399090] usb 2-1.2: new full speed USB device number 10 using ehci_hcd
05.12.2011 22:17:59	XXX	kernel	[ 2751.428123] usb 2-1.2: device descriptor read/64, error -110
05.12.2011 22:18:14	XXX	kernel	[ 2766.560901] usb 2-1.2: device descriptor read/64, error -110
05.12.2011 22:18:15	XXX	kernel	[ 2766.736398] usb 2-1.2: new full speed USB device number 11 using ehci_hcd
05.12.2011 22:18:25	XXX	kernel	[ 2777.114542] usb 2-1.2: device not accepting address 11, error -110
05.12.2011 22:18:25	XXX	kernel	[ 2777.186462] usb 2-1.2: new full speed USB device number 12 using ehci_hcd
05.12.2011 22:18:35	XXX	kernel	[ 2787.564661] usb 2-1.2: device not accepting address 12, error -110
05.12.2011 22:18:35	XXX	kernel	[ 2787.564830] hub 2-1:1.0: unable to enumerate USB device on port 2

```

The following rule file exists for usb devices

/etc/udev/rules.d/80-usbprog.rules
with the following content:
```

ATTR{idVendor}=="03eb", ATTR{idProduct}=="2104", GROUP="plugdev", MODE="0660" # AVRISP mkII

```

The command "$ lsusb -s 0013 -vv" gives the following output
```

Bus 002 Device 013: ID 03eb:2104 Atmel Corp. AVR ISP mkII
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03eb Atmel Corp.
  idProduct          0x2104 AVR ISP mkII
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
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
Device Status:     0x0000
  (Bus Powered)

```


Any hint to get rid of this problem ?

The programmer works fine with a normal windows XP installation and AVR Studio 5.

I am using the latest kernel version:
Linux XXX 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


Greating R.

---

### Post by ritchie-w on 2011-12-29
The supllier told me, that it is a problem of the product.

The "Diamex ALL-AVR Programmer adapter for AVR Controller" does not support the linux OS up to now.

There will work on it (maybe).

Thanks
   R.

---

### Post by Spirail on 2012-03-29
This is NOT solved here. 
I have had this working on Ubuntu before. But that was last year. I have since upgraded to 11.10 and no such luck these days. 


Wish i remember what i did (if that is still valid)

---

### Post by ritchie-w on 2012-04-21
Hi,

you are right, this "Atmel Corp. AVR ISP mkII" is still not working inside my VMware.

I try to use the programmer inside a VMWare under (guest OS) windows, which is running on kubuntu 11.10 (as host os).


I thought after a BIOS Update of the programmer is will work, but it didn't.

Regards
R.

---

