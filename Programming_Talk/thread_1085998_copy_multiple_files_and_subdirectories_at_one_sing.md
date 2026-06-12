---
title: "copy multiple files and subdirectories at one single line"
date: 2009-03-03
forum: Programming Talk
---

### Post by flylehe on 2009-03-03
Hi,
I was wondering how to copy multiple files and subdirectories at one single line? For example, I want to copy two subdirectories /parent/child1 and /parent/child2 and their contents to be under /newparent using cp.
Is it the same as for scp?
Thanks!

---

### Post by Can+~ on 2009-03-03
What do you mean with "a single line"?

The way to move or copy a full hierarchy of files is using the -r flag (recursive).

---

### Post by flylehe on 2009-03-03
I mean copying several files and subdirectories not a hierachy.
Eg, can these be combined together: 
cp -r /parent/child1 /newparent, cp -r /parent/child2 /newparent and cp /parent/text.txt /newparent?

---

### Post by Can+~ on 2009-03-03
> **flylehe said:**
> I mean copying several files and subdirectories not a hierachy.
Eg, can these be combined together: 
cp -r /parent/child1 /newparent, cp -r /parent/child2 /newparent and cp /parent/text.txt /newparent?

Of course

```
cp -r parent/child1 parent/child2 parent/text.txt **as many as you want** newparent
```

if you check the manual on copy, you'll find that allows any amount of input directories. "Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY."

---

