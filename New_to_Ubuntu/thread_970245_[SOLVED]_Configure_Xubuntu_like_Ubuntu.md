---
title: "[SOLVED] Configure Xubuntu like Ubuntu?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by CJ Master on 2008-11-04
Hello there! Well I'm pretty torn up about this. I love my ubuntu desktop and gnome, and all the settings and such that I've toyed with. :P but i've tried out Xubuntu. I don't like the desktop and such as much as gnome. (for example, when I click on the applications menu, and then hover over places, on ubuntu it'd automatically switch over, but not in Xfce >.<) HOWEVER! I'm really enjoying the extra speed. (all my programs seem to run at least twice faster :guitar:)

So is there any way of getting the best of both worlds?

---

### Post by talsemgeest on 2008-11-04
Maybe try some different window managers, for example enlightenment. I can't think of any others right now, but there is sure to be one that suits you.

---

### Post by etnlIcarus on 2008-11-04
Xfwm4 is already an improvement over metacity, I see no need to try another window manager.

The reason the Apps/Places menus behave differently is because they're seperate panel plugins, rather than being part of the one gnome-panel applet.

As for the rest of your problems, if you actually told us what they were, we might be able to offer solutions.

---

### Post by CJ Master on 2008-11-04
List you say?

The aplications menu looks too diffrent and small, the system tabs are in applications (which just seems so wrong after using gnome.), my desktop seems more cluttered then it needs to be, plus I cant get the stupid clock out of 24 hour time >.<

---

### Post by etnlIcarus on 2008-11-04
Add this to your .gtkrc-2.0 file to make the apps menu icons bigger:

```
gtk-icon-sizes="gtk-menu=24,24"
```

You can use the menu editor to create custom menu files so if you want a seperate system menu, it shouldn't be too hard (though it will be time-consuming).

If the desktop is cluttered, go to the second tab of the desktop settings and either disable all icons or disable the default ones. You can also change the icon and text size.

As for the clock, all you should need to do is right-click on it and go to properties.

---

