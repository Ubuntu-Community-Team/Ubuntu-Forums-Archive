---
title: "&quot;Permission denied&quot; fakeroot checkinstall"
date: 2013-11-21
forum: Packaging and Compiling Programs
---

### Post by GlasGhost on 2013-11-21
created the following bash script to create a .deb package from a git url & revision tag:[https://github.com/GlassGhost/GitDeb]("https://github.com/GlassGhost/GitDeb")

but my test script [https://github.com/GlassGhost/GitDeb/blob/d0c24db46244cc34c0cffded57903fddb290d790/tcc.sh]("https://github.com/GlassGhost/GitDeb/blob/d0c24db46244cc34c0cffded57903fddb290d790/tcc.sh")

but on calling line 36 of [https://github.com/GlassGhost/GitDeb/blob/d0c24db46244cc34c0cffded57903fddb290d790/GitDeb.sh]("https://github.com/GlassGhost/GitDeb/blob/d0c24db46244cc34c0cffded57903fddb290d790/GitDeb.sh")
```
fakeroot checkinstall --install=no --pkgname="$PkgName" --pkgversion="$PkgVersion" -y -D make install
```
it fails with the following:
```
Installing with make install...

========================= Installation results ===========================
make -C lib native
make[1]: Entering directory `/home/owner/Documents/GitDeb/tcc/lib'
make[1]: Nothing to be done for `native'.
make[1]: Leaving directory `/home/owner/Documents/GitDeb/tcc/lib'
mkdir -p "/usr/local/bin"
install -m755 tcc "/usr/local/bin"
install: cannot create regular file ‘/usr/local/bin/tcc’: Permission denied
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

```

---

### Post by GlasGhost on 2013-11-22
bump

---

### Post by GlasGhost on 2014-02-09
I solved this with [http://stackoverflow.com/questions/20129788/create-deb-package-from-revision-tag-for-a-git-url](http://stackoverflow.com/questions/20129788/create-deb-package-from-revision-tag-for-a-git-url)

---

