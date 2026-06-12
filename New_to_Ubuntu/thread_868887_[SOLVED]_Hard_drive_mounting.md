---
title: "[SOLVED] Hard drive mounting"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by m_ad on 2008-07-24
My Western Digital My Book automatically mounts, which is nice. But I don't want the icon to appear on the desktop. How do I configure this?

---

### Post by stevoo on 2008-07-24
The only way to do this is to remove all the icons of the mounted partitions from you desktop.

If you are willing to do that 

press alt+f2 
type : gconf-editor
expand apps->nautilus->desktop 
and unclick volumes_visible.

---

### Post by nothingspecial on 2008-07-24
alt + F2
type ```
gconf-editor
```
Navigate to apps > nautilus > desktop
remove the tick from volumes_visible
done

[ATTACH]78782[/ATTACH]

---

### Post by ApOgEEs on 2008-07-24
from your Terminal **(Applications > Accessories > Terminal)** type:
```
gconftool-2 --set /apps/nautilus/desktop/volumes_visible --type bool false
```
* you may copy the code (select and Ctrl+C) and then paste it with (Shift+Insert) on your Terminal.

---

