---
title: "CDs won't appear on the Desktop"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by MakotoTheKnight on 2008-07-28
I never had a problem with this before, but it seems that whenever I put a CD into the drive, it won't pop up an image on my Desktop.

I dunno what's going on with it, and I don't think I did anything super major to the system before this started to happen.

Any help is appreciated.

---

### Post by cprofitt on 2008-07-28
I would review your nautilus preferences using gconf-editor.

---

### Post by MakotoTheKnight on 2008-07-28
That presented me with a (very) confusing dialogue, I'd appreciate a little more clarification!  :)

---

### Post by spiderbatdad on 2008-07-28
gconf-editor: System>>Preferences>>Main Menu

in the left column, click on "system tools" then on the right, put a check in the box "gconf-editor.

Close all. Now from the Applications menu, select "system tools." Click gconf-editor.  You can avoid all this by pressing ALT+F2 and entering gconf-editor....anyway...

From gconf-editor navigate: Apps>>Nautilus>>Preferences...scroll down to Media Auto Mount and Media Auto Open...make sure both are selected.

---

### Post by MakotoTheKnight on 2008-07-28
Both are checked...so I tried entering a CD again to see if it'd appear on the desktop, and to no avail.

EDIT:  I found what to check.  It was in System > Apps > Nautilus, but it was volumes_visible.

Thanks to those that tried to help me.  :)

---

