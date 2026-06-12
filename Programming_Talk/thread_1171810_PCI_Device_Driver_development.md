---
title: "PCI Device Driver development"
date: 2009-05-27
forum: Programming Talk
---

### Post by amit1947 on 2009-05-27
I am developing a PCI driver for some instruments (compiled kernel module .ko file) and I would like to know how to have Ubuntu automatically create the correct /dev node and start the correct .ko file. I know that UDEV is probably the answer to my question, but how do I go about telling Ubuntu the VendorID/DeviceID and matching .ko and /dev node name?

What I am asking for is the equivalent of a .inf file in Windows, where you can install new hardware and have Windows automatically identify and install (run) the correct device driver.

---

