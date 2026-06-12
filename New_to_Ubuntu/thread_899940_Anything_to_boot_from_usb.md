---
title: "Anything to boot from usb?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by zamadatix on 2008-08-24
my bios on an old laptop doesn(or would grub?)

---

### Post by halitech on 2008-08-25
if the hardware doesn't support booting from USB then to my knowledge, nothign else will force it to boot from there.

what laptop do you have?

---

### Post by neurostu on 2008-08-25
If the BIOS doesn't support booting from USB it may still be possible if the bios can mount the USB drive. You would need a physical grub installtion to make it happen but it should theoretically be possible....

---

### Post by halitech on 2008-08-25
possibly booting from a floppy that has USB support may allow them to run an install from the cd but if the BIOS doesn't support booting from the USB then how is it going to mount a USB device for booting?

---

### Post by Dr Small on 2008-08-25
If the BIOS does not support booting from USB, then you could probably add an entry to GRUB that would boot from the USB device.

---

### Post by halitech on 2008-08-25
I guess we've all missed an important question that the OP will need to answer:

are they trying to install on a device that needs to boot from USB or install on an external device and then have that as a boot option.

---

