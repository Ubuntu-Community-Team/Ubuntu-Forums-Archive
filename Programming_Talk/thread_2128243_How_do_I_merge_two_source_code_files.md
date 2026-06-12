---
title: "How do I merge two source code files?"
date: 2013-03-22
forum: Programming Talk
---

### Post by jsmidt on 2013-03-22
Hey everyone,

     I have two files fileA and fileB that depend from common ancestor file.  I do not have access to that common ancestor file, just these two children. (So I can't use diff3) How do I merge these two different files?  Thanks.

---

### Post by MG&amp;TL on 2013-03-22
If I'm getting you right, fileA and fileB do not necessarily have the same information that the ancestor, fileC, has, so you can't. No version control?

---

### Post by The Cog on 2013-03-22
I find **meld** very good for comparing two files and combining them. It's in the repositories.
> meld file1 file2

---

### Post by jsmidt on 2013-03-22
Thanks.  meld looks like it might do the job.

---

