---
title: "Need some help with python udev"
date: 2018-04-29
forum: Programming Talk
---

### Post by pqwoerituytrueiwoq on 2018-04-29
I am trying to fix a broken python script (worked in 14.04, broke in 18.04)
```
#!/usr/bin/python
import pyudev
#from pprint import pprint
context = pyudev.Context()
for device in context.list_devices(subsystem="hidraw"):
    path = device.device_node;
    parentDevice = device.find_parent("usb", device_type="usb_device")
    print parentDevice
    print ""

```
this will print out this:
```
Device(u'/sys/devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13.4')

Device(u'/sys/devices/pci0000:00/0000:00:14.0/usb3/3-13/3-13.4')

Device(u'/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14')

Device(u'/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8')

```
i want to get the content of a files from lest say:[FONT=courier new]
/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8[/FONT]
```
$ ls /sys/devices/pci0000:00/0000:00:14.0/usb3/3-8
3-8:1.0              bmAttributes        dev          manufacturer  speed
authorized           bMaxPacketSize0     devnum       maxchild      subsystem
avoid_reset_quirk    bMaxPower           devpath      port          uevent
bcdDevice            bNumConfigurations  driver       power         urbnum
bConfigurationValue  bNumInterfaces      ep_00        product       version
bDeviceClass         busnum              idProduct    quirks
bDeviceProtocol      configuration       idVendor     removable
bDeviceSubClass      descriptors         ltm_capable  remove

```
How do i use the library to get the content of a file from there?

---

### Post by pqwoerituytrueiwoq on 2018-04-29
Found a way to do it
```
#!/usr/bin/python

import pyudev

context = pyudev.Context()
for device in context.list_devices(subsystem="hidraw"):
    path = device.device_node;
    parentDevice = device.find_parent("usb", device_type="usb_device")
    print '@ USB Bus',parentDevice["BUSNUM"],'Device',parentDevice["DEVNUM"]
    print "ID_VENDOR:",parentDevice["ID_VENDOR"]
    print "ID_SERIAL:",parentDevice["ID_SERIAL"]
    print "ID_MODEL:",parentDevice["ID_MODEL"]
    #print parentDevice.items() # list of names
    print ""
```

---

