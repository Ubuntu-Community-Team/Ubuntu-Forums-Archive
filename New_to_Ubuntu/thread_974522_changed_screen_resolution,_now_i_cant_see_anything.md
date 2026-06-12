---
title: "changed screen resolution, now i cant see anything"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by hondarider777 on 2008-11-07
okay so i guess i did something really stupid and i changed my screen's resolution. its telling me to change it back but i cant because i cant see anything on the screen.
is there some other way to change it back to normal?

---

### Post by bobnutfield on 2008-11-07
You have probably changed it to a resolution which is out of the range your monitor.  You can boot into recovery mode and from the command line:

> sudo dpkg-reconfigure -phigh xserver-xorg

Reboot normally and you should be back to a standard desktop.

---

