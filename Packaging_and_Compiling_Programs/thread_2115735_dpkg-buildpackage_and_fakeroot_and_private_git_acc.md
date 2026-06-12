---
title: "dpkg-buildpackage and fakeroot and private git access"
date: 2013-02-13
forum: Packaging and Compiling Programs
---

### Post by derEremit on 2013-02-13
Hi i'm currently in need to package a node js app
I'm trying to do it automated and that includes a makefile triggered bei debian/rules that calls npm install ( nodejs package manager ) which also pulls dependencies from a private git repository.

now the problem is that when the makefile is run in fakeroot it does not have an ssh key to access that private repository and my build fails.

actually there is a problem before that:

The authenticity of host   'myhost' can't be established.

which already breaks my build.

---

