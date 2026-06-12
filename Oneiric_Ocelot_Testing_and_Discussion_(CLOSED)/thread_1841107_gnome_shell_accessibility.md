---
title: "gnome shell accessibility"
date: 2011-09-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by flipper T on 2011-09-08
how do i assign shortcuts for zoom in / zoom out ? see screenshot.

i would like to control this using mouse wheel & shift key to give graduated zoom.

i do this in unity using compiz.

possible in gnome shell ?

---

### Post by rbrick49 on 2011-09-08
I just use ctrl +

---

### Post by flipper T on 2011-09-08
that only works in some apps & generally does not affect menus.

there must be an option in gnome shell somewhere

---

### Post by flipper T on 2011-09-08
ok, found partial answer

goto keyboard / shortcuts / accessibility & you can assign keys for zoom in / out (doh!)

_2 minor problems_

1. cant figure out how to assign function to mouse wheel

2. the zoom increases / decreases in very large steps...i'm not that blind ! any way to reduce those steps / make smaller steps ?

---

### Post by jbicha on 2011-09-08
I agree that the Keyboard Settings part of Universal Access is confusing; I'm reporting a bug for that if it hasn't already been done but I think we may have to wait for the next GNOME/Ubuntu release cycle, and a fix depends on whether the designers think it's broken too.

For setting your font more precisely, please try gnome-tweak-tool.

---

### Post by flipper T on 2011-09-08
thx for your reply jbicha

now that i assigned keys to zoom on keyboard / shortcuts, the assignments are correctly displayed in the keyboard settings part of Universal Access.

the big issue for me is now that gradation of the zoom steps.

i have adjusted font sizes, but this does not affect all apps.

---

### Post by tobiasquinn on 2011-09-12
> **flipper T said:**
> how do i assign shortcuts for zoom in / zoom out ? see screenshot.

i would like to control this using mouse wheel & shift key to give graduated zoom.

i do this in unity using compiz.

possible in gnome shell ?

I've written a script which can be run at startup that sets left alt and mousewheel to zoom in and out of the gnome3 shell desktop.

On ubuntu it requires python-xlib. It's currently in a git repository at:

[https://github.com/tobiasquinn/gnome-shell-mousewheel-zoom](https://github.com/tobiasquinn/gnome-shell-mousewheel-zoom)

The script can be manually added to startup applications to run at login...

-Tobias

---

