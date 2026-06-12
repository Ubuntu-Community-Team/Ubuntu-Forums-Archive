---
title: "schedule updates 14.04"
date: 2016-02-23
forum: New to Ubuntu
---

### Post by tim148 on 2016-02-23
I searched old posts but they were very old and referenced older versions.  Is there any easy way to schedule updates so my computer doesn't grand to a halt while I'm trying to read the newspaper?

---

### Post by ian-weisser on 2016-02-23
Yes, rather easily.
Reschedule the apt cronjob currently in /etc/cron.daily

Are you really sure apt updates are the issue? That job has high nice settings specifically to prevent users from noticing it, and only one step (about 5 seonds) is CPU-intensive.

I find many web browser media (including news) uses much more cpu (and slows the system more) than background updates.

---

### Post by Geoffrey_Arndt on 2016-02-23
If updates are done regularly (without waiting till they're "huge"). . . they only take from 15 seconds to about 2-4 minutes, and _can run entirely in the background_.    But I don't know your situation, perhaps you're still connecting via a dial-up modem??.

---

