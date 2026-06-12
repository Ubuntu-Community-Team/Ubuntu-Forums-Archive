---
title: "2 second mouse freeze"
date: 2011-08-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kanishkdudeja on 2011-08-08
im experiencing very strange 2-2 second mouse freezes regularly while using ubuntu 11.10 alpha 3..

any idea as to why this is happening? and as to how could it be solved?

---

### Post by lucazade on 2011-08-08
Don't know if it is the same issue you get but while using the keyboard the touchpad is automatically disabled in Oneiric and there is a little delay when you start to use the mouse again.
If this is the same behaviour you can disable it from mouse capplet in control-panel.

---

### Post by MacUntu on 2011-08-08
Hehe, unusable feature since '09:

[https://bugzilla.gnome.org/show_bug.cgi?id=590783](https://bugzilla.gnome.org/show_bug.cgi?id=590783)

It's a GNOME thing.

---

### Post by mc4man on 2011-08-08
This was a change from the previous 0.5 second 'disabling the touchpad' when using keyboard to 2 sec.'s to accommodate users with larger touchpads (mac style

It can be annoying, as mentioned you can disable this in your mouse settings or rebuild gnome-settings-daemon and return the 0.5 value

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/801763)

---

### Post by kanishkdudeja on 2011-08-09
thanks..i disabled the option "disable touchpad while typing" and it got solved..thanks a lot :)

---

