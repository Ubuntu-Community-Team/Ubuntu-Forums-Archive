---
title: "[SOLVED] CImg library installation problem"
date: 2008-09-06
forum: Programming Talk
---

### Post by shankhs on 2008-09-06
I have downloaded CImg library but I dont know how to install it!!!
I went to the examples/ directory(it contains the makefile)
and got this after typing make in the terminal:
```

CImg Library 1.29 : Examples
-----------------------------
  > dlinux   : Compile for Linux/BSD/MacOSX, with X11 display and debug informations.
  > linux    : Compile for Linux/BSD/MacOSX, with X11 display and standard options.
  > olinux   : Compile for Linux/BSD/MacOSX, with X11 display and optimizations.
  > mlinux   : Compile for Linus/BSD/MacOSX, with minimal dependancies.
  > Mlinux   : Compile for Linux/BSD/MacOSX, with maximal dependancies.

  > dsolaris : Compile for Solaris, with X11 display and debug informations.
  > solaris  : Compile for Solaris, with X11 display and standard options.
  > osolaris : Compile for Solaris, with X11 display and optimizations.
  > msolaris : Compile for Solaris, with minimal dependancies.
  > Msolaris : Compile for Solaris, with maximal dependancies.

  > dmacosx : Compile for MacOSX, with Carbon display and debug informations.
  > macosx  : Compile for MacOSX, with Carbon display and standard options.
  > omacosx : Compile for MacOSX, with Carbon display and optimizations.

  > clean    : Clean generated files.

Choose your option :linux
```
and then I got hundreds of errors which I have no idea at all.
PLZ help me I am in urgent need of this library!!!

---

### Post by StOoZ on 2008-09-06
first of all , its in the repositories , so you can install it from there , and if its not the latest version , you can try and download the debian version from here :
[http://cimg.sourceforge.net/download.shtml]("http://cimg.sourceforge.net/download.shtml")

to install the one in the repositories , type in the terminal : 
> sudo apt-get install cimg-dev

---

