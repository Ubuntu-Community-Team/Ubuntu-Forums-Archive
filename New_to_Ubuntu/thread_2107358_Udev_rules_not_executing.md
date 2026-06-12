---
title: "Udev rules not executing"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by labchimp on 2013-01-21
Hi I added some udev rules to make my trackpoint function properly, however they are not executing at startup. I did the udevadm test and it works fine, it just won't execute at startup.

SUBSYSTEM=="serio", DRIVERS=="psmouse", WAIT_FOR="/sys/devices/platform/i8042/serio1/sensitivity", ATTR{sensitivity}="250", ATTR{speed}="130"

my touchpad is disabled my default so my trackpoint is serio 1

---

