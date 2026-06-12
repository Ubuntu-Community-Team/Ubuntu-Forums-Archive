---
title: "Using fdinfo to determine whether file descriptor is a named pipe"
date: 2010-05-25
forum: Programming Talk
---

### Post by DBQ on 2010-05-25
Hi, I need to determine whether the file descriptor opened by a given process refers to a named pipe (FIFO). I tried using ls -l /proc/pid/fd. The file descriptor opened to a named pipe appears there, but none of its attributes indicate anything about it being a FIFO. Any ideas?

Thank You!

---

### Post by MadCow108 on 2010-05-25
[http://linux.die.net/man/2/stat](http://linux.die.net/man/2/stat)
look at the S_ISFIFO macro

edit just realized you probably are working on the shell
the descriptors in  /proc/pid/fd are links to the file
so use stat -L

---

### Post by DBQ on 2010-05-26
Thank you very much! -- got the job done.

Cheers!

---

