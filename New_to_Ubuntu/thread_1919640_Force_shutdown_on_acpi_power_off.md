---
title: "Force shutdown on acpi power off"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by Pontiac on 2012-02-03
I've just installed Hardy Heron from the mini install, ground up, then installed kde-desktop on top of it, all to be run in Virtual Box.

Is it possible when I click X to close the Virtual Box, when selecting the "Send the shutdown signal" and OKing that dialog, to have KDE just do the shutdown instead of prompting again to shut down?

Basically, I want the virtual machine to shut down when I hit the virtual power button without being asked again.

Thanks!

---

### Post by Pontiac on 2012-02-03
Disregard.  Found answer here:

[http://askubuntu.com/questions/66723/how-do-i-set-the-power-button-to-shutdown-instantly-instead-of-opening-a-dialog](http://askubuntu.com/questions/66723/how-do-i-set-the-power-button-to-shutdown-instantly-instead-of-opening-a-dialog)

What worked for me was replacing **action=/etc/acpi/powerbtn.sh** with **action=/sbin/poweroff** in */etc/acpi/events/powerbtn* and then restarting the acpid daemon.

---

