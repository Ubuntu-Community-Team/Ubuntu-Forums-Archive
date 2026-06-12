---
title: "installing gcc-4.1 on dapper"
date: 2006-10-31
forum: Programming Talk
---

### Post by AntonioFabio82 on 2006-10-31
Hi all.
I would install gcc-4.1 (default compiler in edgy) on my dapper AMD64 system.
Compilation from sources doesn't work out of the box.
I was wandering if someone has some hints for:
1) get gcc-4.1 compiled from sources on my dapper-amd64 system (by copying config options in ubuntu edgy AMD64 ?)
2) install the edgy precompiled gcc-4.1 packages in the dapper system

For various problems, actually I can't upgrade the whole system to edgy.

Tnx all,
Antonio.

---

### Post by toojays on 2006-10-31
Here's the quick version of what I would try. Read the man pages for the various commands mentioned before you try it.

1) Download the three files mentioned at [http://packages.ubuntu.com/edgy/source/gcc-4.1](http://packages.ubuntu.com/edgy/source/gcc-4.1) on the bottom of the page (where it says download gcc-4.1).

2) Unpack the debian sources with "dpkg-source -x".

3) Change into the source directory and build the package with "dpkg-buildpkg -rfakeroot -b".

4) Use "dpkg -i" to install the packages you created.

You may have to repeat step three a couple of times until you have all the necessary build deps.

---

