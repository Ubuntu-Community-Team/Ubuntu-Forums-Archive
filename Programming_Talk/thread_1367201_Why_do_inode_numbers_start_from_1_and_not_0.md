---
title: "Why do inode numbers start from 1 and not 0 ?"
date: 2009-12-29
forum: Programming Talk
---

### Post by manavendra on 2009-12-29
The C language convention counts array indices from 0. Why do inode numbers start from 1 and not 0 ?

I am currently reading "The design of the Unix Operating System" by Maurice J Bach and was struck on this question from the exercises.

As I am a newbie, i guess inode 0 may be reserved for some special files or mount points like "/". What is the exact answer?

---

### Post by dhillonv10 on 2010-01-01
I think the inode 0 is kept for all the meta-data about the directory that you are currently in (please correct me if I am wrong)

---

