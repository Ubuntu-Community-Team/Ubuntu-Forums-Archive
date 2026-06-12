---
title: "Anjuta: target that contains files from multiple dirs"
date: 2010-06-12
forum: Programming Talk
---

### Post by FalFire on 2010-06-12
Hi,

I want to organize my C++ project into multiple directories and I am using the Anjuta IDE to do this. My project is a shared library, and I want to add all the source files from all the subdirectories of my project to the one shared library target in the project root. However, Anjuta seems to require that all files added to a target are in the same directory as that target, in other words you have to make a new target for every directory.
I am sure this is not right, as there surely must be a way to have a multiple-directory project that compiles into one library??
How do you do this in Anjuta?

---

### Post by FalFire on 2010-06-13
I edited the Makefile.am in my project root manually to include the files subdir/file.cpp and subdir/file.h. This does allow my project to compile and work as it should, but anjuta just puts the two files from my subdir into the "src" group, not in a "subdir" group. Again, I'm sure there is an other (correct) way to do this?

Any help would be greatly appreciated!

---

