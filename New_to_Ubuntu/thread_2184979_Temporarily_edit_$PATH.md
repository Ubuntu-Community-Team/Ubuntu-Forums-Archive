---
title: "Temporarily edit $PATH"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by sha1sum on 2013-10-31
Is it possible to add a directory to $PATH for the length of one shell session? What command should I use for that?

---

### Post by The Cog on 2013-10-31
A command like this will do it (this adds /foo to the path):
```
PATH=$PATH:/foo
```
And that will last until the shell exits.

---

### Post by sha1sum on 2013-10-31
Thanks that was exactly what I was looking for. :D

---

