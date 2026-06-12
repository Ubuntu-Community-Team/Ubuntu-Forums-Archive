---
title: "upper level import"
date: 2009-08-01
forum: Programming Talk
---

### Post by kumoshk on 2009-08-01
How do I import a module I wrote that is in the directory one above the code where I'm importing it?

i.e.

FolderX/toBeImported.py

FolderX/FolderY/projectWhereImported.py

Is there something like this
(in projectWhereImported.py)
import ../toBeImported.py
?

---

### Post by smartbei on 2009-08-01
If the folders are also python packages that are imported, you can use relative importing: [http://www.python.org/dev/peps/pep-0328/](http://www.python.org/dev/peps/pep-0328/)

Otherwise, you can either re-structure your project, or use execfile:
```

execfile("../file.py")

```
Note that execfile works according to the path that the script was run from, and not according to the script's location in the filesystem.

---

### Post by kumoshk on 2009-08-02
Hmm. I don't know that either of those suggestions will quite work for me.

I'm not dealing with packages. However, I've never created a package—so maybe learning more about this may help.

I need the objects and classes to be available in the calling module (not just to be run). Will they be available for manipulation after running them execfile, or will that just run them?

Restructuring the code is a last resort (if even that), unless there actually exists a good way to do it. I think I might see some ways to do it, though, but we'll see.

---

