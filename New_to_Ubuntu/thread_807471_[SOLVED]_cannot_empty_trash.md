---
title: "[SOLVED] cannot empty trash"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by oliviacond on 2008-05-25
i tried to delete a folder in a trash. but it said "Permission denied".
so i manually delete it using terminal,
```

sudo rm -f trash:///_ktorrent-kde4_3.0.2

```
after that, i checked the trash, the folder is still there.
the folder didn't appear in "sudo nautilus", but appears in usual trash folder.

---

### Post by oliviacond on 2008-05-25
thanks, google.
```

sudo rm -rf ~/.local/share/Trash/files/*

```

---

### Post by jpeddicord on 2008-05-26
You'll most likely want to remove ~/.local/share/Trash instead of ~/.local/share/Trash/files. There is another directory in there that contains trash metadata that might make Nautilus think the files still exist if they aren't removed.

---

