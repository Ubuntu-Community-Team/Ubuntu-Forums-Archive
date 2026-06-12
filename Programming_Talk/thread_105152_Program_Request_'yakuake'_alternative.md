---
title: "Program Request: 'yakuake' alternative"
date: 2005-12-17
forum: Programming Talk
---

### Post by benplaut on 2005-12-17
in the Universe repos lies a usefull program called Yakuake - it is a pop-down terminal similar to those found in Quake and Doom.

with my very limited scripting experience, i've run into several brick walls trying to make an alternative. Although i'm not a coder, it seems that it should be a relatively simple task, possibly just a compilation of Alltray, devilspie, and a bit of clever working with minimizing and re-opening windows (my brick wall).

anyone know how to make something like that? (animations, etc like those in Yakuake are pointless, btw)

thanks,
Ben

---

### Post by cwaldbieser on 2005-12-17
[QUOTE=benplaut]in the Universe repos lies a usefull program called Yakuake - it is a pop-down terminal similar to those found in Quake and Doom.

with my very limited scripting experience, i've run into several brick walls trying to make an alternative. Although i'm not a coder, it seems that it should be a relatively simple task, possibly just a compilation of Alltray, devilspie, and a bit of clever working with minimizing and re-opening windows (my brick wall).

anyone know how to make something like that? (animations, etc like those in Yakuake are pointless, btw)

thanks,
Ben[/QUOTE]

I'm not sure I understand exactly what you are trying to do.  You didn't really expalin why you are making an alternative, and I am not exactly sure from the Yakuake home page what differentiates it from other terminal emulators.

---

### Post by benplaut on 2005-12-17
pretty much, how would i have a program open, then minimize (not showing on the tasklist or pager), on a key command, using to command to toggle the visibility.

i'm not really sure if it's easily possible, but i'm hoping ;)

---

### Post by cwaldbieser on 2005-12-17
[QUOTE=benplaut]pretty much, how would i have a program open, then minimize (not showing on the tasklist or pager), on a key command, using to command to toggle the visibility.

I'm not really sure if it's easily possible, but i'm hoping ;)[/QUOTE]

Well, in KDE, you can use the "dcop" command line utility to control the behavior of different KDE apps via shell scripts, so you could use KHotKeys to link a key command to a script that alternatively minimizes and hides a program, then maximizes and shows it.  You can play around with the "kdcop" GUI to get a feel of what you can do with it.

Not sure if that is the kind of thing you are looking for...

---

