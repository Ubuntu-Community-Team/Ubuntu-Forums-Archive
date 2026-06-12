---
title: "Finding a directory's creation date in Python...impossible?"
date: 2008-07-21
forum: Programming Talk
---

### Post by Tadpole on 2008-07-21
I tried using [Python's os.stat](http://docs.python.org/lib/os-file-dir.html), st_ctime in particular, but as the documentation states it only shows creation date in Windows -- on *nix, it only shows the last metadata modification date. I also tried st_birthtime, but that doesn't work in Linux.

Anyone have another suggestion for getting a directory's creation date?

---

### Post by ghostdog74 on 2008-07-21
you can use os.path.getmtime()

---

