---
title: "Linux command for creating a shadow tree"
date: 2011-03-07
forum: Packaging and Compiling Programs
---

### Post by CUJimmy on 2011-03-07
Hi all,

The source files for a project i'm working on have become quite numerous, so I was thinking of placing them in separate directories. I have been using make to compile the code, but I hear things can get a little interesting when using make with source files that are split across multiple directories. To get around this, I was thinking of creating a build directory and copying over sym links to the source files before compiling (effectively creating a shadow tree). I've been told there might be a unix command out there that will save me writing a script to do this. Has anybody heard of anything like this?

Thanks.

---

### Post by MadCow108 on 2011-03-07
```
find /top/src/dir -type f| xargs -n 1 ln -s 
```
(won't handle spaces in filenames)

but I don't think its a good idea. what is with duplicate names in different directories?
maybe you should use a better build system than pure makefiles, e.g. cmake, scons or autotools

---

### Post by CUJimmy on 2011-03-11
> **MadCow108 said:**
> ```
find /top/src/dir -type f| xargs -n 1 ln -s 
```
(won't handle spaces in filenames)

but I don't think its a good idea. what is with duplicate names in different directories?
maybe you should use a better build system than pure makefiles, e.g. cmake, scons or autotools

Thanks for this. After trialling it, I found out it wasn't the ideal solution, as you thought. Is there much to choose between either of these alternative build systems? SCons looks great, but I don't think it is supported by the ide I am using (netbeans). I believe cmake is, however.

Thanks again.

---

### Post by n.williams0440 on 2011-03-14
but I don't think its a good idea. what is with duplicate names in different directories?
maybe you should use a better build system than pure makefiles, e.g. cmake, scons or autotools

---

