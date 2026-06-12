---
title: "How to make SD slot Bootable as &quot;USB Device&quot; in Bios (Windows 8.1/Ubuntu 13.10)"
date: 2014-02-03
forum: New to Ubuntu
---

### Post by Evan_Hart on 2014-02-03
My dream is to have a multiboot disc utility SD card that I can leave in my new laptop (Sony Vaio Fit 13a Win 8.1/Ubuntu 13.10) that doesn't have a CD drive. You may know that you can boot from an SD card if it's in a card reader and plugged in to a USB slot, but the SD slot is not bootable as it is from the factory.

Advice appreciated

_________________________
Sony Vaio Fit 13a, Intel i5
Windows 8.1 and Ubuntu 13.10

---

### Post by sudodus on 2014-02-03
I think it works in somewhat different ways in different computers depending on the hardware and BIOS/UEFI systems.

A. In some cases an SD card in the slot is recognized as 'any' mass storage device alongside hard disk drives and USB drives. In such cases, it is possible to have the card inserted and boot into the BIOS menus, change the boot order, so that the SD card is selected before the hard disk drive.

B. In some cases an SD card in the slot is recognized as a USB device. In such cases you can try to

- either press a hotkey to get a boot menu and select 'boot from USB'

- or have the card inserted and boot into the BIOS menus, change the boot order, so that USB  is selected before the hard disk drive.

See also this link (and links from it)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Evan_Hart on 2014-02-03
It was the same with my last laptop...
 It won't start from "USB device" unless it is through a card reader (tested-working) and changing the boot order doesn't help.
 The slot is treated differently for some reason. (It's a different computer but it may be the same problem). From this forum:
[http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/X220-boot-from-SD-slot/td-p/494013#M28571](http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/X220-boot-from-SD-slot/td-p/494013#M28571)
 "The internal SD card reader is not a bootable device.
 It's connected to PCI-E bus (for better performance I think, it showed much higher speed than average external ones), which means BIOS could not access it like commom internal/USB drives (mSATA is a new category but basically internal drive with a new interface).
 Even the BIOS could recognize it, the on-card software needs driver for the card reader, or they will simply fail to load themselves because they cannot access their own media."

Is there any workaround?

---

### Post by C.S.Cameron on 2014-02-03
You might have some luck using Plop or EasyBCD or some another boot manager.

You get similar to grub menu at start then can boot the USB from there.

---

### Post by Evan_Hart on 2014-02-03
[URL="http://www.mydellmini.com/forum/general-discussion/6670-boot-internal-sd-card-slot-howto-workaround.html"]http://www.mydellmini.com/forum/general-discussion/6670-boot-internal-sd-card-slot-howto-workaround.html
[/URL]
Will this work?

---

### Post by sudodus on 2014-02-04
> **Evan_Hart said:**
> It was the same with my last laptop...
 It won't start from "USB device" unless it is through a card reader (tested-working) and changing the boot order doesn't help.
 The slot is treated differently for some reason. (It's a different computer but it may be the same problem). From this forum:
[http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/X220-boot-from-SD-slot/td-p/494013#M28571](http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/X220-boot-from-SD-slot/td-p/494013#M28571)
 "The internal SD card reader is not a bootable device.
 It's connected to PCI-E bus (for better performance I think, it showed much higher speed than average external ones), which means BIOS could not access it like commom internal/USB drives (mSATA is a new category but basically internal drive with a new interface).
 Even the BIOS could recognize it, the on-card software needs driver for the card reader, or they will simply fail to load themselves because they cannot access their own media."

Is there any workaround?
You know more than I about this.

---

### Post by sudodus on 2014-02-04
> **Evan_Hart said:**
> [URL="http://www.mydellmini.com/forum/general-discussion/6670-boot-internal-sd-card-slot-howto-workaround.html"]http://www.mydellmini.com/forum/general-discussion/6670-boot-internal-sd-card-slot-howto-workaround.html
[/URL]
Will this work?

You can try :-)

---

### Post by C.S.Cameron on 2014-02-04
> **Evan_Hart said:**
> [URL="http://www.mydellmini.com/forum/general-discussion/6670-boot-internal-sd-card-slot-howto-workaround.html"]http://www.mydellmini.com/forum/general-discussion/6670-boot-internal-sd-card-slot-howto-workaround.html
[/URL]
Will this work?

I think plop will be simpler.

---

