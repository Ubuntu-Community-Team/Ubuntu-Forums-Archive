---
title: "New ubuntu installation from Windows goes straight to grub"
date: 2020-06-01
forum: New to Ubuntu
---

### Post by haycon42 on 2020-06-01
Hey,

I'm trying to install Ubuntu on my Windows 10 PC.

I've pretty much followed the guide at [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows#1-overview)

I downloaded Ubuntu 20.04, then I did an MD5sum to verify the download. Afterwards I burned the ISO file onto a USB stick with Rufus.

However when I try to boot from the USB the installation does not start, but instead I get a grub terminal window showing up.

I have tried re downloading the ISO file, and I have tried reburning the USB stick with no success. Also tried writing to the usb stick with Win32diskimager.

Any suggestions on how I can resolve this problem?

Thanks

---

### Post by TheFu on 2020-06-01
Look for incorrect BIOS settings.  Anything specific to Windows is probably a problem.  Also, there are some Windows settings that will make any Linux not see the storage, so you'll want to change or disable those things ... like fast startup, hibernation, and Windows volume management.

Also, be certain there is sufficient empty storage for Linux to install into.  50G would be great to start. 25G is fine, 15G will become tight quickly.

I don't dual boot. There were too many hassles for me doing that.  It was just easier to run Windows inside a virtual machine those few times I needed Windows and have Linux running on the physical hardware for the greater security, performance and peace of mind.  As a beginner, I'd suggest you strongly consider running Linux inside a VM even if Windows is the hostOS.  Get a little background, learn the names for devices before you can delete all your data by accident.  During a VM install, it is nearly impossible to harm the hostOS at all. Much safer.  With a dual-boot install, people routinely wipe Windows because they are seeing lots of unfamiliar terms.  Please be very careful.

---

### Post by haycon42 on 2020-06-01
Thanks for replying

I'll try to look into it, maybe I will just stick to VM for now

---

### Post by yancek on 2020-06-01
You might try the link below which is the official Ubuntu documentation on dual booting with windows 10 and has a lot of detailed information.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

