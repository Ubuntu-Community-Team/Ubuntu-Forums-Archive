---
title: "Segmentation fault (core dumped)"
date: 2007-11-28
forum: Programming Talk
---

### Post by belikewater on 2007-11-28
dev on g++ , is this error has a connection with allocation?

what can be the cause?

---

### Post by MicahCarrick on 2007-11-28
Could be any number of things. You'll want to find out where the segmentation fault occured. Compile it with the -g switch and then run it through gdb to find out where the problem is.

---

