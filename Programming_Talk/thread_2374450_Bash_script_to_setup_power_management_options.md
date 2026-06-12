---
title: "Bash script to setup power management options"
date: 2017-10-16
forum: Programming Talk
---

### Post by erotavlas on 2017-10-16
Hi,
I'm interested about creating a bash script that allows to setup power management options as in control panel of gnome classic or other GUI manager.
I would like to change monitor dim and sleep timeout and system sleep inactivity timeout. I know that since ubuntu 16.04 is used systemd and I found [this documentation]("https://www.freedesktop.org/software/systemd/man/logind.conf.html") about ```
/etc/systemd/logind.conf
```.
I can only change system sleep inactivity via, e.g.:
```
IdleAction=hibernate
IdleActionSec=30min
```
How can I change other parameters? Is there any better way than systemd?

Thank you

---

