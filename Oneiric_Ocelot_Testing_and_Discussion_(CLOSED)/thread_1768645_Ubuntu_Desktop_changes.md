---
title: "Ubuntu Desktop changes"
date: 2011-05-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-27
Ubuntu Desktop (the default one originating from installation media) has changed or should I say evolved a bit.
The package name is ubuntu-desktop (1.223) and it is part of the meta package called ubuntu-meta.
As it is a meta package, it only serves to pull in dependencies.

Now these dependencies have changed so that these packages are removed (not installed by default):
> 
  * Removed alacarte from desktop
  * Removed compiz from desktop-recommends
  * Removed desktop-file-utils from desktop
  * Removed gconf-editor from desktop
  * Removed gnome-about from desktop
  * Removed gnome-applets from desktop
  * Removed gnome-icon-theme from desktop
  * Removed gnome-panel from desktop
  * Removed gnome-system-tools from desktop
  * Removed gnome-themes-ubuntu from desktop
  * Removed gtk2-engines from desktop
  * Removed gtk2-engines-pixbuf from desktop
  * Removed metacity from desktop
  * Removed pulseaudio-esound-compat from desktop


---

### Post by lucazade on 2011-05-27
> **Harry33 said:**
> Ubuntu Desktop (the default one originating from installation media) has changed or should I say evolved a bit.
The package name is ubuntu-desktop (1.223) and it is part of the meta package called ubuntu-meta.
As it is a meta package, it only serves to pull in dependencies.

Now these dependencies have changed so that these packages are removed (not installed by default):

I didn't expect metacity drop so early.. unity-2d, added to ubuntu-desktop some days ago, is still based on metacity and didn't switch yet to compiz. :confused:

---

### Post by chrisccoulson on 2011-05-27
> **lucazade said:**
> I didn't expect metacity drop so early.. unity-2d, added to ubuntu-desktop some days ago, is still based on metacity and didn't switch yet to compiz. :confused:

unity-2d depends on metacity, so there's no point in having it seeded

---

### Post by lucazade on 2011-05-27
> **chrisccoulson said:**
> unity-2d depends on metacity, so there's no point in having it seeded

ok, thanks! So I believe the same happens with compiz provided directly by unity-3d.

---

### Post by Harry33 on 2011-05-27
> **chrisccoulson said:**
> unity-2d depends on metacity, so there's no point in having it seeded

Also gnome-session-fallback depends on metacity.
Gdm recommends metacity.

---

