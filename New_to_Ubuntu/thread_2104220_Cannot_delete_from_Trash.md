---
title: "Cannot delete from Trash"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by ljr1981 on 2013-01-12
I have two items in my "Trash" that give this error response when attempting to "Empty the trash":

"Could not delete file /home/[name]/.local/share/Trash/files/[folder]/[garbage_characters]"

There are two folders (items) in the trash that both have this behavior. Can anyone give me clues about how to correct this problem?

Thanks

---

### Post by mapes12 on 2013-01-12
Terminal ```
gksu nautilus
```will open  Nautilus as root. In the /home/[user] folder hit Ctrl+h to reveal your hidden files. Find the .trash file then the items you need to get rid of. Highlight them then Shift+del to permanently delete. The shift+del operation is important otherwise all you will do is move the offending files into Root's trash and clog up your system.

Close down Nautilus. Close down Terminal.

---

### Post by entw on 2013-01-12
> **mapes12 said:**
> Terminal ```
gksu nautilus
```
```
kdesudo dolphin
```i guess.
And "Alt + ." to see hidden files.

---

