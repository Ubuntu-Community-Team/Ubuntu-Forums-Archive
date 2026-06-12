---
title: "New gnome-settings-daemon build failures"
date: 2011-08-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-22
There has been a number of trials to build the new gnome-settings-daemon recently.
From the version 3.1.4-0ubuntu4 up to the version 3.1.5-0ubuntu3 of today all builds failed due to the dependency wait of the packages libcolord-dev (reason: missing build dependency).
What is funny is that the libcolord-dev is not missing from repos, it is in universe.

HERE:
[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.4-0ubuntu4](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.4-0ubuntu4)
[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.4-0ubuntu5](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.4-0ubuntu5)
[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.5-0ubuntu1](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.5-0ubuntu1)
[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.5-0ubuntu3](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.1.5-0ubuntu3)

---

### Post by mc4man on 2011-08-22
They're also missing a dep in the control.ini, (liblcms2-dev), I'm sure it will get squared shortly

---

