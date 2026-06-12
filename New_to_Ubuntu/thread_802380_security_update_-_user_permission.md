---
title: "security update - user permission"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-05-21
Will security update download and install if a user is logged, with only user permission or do they need to be admin permission to install?

Is there a way for there to be a admin account just to allow updates, so they couldn't install any new apps just patches?

Cheers

---

### Post by hovzio on 2008-05-21
You need to have root permissions to install anything, so no, an ordinary user cannot install updates. Only users in the admin group have root access using sudo and gksudo. (that is for ubuntu) Go to system, administration, users and groups, and under properties, click the user privledges tab. There you can customize your account. I'm not sure if you can just allow the security updates and not any other software. This is a wild guess.. maybe one could set up a crontab to run as root and periodically check/install the updates?? Like I said, just a guess.

---

