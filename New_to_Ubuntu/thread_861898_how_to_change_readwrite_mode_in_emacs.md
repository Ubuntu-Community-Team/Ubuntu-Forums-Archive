---
title: "how to change read/write mode in emacs ?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by mgph on 2008-07-17
Hi....I'm really sorry for my stupid question but how can I change to read/write mode in emacs ?

When I enter the emacs, the bottom line says
"Buffer is read-only" and I cannot write anything...How can I solve it ?

Thanks in advance

---

### Post by andrewc6l on 2008-07-17
Emacs usually won't say that unless you don't have appropriate permissions to edit the file. If you own the file, you can use chmod u+w to add write permissions to it. If you don't own the file, you can start Emacs with:
```
sudo emacs *filename*
```

If you've made a lot of chages to the file and don't want to lose them,
C-x C-w, write the file to /tmp/foo, and then copy it over your existing file.

If you really just want to toggle the read-only state, C-x C-q (or M-x toggle-read-only).

---

