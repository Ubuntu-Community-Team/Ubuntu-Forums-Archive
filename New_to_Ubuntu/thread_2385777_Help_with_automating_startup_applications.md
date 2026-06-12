---
title: "Help with automating startup applications"
date: 2018-02-24
forum: New to Ubuntu
---

### Post by muaddibxx on 2018-02-24
Hey guys, I just installed ubuntu 17.10  and most things are working perfectly well so far. I'm primarily using it for HTPC duty, and as a music player from my phone. I want to be able to boot into ubuntu and startup my music player without ever turning on the tv. So far, I've got it to bypasses the user login from cold boot and suspend, the only issue is that I can't get clementine to start up automatically. I have a suspicion it's to do with me bypassing the login screen and no by definition starting a session. If anyone has any ideas, I would be very grateful!

Thanks,

Nadim

---

### Post by kerry_s on 2018-02-24
so you disabled the gui?
bypassing the login?

sounds like you did the whole thing in a round about way.

if it was me, simple setting the user to autologin and then adding clementine to startup, disabling lock in dconf-editor-> lockdown(for suspend)

other wise i just would have done a server install, if only for music.

---

