---
title: "Is it safe to remove ubuntu-base, and what exactly will this remove?"
date: 2005-01-25
forum: Repositories &amp; Backports
---

### Post by black hole sun on 2005-01-25
As the topic suggests. I want to remove loads of unnecessary and unneeded programs (such as "ed," among many others) but I dont want to bork Ubuntu in the process. Thanks!

---

### Post by az on 2005-01-26
You can do whatever you want.  As a rule, removing a metapackage does not remove all the package's dependancies, so you will not be removing the whole ubuntu base system.

That being said, the base system is really that basic tools you need on a GNU system.  I do not know if gaining a few megs of disk space is going to be worth, for example not being able to build new packages because you no longer have the neccessary tool to do it.

Most of the base system is pretty lean stuff.  Removing ed should not be a problem, but how much disk space does it take?

---

