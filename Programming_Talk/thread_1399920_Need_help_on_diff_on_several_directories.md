---
title: "Need help on diff on several directories"
date: 2010-02-06
forum: Programming Talk
---

### Post by razor7 on 2010-02-06
Hi...I need to compare the files on a directory with the files on another directoryto see which are different and in wich parts...

It is possible to perform a diff command on all files recursively?

Is there some kind of GUI program?

Thanks a lot!

---

### Post by Reiger on 2010-02-06
Meld, Kompare, ... . Meld is very good, it does 3 way compare/merges as well.

---

### Post by geirha on 2010-02-06
diff has a recurisve option, -r.

```
diff -ur /path/to/dir1 /path/to/dir2
```

---

### Post by razor7 on 2010-02-06
Thanks a lot, will try both.

---

