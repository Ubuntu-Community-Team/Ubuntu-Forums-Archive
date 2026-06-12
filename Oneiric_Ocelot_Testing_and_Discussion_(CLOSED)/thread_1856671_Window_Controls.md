---
title: "Window Controls"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-10-08
Is there a way to get the window controls for a particular app on that window instead of on the top panel in unity?

---

### Post by mc4man on 2011-10-08
Sure - several ways - care to mention an app
Apps started from their desktop file can have an env set on the Exec= line, same if started from a quicklist entry.
If starting from a terminal then you can create an alias using an export or start the terminal itself with an env set, any app run from that terminal will do likewise

Typically for most apps I use
env UBUNTU_MENUPROXY=0 <app command here>
So Ex. audacious - the Exec= line in it's .desktop & or a quicklist
Exec=env UBUNTU_MENUPROXY=0 audacious

For qt4 apps I use  - Ex. vlc
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 vlc %U

(nautilus itself can be a bit 'tricky', I generally just let it have the G menu

---

### Post by mdhollis on 2011-10-09
Thanks.  That did the trick.

```
Exec=env UBUNTU_MENUPROXY=0 banshee
```

What about on a permanent basis?

---

