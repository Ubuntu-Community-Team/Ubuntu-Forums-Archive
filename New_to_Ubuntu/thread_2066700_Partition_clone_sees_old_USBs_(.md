---
title: "Partition clone sees old USBs :("
date: 2012-10-05
forum: New to Ubuntu
---

### Post by jalirious on 2012-10-05
Hello.

I cloned a partition (with 8.04 kde) from an old laptop

I then copied the partition to another new laptop, running 12.04.
With gparted (used to do this) I set the 8.04 partition as bootable.

Then booting into 12.04 I update the boot list. 
sudo update-grub
sudo update-grub2

Then, upon rebooting the new laptop, I can boot into the 8.04 partition, connect via the ethernet cable, etc.

I am struggling to make it recognize the USB ports.

The old laptop had 4x USB2.0
The new has 2x USB2.0, 1x USB3.0 & a hdmi out.

lsusb reveals
Bus 002 Device 002: ID 8087:0020
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 0c.. ENE Tech (blah blah - sd card)
Bus 001 Device 002: ID 8087:0020
Bus 001 Device 001: ID 0000:0000

It seems I have to make it rescan the usb hardware. No flash drives recognized. 

Any help appreciated.

---

