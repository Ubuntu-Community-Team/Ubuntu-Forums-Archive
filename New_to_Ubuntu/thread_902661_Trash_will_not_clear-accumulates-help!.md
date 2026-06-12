---
title: "Trash will not clear-accumulates-help!"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Hoofinit on 2008-08-27
Error states the file was deleted already and just goes from trashed info to trashed files, adding a 1 each attempt at deletion... how to delete this trash?

---

### Post by nkri on 2008-08-27
Try selecting all the files you want to delete and press Shift+Delete.  This should delete them for good:)

Good luck!
-nkri

---

### Post by Hoofinit on 2008-08-27
ok trash shows as emptied but gives error file doesn't exist and then see them as accumulating under /cbs/.Trash-0 1 folder is info, 1 folder is files totaling approx 6 mb of space; do we delete the folder?

---

### Post by cariboo on 2008-08-27
Navigate to .local/share/Trash and delete everything tin the files and info directories. To view hidden files and directories, in Nautilus (Places-->Home Folder) press Ctrl-h or View-->Show Hidden folders. You may have to be root to delete the files, if so, press Alt-F2 then type:

```
gksu nautilus
```

Jim

---

