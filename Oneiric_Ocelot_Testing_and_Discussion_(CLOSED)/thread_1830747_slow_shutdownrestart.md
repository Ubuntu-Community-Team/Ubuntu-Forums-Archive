---
title: "slow shutdown/restart"
date: 2011-08-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-08-22
Any ideas why shutdown and restart routines are so slow in Oneiric compared
to Natty one?

This annoying behaviour is present on different machines and also with clean installations.

When the Ubuntu session is already closed (both unity-2d and 3d), there is a long, long delay before machine really restart or shutdown.
Also disabling plymouth splashscreen, to get more verbose output, I haven't seen anything particular about this delay.

note: when using unity-2d there is a delay also for closing this session.. the bug was report and is triaged for next releases, anyway not strictly related to my question.

---

### Post by mc4man on 2011-08-22
It does  in general seem slower but I've noticed that if using more than 1 session or if shutting down from 1 and restarting into another it takes awhile
(but this is after the login screen so maybe not what you're referring to.

---

### Post by lucazade on 2011-08-22
> **mc4man said:**
> It does  in general seem slower but I've noticed that if using more than 1 session or if shutting down from 1 and restarting into another it takes awhile
(but this is after the login screen so maybe not what you're referring to.

I haven't  tried to switch from a session to another, I'll try to see if I can figure out something useful.

Anyway I should have say "reboot" instead of "restart" to avoid misunderstandings (in italian are translatable in the same way, so here the error!)
Hope this way the question is better written.

---

