---
title: "2 different taskbars in Unity"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coco_loco on 2011-09-27
Hello all

I know that it is a kind of kamikaze behaviour, I use oneiric with compiz on a dualscreen system - not really stable but quite nice (dualscreen seems to be a problem child for compiz)!

Besides some regular crashes (had to disable screenlets which are sometimes blocking the whole system) there seem to be 2 independent taskbars, one on each screen. The one on the main screen does not overtake the opacity settings and stays black while the second one is transparent.

Looks like being once the Unity-2d and once the Unity-comiz-panel to me... do I have a config-mismatch? 

Thanks in advance for bringing some light in my dark

---

### Post by chicken159 on 2011-09-28
I seem to have a similar symptom, only I only have 1 screen - but if I set Panel Opacity to 0% (compizconfig - Unity Plugin), it reveals what looks like a panel hidden behind the Unity one with a set of nautilus menus "File Edit View Go Bookmarks Help". Kill nautilus and it disappears...does that work for you?

Wondering whether this is anything to do with getting Metacity crash reports...there's obviously something weird going on.

---

### Post by coco_loco on 2011-09-28
Nautilus is actually not drawing my desktop - I use wallpaper-plugin to draw my desktop (and I hate icons on the desk), so i had to disable nautilus' desktop control using the dconf-editor. I think we do not encounter the same problem since I do not have the nautilus menu appearing - perhaps you just have to disable nautilus from drawing the desktop.

I don't have metacity activated neither - my window-decorations run with emerald.

---

