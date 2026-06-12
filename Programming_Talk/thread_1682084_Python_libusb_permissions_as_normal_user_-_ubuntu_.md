---
title: "Python libusb permissions as normal user - ubuntu 10.10"
date: 2011-02-05
forum: Programming Talk
---

### Post by gratzimilian on 2011-02-05
I have a python script which employs pyusb to scan connected usb devices matching against a specific device 0403:6001 which is an FTDI USB to RS232 converter but this seems to require being run as root. Here is the portion of the script that fails:

...
if device != None:
    handle = None
    handle = device.open()
    if handle != None:
        print "Vendor: %s - %s" % (hex(device.idVendor), handle.getString(device.iManufacturer, 30))
        print "Product: %s - %s" % (hex(device.idProduct), handle.getString(device.iProduct, 30))
        print "Serial: %s" % handle.getString(device.iSerialNumber, 30)

Producing the following error:

Traceback (most recent call last):
  File "test.py", line 28, in <module>
    print "Vendor: %s - %s" % (hex(device.idVendor), handle.getString(device.iManufacturer, 30))
usb.USBError: error sending control message: Operation not permitted

As mentioned when running as root this works fine but I need it to run as a standard user. I have checked the permissions of the device with this:

$ ls -s /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 2011-02-05 13:33 /dev/ttyUSB0

And the user account is a member of dialout (and tty, and plugdev) but still I get the permission denied error..

I have read about setting up udev rules for this and have tried many variations but it seems to have the correct permissions and groups anyway..?

I also read an article about modem-manager taking control of serial devices and that removing this may work but it didn't for me.. Any ideas?

Thanks

---

### Post by gratzimilian on 2011-02-05
Ok so I figured out that it's related to file permissions in that doing the following then allowed the user to communicate with the device:

$ ls -l /dev/bus/usb/005/006

crw-rw-r-- 1 root root 189, 517 2011-02-05 17:44 /dev/bus/usb/005/006

So I temporarily granted other access and the script will run as a normal user:

$ sudo chmod o+rw /dev/bus/usb/005/006

Where as before I was trying to modify /dev/ttyUSB0 permissions.

I guess I need to sort out some udev rule for this now..

---

### Post by gratzimilian on 2011-02-05
If anyone is interested.. fixed with udev rule:

SUBSYSTEM=="usb", ATTRS{idVendor}=="0403", GROUP="dialout"

then reloaded udev rules:

$ udevadm control --reload-rules

---

