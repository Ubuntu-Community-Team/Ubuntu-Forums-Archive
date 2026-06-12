---
title: "Gnome-shell's Alt+F2"
date: 2011-08-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rorschachwalter on 2011-08-16
Is Alt+F2 broken in Oneiric's gnome-shell, or am I just missing a package?

Also, does anyone know why Alt+F2 in gnome-shell isn't able to launch all the programs that the terminal is able to? For instance, gconf-editor?

---

### Post by t.rei on 2011-08-16
Thats's a gjs error - we'll have to wait for an update.


[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/816762](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/816762)

---

### Post by pressureman on 2011-08-16
I found that Alt-F2, and many other shortcuts are were disabled. Just go into System Settings > Keyboard, and set them to what you want.

---

### Post by dsfitzpat on 2011-08-20
It seems odd that a gnome command people have used since the dawn of time would be disabled by default.  I was fairly comfortable with Unity because all my keyboard shortcuts still worked (and a few useful new ones were introduced) but gnome shell occasionally gives me the feeling that it was designed with the intention of annoying existing users.

---

### Post by jerrylamos on 2011-08-20
As of 19 August updates Alt-F2 worked.

Ctrl-Alt-t used to start a terminal session but not now.

Just tried: 
BFB > Systems Settings 
and xorg froze altogether.

Time for manual power off.

Jerry

p.s. Entered a launchpad bug #830319 since I could repeat the hang.

---

### Post by t.rei on 2011-08-22
Hm, this is still not working for me. (Just noticed when accidentally not using my xfrun4 launcher)

---

### Post by Quackers on 2011-08-22
For me neither.

---

