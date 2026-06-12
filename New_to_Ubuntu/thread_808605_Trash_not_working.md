---
title: "Trash not working???"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by d.kusummmanth@gmail.com on 2008-05-26
When I'm deleting any file, for e.g., of 700 MB or 1.4 GB, the Filesystem is **not showing an increment of free space** of more than 48 MB!!! Why?

---

### Post by shae on 2008-05-26
After you delete, are you clearing your trash or leaving it in there?

---

### Post by d.kusummmanth@gmail.com on 2008-05-27
> **shae said:**
> After you delete, are you clearing your trash or leaving it in there?
i'm clearing the trash. even then, there is no use. Plus, my harddisk is nearly full.

---

### Post by sayakb on 2008-05-27
Don't send the files to Trash then. Either Shift+Delete them or open Nautilus preferences, goto Behavior tab and check the "Include a delete command..." option and "Delete" your files rather than Move to trash.
Also, do this:
```
sudo rm -rf ~/.local/share/Trash/files
```

---

