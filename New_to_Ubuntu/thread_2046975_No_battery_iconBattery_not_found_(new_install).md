---
title: "No battery icon/Battery not found (new install)"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by zuren on 2012-08-23
I just got Lubuntu running on my old Dell Inspiron 2500 laptop and I'm sorting out the issues.  One is that the software doesn't see the battery.  There is no icon on the desktop and under System Profiler it says, "No batteries found on this system."  I'm using it on battery power now...

I was having issues with Lubuntu installing and so I set the mode to "acpi=off" (as suggested in another thread), solving that problem.  I'm not sure if that is contributing to this issue.  I did some searching and tried running the following command with no change:

```
sudo apt-get install --reinstall gnome-power-manager
```

Thank you for any suggestions!

Computer:
Dell Inspiron 2500
Celeron 700
512MB RAM

---

### Post by zuren on 2012-08-24
Also forgot to mention that the battery was weak/failing (would only run for 10 minutes off of AC power) when Lubuntu was installed but I now have a new battery in it.

---

### Post by dozdozez on 2012-08-24
Right click on the panel > panel > Add new items > Battery Monitor

---

### Post by dozdozez on 2012-08-24
Sorry, i thought you mean xubuntu ....

It sholudn't be so different in lubuntu thought....

---

### Post by zuren on 2012-08-25
> **dozdozez said:**
> Right click on the panel > panel > Add new items > Battery Monitor

I just tried this with no luck.  

It seems that the battery not being found (and the black/white vertical  lines in place of the Lubuntu splash screen) may have something to do with  "ACPI=OFF" that I need to sort out.  Unfortunately, ACPI=OFF is needed  to boot the computer.  I went into the BIOS and do not see ACPI as an option anywhere, so is it correct for me to assume this is why ACPI must be off with my install?

Here is how it behaves after some testing:    

If I leave "acpi=off" active in the command line, the laptop will boot but I get black/white  vertical lines (on both start-up and shutdown) rather than Lubuntu  splash screen.  This is tolerable but obviously not correct.

When logged in and I disable "acpi=off" in GRUB Customizer then restart,  the computer will not boot and hangs on a black screen.  

If I disable "acpi=off" in GRUB Customizer, restart, enter GRUB after  the BIOS splash screen and insert "acpi=off" in the command line, the  laptop boots with Lubuntu splash screens.  This is the closest  "normal" behavior I've seen to date.  

The battery is not seen in all of the conditions above.  In order to get into the OS at all, GRUB must see ACPI=OFF.  If there  is a way to correct this, it will probably solve several issues.

Thanks!

---

