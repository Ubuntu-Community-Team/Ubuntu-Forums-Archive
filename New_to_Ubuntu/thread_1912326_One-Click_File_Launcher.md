---
title: "One-Click File Launcher?"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-01-20
I have a number of files I want to get at quite frequently.
Before Unity, this was easy - I had launchers/links on the top panel with small custom icons.
One click & voila!

Since Unity, I can't find any convenient solution.
The best so far is to put links on the desktop, but that looks a mess & getting to the desktop is at least a 2-click process in itself (or a 3-finger process which is worryingly similar to C/A/Delete & to be avoided for that reason).

Is there a good answer?

Best would be to be able to pin launchers on the top panel again. PLEASE!
Another obvious solution would be to be able to pin favorite file launchers in the Dash, as it opens, without further digging. I would happily have a full-screen dash if I could pin links to all my favorites in it.
A distant third best might be to be able to pin launchers to THE Launcher, but mine is already overloaded with apps. (I have seen some workarounds to make files available after right-clicking launcher icons, but the procedure looks messy).
Another might be to be able to pin launchers in Nautilus immediately as it is opened from the Launcher, but all this is getting further from One-Click.
The existing bookmarking system in Nautilus is somewhere near, but only works for folders, not files, as far as I can see?

Surely there must be some way?

---

### Post by Fernhill Linux Project on 2012-01-20
Typing ```
gnome-panel
``` in a teminal will launch gnome panel and display it over the unity top bar, and closes when you exit the terminal. I have not played around with it too much but you can probably pin launchers and files to it and set it to run at startup. Hope that helps.

EDIT : Just checked and it does what you want :o) but you need to use alt F5 to restore maximised windows. Gnome shell classic may be a better option if you really need this function, or perhaps cairo dock may be useful.

---

### Post by 2CV67 on 2012-01-21
Thanks!
I tried "gnome-panel" but it threw up warnings:
```
chris@Acer-desk:~$ gnome-panel

(gnome-panel:5789): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal `size_request' is invalid for instance `0xa1f5030'
```

and only half worked.

After a lot of struggling on this & other points, I have gone back to Gnome Classic & everything is wonderful again!

I now have one-click launchers on top panel for:
FF & TB & Picasa & Calculator & Text-Editor & Draw & Calc & 2 frequently used documents & Terminal & Synapt & Grsync & iScan & Shutter & System monitor & TB Firetray.

*[EDIT: & Hide-panel-buttons & Show-Desktop & Root-Nautilus & Root-Terminal & Big Red Quit button top left where all application quits are now, all this in space unusable in Unity...]*

If somebody had just invented Gnome Classic after Unity, I would have given them a medal. :D

I won't call this [SOLVED] because the problem is still open for Unity & maybe the Gnome Classic option will be withdrawn soon?

---

### Post by alphacrucis2 on 2012-01-21
.

---

### Post by 2CV67 on 2012-01-21
> **alphacrucis2 said:**
> Why don't you just put them on the unity bar?

I have not found how to put FILE launchers on the Unity Launcher bar.

I obviously (?) did put Application Launchers there OK, except that the icons are way too big so I have to keep scrolling up & down the bar.
So that makes it a 4-action move (Point to left edge, wait for Launcher, Scroll, Click) instead of a 2-action move (Point to icon, Click) with Classic.

Using Unity 2D it seems impossible to reduce the Launcher Key sizes:
[http://ubuntuforums.org/showthread.php?t=1910114](http://ubuntuforums.org/showthread.php?t=1910114)

---

