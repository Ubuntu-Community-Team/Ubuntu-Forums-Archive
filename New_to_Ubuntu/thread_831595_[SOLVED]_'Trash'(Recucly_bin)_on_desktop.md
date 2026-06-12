---
title: "[SOLVED] 'Trash'(Recucly bin) on desktop"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Kronie on 2008-06-17
how do u make one? 0_o the only one i have is on the AWN..

---

### Post by jordanmthomas on 2008-06-17
```
gconftool-2 --set /apps/nautilus/desktop/trash_icon_visible --set --type bool true
```

---

### Post by Daedal Dementia on 2008-06-17
system>preferences>main menu.

enable configuration editor under system tools.


applications>system tools>configuration editor.



drop down "apps"



scroll down to "nautilus"


drop down "nautilus"


scroll to "desktop" under "nautilus"


on the right side you should be able to ping "trash icon" to visible.

---

### Post by Daedal Dementia on 2008-06-17
wow i wasted my time lol

---

### Post by Kronie on 2008-06-17
thanx :P

---

