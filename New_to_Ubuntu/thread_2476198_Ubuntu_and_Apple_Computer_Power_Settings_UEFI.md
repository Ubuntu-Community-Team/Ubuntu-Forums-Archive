---
title: "Ubuntu and Apple Computer Power Settings UEFI"
date: 2022-06-19
forum: New to Ubuntu
---

### Post by jakemoore1 on 2022-06-19
I'm trying to up-cycle some old Macs.   It kills me that the hardware is perfect but the OS no longer supports updates.  I have Ubuntu-Desktop and Ubuntu-Budgie both 22.04 up and running so thank you to the developers and community. 

Apple offers in its OS the ability to schedule power-on times and to automatically restart the computer after a power failure.  I suppose this setting is in the UEFI but it is accessed in the OS with a fully booted computer and Apple gives no tool to adjust outside OS-X.

My question to the community:  Is there a way to find and change these settings outside of OS-X?

---

### Post by yancek on 2022-06-19
There are a number of ways to schedule a shutdown and reboot and doing an online search should give you a number of sites, one at the link below.

[https://notesread.com/how-to-schedule-an-automatic-power-on-and-off-in-ubuntu-linux/](https://notesread.com/how-to-schedule-an-automatic-power-on-and-off-in-ubuntu-linux/)

The link below discusses using the BIOS set up auto restart after a power failure.  Never done this but you can search your BIOS options to see if you can find anything.

---

### Post by jakemoore1 on 2022-07-03
> **yancek said:**
> There are a number of ways to schedule a shutdown and reboot and doing an online search should give you a number of sites, one at the link below.

[https://notesread.com/how-to-schedule-an-automatic-power-on-and-off-in-ubuntu-linux/](https://notesread.com/how-to-schedule-an-automatic-power-on-and-off-in-ubuntu-linux/)

The link below discusses using the BIOS set up auto restart after a power failure.  Never done this but you can search your BIOS options to see if you can find anything.

Thank you so much.  The link addresses the shutdown command which I am familiar with and I have also have used with crontab to schedule shutdowns.

But the real challenge for me is to turn the computer back on.  The BIOS/UEFI settings in an Apple computer are normally accessed through Mac OS X.  (I don't think the Apple calls it a BIOS) There must be a way to see and modify the settings when OS X is replaced with Ubuntu?  

I suppose I am more likely to find the type of person who taken a deep dive into the power settings on an Apple computer on a Ubuntu forum rather than an Apple forum.

---

### Post by grahammechanical on 2022-07-03
As regards what passes for what you and I call BIOS/UEFI on Apple machines this link shows what you are limited to.

[https://support.apple.com/en-gb/HT201255](https://support.apple.com/en-gb/HT201255)

On what I would call less closed and locked machines the Grub boot menu of Ubuntu 20.04 and onwards will have a boot menu entry to load into the UEFI.

Regards

---

