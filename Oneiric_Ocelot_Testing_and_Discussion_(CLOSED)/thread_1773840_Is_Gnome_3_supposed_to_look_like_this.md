---
title: "Is Gnome 3 supposed to look like this?"
date: 2011-06-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xxhopingtearsxx on 2011-06-02
Because I'm assuming it's not. Looks like something from Windows 3.0.
Got Ubuntu 11.10 Alpha.
Unity's broken. Never had much experience with Gnome 3.

---

### Post by lucazade on 2011-06-02
> **xxhopingtearsxx said:**
> Because I'm assuming it's not. Looks like something from Windows 3.0.
Got Ubuntu 11.10 Alpha.
Unity's broken. Never had much experience with Gnome 3.

At the moment is normal because both theming engine (Unico) and theme (Ambiance) are not ready for Gtk3.

---

### Post by ranch hand on 2011-06-02
It looks like a working desktop to me.  I would say the blue background is there because the package is lifted straight from the Debian repo.  If it were a Debian install it would have a different background because it would be looking at (and I bet yours is) /usr/images/desktop-base for a particular image (don't know what it is called, don't have the new gnome stuff here at all yet on testing or Sid).  You need to set a wallpaper on it so that it is looking for a file that exists.

---

### Post by jfernyhough on 2011-06-02
Make sure you have gnome-themes-standard installed. By default GNOME3 uses the Adwaita theme, which isn't installed by default. :D

---

### Post by xxhopingtearsxx on 2011-06-02
> **jfernyhough said:**
> Make sure you have gnome-themes-standard installed. By default GNOME3 uses the Adwaita theme, which isn't installed by default. :D

Neat! Now it looks better.

I thought Gnome 3 had a dock. Is there a way to have a dock that always shows? Instead of only when I go to Activities..

---

### Post by NormanFLinux on 2011-06-02
Not in fallback mode. You'd be better off running Unity 2D in GNOME 3 if your graphics card can't support the accelerated version of GNOME Shell.

---

### Post by xxhopingtearsxx on 2011-06-02
> **NormanFLinux said:**
> Not in fallback mode. You'd be better off running Unity 2D in GNOME 3 if your graphics card can't support the accelerated version of GNOME Shell.

Oh dear God. Was I using Fallback mode?
Because when I first got 11.10 alpha, Gnome didn't work. It took me to fallback mode. What I'm using looks different.

---

### Post by uBeer on 2011-06-02
Looking at the screenshots: you're not in fallback mode.

What you have to do to make the dock stay is to install an extension. If you look on Wepupd8 or OMGUbuntu blogs, you'll be able to find how to do that and where to get some extensions.

Also, install gnome-tweak-tool. I hope for you it's in Oneiric's repositories. At least it's in the Gnome3 team ppa. And otherwise you can download it somewhere.

Edit: gnome-tweak-tool is an application with which you can easily change some interface settings in Gnome-shell/gnome3, stuff like fonts and themes.

---

### Post by Harry33 on 2011-06-02
> **xxhopingtearsxx said:**
> Oh dear God. Was I using Fallback mode?
Because when I first got 11.10 alpha, Gnome didn't work. It took me to fallback mode. What I'm using looks different.

No no, that is definitely gnome-shell session you have there, just without adwaita.

---

