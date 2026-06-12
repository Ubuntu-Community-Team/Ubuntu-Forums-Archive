---
title: "Invalid Linker Path when Cross-Compiling"
date: 2014-06-05
forum: Packaging and Compiling Programs
---

### Post by SamBam77 on 2014-06-05
I am trying to cross-compile a program within a linux environment for windows.  I am using mingw32 and can compile simple test programs/exes just fine.
 But when I try to compile my package, after configuration,
```

./configure --host=x86_64-w64-mingw32--build=x86_64-w64-mingw32 --with-dest=$PWD/_install./configure--host=x86_64-w64-mingw32 --build=x86_64-w64-mingw32--with-dest=$PWD/_installPKG_CONFIG_PATH=/home/SamBam77/mingw/mingw-w64-x86_64/lib

```
When I run a “make” command, get errors such as:
```

libtool: link: Could not determine hostfile name corresponding to
libtool: link:   `.libs/'
libtool: link: Continuing, but uninstalled executables may not work.
*** Warning: linker path does not have real file for library -lgmodule-2.0.
*** I have the capability to make that library automatically link in when
*** you link to this library.  But I can only do this if you have a
*** shared version of the library,which you do not appear to have
*** because I did check the linker path looking for a file starting
*** with libgmodule-2.0 and none of thecandidates passed a file format test
*** using a file magic. Last filechecked: /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3800.1

```
with additional errors like what I show directly above, but for other packages, including:
lgthread-2.0, lm, lgtk-x11-2.0, lfftw3, lgdk-x11-2.0, latk-1.0, lgio-2.0, lpangoft2-1.0, lpangocairo-1.0,lgdk_pixbuf-2.0, lpango-1.0, lfontconfig, lgobject-2.0, lglib-2.0,and
```

*** Warning: libtool could not satisfy all declared inter-library
*** dependencies of module threshold-example.  Therefore, libtool will create
*** a static module, that should work as long as the dlopening
*** application is linked with the-dlopen flag.

```
So it looks like I have the dependency files, but they are not the correct version?  I am not sure.  It seems like the solution to this problem is just to install the correct dependencies and/or point the compiler to the correct directory containing them.  But I am at a loss for how to do this? I have searched to the best of my ability, but I do not see anything else I can install or where to point the compiler other than to the stuff that it can already find.

---

### Post by steeldriver on 2014-06-05
Your ./configure line looks messed up - why is another ./configure buried in there? why no spaces between the '--' options (like --build=x86_64-w64-mingw32**[COLOR=#ff0000]--[/COLOR]**with-dest=$PWD/_install)? why is the PKG_CONFIG_PATH tacked on the end like that?

---

### Post by SamBam77 on 2014-06-06
Oh, that was my mistake copy-pasting multiple versions of the ./configure command that I have tried.
Normally, I simply use
```

./configure --host=x86_64-w64-mingw32 --build=x86_64-w64-mingw32 --with-dest=$PWD/_install

```
and I receive the same errors that I quoted before.

---

### Post by SamBam77 on 2014-06-07
Additional help would be greatly appreciated.
Let me know what other information I can provide to help you help me, thanks,

---

