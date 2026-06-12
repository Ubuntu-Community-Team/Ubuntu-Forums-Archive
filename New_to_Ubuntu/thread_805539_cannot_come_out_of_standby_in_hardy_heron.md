---
title: "cannot come out of standby in hardy heron"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by philphil on 2008-05-24
I can go into standby fine but when I try to come out of it, all I get is a bunch of messages in a terminal window from network manager (I think) saying 'new device added', the password entry box to unlock the screen never appears.

The workaround is to press Ctrl+Alt+F7 to force it to switch to my GUI window thing (what's the real name for this? X Window?) which works fine except that Networking is always disabled so I always have to re-enable that and wait 10-15 secs or so for it to re-connect.  

This is ok but not what I'd expect from my O/S.

Come to think of it, it used to work on Gutsy and was even working for a time on Hardy but something seems to have changed...

Any ideas?

---

### Post by philphil on 2008-05-25
bump

---

### Post by philphil on 2008-06-01
bumpity-bump.

---

### Post by hotweiss on 2008-06-01
Edit /etc/default/acpi-support and make sure you have these valuse set like this:

POST_VIDEO=false

By default it is set to true.

---

