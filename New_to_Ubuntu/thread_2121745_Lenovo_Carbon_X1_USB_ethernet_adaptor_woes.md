---
title: "Lenovo Carbon X1 USB ethernet adaptor woes"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by yakinikku on 2013-03-02
Hi guys, I just got my hands on a think pad carbon x1 and the Lenovo Ethernet adaptor (not gigabit, but meh).  My problem is that Ubuntu is not using the adaptor.  The results of Lsusb indicate that it is detecting the adaptor, but when trying to set up a wired network connection it will not work.  Any ideas as to if I can get this working?  If not, would I be able to pick up an Apple USB ethernet adaptor and have that work?  

EDIT: I will post the output of lsusb in a minute.  Please let me know if the apple one will work without a hitch.

---

### Post by yakinikku on 2013-03-03
Is everyone waiting for me to post the LSUSB info?

---

### Post by yakinikku on 2013-03-03
No responses?

As promised, here is the output of lsusb

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 004: ID 147e:2020 Upek 
Bus 001 Device 005: ID 0a5c:21e6 Broadcom Corp. 
Bus 001 Device 006: ID 04f2:b315 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 17ef:7203 Lenovo 

```

The adaptor in question is the one with the label "Lenovo".  Does anyone know how I can get this working?

---

### Post by yakinikku on 2013-03-03
This will solve the problem with the Lenovo adapter

[https://chentiangemalc.wordpress.com/2012/10/22/case-of-the-broken-linux-driver-lenovo-usb-2-0-ethernet-10100-dongle/](https://chentiangemalc.wordpress.com/2012/10/22/case-of-the-broken-linux-driver-lenovo-usb-2-0-ethernet-10100-dongle/)

However, can someone verify that the apple usb ethernet adapter will work 100% out of the box without any fiddling?

Or does anyone have any suggestions for gigabit adapters that will work out of the box in linux?

---

### Post by yakinikku on 2013-03-03
Follow up question, would anyone know a way that I could have the lenovo adapter work from a live cd without futzing around with it every time I boot in to one?

---

### Post by darkcrimson on 2013-03-03
I've had bad experiences with USB dongles in general. If you've got one that works, I'd stick to it. Unfortunately, running a live cd instance would reset your hard work each time you reboot.

---

### Post by yakinikku on 2013-03-04
It's a shame.  If I run this through a VM the adapter works, but wifi doesn't.  haha.

---

### Post by yakinikku on 2013-03-20
Well, I just installed it to bare metal.  Followed the instrucitons in the link I posted above and the adapter does not connect to my wired network.  Can anyone assist with getting this working?

EDIT: I should mention that when I tested a debian variant (actual debian) the wired adapter worked without me having to do anything.  Hints?

---

### Post by emdeem on 2013-03-20
The Lenovo adapter works out of the box for me on Quantal.  The driver for the 17ef:7203 has been in the kernel for at least a few months.  You don't need to manually build or install any drivers.

---

