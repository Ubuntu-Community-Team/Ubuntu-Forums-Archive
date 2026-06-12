---
title: "[SOLVED] How to create a trash launcher?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by m_ad on 2008-07-23
I know the location and I know how to create the launcher. However, if you set the icon as an empty trash can, the icon doesn't change to a full trash can when it has something in it.

Is there a simple way to do this? Ultimately, I would like a launcher on Cairo-Dock, but if that's harder then just an icon on my desktop would be OK :)

---

### Post by PurposeOfReason on 2008-07-23
Cairo-dock has that applet with the cairdock-plugins package.

---

### Post by m_ad on 2008-07-23
> **PurposeOfReason said:**
> Cairo-dock has that applet with the cairdock-plugins package.

true, but it sets its own ugly icon for it :lolflag:


anyone know how to create a launcher with the empty/full icons?

---

### Post by Tim Sharitt on 2008-07-23
I can't help you on the cairo-dock, but here's how to put it on the desktop until someone else can.
 Hit Alt-F2 and type gconf-editor. Goto apps > nautilus > desktop and check the box beside trash_icon_visible. That's all there is too it.

---

### Post by m_ad on 2008-07-23
Thanks!

---

### Post by fabounet on 2008-07-24
edit the config of the "Dustbin" applet, then you can either select a theme or set 2 personnal images (one for empty and one for full trash)

Then you might want to detach the applet from the dock to place it on your desktop ;-)

---

