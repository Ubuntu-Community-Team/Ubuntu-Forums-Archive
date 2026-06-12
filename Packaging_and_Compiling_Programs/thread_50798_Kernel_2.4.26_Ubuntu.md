---
title: "Kernel 2.4.26 Ubuntu"
date: 2005-07-21
forum: Packaging and Compiling Programs
---

### Post by itstudent on 2005-07-21
hello,

I want to compile the kernel 2.4.26, because i want to use openmosix with the migshm (migrated shared memory) patch. how should i do this ?

olaf

---

### Post by Vesku on 2005-08-24
Did you get OpenMosix to work?

I would need some help on that too

---

### Post by bluesceada on 2005-09-08
maybe try this *.deb packages from here [http://klustrix.ghuug.org/](http://klustrix.ghuug.org/)
tell me if it works  ;-)

---

### Post by ronharts on 2005-09-24
itstudent (Olaf): Ive been tinkering with this, so far with no success.
I compiled 2.4.26 kernel with modules into a deb and installed.
upon restart I get a few errors:
*udev not started kernel <2.6.8 - All other probs may come from this - I cant see what the resolution will be, OM for 2.6 is not ready yet (apparently it can work but there are no user space tools avail. - preety important since a lot of things were moved to user space).
*nautilus/bug buddy/panel -crash repeatedly.
*eth0/1 not recognized - after putting driver into kernel rather than modules worked.

bluesecada: I tried this and got same results with self compiled kernel.

my next course of action is to try a cluster cd and see how that works.

---

