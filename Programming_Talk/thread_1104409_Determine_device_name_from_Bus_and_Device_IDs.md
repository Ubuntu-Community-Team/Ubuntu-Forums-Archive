---
title: "Determine device name from Bus and Device IDs"
date: 2009-03-23
forum: Programming Talk
---

### Post by BillRebey on 2009-03-23
I'm using some RS232-USB dongles on an Ubuntu box, and am interfacing with them in a C program.  I need to be able to detect when a dongle in inserted/removed.  

Is there a signal/event/etc. that I can handle to notify my of the insertion/removal?  

I'm using libusb to interact with the devices, and I can use libusb to get a list of installed devices.  From this list I can determine the Bus and DeviceID of each attached device, but I can't figure out how to equate that Bus/ID pair to a device name suitable for "open(...)", such as "/dev/ttyUSB0".  

How can I figure out which "/dev/ttyUSBxxx" device a given Bus/DevID is attached to?

---

