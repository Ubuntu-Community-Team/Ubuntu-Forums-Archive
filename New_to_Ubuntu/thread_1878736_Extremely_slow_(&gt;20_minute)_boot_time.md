---
title: "Extremely slow (&gt;20 minute) boot time"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by _dmr on 2011-11-10
I dual boot Ubuntu 11.04 with Windows XP, on my Packard Bell Dot S, and have had no problems until recently, when Ubuntu became unresponsive and I held down the power button to shutdown the system. 
I booted back up, selected Ubuntu from the grub menu, then waited at a blank screen for ~6 minutes, then a blinking | to enter text, although nothing happens when anything is typed, follwed by a purple screen for ~10 minutes. The ubuntu logo and flashing dots appear for ~5 minutes, then the desktop loads, but also takes a very long time to initialise, for example, Chromium takes ~4 minutes to load from clicking the shortcut, with heavier applications taking much, much longer. This happens every single time I boot.
How can I fix this?
Please help!

---

### Post by BillyBoa on 2011-11-10
Sorry to say but the installation failed. You should consider to reinstall the system.

---

### Post by _dmr on 2011-11-10
> **BillyBoa said:**
> Sorry to say but the installation failed. You should consider to reinstall the system.
 
But I've been using this installation without any errors for around 5 months, up until around a week ago? :confused:

---

### Post by Mark Phelps on 2011-11-10
Most probably, the filesystem became corrupted in some way because of the power-down.  The new Disk Utility app provides an option to run a Disk Check. You should launch that and choose that option.

Then, reboot and see if that helps.

---

