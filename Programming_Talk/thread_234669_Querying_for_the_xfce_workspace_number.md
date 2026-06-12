---
title: "Querying for the xfce workspace number"
date: 2006-08-11
forum: Programming Talk
---

### Post by Liam on 2006-08-11
I'm attempting to be really l33t and go panel-less. I'm instead piping essential system info (clock, battery, etc) to a couple of shell scripts that run osd_cat and get called by hotkeys.

Anyway, one thing I'm missing is some way to figure out what virtual desktop I'm on without cycling through them. Is there a way to query xfce or xorg to return the number of the desktop I happen to be on?

I'd appreciate any other suggestions on a text-based workspace pager.

---

### Post by Liam on 2006-08-11
I should probably add that, while I'm aware of the xfce window list, I'd like something I can dump to my OSD without having to take my hands off the keyboard.

---

### Post by 23meg on 2006-08-11
I'm not sure if it will work with Xfwm but check out *wmctrl*.

---

