---
title: "Freeze at Shut Down"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-05-28
Hey guys, so when i shut down my machine using Hardy, the shutdown gets to its final part where the orange bar goes down, the orange bar goes all the way down and disappears, but then it just stops at that point. The Ubuntu logo and the bar outline are still there. If anyone knows how to fix this, or has had problems in the past please let me know :)

---

### Post by ARhere on 2008-05-28
When it does that, press CTRL+F1 (*it may be CTRL+F2, I cannot remember.  Try a couple as it is to early in the morning right now*) to see the current status of the shut-down and were it stopped.

-AR

---

### Post by gali98 on 2008-05-28
How old is this computer? You may have to put "acpi=force" in your /boot/grub/menu.lst by the kerenel you use.
That's what I did.
Kory

---

### Post by Codemastadink on 2008-05-28
> **gali98 said:**
> How old is this computer? You may have to put "acpi=force" in your /boot/grub/menu.lst by the kerenel you use.
That's what I did.
Kory

The computer is old, and i do get a message saying something about acpi=force when i start it also, but it boots just fine. Hwo would i go about doing that? just open the file and edit the text?

---

