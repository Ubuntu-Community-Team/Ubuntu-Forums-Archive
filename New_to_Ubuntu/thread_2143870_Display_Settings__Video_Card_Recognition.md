---
title: "Display Settings / Video Card Recognition"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by Gargi on 2013-05-10
As learning projects, I've got two Ubuntu versions running on two separate pcs - 12.10 on a system which still has Windows XP on it, and 9.04 which has only Ubuntu. The display on the 12.10 system works great. On the 9.04 though, it looks as though I've only got 16 colors, etc. I can't seem to set the resolution higher. This is causing some side to side scrolling, etc. I'm guessing that it's using some default display drivers, and not the optimal settings for the video card. I have no idea where to look. Help?

---

### Post by sandyd on 2013-05-10
> **Gargi said:**
> As learning projects, I've got two Ubuntu versions running on two separate pcs - 12.10 on a system which still has Windows XP on it, and 9.04 which has only Ubuntu. The display on the 12.10 system works great. On the 9.04 though, it looks as though I've only got 16 colors, etc. I can't seem to set the resolution higher. This is causing some side to side scrolling, etc. I'm guessing that it's using some default display drivers, and not the optimal settings for the video card. I have no idea where to look. Help?

Support for 9.04 ended on October 2010. As a result, it is likely that your graphics drivers are out of date.

---

### Post by Gargi on 2013-05-10
Thanks! I already tried upgrading this system to 12.10, using an external cd/dvd drive (no internal)..sigh. Failed attempts. The drivers must be out of date for that as well. It's got a cd drive, but not the required dvd drive. Admittedly, I'm not that sharp as a programmer or with hardware. The trial by fire learning program...screw it up and start over :).

---

### Post by Mark Phelps on 2013-05-10
On your 9.04 system, please open a terminal and enter the command "lspci" (without the quotes) and look for the line containing "VGA".  That will tell us the make and model video chipset you're running.  It could be that there are no current drivers in 12.x for that chipset.

---

### Post by Gargi on 2013-05-10
Thanks Mark! I'll try that next.

---

