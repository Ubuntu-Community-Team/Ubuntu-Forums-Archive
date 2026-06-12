---
title: "Dumb dpkg/apt question..."
date: 2006-07-26
forum: Programming Talk
---

### Post by Liam on 2006-07-26
Say I want to create a dummy package that contains a list of all of my favorite non-standard packages for a future fresh install in the deps. Would doing something like the following work?

1) Create the control file:

```

Package: bookmarks
Version: 0.0
Section: utils
Priority: optional
Architecture: i386
Depends: packagefoo, packagebar, packagewhatever
Installed-Size: 0
Maintainer: Joe Mama
Description: Personal .deb bookmarks for later installation

```

2) tar -cxvf control.tar.gz control

3) ar q bookmarks.ar control.tar.gz

4) mv bookmarks.ar bookmarks.deb

When I do that, and try to install it with dpkg, I get the following error:

> 
dpkg-deb: file `bookmarks.deb' is not a debian binary archive (try dpkg-split?)
dpkg: error processing bookmarks.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 bookmarks.deb


So what am I doing wrong? Do I need to include a dummy data tarball?

Will this method even work?

Thanks.

---

### Post by LordHunter317 on 2006-07-26
I don't know if it'll work, but just use equivs to generate dummy packages as needed.

---

### Post by Liam on 2006-07-26
> **LordHunter317 said:**
> I don't know if it'll work, but just use equivs to generate dummy packages as needed.

Sweet. That worked perfectly.

---

