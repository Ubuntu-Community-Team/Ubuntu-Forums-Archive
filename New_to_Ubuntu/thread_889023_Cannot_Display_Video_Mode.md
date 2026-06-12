---
title: "Cannot Display Video Mode"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Hastings101 on 2008-08-13
During the installation of ubuntu I had this annoying screen that said something similar to "Cannot Display Video Mode, Optimum Resolution is 1280x1024 60hz" That was ok because I could still use the computer and installed Ubuntu without any problems.  However, once ubuntu rebooted and loaded up, I had the same problem at the login screen. I was able to use the computer and after logging in I changed the resolution and had no problems.  After installing the proprietary drivers for my ATI Radeon HD 2600 Pro video card I rebooted.  This time after Ubuntu loaded up I simply got a black screen with the "Cannot Display Video Mode" message. I can't use the computer at all after Ubuntu loads.  Is there any way to correct this?

---

### Post by WRDN on 2008-08-13
Is it possible to boot into the recovery mode? If so, you may be able to remove the ATI drive you installed.

EDIT: Rather than uninstalling, first boot into Recovery Mode, and select "Fix X Server". Alternatively, select to drop to root shell, and enter the command:

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Hastings101 on 2008-08-13
> **WRDN said:**
> Is it possible to boot into the recovery mode? If so, you may be able to remove the ATI drive you installed.


Yea, I have an option to do that when Ubuntu is loading up.  How would I go about removing the drivers? And is there possibly a way to fix the resolution and keep the driver?

---

### Post by Hastings101 on 2008-08-13
Oops, didn't see that while I was typing my reply, I'll try that first.

---

