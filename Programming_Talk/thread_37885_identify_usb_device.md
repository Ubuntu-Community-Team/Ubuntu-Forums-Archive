---
title: "identify usb device"
date: 2005-05-29
forum: Programming Talk
---

### Post by shortcircuit on 2005-05-29
i have several different types, brands, makes and models of usb devices (drives) and i was wondering if it would be possible to code a method of doing different things with different types of thumb drives

i have a neuros audio computer that works like a usb drive, but the apps to sync music with are all hardcoded to look for the neuros mounted at neuros/ (witch is gay) I also have a normal thumb drive

i want to code an app to automagicly mount a usb device with user specifyed unique descriptors (from lsusb -v) to a different mount point.

i know in ubuntu gnome-vfs does the mounting, udev does the naming, and hotplug does the calling. what i dont know is on what level my app should interface

this is the output from lsusb i wanted to use to trigger the alternate mount point:

[code]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.01
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        16
  idVendor           0x0451 Texas Instruments, Inc.
  idProduct          0x5409
  bcdDevice            0.01
  iManufacturer           1 Digital Innovations
  iProduct                2 NEUROS Digital Audio Device
  iSerial                 3 0A010F030C0A0109060A000D000C0101
  bNumConfigurations      1
[code/]

the serial number seems like a good bit of information to use to identify a unique device

---

### Post by RockyRoads on 2008-06-16
Hi shortcircuit

I know its been a while since you posted this but you might want to check out Sutekh guide for creating mount rules that uniquely ID devices.

Sutekh's guide
[http://ubuntuforums.org/showthread.php?t=168221&highlight=automatically+mount+external+hard+drive]("http://ubuntuforums.org/showthread.php?t=168221&highlight=automatically+mount+external+hard+drive")

---

