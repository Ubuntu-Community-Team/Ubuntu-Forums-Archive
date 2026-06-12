---
title: "webcam help dmesg output"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by muted1987 on 2008-04-27
hey guys anyone help with this 

[40448.605144] usb 2-2: new full speed USB device using uhci_hcd and address 6
[40448.791900] usb 2-2: configuration #1 chosen from 1 choice
[40448.794835] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0323) 
[40685.413269] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[40685.413326] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[40685.413359] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[40862.781154] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[40867.780380] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[40877.776738] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (1)
[40877.776793] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[41286.690165] usb 2-2: USB disconnect, address 6

---

### Post by janmartin on 2008-04-27
By chance, do you have an Acer Laptop?

Try this in terminal: lsusb
```
i@me:~$ lsusb
Bus 005 Device 002: ID 046d:0896 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

First one is your camera. Write down the "046d:0896" part. Search this forum for it.

If nothing helps, try to follow this thread:
[http://ubuntuforums.org/showthread.php?t=322218](http://ubuntuforums.org/showthread.php?t=322218)

Good luck!

---

