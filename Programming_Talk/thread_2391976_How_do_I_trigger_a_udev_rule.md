---
title: "How do I trigger a udev rule?"
date: 2018-05-15
forum: Programming Talk
---

### Post by andremanteimsn.com on 2018-05-15
I have a barcode scanner, and I would like to run a script when I connect it.
With the command 
   

    udevadm info -ap /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/tty/ttyACM0

 
I get information about the device. Here is an excerpt:

      looking at parent device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5':
        KERNELS == "2-1.5"
        SUBSYSTEMS == "usb"
        DRIVERS == "usb"
        ATTRS {authorized} == "1"
    ...

Now I've created a new file under / etc / udev / rules /:

    rzha097: /etc/udev/rules.d # cat 90-barcode.rules
    KERNELS == "2-1.5", SUBSYSTEMS == "usb", ACTION == "add", RUN + = "/home/iuk323/authorun.sh"

Unfortunately, the autorun.sh script is not running. Could someone give me a hint why this did not happen? 

The autorun script has sufficient permissions.

---

### Post by jeremy31 on 2018-05-15
It could be a typ0 RUN + = "/home/iuk323/authorun.sh"  did you want RUN + = "/home/iuk323/autorun.sh"



```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0a5c", ATTRS{idProduct}=="217f", RUN + = "/home/iuk323/autorun.sh"
```Replace the 0a5c and 217f with the data from lsusb results for the scanner

---

### Post by andremanteimsn.com on 2018-05-16
What ? Where is the difference ? I don't get it

---

