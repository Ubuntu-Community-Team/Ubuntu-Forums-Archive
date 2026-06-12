---
title: "emerald theme manager"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by waffleturd on 2008-11-13
i got emerald theme manager, however you need the themes.
So I got emerald themes through applications>add/remove.
But whenever I do that theres a popup stating unable to find emerald themes. Then there's another popup stating unable to find universal.
How do get this to work.

---

### Post by Shwefty on 2008-11-13
I didn't know you could go about Emerald that way.

I search for Emerald themes by some website like [http://art.gnome.org/]("http://art.gnome.org/") or typically more often [http://www.gnome-look.org/]("http://www.gnome-look.org/").  

There's typically instructions on how to install themes from there, but if not... You download the themes from the website (Emerald or Beryl themes).  Go System-> Preferences-> Emerald Theme Manager.  Then click import.  Occasionally drag and drop works too.

---

### Post by waffleturd on 2008-11-13
thnx

---

### Post by Hospadar on 2008-11-13
There's something wierd with emerald themes, it used to be that there were two packages in the ubuntu repositories, "emerald" which was the actual theme manager, and "emerald-themes" which had some stock themes in it.  For some reason or another, "emerald-themes" got removed from the repos, but emerald still suggests emerald-themes, which no longer exists

You can either:
install emerald from the command line "sudo apt-get install emerald" and it will just ignore emerald-themes, then you get find themes wherever and install them,

Or grab emerald-themes from the fiesty repos and install it by hand [http://packages.ubuntu.com/feisty/emerald-themes](http://packages.ubuntu.com/feisty/emerald-themes)

---

