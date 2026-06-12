---
title: "Python list directories and files in current  directory"
date: 2010-03-25
forum: Programming Talk
---

### Post by goseph on 2010-03-25
Hi everyone!

os.walk() appears to list files and directories recursively whereas os.dir() lists files and directories indistinguishably in a single list.

Is there any way to get lists separately and non-recursively, of the files and directories contained within a given directory?

Thanks,

Luke

---

### Post by heikaman on 2010-03-25
I hope this helps:

[PHP]
files = filter(os.path.isfile, os.listdir('.'))
dirs = filter(os.path.isdir, os.listdir('.'))
[/PHP]

---

### Post by goseph on 2010-03-25
> **heikaman said:**
> I hope this helps:


Yes it does!

Thankyou.

---

