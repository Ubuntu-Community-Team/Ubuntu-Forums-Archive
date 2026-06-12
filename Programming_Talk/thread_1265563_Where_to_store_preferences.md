---
title: "Where to store preferences?"
date: 2009-09-13
forum: Programming Talk
---

### Post by hofsmo on 2009-09-13
I'm writing an app in Gtk+ an need to store some preference regarding layout, plugins etc. And I'm wondering where the best place to store this information is? I see that some apps have hidden folders in my home folder, however many of them also have folders in ~/.local/share, ~/.gnome2 and in ~/.gconf/apps. Some of the folders are even empty.

Since I'm developing in Gtk+ the best is probably to follow the gnome convention, my understanding are that I'm supposed to use GConf, but why do most of the apps have folders scattered all over the place?

Does anyone know how to do it standardized and clean?

---

### Post by Nevon on 2009-09-13
The hidden folders are most times used for resources of different kinds. For example, with [Caffeine](http://www.blastfromthepast.se/caffeine) we're putting the list of applications that should cause Caffeine to activate in ~/.local/share/caffeine/. However, preferences that can easily be represented by a single character or a string or something, Gconf is pretty much perfect for that.

---

### Post by jpkotta on 2009-09-13
Personally, I prefer it when an app has it's own .dir/ or .file in $HOME.  I don't use a desktop environment.  If this app is supposed to integrate pretty well with Gnome or KDE, follow their convention, otherwise, just make your own.

I think freedesktop.org has some sort of standard to have apps store things in ~/.config/.  I don't really understand the advantage, because all you're doing is moving the clutter from one dir ($HOME) to another ($HOME/.config).

---

### Post by linkmaster03 on 2009-09-13
I agree with jpkotta. Unless your program uses GNOME libraries or integrates with GNOME, you shouldn't use gconf. I don't use a desktop environment either (nor Ubuntu, but still). You should store configuration in ~/.config/[app_name]/.

---

### Post by hofsmo on 2009-09-15
Many thanks, I think I'll go for ~./config at the moment, however there are plans about a GConf based on d-bus, which as I understand would make it more compatible with more systems . Though it looks like it's some controversy surrounding it, maybe it will come with gnome 3?

---

