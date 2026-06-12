---
title: "search /sys/bus/usb/devices"
date: 2013-03-30
forum: Programming Talk
---

### Post by hakuch on 2013-03-30
hello, i have a question about searching through /sys/bus/usb/devices :
before my prog would open devices file in /proc/bus/usb but with ubuntu upgrade this file is no longer available.
what i need to acomplish is to search inside /sys/bus/usb/devices folers/files for idVendor and ProdID (both have to match to my hex value - ex:Vendor =12a4 and ProdID=5678 ), if found - a happens, not found b happens.
someone suggested to me to iterate through all subdirectories using opendir, readdir_r and closedir and then try to read idProduct and idVendor using ReadSingleLineFile ... but i am not quite sure how to proceed. Can anyone help me this issue? thanks a lot for help.

---

### Post by schragge on 2013-03-30
I guess you can accomplish this in shell with
```

lsusb -d12a4:5678 >/dev/null && echo Device found || echo Device not found
```
You can see the source code of *lsusb* on github: [https://github.com/gregkh/usbutils/](https://github.com/gregkh/usbutils/)

There's also a bash script [/usr/bin/usb-devices]("http://manpages.ubuntu.com/manpages/precise/en/man1/usb-devices.1.html") that you may want to have a look at. It recursively iterates over */sys/bus/usb/devices/usb**:
```

for device in /sys/bus/usb/devices/usb*
do
        print_device $device 0 0 0
done

```
This script is supposed to be a drop-in replacement for the file *usb/devices*.

Alternatively, if you can mount [debugfs](http://en.wikipedia.org/wiki/Debugfs) then your program will work practically unchanged by evaluating the contents of */sys/kernel/debug/usb/devices*.

---

### Post by hakuch on 2013-03-30
maybe i should explain what is purpose of this action - i have a custom system and 3 different usb devices that could be pluged-in, so after boot i need to see which device is currently plugged and display proper image of this device (system is kind of embeded but running ubuntu kernel 3).
thanks

can not use shell - dont have it installed, have to do it inside c++ application

---

### Post by schragge on 2013-03-30
I've edited my post and added info about *debugfs*.

---

### Post by hakuch on 2013-03-30
schragge - thanks a lot for your suggestion.
normally they would work - but in this system is very minimum setup, so no bash installed and no debug.
so need to find other way to do it.

---

### Post by schragge on 2013-03-30
What I suggested is that you study the source code of the bash script */usr/bin/usb-devices* in order to understand how it works, then write an equivalent code in C++.

---

