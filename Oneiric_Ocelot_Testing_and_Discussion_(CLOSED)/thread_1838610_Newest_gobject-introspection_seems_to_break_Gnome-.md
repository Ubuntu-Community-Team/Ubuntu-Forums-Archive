---
title: "Newest gobject-introspection seems to break Gnome-shell"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-09-04
The newest gobject-introspection packages (gir1.2-freedesktop, gir1.2-glib-2.0, libgirepository-1.0-1, version 1.29.17) seems to break Gnome-shell.
I am talking about the gnome-shell (3.1.4) and mutter (3.1.4) from Oneiric repos.

When upgraded to (mutter and gnome-shell) to the version 3.1.90.1 (Ricotz Testing PPA), the Gnome-shell works just fine.
The issue can also be solved by downgrading gobject-introspection packages to the previous version 1.29.16.

Symptoms are:
GS starts OK, but the moment you move the mouse cursor to the hot spot of the left upper corner, GS crashes.

---

### Post by jbicha on 2011-09-04
That's an interesting diagnosis. It perhaps explains why I've been having such stability issues with GNOME Shell. I am able to run the Oneiric GNOME Shell but it takes several tries after a crash. I have to switch to a virtual terminal (Ctrl+Alt+F1), run DISPLAY=:0.0 gnome-shell --replace (the ---replace is optional in this case since gnome-shell has crashed) and then switch back to my main screen (Ctrl+Alt+F7 or in some cases, Ctrl+Alt+F8) and hope it works. Otherwise I have to try again.

However, I'm also having huge trouble with my indicators crashing in Unity or Unity 2D so I can't really run that today.

The reason GNOME Shell 3.1.90 isn't in the repositories is that GNOME Shell now has a (sorta-hidden) dependency on Caribou which isn't yet in the Ubuntu repositories. I expect Caribou to be straightened out within the week, but it needs a Feature Freeze Exception too.

---

### Post by pressureman on 2011-09-04
I'm seeing exactly the same symptoms as jbicha... usually after 2 or 3 attempts, it settles down, but this morning it took over ten attempts to get a stable desktop. Looking forward to this being resolved.

---

### Post by jbicha on 2011-09-04
All right, I can confirm that after upgrading gnome-shell, gjs, mutter, and clutter to the 3.1.90ish version, gnome-shell doesn't seem to be as crash-prone. I think we can get all of that uploaded within a few days assuming things go smoothly. It looks like we can cheat and avoid caribou for now, which should be easier than getting caribou and onboard to play nicely together.

Sorry that gnome-shell has broken so much this cycle but that's what happens during alpha. Fortunately, GNOME 3.2 development is almost over so things should stabilize soon.

---

### Post by Harry33 on 2011-09-04
I also had to update gjs (gjs, libgjs0c) version 1.29.17 and clutter (gir12-clutter-1.0, libclutter-1.0-0) version 1.7.12-1 before I could get gnome-shell running.
And yes, gir1.2-caribou-1.0 and libcaribou0 must be installed from Ricotz Testing PPA.
These are the other new gnome-shell dependencies (can be found on Oneiric repos):
- gir1.2-accountsservice-1.0
- gir1.2-gee-1.0
- gir1.2-folks-0.6
- gir1.2-gmenu-3.0
- libfolks25

---

