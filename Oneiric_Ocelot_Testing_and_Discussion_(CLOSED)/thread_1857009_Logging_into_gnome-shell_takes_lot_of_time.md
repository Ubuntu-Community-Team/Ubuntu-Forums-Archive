---
title: "Logging into gnome-shell takes lot of time"
date: 2011-10-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rapiertg on 2011-10-09
While logging into unity 2d takes about 5 seconds, doing it for shell takes about a minute. I was curious if it is normal. Disabling all of startup apps helps a little (about 10 seconds). Weird is, that if i log out from shell and that log in again it takes just a few seconds then. I prefer to ask, before ill mess things worse trying fix it.

---

### Post by sgage on 2011-10-09
> **rapiertg said:**
> While logging into unity 2d takes about 5 seconds, doing it for shell takes about a minute. I was curious if it is normal. Disabling all of startup apps helps a little (about 10 seconds). Weird is, that if i log out from shell and that log in again it takes just a few seconds then. I prefer to ask, before ill mess things worse trying fix it.

Hmmm... I've not experienced this. If anything, Unity takes a few seconds more than GS.

---

### Post by tista on 2011-10-09
Hi rapiertg, 

OMG... never experienced... :S

So did you see any faults in .xsession-errors?
Mine seems to be fastest than any other composited desktop session, obviously than even unity-2d...

cheers.

---

### Post by rapiertg on 2011-10-09
Thanks.

Tista, according to file you suggested, my config files were screwed. Lots of errors about gsetting, schemas, etc. Looks like my upgrade went not very well...

Purged all .local .gnome2 .gconf .gconfd and every conf file i found in my dir.

Before 1:30 (only login took that much, not whole boot)
Now 0:15
:guitar:

---

