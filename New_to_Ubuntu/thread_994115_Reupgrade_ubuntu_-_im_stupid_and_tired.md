---
title: "Reupgrade ubuntu - im stupid *and tired*"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Dthorton15 on 2008-11-26
Okay so last night I was lying in bed using my laptop connected to putty SSH'd into my server and was upgrading it.. I guess I was really tired because I fell asleep right in the middle of the upgrade(LOL). My laptops battery ran out and I lost connection to my server right at the mysql part... I could enter Y/N/something else and I was so tired i hit t and enter.... goood times(this didnt do anything i just found it funny to share)

it works fine but I screwed some stuff up previously on 8.04 and was hoping that the update would fix it... the update didnt go completely so huzzah i fail.

This morning when I ran sudo do-release-upgrade it said I was up to date. OOPS! Is there a way to force a re-update? I wont fall asleep again, promise.

Sorry if this doesent make sense... I'm writing this 10 minutes after sleeping for 12 hours with my laptop on my chest all night.

---

### Post by Titan8990 on 2008-11-26
Anything you know that you might not of got to configure during updating you can do later. An example for mysql:


sudo dpkg-reconfigure mysql

---

### Post by Dthorton15 on 2008-11-26
did it, this is what i got

```
admin@host42:~$ sudo dpkg-reconfigure mysql
Package `mysql' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: mysql is not installed
```

---

### Post by Titan8990 on 2008-11-26
Sorry, try this:


sudo dpkg-reconfigure mysql-server

---

