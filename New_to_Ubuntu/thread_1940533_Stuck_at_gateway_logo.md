---
title: "Stuck at gateway logo?"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by Mikepmarkey on 2012-03-13
I'm a complete newb, but I managed to put 11.10 on my Gateway laptop (AMD 64, Athalon x2, Nvidea) and update it.  I also activated one proprietary driver, the one "recommended" for Nvidea.  Later it hung in Firefox and I couldn't do anything but force the laptop to power down.  It froze while trying to upload to Facebook, if that makes a difference.  

Now on startup I get to the first screen, the Gateway splash screen, and it never gets further than that.  Ive tried leaving it overnight, but there's no progress.  The menu options also don't ever come up (boot menu F10, BIOS Settings F2, PXE Boot F12, Enter for Menu).  

Most of the help documents I've read so far assume I can get to GRUB, or are beyond my meager comprehension  Please help!

---

### Post by acimi66 on 2012-03-13
Are you able run it from the live CD?

---

### Post by Mikepmarkey on 2012-03-14
> **acimi66 said:**
> Are you able run it from the live CD?

I will get a disk and give it a try...

---

### Post by donkyhotay on 2012-03-15
If you can't even get into the BIOS (F2 based on your post) then a liveCD won't work. The BIOS is before the OS and you should be able to access it regardless of whether you have windows, linux, or anything else installed on the system. That means you most likely have a HW failure. It could be anything but I would probably look at your HDD first. In my experience the HDD is the component most likely to cause the computer to lock up to the point you can't even get into the BIOS. If you have another HDD somewhere try swapping it, if you don't then try unplugging the HDD and see if you can at least get into the BIOS (though of course the computer won't boot with HDD disconnected). If that doesn't do it then start looking at RAM, CPU, etc.

---

### Post by Mikepmarkey on 2012-03-15
So the live cd worked!  It started up and went to the installer, which I closed.  I restarted again with the disk out and it started up normally.  Interestingly, it now goes to an Ubuntu starts screen without ever going to the gateway splash screen.

---

