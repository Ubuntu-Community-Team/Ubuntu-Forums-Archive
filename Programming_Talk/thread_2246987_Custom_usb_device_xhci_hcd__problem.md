---
title: "Custom usb device xhci_hcd  problem"
date: 2014-10-04
forum: Programming Talk
---

### Post by MonsterPipe on 2014-10-04
I have developed a custom USB 2 device that communicate with a computer via a USB port. WHen I plug it on a USB 3 port, the device is not recognized by xhci_hcd. On a USB 2 port, it works fine. My question is: Is there a way for me in the firmware of the device to specify in the device descriptor on anywhere else to tell Ubuntu to use the old ehci_hcd?

Or do you see another way around that does not involve recompiling the kernel?

Thank you,

---

### Post by MonsterPipe on 2014-10-07
To help understanding my question, here is the dmesg output when I connect my device:

[607170.226639] usb 3-2: new full-speed USB device number 26 using xhci_hcd
[607170.242951] usb 3-2: device descriptor read/8, error -75
[607170.363143] usb 3-2: device descriptor read/8, error -75
[607170.578852] usb 3-2: new full-speed USB device number 27 using xhci_hcd
[607170.595155] usb 3-2: device descriptor read/8, error -75
[607170.715308] usb 3-2: device descriptor read/8, error -75
[607170.931015] usb 3-2: new full-speed USB device number 28 using xhci_hcd
[607170.947362] usb 3-2: device descriptor read/8, error -75
[607171.067452] usb 3-2: device descriptor read/8, error -75
[607171.283214] usb 3-2: new full-speed USB device number 29 using xhci_hcd
[607171.299583] usb 3-2: device descriptor read/8, error -75
[607171.419709] usb 3-2: device descriptor read/8, error -75
[607171.523427] hub 3-0:1.0: unable to enumerate USB device on port 2

---

### Post by ofnuts on 2014-10-07
Looking at dmesg output when I plug/unplug my mouse dongle in my USB2 and USB3 ports, the big difference seems to be the timing:

About 100ms in USB2

```

[317168.654000] usb 2-1.5: new full-speed USB device number 7 using ehci_hcd
[317168.749502] usb 2-1.5: New USB device found, idVendor=046d, idProduct=c52b

```

Only 20ms in USB3:

```

[317306.857737] usb 3-2: new full-speed USB device number 4 using xhci_hcd
[317306.876634] usb 3-2: New USB device found, idVendor=046d, idProduct=c52b

```

So it could be a matter of having you device ready to answer more quickly?

Otherwise investigate the contents of /sys/module/usbcore/parameters/

---

### Post by xb12x2 on 2014-10-07
For what it's worth:

device descriptor **read/8**, error -75

From /usr/include/asm-generic/errno.h

#define    EOVERFLOW    75    /* **Value too large for defined data type** */

---

### Post by MonsterPipe on 2014-10-08
Thanks a lot guys, I will look into it. 

I'll keep you posted.

---

### Post by MonsterPipe on 2014-10-08
Thank you [COLOR=#000000]xb12x2 for pointing that out. I found out an error in the firmware and I was not sending the correct value in the device descriptor. :)[/COLOR]

---

### Post by MonsterPipe on 2014-10-08
Is there a point/score system? Can I tell that you have found the solution somewhere?

---

