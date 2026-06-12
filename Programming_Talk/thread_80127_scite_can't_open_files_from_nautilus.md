---
title: "scite: can't open files from nautilus"
date: 2005-10-21
forum: Programming Talk
---

### Post by dudinatrix on 2005-10-21
Whenever I try and open a file with scite from nautilus, it tries to open it from the home folder (/home/david/file:/var/www/file.php)

Anybody know of a workaround for this?

---

### Post by dudinatrix on 2005-10-21
Ok, I figured out one workaround by creating a simple nautilus script in ~/.gnome2/nautilus-scripts/edit-scite

```
scite -open:$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
``` 
Seems to be working, although I still don't get why it wont just work by itself from nautilus. Does this happen with anyone else?

---

