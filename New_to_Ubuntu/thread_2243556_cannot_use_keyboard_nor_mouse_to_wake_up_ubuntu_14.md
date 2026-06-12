---
title: "cannot use keyboard nor mouse to wake up ubuntu 14.04 LTS"
date: 2014-09-09
forum: New to Ubuntu
---

### Post by Jesse_Zexi_Zhuang on 2014-09-09
I have a Dell dimension 9200 desktop with windows 8 and ubuntu installed side by side.
  keyboard will wakeup windows 8 from sleep but ubuntu will only wake up when I press the power button.
  tried cat /proc/acpi/wakeup
  Device  S-state   Status   Sysfs node
VBTN      S4    *enabled 
PCI0      S5    *disabled  no-bus:pci0000:00
PCI4      S5    *disabled  pci:0000:00:1e.0
PCI2      S5    *disabled  pci:0000:00:1c.0
PCI3      S5    *disabled
PCI1      S5    *disabled  pci:0000:00:01.0
PCI5      S5    *disabled  pci:0000:00:1c.4
PCI6      S5    *disabled
USB0      S3    *enabled   pci:0000:00:1d.0
USB1      S3    *enabled   pci:0000:00:1d.1
USB2      S3    *enabled   pci:0000:00:1d.2
USB3      S3    *enabled   pci:0000:00:1a.0
USB4      S3    *enabled   pci:0000:00:1a.1
  Looks like all the usb ports were enabled so I don't know where else to look for now.
      
I have dell usb keyboard and microsoft usb  mouse. I would prefer to use the keyboard to wakeup if possible.
-----------Bus 007 Device 003: ID 413c:2005 Dell Computer Corp. RT7D50  Keyboard
 ----------- Bus 007 Device 002: ID 045e:0084 Microsoft Corp.  Basic Optical Mouse

Any help is appreciated.

---

### Post by Jesse_Zexi_Zhuang on 2014-11-21
Nobody is around or interested to help?

---

