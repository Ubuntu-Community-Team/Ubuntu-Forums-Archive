---
title: "Is there a metapackage that would install a minimal pure gnome3 environment?"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonnet on 2011-09-21
I used to install ubuntu from command line and then install minimal gnome environment by installing xorg and **gnome-session**.
Problem is that with Oneiric ,is still there the "gnome-session" meta-package.
But with my surprise, after i installed I found something completely different from what I was expecting: compiz is installed as default wm.
Even I want uninstall it, synaptic then would force me to install unity.

Is it possible to have (starting from a command line) a pure Gnome3 environment without unity or compiz?

---

### Post by jbicha on 2011-09-21
Debian has a meta-gnome3 package which should theoretically do this but it hasn't been released yet. The code is hiding [here]("http://anonscm.debian.org/viewvc/pkg-gnome/desktop/experimental/meta-gnome3/"). But probably someone here could give you a long apt-get install string to enter. I personally have no reason to remove Unity so I haven't bothered trying.

---

### Post by seeker5528 on 2011-09-21
No metapackage, but installing gnome-shell and, if it doesn't get pulled in automatically, gnome-session-fallback should be enough.

Later, Seeker

---

### Post by paul_in_london on 2011-09-21
This may not be exactly what you want, but I suggested a set of packages to install (on top of a minimal base system) in this thread:

[http://ubuntuforums.org/showthread.php?t=1845284&highlight=frugal](http://ubuntuforums.org/showthread.php?t=1845284&highlight=frugal)

---

### Post by jerrrys on 2011-09-21
Here's the way Im doing it from a terminal install:

First install a display manager.  I believe that LDM (lightdm) is the default install, but I have installed GDM (gnome Display manager).

Then install "gnome-panel".  This will pull in gnome3, gnome fallback and of course other packages.  This will not load gnome-shell.

With gnome-panel, comes compiz and unity.  Remove compiz and unity (3d) will be replaced with unity 2d.  I have not yet found a way to completely remove unity and since unity 2d works on my box, I want to keep it for now.

---

