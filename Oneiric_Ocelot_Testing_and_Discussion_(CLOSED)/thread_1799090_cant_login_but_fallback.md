---
title: "cant login but fallback"
date: 2011-07-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-07-07
every time i'm trying to login as "gnome" or "unity" or "unity-2d", i only get logged into "fallback" (no warning, no crash)

---

### Post by vhaarr on 2011-07-07
Same thing happened to me, then I noticed in .xsession-errors that GLX failed.

I reinstalled the nvidia package and then everything worked fine.

---

### Post by Harry33 on 2011-07-07
After a mesa update you always have to reinstall proprietary drivers.
Otherwise no 3D.

---

### Post by dino99 on 2011-07-07
i dont install .run file, only OO packages. To work around this issue:
- open additional drivers and uninstall the driver used, then select it again
- on next reboot the driver is back and the login issues gone, except for unity-2d on my side: it hardly flash a few seconds then desktop icons appear but no dash/menu nor unity icons.

Seems to be a compositing issue. Watch bug #806888

---

### Post by Quackers on 2011-07-07
> **Harry33 said:**
> After a mesa update you always have to reinstall proprietary drivers.
Otherwise no 3D.

Well that hasn't gone very well at all.
4 times I've removed nvidia-current and associated stuff and 3 times only fallback would boot to a usable desktop.
On my last attempt Unity now loads fully, but gnome-shell just loads an empty desktop.
Jockey-gtk in Unity shows that the nvidia-current driver is activated but not in use, even though the green light shows.
In gnome-shell I can't get that far. :(

---

### Post by Quackers on 2011-07-07
This is silly now. I've removed/re-installed nvidia-current 6 times. Unity and Classic boot ok, but gnome-shell boot s to a desktop with no top panel or dash.
Running Additional drivers says that nvidia-current is not installed, but it is. I installed via terminal. When I try to activate nvidia-current through additional drivers I get this! What's that all about :-)  Not allowed?

---

### Post by dino99 on 2011-07-07
some more cleanup done: removed .gconf, .gnome2, .local

After reboot get less troubles into logs file (some oldish applets removed)

---

### Post by Harry33 on 2011-07-07
Dino and Quackers,

Can you specify which update could have caused this?
You see I have fully updated 64-bit Oneiric with nvidia-current and gnome-shell works fine.
I have:
- mesa_7.11~1-0ubuntu3
- json-glib_ 0.13.4-2
- gobject-introspection_1.29.0-0ubuntu1
- gtk-3_3.1.8-0ubuntu1

---

### Post by Harry33 on 2011-07-07
Oh, and yes there is one thing, however.
I am using Ricotz Testing PPA, so I have newer clutter, mutter and gnome-shell packages than in Oneiric repos.

---

### Post by Quackers on 2011-07-07
> **Harry33 said:**
> Oh, and yes there is one thing, however.
I am using Ricotz Testing PPA, so I have newer clutter, mutter and gnome-shell packages than in Oneiric repos.
Harry33, I have no real idea what is causing the problem, though it was after mesa updated. I did see a clutter error at some time though.
As far as those packages are concerned I have the following

- mesa_7.11~1-0ubuntu3 
- json-glib_ 0.13.4-1 instead of 0.13.4-2 but -2 is showing as an update
- gobject-introspection_1.29.0-0ubuntu1 is available but not installed
- gtk-3_3.1.8-0ubuntu1 appears to be unavailable in synaptic
although gtk-3-examples appears in that version, but is not installed.

I don't have the ricotz ppa enabled.

I'll run the newest updates and get back to you.

---

### Post by Quackers on 2011-07-07
Oh dear.
After the latest updates and 3 attempted reboots I have got no keyboard/mouse action so I can't login at all now :-)
I'm back in Natty now :-(

Here's a screenshot of system monitor. No clutter or mutter.

---

### Post by cariboo on 2011-07-07
I still can't get gnome-shell from the repos to work, but I installed the fallback seesion, after re-installing nividia-current, and it works like it should.

---

### Post by Quackers on 2011-07-07
Maybe my alpha1 install is not everything it should be :-)
I'm downloading alpha2 and I'll try again. I won't install the nvidia driver until all updates have been run.

---

### Post by Harry33 on 2011-07-07
> **Quackers said:**
> Maybe my alpha1 install is not everything it should be :-)
I'm downloading alpha2 and I'll try again. I won't install the nvidia driver until all updates have been run.

The new mesa and drm packages should give a better nouveau experience concerning 3D.

---

### Post by Quackers on 2011-07-08
> **Harry33 said:**
> The new mesa and drm packages should give a better nouveau experience concerning 3D.

Thanks Harry33. Presumably that's with the experimental 3D driver?

---

### Post by Quackers on 2011-07-08
You were correct Harry33. The video performance is a little slower and a bit more jerky but the experimental 3D drivers are getting better all the time, it seems :-)
It's definitely a usable configuration.

---

### Post by Harry33 on 2011-07-08
After todays update (possibly libappindicator3-1 and libindicator3-6) the gnome--shell (from Oneiric repos) should work again.

---

### Post by Quackers on 2011-07-08
Lol, that installation has gone now :-)
I have other problems with my new alpha2 install (no Nvidia). Different thread.

---

