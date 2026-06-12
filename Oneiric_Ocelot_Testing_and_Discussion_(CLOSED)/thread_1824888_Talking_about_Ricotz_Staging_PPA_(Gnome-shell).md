---
title: "Talking about Ricotz Staging PPA (Gnome-shell)"
date: 2011-08-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-14
I am constantly using Oneiric with Gnome-shell installed and Unity completely purged
(well almost, as Nautilus depends on libunity5, which is not funny).

Anyways, Ricotz PPA works well, except the gobject-introspection package group.
Lately it has been broken (version 1.29.17~git20110810.d19fcd09-0ubuntu1~11.10~ricotz0 is the latest). It kills the panels of Gnome-shell.
I have solved that by using the one from Oneiric repos (1.29.16-0-ubuntu1).

Someone else seeing this too?

---

### Post by Captain James T Kirk on 2011-08-14
I believe this is simalar to what many are experinecing.

---

### Post by Harry33 on 2011-08-14
> **Captain James T Kirk said:**
> I believe this is simalar to what many are experinecing.

Yes, I thought so.
Thanks

---

### Post by sgage on 2011-08-14
> **Harry33 said:**
> I am constantly using Oneiric with Gnome-shell installed and Unity completely purged
(well almost, as Nautilus depends on libunity5, which is not funny).

Anyways, Ricotz PPA works well, except the gobject-introspection package group.
Lately it has been broken (version 1.29.17~git20110810.d19fcd09-0ubuntu1~11.10~ricotz0 is the latest). It kills the panels of Gnome-shell.
I have solved that by using the one from Oneiric repos (1.29.16-0-ubuntu1).

Someone else seeing this too?

I have been running GS practically exclusively, but the stock version from the repos. I gave up on ricotz I guess because of the problem you are describing. I'd like to try it though... 

Which packages would I want to pin in order to keep the OO versions? I notice that the package gobject-introspection itself is not even installed. Would I just pin everything that's version 1.29.16, or everything gir1.2, or some subset?

---

### Post by Harry33 on 2011-08-14
> **sgage said:**
> I have been running GS practically exclusively, but the stock version from the repos. I gave up on ricotz I guess because of the problem you are describing. I'd like to try it though... 

Which packages would I want to pin in order to keep the OO versions? I notice that the package gobject-introspection itself is not even installed. Would I just pin everything that's version 1.29.16, or everything gir1.2, or some subset?

You should pin all these three from that group:
- gir1.2-freedesktop
- gir1.2-glib-2.0
- libgirepository-1.0-1

All others work well ATM (though I don't use gs-extensions):
- clutter-1.0 + cogl
- gtk+3.0
- mutter
- gnome-shell
- pango
- gnome-themes-standard
- gjs
- glib2.0
- gtksourceview3

---

### Post by sgage on 2011-08-14
> **Harry33 said:**
> You should pin all these three from that group:
- gir1.2-freedesktop
- gir1.2-glib-2.0
- libgirepository-1.0-1

All others work well ATM (though I don't use gs-extensions):
- clutter-1.0 + cogl
- gtk+3.0
- mutter
- gnome-shell
- pango
- gnome-themes-standard
- gjs
- glib2.0
- gtksourceview3

I pinned those three packages and upgraded to ricotz, but no panel or launcher. I ppa-purged back to stock OO. Is there anything improved or markedly different in the ricotz build?

---

### Post by Harry33 on 2011-08-14
> **sgage said:**
> I pinned those three packages and upgraded to ricotz, but no panel or launcher. I ppa-purged back to stock OO. Is there anything improved or markedly different in the ricotz build?

The best change is that the effects (movement from and to the overview) run smoother from the version 3.1.4 (gnome-shell, mutter).
I cannot tell any difference with the git versions of gjs, glib2.0, pango or gtksourceview3 though.

---

### Post by dino99 on 2011-08-15
> **Harry33 said:**
> I am constantly using Oneiric with Gnome-shell installed and Unity completely purged
(well almost, as Nautilus depends on libunity5, which is not funny).

Anyways, Ricotz PPA works well, except the gobject-introspection package group.
Lately it has been broken (version 1.29.17~git20110810.d19fcd09-0ubuntu1~11.10~ricotz0 is the latest). It kills the panels of Gnome-shell.
I have solved that by using the one from Oneiric repos (1.29.16-0-ubuntu1).

Someone else seeing this too?

Looking at my installed packages, this one is needed by any other, so its not installed.

---

### Post by jbicha on 2011-08-15
> **Harry33 said:**
> Anyways, Ricotz PPA works well, except the gobject-introspection package group.
Lately it has been broken (version 1.29.17~git20110810.d19fcd09-0ubuntu1~11.10~ricotz0 is the latest). It kills the panels of Gnome-shell.
I have solved that by using the one from Oneiric repos (1.29.16-0-ubuntu1).

I definitely do not recommend using Ricotz' development PPAs.

If things go as I expect, Gnome Shell 3.1.5 (& the rest of Gnome 3.1.5) should be in the repositories within a week. And Gnome's development release cycle is almost over so you should just be able to use the regular repositories from here on out.

We never got Gnome Shell 3.1.4 in because we were waiting on dependencies to get packaged.

---

### Post by sgage on 2011-08-15
> **jbicha said:**
> I definitely do not recommend using Ricotz' development PPAs.

If things go as I expect, Gnome Shell 3.1.5 (& the rest of Gnome 3.1.5) should be in the repositories within a week. And Gnome's development release cycle is almost over so you should just be able to use the regular repositories from here on out.

We never got Gnome Shell 3.1.4 in because we were waiting on dependencies to get packaged.

Every time I try to use the ricotz ppa, I end up having to reinstall. Which I have just done with today's daily build.

---

### Post by Harry33 on 2011-08-15
> **jbicha said:**
> I definitely do not recommend using Ricotz' development PPAs.

If things go as I expect, Gnome Shell 3.1.5 (& the rest of Gnome 3.1.5) should be in the repositories within a week. And Gnome's development release cycle is almost over so you should just be able to use the regular repositories from here on out.

We never got Gnome Shell 3.1.4 in because we were waiting on dependencies to get packaged.

That is some very good news.

---

### Post by Harry33 on 2011-08-15
Hmm, just installed the fresh git version of gobject-introspection from Ricotz PPA
(1.29.17~git20110815.684bc338-0ubuntu1~11.10~ricotz1).

It is not running well at all.
The moment I put mouse cursor over the panel, all panels die instantly.
So only Oneiric official version of gobject-introspection works fine here.

---

### Post by bmbaker on 2011-08-16
The latest update from the ppa have fixed this problem :-)
i am getting itchy to install Oneric on my main machine though :-) :-)

---

### Post by Harry33 on 2011-08-16
The latest update is this:

clutter-1.0  v. 1.7.11~git20110816.98b3834d-0ubuntu1~11.10~ricotz0

And yes I can also confirm the panels do not crash anymore.
Anyway, Oneiric is upgrading Gnome3 to v. 3.1.5, that will make things easier.
Just noticed that glib2.0_2.29.16 is building in Launchpad and soon in repos.

---

