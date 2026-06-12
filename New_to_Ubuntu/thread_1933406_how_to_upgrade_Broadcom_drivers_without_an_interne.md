---
title: "how to upgrade Broadcom drivers without an internet connection"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by Inisfad on 2012-02-29
In preparation for my upgrade, I have some questions about the Broadcom driver that my wireless will need.  Presently, I have only a wireless connection, and this works off the Broadcom b43 hardware driver. Upgrading to Oneiric or Pangolin, I see that the driver that is installed for activation is the STA driver, which my wireless will not use.  Once I install my upgrade, I will need to download the b43 driver, the fw-cutter file and installation file, etc., however, the quandary is that I will not have a wireless connection to get on to the internet without downloading the drivers that I will need. So, my question is, how do you do this with no internet connection? Thanks!

---

### Post by yo_bhan on 2012-02-29
using ndiswrapper, windows driver broadcom.
search file with blabla.inf and just install, simple. bluetooth and wifi worked fine on broadcom BCM4312

---

### Post by lkraemer on 2012-02-29
If you have the firmware installed on your computer now, you can just copy it to a USB Flash Drive, or download it from:
[www.omattos.com/broadcom](www.omattos.com/broadcom)

The firmware is installed at /lib/firmware or possibly in
/lib/firmware/b43

These are the *.fw files.

That is the same end result as what the previous software does, once extracted.

After you replace the files in the new install, just enable the Hardware
Drivers and everything should work properly.  You may need to Toggle it twice.

lk

---

