---
title: "How to detect a USB Port's speed"
date: 2013-09-04
forum: New to Ubuntu
---

### Post by czgirb on 2013-09-04
Currently I installed **12.04** in **Compaq CQ40** ... so far so good.
But one of my USB port ... **sometimes able to run 2.0, but it mostly detect my FDD as 1.0** only.

When using Windows, if we plugged the FDD, it will automatically detect and inform us if there is something wrong.
So we are able to unplugged and re-plugged again.
But in Ubuntu, I do not know how to detect the FDD.
**Would you mind to guide me how to do so?**
 So, in order to move a HUGE file, it will need not a long time to wait.

Thank you.

---

### Post by zero2xiii on 2013-09-04
Hay,

Not sure what you mean by "detecting" the FDD. (Floppy disk drive? 1.4MB? or those larger black ones... either way around)

You can see speeds by:

```
lsusb -t
```
Example output:
```
~/:~$ lsusb -t
2-1:1.0: No such file or directory
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, **12M**
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, **12M**
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, **12M**
    |__ Port 2: Dev 2, If 0, Class=HID, Driver=usbhid, **12M**
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, **12M**
    |__ Port 1: Dev 2, If 0, Class=vend., Driver=, **12M**
    |__ Port 2: Dev 3, If 0, Class=HID, Driver=usbhid, **1.5M**
    |__ Port 2: Dev 3, If 1, Class=HID, Driver=usbhid, **1.5M**
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, **480M**

```

---

