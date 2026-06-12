---
title: "[SOLVED] sudo in GUI?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by Line on 2008-09-09
Hi! I want to be able to edit the root files from the "File Browser" in the ubuntu 8.04.. How is this possible? Thanks

---

### Post by bobnutfield on 2008-09-09
Alt+F2, then in the box type:

> gksudo

But, be careful what you edit or delete.  This command gives complete root priveleges

---

### Post by wolfen69 on 2008-09-09
```
gksudo nautilus
``` to be specific

---

### Post by SunnyRabbiera on 2008-09-09
also you can try the nautilus administration mode package too, it should give you extra options when clicking on a folder/file.

---

