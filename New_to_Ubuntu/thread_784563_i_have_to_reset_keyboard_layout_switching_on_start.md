---
title: "i have to reset keyboard layout switching on startup"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by paranoid_humanoid on 2008-05-06
i use two keyboard layouts, Arabic and English USA, whenever i reboot i have to open the layout switching interface and reset my combinations so it would work. they are already selected when i check, i just need to deselect then select them everytime my system reboots.
can someone help me with this? it used to be fine till a while ago. i don't know what i did to make it angry! :)

---

### Post by spiderbatdad on 2008-05-06
possibly running sudo dpkg-reconfigure xserver-xorg and selecting your keyboard layout that way, so that the changes are written to /etc/X11/xorg.conf

---

### Post by paranoid_humanoid on 2008-05-07
> **spiderbatdad said:**
> possibly running sudo dpkg-reconfigure xserver-xorg and selecting your keyboard layout that way, so that the changes are written to /etc/X11/xorg.conf

didn't work. after i rebooted, i still had to reset my keyboard layout switching combinations manually for them to work!
any help?!?

---

