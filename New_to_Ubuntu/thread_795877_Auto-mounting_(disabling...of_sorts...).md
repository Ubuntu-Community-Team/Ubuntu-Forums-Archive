---
title: "Auto-mounting (disabling...of sorts...)"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by cong06 on 2008-05-15
Is there a way to prevent mounted drives from showing up as icons on the desktop?

I want them to still mount, just not show up as icons on the desktop...

---

### Post by PurposeOfReason on 2008-05-15
Open up gconf ('gconf' in a terminal) and go from apps -> nautilus -> something about desktop icons.

---

### Post by UnWarierMage224 on 2008-05-15
I think the command is gconf-editor
... Under nautilus folder in gconf-editor there is desktop folder, in that at the bottom there is tickbox "volumes-visible"... untick that and any mounted volumes on your desktop will go away, but still be accessible. 

-'Mage

---

### Post by cong06 on 2008-05-16
well, for hardy you were both half right.

terminal:
```
gconf-editor
```

then
apps -> nautilus -> desktop

uncheck volumes_visible


Thanks both.

---

