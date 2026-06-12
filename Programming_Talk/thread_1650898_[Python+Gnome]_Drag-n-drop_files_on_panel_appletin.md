---
title: "[Python+Gnome] Drag-n-drop files on panel applet/indicator applet"
date: 2010-12-22
forum: Programming Talk
---

### Post by spupy on 2010-12-22
I'm writing a small python application that should be located on the gnome panel and accept file (and possibly text) drag-and-drops.

The direction that I've taken now is to create the application as a gnome panel applet. File drag-and-drop works, and it seems I might be able to include all other futures that I wanted to.

BUT I recently found out that panel applets will be deprecated in favor of indicators. Indicators seem to be the future, although I personally find their concept stupid (restricting customization of panels, etc; but that is not the point.)

So I started to read about python libindicate. By the way, the documentation for python is absent, the C docs consist of the bare minimum (but that is the point of another rant). Still, turns out creating an indicator applet is much much easier than creating panel applets. But it seems they  don't have DnD. In the few indicator applets that I've seen none had any DnD functionality.

So is it possible? Drag-and-drop on indicator applets?

---

