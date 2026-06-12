---
title: "Upgraded from 12.04 to 12.10, now getting error on bootup related to graphics drivers"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by katana0182 on 2012-11-16
Hi,

I'm very new to Ubuntu, and I really like it so far, especially the package manager and the price. A few months ago, I did a clean install of Ubuntu 12.04 x64 from media onto a family member's computer (with an AMD 3 core processor and Nvidia GT 240) - it worked great. 

Today, I upgraded it to 12.10 using the upgrade manager included in Ubuntu. Upon upgrade, the startup sequence endlessly loops with the monitor going to a black screen, then text coming back, saying:

```
[time from startup] [drm] nouveau 0000:01:00.0: Failed to idle channel 2
```

I've rebooted repeatedly, but this error constantly repeats itself no matter how many times I reboot.

Googling the string "drm nouveau failed to idle channel", it talks about the x server not starting up correctly presumably due to a graphics driver bug. If it helps, I activated the proprietary Nvidia driver in 12.04.

Following this, I used GRUB (pressing shift and F1 at startup) to put the install into safe mode and then used the menu that pops up to put x into graphics safe mode. 

This gets me a login screen and desktop, albeit at lower resolution. However, on this desktop, the top bar (with the time and date) and the left sidebar (with the program icons) are missing. 

This makes the system unusable.

I am wondering if I should pull my gfx card and try to boot using integrated graphics or if there's some terminal wizardry to switch out the graphics driver for one that works to fix this situation.

Thanks.

---

### Post by monkeybrain2012 on 2012-11-16
If you have installed the Nvidia driver (or any driver not part of the kernel for that matter) before you need to remove it before you run upgrade or it will break. One of many reasons why I never upgrade, always do a clean install, it is simple, clean way faster and trouble free.

---

### Post by katana0182 on 2012-11-16
Is there a way to do this without losing documents, settings, and stuff like Internet history, passwords, etc, on Chromium?

---

### Post by cryptotheslow on 2012-11-16
Use Ctrl-Alt-T to open up a terminal on that low res desktop and enter the command:
```
jockey-gtk
```That is the "Additional Drivers" program in 12.04. However it was superceded in 12.10 by software-properties so may have been removed when the upgrade was performed.

If it does exist and startup correctly, hopefully you can use it to remove the installed Nvidia driver.

Alternatively the solution in this thread may help you:
[http://ubuntuforums.org/showthread.php?t=2084478](http://ubuntuforums.org/showthread.php?t=2084478)

---

### Post by katana0182 on 2012-11-16
That alternative solution worked - I had to use apt-get to reinstall the NVidia drivers. Now everything's working smoothly. Thanks again!

---

