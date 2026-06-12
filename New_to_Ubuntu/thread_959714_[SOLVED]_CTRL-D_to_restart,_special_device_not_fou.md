---
title: "[SOLVED] CTRL-D to restart, special device not found"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-26
I have been trying to install an external usb 2.0, hard drive. The relevant output of lsusb is:

Bus 001 Device 002: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI

So the device is seen. And in media, it appears under the name: usbdrive with my (user) permissions, that is, it isn't owned by root. But after upgrading to II (Intrepid Ibex, ver. 8.10), on boot-up (or restart) the spash screen drops down to the ascii lines and halts at "can't find special device" CTRL-D to continue (or restart, I didn't write the exact language down). On CTRL-D, boot resumes, and I must input user name and password. After that, the OS seems pretty normal, except drive icon does not appear on the Desktop. And after II, even with the device powered up before the OS is powered up, I still have to CTRL-D.

So my question is: how and I uninstall and reinstall this device so Ibex will treat it properly?

---

### Post by Mark_in_Hollywood on 2008-10-28
The device had become unusable due to an electrical or electronic problem. By unplugging both the power and the usb cable, on another re-try, the device "fixed" itself.

---

