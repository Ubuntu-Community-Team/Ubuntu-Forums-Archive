---
title: "Xorg record extension can't compile"
date: 2011-08-09
forum: Programming Talk
---

### Post by Bucky24 on 2011-08-09
I'm using the unmodified source code listed here:
[http://blog.csdn.net/findsun/article/details/187878](http://blog.csdn.net/findsun/article/details/187878)

For the Xorg record extension. I have verified that the extension and development library is installed, but when I compile with the following:

gcc -o record record.c -lX11

I get these linker errors:
undefined reference to `XRecordQueryVersion'
undefined reference to `XRecordAllocRange'
undefined reference to `XRecordCreateContext'
undefined reference to `XRecordEnableContextAsync'
undefined reference to `XRecordProcessReplies'
undefined reference to `XRecordDisableContext'
undefined reference to `XRecordFreeContext'
undefined reference to `XRecordFreeData'
undefined reference to `XRecordFreeData'

I know I'm missing a library in the arguments to gcc but I can't find the name of it anywhere.

Does anyone know the name of the xorg record library that I need to pass to gcc in order to get this to link properly?

-Bucky24

---

### Post by Zugzwang on 2011-08-10
Here is how you find it: Search for the package that contains the header files that you included. In this case this is "X11/extensions/record.h". Using the search engine on packages.ubuntu.com, this package appears to be "libxtst-dev". Then, look into the file list of the package and watch out for the library. You can find the file list [here]("http://packages.ubuntu.com/natty/i386/libxtst-dev/filelist"). As you can see, there's only one .so file in there, so this is the library to link against! Note that there is also a .pc file, so you can use pkgconfig for obtaining the correct compiling & linking parameters.

---

