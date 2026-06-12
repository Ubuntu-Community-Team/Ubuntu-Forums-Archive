---
title: "[SOLVED] Install gutsy packages on Hardy"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-27
I have a few Gutsy packages (that use older version of dependencies)
So what if I install them on Hardy using dpkg or GDebi? Will it break my libc6?

---

### Post by iaculallad on 2008-05-27
Just a guess since I did not experience it first-hand:

Probably it will not break your libc6 library since you're using the latest version (and for sure, Synaptics or apt-get will warn you that are using current version of libc6), but using the other way around on installing Hardy apps to Gutsy would mess up libc6 (but can be restored with Synaptics).

If you plan on doing it, kindly post the result so we will know :)

---

### Post by billgoldberg on 2008-05-27
I installed some gutsy .deb files without any problems.

(a warning was issued though)

---

### Post by sayakb on 2008-05-27
Seems to have worked for me too! :D

---

