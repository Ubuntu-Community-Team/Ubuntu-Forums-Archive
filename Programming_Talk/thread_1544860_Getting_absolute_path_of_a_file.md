---
title: "Getting absolute path of a file"
date: 2010-08-03
forum: Programming Talk
---

### Post by sazan on 2010-08-03
Hi
I am a newbie in Linux Kernel.
I am writing a code in fs/ext3/namei.c under ext3_unlink(), and that code requires to get the absoulte path of the file.

While exploring, I came across a function called d_path(), but I am not sure how to use it, esp. to pass the second parameter of vfsmount to it without "struct file *".

Any alternative ways to find the path, will also do.

Also, I explored that d_path() trucates the path, if the path is too long. Any good solutions to this ?

---

