---
title: "x server won't start"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-04
i just finished doing a fresh install of ubuntu 8.10 on my computer.  the installation went fine and i was able to install the newest updates, but when i rebooted after the most recent updates were installed i encounter a screen that reads as follows:

***Could not start the x server (your graphical environment) due to some internal error.  Please contact your system administrator or check your syslog to diagnose.  In the meantime this display will be disabled.  please restart GDM when the problem is corrected.***

followed by a terminal login prompt.

does anyone have any suggestions on how i can correct this issue?

thanks.

---

### Post by Bölvaður on 2008-11-04
This is just a shot in the dark, but wasnt there a kernel update that could have caused this?

---

### Post by Matt26 on 2008-11-04
> **Bölvaður said:**
> This is just a shot in the dark, but wasnt there a kernel update that could have caused this?

i have no idea, but if i remember correctly, the last updates that were installed which required a reboot (which resulted in the error message) included a kernel related update...

---

### Post by Matt26 on 2008-11-12
i discovered the cause of the issue here, although i dont' quite understand it- i have an 80GB western digital hard drive connected a slave drive on the same IDE channel as my boot drive.  once i disconnected this drive ubuntu loaded up normally.  does anyone have any ideas as to what might cause this issue to happen?

---

