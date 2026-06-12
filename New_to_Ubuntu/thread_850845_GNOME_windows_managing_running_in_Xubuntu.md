---
title: "GNOME windows managing running in Xubuntu?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by mingle on 2008-07-06
Hi,

When I shut down Xubuntu (8.04) I notice that the console output says "Shutting down Gnome Windows Manager" (or similar).

Does Gnome run on Xubuntu?

Can anyone (without directing my to hundreds of pages of dry tech-talk!) explain what the relationship is between Linux, X-Windows and Xfce/Gnome/KDE?

I used to tinker with X-Windows on old DEC VMS boxes and understand that X-Windows sits on to of the actual OS, but I'm a bit vague on how X-Windows interacts with the desktop systems...

Any help or comments greatly appreciated!

Cheers,

Mike.

---

### Post by jw5801 on 2008-07-06
The message is 'Shutting down Gnome Display Manager.' GDM controls your graphical login and creation of an X session. KDE, Gnome, Xfce or any other desktop environment can run on top of GDM. The same applies for KDM (the KDE equivalent) and numerous other display managers.

As for the relationships:
Linux = kernel, handles all low level hardware interfacing and many other function.
X = A process that interfaces the user, kernel and graphics devices.
Xfce/Gnome/KDE = Desktop Environment, determines the pretty bits you actually see.

---

