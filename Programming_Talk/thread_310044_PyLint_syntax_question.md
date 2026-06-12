---
title: "PyLint syntax question"
date: 2006-11-30
forum: Programming Talk
---

### Post by GoUbuntu on 2006-11-30
Hi,

This may seem like a stupid question, but I'd like to know anyway.  How do I used pylint's --ignore option to prevent it from looking at some files?  The documentation says you have to use a base name.  What the heck is a base name?

Are there any other ways to stop it looking at certain files?  At the  moment I'm trying to get it to avoid the ones that contain 'import wx'.

Thanks,
Brendon

---

### Post by po0f on 2006-11-30
GoUbuntu,

A file's basename is the filename without a leading directory structure.  So for a file /home/foo/bar.py, the basename would be just bar.py.

---

### Post by GoUbuntu on 2006-11-30
Thanks po0f.

---

