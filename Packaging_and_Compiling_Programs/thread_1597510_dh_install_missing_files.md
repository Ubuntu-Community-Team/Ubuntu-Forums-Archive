---
title: "dh_install missing files"
date: 2010-10-15
forum: Packaging and Compiling Programs
---

### Post by martron88 on 2010-10-15
Hi all,

I'm trying to package the gavl library from source on my amd64 system.  While everything compiles fine when running 
```
sudo pbuilder build ../*.dsc
```
I run into the following error:
```
dh_install: gavl-dev missing files (usr/lib/lib*.a), aborting
```

Searching for similar problems it sounds like this has potentially something to do with 64 bit libraries but I'm not too well versed in this (this is my first attempt at packaging from source).
[http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/6e7b2e94686b06a3](http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/6e7b2e94686b06a3) looks like a similar problem but the solution is not clear to me.

I've been following [https://wiki.ubuntu.com/PackagingGuide/Basic#Building%20the%20Source%20Package](https://wiki.ubuntu.com/PackagingGuide/Basic#Building%20the%20Source%20Package) as a guide to building the package and it seems to me that I'm almost there, but I don't quite understand fully how all the pieces work and thus can't seem to fix this issue myself.

Any help or insight is appreciated.

---

### Post by martron88 on 2010-10-15
Nevermind, I solved it by taking and modifying the debian/rules file from Hello-debhelper

---

