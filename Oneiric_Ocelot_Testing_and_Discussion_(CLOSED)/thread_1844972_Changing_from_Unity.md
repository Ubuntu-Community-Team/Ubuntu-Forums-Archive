---
title: "Changing from Unity?"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by vDub2000 on 2011-09-16
I installed the beta of Ubuntu 11.10. I'm still not a fan of Unity, so I was wondering if there was any way for me to switch from Unity back to the classic theme? If so, how do I go about doing it?

---

### Post by dino99 on 2011-09-16
install gnome-session-fallback &  gnome-shell

---

### Post by Harry33 on 2011-09-16
> **vDub2000 said:**
> I installed the beta of Ubuntu 11.10. I'm still not a fan of Unity, so I was wondering if there was any way for me to switch from Unity back to the classic theme? If so, how do I go about doing it?

If it is the desktop shell environment you mean and not actually a theme, then you can do the following.

For the new Classic Ubuntu Desktop you can install the session package "gnome-session-fallback" (which depends on gnome-panel and metacity). It is, however, not actually the same as Classic Ubuntu used to be (in Maverick and earlier), but it looks like it a lot. It is based on GTK+3 and not the older GTK+2 toolkit.

Then again, if you like to have the default gnome desktop environment do the following.
Install in addition to the package gnome-session-fallback also the package gnome-shell (which depends on a number of other packages, like clutter and mutter).
In the default gnome setup, the fallback session (classic ubuntu) is used instead if the gnome-shell session (gnome) cannot be started.

---

