---
title: "Terminator--tranparency"
date: 2010-01-04
forum: Philippine Team
---

### Post by guitar_man on 2010-01-04
Mg sir patulong nga....


Pano ko ka enable yung transparency ng terminator na kagaya na sa terminal ko....Mas pogi kasi pag transparent na kagaya ng sa terminal..

Yung sa terminal kasi kita yung icon...Sa terminator ayaw.

---

### Post by loell on 2010-01-04
kung sa karmic ito, yung real transparency ng terminator ay hindi naka enable by default.

check mo lang yung configuration

**~/.config/terminator/config**

enable mo lang yung transparency

**enable_real_transparency = True**

---

### Post by guitar_man on 2010-01-04
Thanks for the tip sir loell

Question lang...Bakit wala sa ~/.config/terminator yung terminator config?


/usr/share/terminator/terminatorlib

---

### Post by pinoyskull on 2010-01-05
> **guitar_man said:**
> Thanks for the tip sir loell

Question lang...Bakit wala sa ~/.config/terminator yung terminator config?


/usr/share/terminator/terminatorlib
optional configs kasi ang nasa ~/.config/terminator kaya wala sya dyan by default :)

---

