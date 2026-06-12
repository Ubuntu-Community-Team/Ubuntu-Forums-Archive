---
title: "New projects: makefile and directory structure"
date: 2008-10-06
forum: Programming Talk
---

### Post by omegga on 2008-10-06
I want to start a project in C/C++. But I don't know the "best" way to organize all the files and haven't found any good information on it. I tried to look at open source projects to look how they did it. But either the project I picked was too big and complicated.. or it was small and not very useful to study how they did it. So:

So does anyone know a good tutorial on makefiles?
Best practices?
How to organize your source directory?

---

### Post by kknd on 2008-10-06
Most of the GNOME programs follows the layout:

main folder
    -> src/  (for source code)
    -> po/   (translations)
    -> docs/ (documentation)
    -> m4/   (macros for the build system)
    -> COPYING (license, usally called COPYING for GPL or COPYING.LESSER for LGPL
    -> Makefile
    -> README
    -> And other things

I use this layout, but I don't like autotools and etc.

---

### Post by hod139 on 2008-10-06
If you are starting a new project I would suggest you look at using more modern build tools, e.g. [cmake]("http://www.cmake.org/").  This would leave (following kknd's example),
src/
po/
docs/
COPYING
README
CMakeLists.txt

**EDIT:**
I should also add, I also like to have a build folder, and build everything in that folder.  It keeps everything nice and clean (and local).
```

cd build
ccmake ../
make

```
I don't add this folder to the version control system, only have it on my local machine.  If a build ever gets messed up, I can always simply delete this folder.

---

