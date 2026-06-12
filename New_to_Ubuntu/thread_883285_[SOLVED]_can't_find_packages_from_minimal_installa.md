---
title: "[SOLVED] can't find packages from minimal installation"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by eilenbeb on 2008-08-07
I have 2 installations of Ubuntu; the normal installation, and a minimal install (using the -cli- option from the mini hardy cd).

In my mini system, apt-get is unable to find any packges.
I am connected to the internet, and am able to ping successfully.
I have edited my sources.lst file to match the one from my full install.

I do not want to resolve this by using chroot if possible.
I would much rather fix my mini install, but I am stumped as to what the problem is.

Any ideas?

laters,
b

---

### Post by PmDematagoda on 2008-08-07
Did you do:-
```
sudo apt-get update
```
and then try installing the necessary packages?

---

### Post by eilenbeb on 2008-08-07
heheh... nope.
Thanks, that seems to be what I was missing.

laters,
b

---

