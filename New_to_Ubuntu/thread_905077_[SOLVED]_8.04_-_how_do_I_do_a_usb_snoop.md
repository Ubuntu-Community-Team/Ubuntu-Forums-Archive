---
title: "[SOLVED] 8.04 - how do I do a usb snoop?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by anewguy on 2008-08-30
My other post seems to have gotten no replies, and it is probably buried in the ranks now, so I'll go back and close it and open this one.

I need to run usb snoop but not on a usb file system, just a device.  Prior to 8.04, I echo'd Y to /sys/module/usbcore/parameter/usbfs_snoop, modprobe'd usbcore,  and everything showed up in syslog with the detail of the data, etc., being put across a usb device.  When finished, I just replace the "Y" with and "N" and did the 2 steps.

This apparently either doesn't work in 8.04, or something has changed, as I get none of the detail I did before.  I have searched the web, and seen reference to something called usbmon, so I modprobe'd it but still don't see a log or any detail.

So, can someone please tell me how to run detailed usb snoops in 8.04?


EDIT:  Okay, I don't know what happened (maybe it was the modprobe of usbmon??) but the snoop works now.

Thanks in advance!

Dave:)

---

