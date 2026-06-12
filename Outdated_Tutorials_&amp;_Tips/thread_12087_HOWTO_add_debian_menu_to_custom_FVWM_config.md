---
title: "HOWTO: add debian menu to custom FVWM config"
date: 2005-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by stateq2 on 2005-01-21
This is for FVWM users who have a custom .fvwm2rc file, and want to add the debian auto menu to it.

right before the first "DestroyMenu" entry for the root menu, put insert this text:
```

Read /etc/X11/fvwm/menudefs.hook Quiet
Read menudefs.hook Quiet

```
then, somewhere in the main root menu area (the place where you add the main popup menus and stuff),  insert this
```

+ "Debian"                  Popup "/Debian"

```
restart fvwm, and you should have a new entry in your menu named "Debian", which contains all of the menu enabled software.

---

### Post by Tichondrius on 2005-01-21
why use primitive window manager, possibly with kudged add-ons, when you have an integrated desktop manager such as gnome ?

---

### Post by stateq2 on 2005-01-22
[QUOTE=Tichondrius]why use primitive window manager, possibly with kudged add-ons, when you have an integrated desktop manager such as gnome ?[/QUOTE]

I don't know....personally, over time, I've customized a .fvwm2rc config file to my liking....and I figured it would be nice if I could also use the debian menu w/ it.  if no one else finds it useful....oh well 8)

---

### Post by az on 2005-01-22
"f no one else finds it useful....oh well"

I think it is a great suggestion.  Many people need a quicker and simpler window manager for their desktop.    How would you compare FVWM with working menus to icewm of XFCE?

---

### Post by eNiNjA on 2005-01-22
[QUOTE=Tichondrius]why use primitive window manager, possibly with kudged add-ons, when you have an integrated desktop manager such as gnome ?[/QUOTE]
 
 wowee, and i put blackbox on my first ubuntu install, shame on me!
 
 nice work stateq2

---

### Post by jpkotta on 2005-09-23
[QUOTE=Tichondrius]why use primitive window manager, possibly with kudged add-ons, when you have an integrated desktop manager such as gnome ?[/QUOTE]
Why use a bloated desktop environment when a capable window manager is all that I need?  I use Linux because I have choices, and I choose fvwm.  Seriously, this comment is completely off topic.

Anyway, I like to use the latest fvwm, and that means building from source.  There's probably a way to easily generate a .deb file, but I don't know it.  I (and you too) can still use the debian menu, no problem.  Just add this to your ~/.fvwm/config:
```
DestroyFunc UpdateDebianMenu
AddToFunc UpdateDebianMenu
+ I     Exec test -f $[FVWM_USERDIR]/DebianMenu \
        && /bin/rm -f $[FVWM_USERDIR]/DebianMenu
+ I     PipeRead 'update-menus --menumethod $[FVWM_SCRIPTDIR]/fvwm.menu-method >/dev/null'
+ I     Read DebianMenu

UpdateDebianMenu
``` 
The menu-method file is in the debian directory in the fvwm source tree.  Also note that you need to install the "menu" package.

---

### Post by jpkotta on 2008-02-25
My above post is outdated.  See [https://help.ubuntu.com/community/FVWM](https://help.ubuntu.com/community/FVWM).

---

