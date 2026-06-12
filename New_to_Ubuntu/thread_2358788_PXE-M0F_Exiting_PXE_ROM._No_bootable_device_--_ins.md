---
title: "PXE-M0F: Exiting PXE ROM. No bootable device -- insert boot disk and press any key"
date: 2017-04-17
forum: New to Ubuntu
---

### Post by tzujira on 2017-04-17
Hello,
I tried using SeaTools for Free-DOS to check the HDD on a Lenovo Ideapad 110 15IBR. I changed the boot order in BIOS to boot from cd first and proceeded to boot from cd. The SeaTools for Free-DOS booted as expected, but it didn't see the HDD, so I rebooted the system only to get stuck in a "PXE-M0F: Exiting PXE ROM. No bootable device -- insert boot disk and press any key" loop.

I tried using Boot-Repair from a LiveUSB via "Try Ubuntu" option, but that didn't fix it.
Here is the Boot-Repair log: [http://paste2.org/mjOGnEGU](http://paste2.org/mjOGnEGU)

How can I fix this error and boot from the installed Ubuntu OS?

I made no changes in the hardware configuration, I only changed the Bios settings and ran the SeaTools bootable cd.

Thank you!

---

### Post by Tadaen_Sylvermane on 2017-04-17
Looks like it is trying and stopping after trying to PXE boot, maybe disable network booting completely in the bios.

---

### Post by tzujira on 2017-04-17
It worked! I started spamming Fn+F2 right after I powered up the laptop and I was able to get into Bios and disable network booting. Now it boots to Ubuntu OS without a problem.
Thank you!

---

