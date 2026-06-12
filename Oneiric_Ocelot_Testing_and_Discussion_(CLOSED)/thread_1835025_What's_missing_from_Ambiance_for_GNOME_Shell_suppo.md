---
title: "What's missing from Ambiance for GNOME Shell support?"
date: 2011-08-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by jbicha on 2011-08-28
As those of you who've used GNOME Shell have seen, Ambiance & Radiance don't fully work in GNOME Shell. I know that some have hacked Ambiance to get it to display correctly. I'm willing to help shepherd those fixes into light-themes fixed but I don't know what specifically needs to be added to the themes.

---

### Post by bash on 2011-08-28
The problem is not with the GTK part but with the metacity theme part in [b]Ambiance/metacity-1/metacity-theme-1.xml[b].

Been a while since I toyed around with it, so just took a look at itagain  and from a quick test it just seems to be the **<shadow>** and **<padding>** entries in the **<!-- frame style -->** section that need to be removed. Attached my version of the **metacity-theme-1.xml** that works flawlessly in GNOME-Shell for me (Attached as .tar.gz since I can't upload xml directly).

---

### Post by lucazade on 2011-08-29
[https://bugs.launchpad.net/ayatana-design/+bug/800315](https://bugs.launchpad.net/ayatana-design/+bug/800315)

Default shell is unity so try to not sacrifice features like shadows only to support gnome-shell and ask directly to Cimi who worked on this stuff.

---

