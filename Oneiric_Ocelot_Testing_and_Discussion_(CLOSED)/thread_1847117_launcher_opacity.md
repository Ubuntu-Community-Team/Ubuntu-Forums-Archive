---
title: "launcher opacity"
date: 2011-09-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-09-20
this problem has existed for about a week, not gone away.

i have ccsm launcher opacity set to 0, but while the launcher is transparent, it has a background that is several shades lighter than the wallpaper, any wallpaper. see attached.

any ideas other than unity--reset ?

---

### Post by mc4man on 2011-09-20
I believe that is a "feature", the launcher is now tinted off of the desktop background
I guess you could try a bug on that when set to 0 opacity it should be clear, though if it's in the 'design' then ...

Edit: here is the change in unity-4.16
 > - Launcher - the background of the Launcher should be tinted using the
      average colour of the wallpaper (LP: #850068)

---

### Post by flipper T on 2011-09-20
up to a week ago it was fully transparent & un-tinted.

if it is a feature, then a poor one that should be optional.

---

### Post by mc4man on 2011-09-20
> **flipper T said:**
> up to a week ago it was fully transparent & un-tinted.

if it is a feature, then a poor one that should be optional.
This was part of the unity upgrade from last thur. to 4.16

You should file a bug - you never know
For instance I had this one on the drop shadow on the unity panel, I wanted it gone when the panel opacity was at 0 - that's been fixed.
Additionally others wanted the shadow's opacity to match the panel's as you lowered it - currently in progress and may be implemented

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/747682](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/747682)

---

