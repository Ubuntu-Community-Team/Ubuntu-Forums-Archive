---
title: "Need help with ATI graphics / blank screen"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Xerius_fire on 2008-05-06
I installed 8.04 on Sunday and when I rebooted I loaded up to a blank screen and my monitor acted like it was disconnected from my CPU. I have determined that the drivers for my ATI graphics card are missing and have been replaced by a generic driver that is not allowing it run. I can not get into Ubuntu at all but I am able to activate the Terminal by using CTRL+ALT+F1 at the blank screen. 

I have tried to manually install the drivers but have had no luck. I have also tried to install Envy by using the code:

sudo aptitude update
sudo aptitude install envyng-gtk

but it can't find the package. 

I have also tried to uninstall xserver and fix it but all to no avail. I have also tried to reboot in recovery mode but I can't get in still.

If somebody has discovered how to fix this issue, I'd be most happy to know how.

Thanks in advance.

---

### Post by Xerius_fire on 2008-05-06
Okay. I may have found the way to install Envy but I have to get into "/etc/apt/sources.list" so that I can add the universe repository.

When I type "/etc/apt/sources.list" into terminal, it says that my permission is denied and I don't have access to gedit or nano. Anybody know why?

---

