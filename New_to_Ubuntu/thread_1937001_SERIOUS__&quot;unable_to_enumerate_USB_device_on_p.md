---
title: "SERIOUS ? &quot;unable to enumerate USB device on port 2&quot;"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by suomalainen on 2012-03-07
Ubunteros,

Using 11.10 and saw this as fsck took over automatically during boot-up:

[   44.096255] hub 4-0:1.0: unable to enumerate USB device on port 2

Serious?

---

### Post by LowSky on 2012-03-08
Did you have a usb hard drive connected at some point? sometimes during an update it populates that drive to be mounted at boot for some reason.

---

### Post by xxlray on 2012-05-22
I have the same problem when I try to use my USB-Stick:

```
dmesg

[  117.501475] usb 2-1.2: new full speed USB device number 9 using ehci_hcd
[  117.573374] usb 2-1.2: device descriptor read/64, error -32
[  117.749033] usb 2-1.2: device descriptor read/64, error -32
[  117.924799] usb 2-1.2: new full speed USB device number 10 using ehci_hcd
[  117.996582] usb 2-1.2: device descriptor read/64, error -32
[  118.172492] usb 2-1.2: device descriptor read/64, error -32
[  118.347999] usb 2-1.2: new full speed USB device number 11 using ehci_hcd
[  118.753376] usb 2-1.2: device not accepting address 11, error -32
[  118.827125] usb 2-1.2: new full speed USB device number 12 using ehci_hcd
[  119.232507] usb 2-1.2: device not accepting address 12, error -32
[  119.234497] hub 2-1:1.0: unable to enumerate USB device on port 2
```

```
sudo lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
```

---

### Post by deadmantfa on 2012-11-11
Hey I the same problem did you ever find a solution

---

### Post by squakie on 2012-11-11
OK, a dumb thought here, but as previously noted, did any of you install with those devices connected?  Are you by any chance trying to put a USB 3 device in a USB 2 port?

---

### Post by xxlray on 2012-11-11
The problem still exists for me. I didn't install with this device plugged in and USB 1.0 devices seem to work fine. But as I don't have the problem especiylly on boot my problem might be a different one here.

---

