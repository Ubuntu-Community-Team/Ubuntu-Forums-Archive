---
title: "[SOLVED] usbview error"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-04
whenever i fire up usbview i get this error:cannot open the file
/proc/bus/usb/devices,verify that you have usb compiled into your kernel,
have the usb core modules loaded,and have the usbdevfs file system mounted.
i dont understand this error because i use an usb mouse with my laptop,and
i use a 2g memory key with no problem,so what am i to make of this?
i recently had troubles with mounting and permissions for the key,but
they where solved.bad program maybe?:confused:
rick

---

### Post by polmir on 2008-07-04
What is your problem, turn the device into a port usb and write in the terminal ```
sudo lsusb
```and post output.

---

### Post by rixtr66 on 2008-07-04
rick@rick-laptop:~$ sudo lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0461:4d42 Primax Electronics, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
rick@rick-laptop:~$

---

### Post by polmir on 2008-07-04
And what will be the outcome ```
cat /proc/bus/usb/devices
```

---

### Post by rixtr66 on 2008-07-05
No such file or directory.  ???
rick

---

### Post by getglenn on 2008-08-30
if this has truly been SOLVED could you please post the SOLUTION as i am having the same problem?

---

### Post by Honeyisland on 2008-11-30
me too!

---

### Post by adam s on 2008-12-24
This was posted by lostdave in a different thread and solved this exact problem for me.

 Re: USBView error
from the Following List Posting
[https://lists.ubuntu.com/archives/ub...ne/148307.html](https://lists.ubuntu.com/archives/ub...ne/148307.html)

Make sure you have usbfs mounted, which can be found in /etc/fstab, by adding the following line:
Code:

 # <file system> <mount point>   <type>  <options>
 none            /proc/bus/usb   usbfs   defaults

Then 'mount -a' to make sure its mounted. You should now have a /proc/bus/usb directory heirarchy. The "new" udev and libusb will be using /dev/bus/usb, but many applications still use /proc/bus/usb, so we'll mount it until that gets deprecated.

---

