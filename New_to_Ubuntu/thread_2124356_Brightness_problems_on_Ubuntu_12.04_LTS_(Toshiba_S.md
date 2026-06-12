---
title: "Brightness problems on Ubuntu 12.04 LTS (Toshiba Satellite-L670)"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by a_m_100 on 2013-03-10
Hi everyone, 

I have a typical problem, I can't control the brightness. Neither through the hotkeys or the applet. I've tried the 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" solution, but it didn't work. 



I'd appreciate if someone could walk me through or point me towards other solutions. 

System details:

Processor - Intel® Pentium(R) CPU P6200 @ 2.13GHz × 2 
Graphics - Gallium 0.4 on AMD CEDAR 
OS type - 32-bit

---

### Post by cmcanulty on 2013-03-10
did you try installing xbacklight, set the brightness to what you want ,and then add xbacklight to startup apps? This is truly a problem that needs  a fix for a lot of people

---

### Post by a_m_100 on 2013-03-10
Yes, I tried that as well. Sorry I didn't mention it. I've been trying to fix this on and off for weeks but no luck.
I also tried this [http://www.refreshit.info/2012/05/solved-brightness-problem-in-ubuntu.html](http://www.refreshit.info/2012/05/solved-brightness-problem-in-ubuntu.html)

But then this shows up

warning: output LVDS1 not found; ignoring
xrandr: Need crtc to set gamma on.

---

### Post by a_m_100 on 2013-03-11
I just tried this solution [http://followthegeeks.com/how-to-solve-brightness-is-not-changing-issue-in-12-04/](http://followthegeeks.com/how-to-solve-brightness-is-not-changing-issue-in-12-04/)
and I got this ```
bash: /sys/class/backlight/toshiba/brightness: Permission denied
```

Do I have to login as root, and should I?

---

### Post by Toz on 2013-03-24
You need to run the command with sudo. Something like:
```
echo <value> | sudo tee /sys/class/backlight/toshiba/brightness
```
...where <value> is a number between 0 a the contents of /sys/class/backlight/toshiba//max_brightness.

Can you also try the kernel parameter **acpi_osi=** in place of **acpi_backlight=vendor**?

---

### Post by a_m_100 on 2013-03-24
Great, changing it to "acpi_osi=" worked! Thanks so much. 
But, the brightness display doesn't appear anymore when using hotkeys. This isn't really an issue for me, just saying.

---

### Post by Toz on 2013-03-24
Out of curiosity, does using both **acpi_osi= acpi_backlight=vendor** return the functionality of the brightness notification?

---

