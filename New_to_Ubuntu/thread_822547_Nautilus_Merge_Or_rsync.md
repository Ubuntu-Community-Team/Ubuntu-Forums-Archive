---
title: "Nautilus Merge Or rsync?"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by tdrusk on 2008-06-08
I have a lot of music on one external hard drive. I have almost the same music on my computers hard drive. I guess all the music didn't copy over, so now I am missing some folders that are on my external. Will the merge feature fix this or is it safer to use rsync?

---

### Post by quelx on 2008-06-08
Without knowing what Nautilus *merge* does under the hood, stick with **rsync**.
```
rsync -a --progress /path/to/source/ /home/me/incompletedest/
```
make sure to include the last *slash* at the end of each source and destination directory.

---

### Post by tdrusk on 2008-06-08
> **quelx said:**
> Without knowing what Nautilus *merge* does under the hood, stick with **rsync**.
```
rsync -a --progress /path/to/source/ /home/me/incompletedest/
```make sure to include the last *slash* at the end of each source and destination directory.
Yeah. I figured this would be the safest bet.

Will this just copy files? I don't want them moved off my external.

---

### Post by bruce89 on 2008-06-08
> **tdrusk said:**
> Will this just copy files? I don't want them moved off my external.

Yes.

---

