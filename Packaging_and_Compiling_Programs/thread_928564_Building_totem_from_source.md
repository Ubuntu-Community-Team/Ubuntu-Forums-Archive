---
title: "Building totem from source"
date: 2008-09-24
forum: Packaging and Compiling Programs
---

### Post by peter.everix@telenet.be on 2008-09-24
Hi all

I try to compile totem from source on ubuntu 8.04 box.
I get the source from totem from svn and then run autogen.sh with complaining missing gnome-common.m4 ....

I search internet and found i also need gnome-common so i get this from svn and did run autogen, configure, make and sudo make install. This all went ok , only saying many times 'nothing to be done' when doing make and make install.

When i try to do autogen for totem i still get this error messages about missing gnome-common.

What i'am doing wrong ?
All this still very new to me !

---

### Post by InfinityCircuit on 2008-09-24
Did you run:

```
sudo apt-get build-dep totem
```

This will install the build-dependencies of totem.

---

### Post by peter.everix@telenet.be on 2008-09-29
Yes, after doing

sudo apt-get build-dep totem

and
sudo apt-get source totem

I could build totem from source on my ubuntu box.
Thanks for the info, i'm learning every day.

---

