---
title: "upgrade failing"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-08-30
trying to upgrade from 11.04 to 11.10

i get the errors shown in the screenshots and then upgrade stops

any ideas ?

---

### Post by NightwishFan on 2011-08-30
The first one is not an error. Perhaps the mirror is out of sync? Try changing to the official main ubuntu mirror in software sources before you do the upgrade.
Edit: What does it say in /var/log/dist-upgrade/?

---

### Post by flipper T on 2011-08-30
this is the error in the main log

> 2011-08-30 21:58:34,341 ERROR No 'ubuntu-minimal' available/downloadable after sources.list rewrite+update

will try main mirror

---

### Post by ranch hand on 2011-08-30
You really should just go and look at your /etc/apt/sources.list.  Make sure it is correct.

This is a good thing to do before any upgrade so that you can comment out any strange repos that may have been added to your list.  These do not make upgrades work well.

A bad address or a repo not included will cause problems, such as not finding packages.

---

### Post by flipper T on 2011-08-30
changing to main server did the trick

thx

:)

---

