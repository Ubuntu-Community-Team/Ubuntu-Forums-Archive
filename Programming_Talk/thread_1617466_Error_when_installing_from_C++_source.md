---
title: "Error when installing from C++ source"
date: 2010-11-09
forum: Programming Talk
---

### Post by japhyr on 2010-11-09
Hello,

I am trying to install a c++ program, eboard-1.1.1, from source for the first time.

I downloaded the source, unpacked it, and read the install file.  I ran "./configure" from the source directory, and that seemed to be successful:```
Summary:

eboard version 1.1.1
binaries  will be installed to    /usr/local/bin
man pages will be installed under /usr/local/man
datafiles will be installed to    /usr/local/share/eboard
NLS support: yes

done.

```I then tried to run "make".  I got a whole bunch of warnings, and then one error:```
g++ -O6 -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -c ntext.cc -o ntext.o
ntext.cc: In member function ‘void NText::append(const char*, int, int)’:
ntext.cc:247: error: invalid conversion from ‘const char*’ to ‘char*’
make: *** [ntext.o] Error 1

```I have looked at this part of the code, but can't see a quick fix.  I am pretty sure the code can compile, because this is not a development release.  I believe it's an issue of a newer compiler version and older code (2008 release).  Is there a way to tell the compiler to ignore this error?

---

### Post by spjackson on 2010-11-09
> **japhyr said:**
> Hello,

I am trying to install a c++ program, eboard-1.1.1, from source for the first time.

I downloaded the source, unpacked it, and read the install file.

I then tried to run "make".  I got a whole bunch of warnings, and then one error:```

ntext.cc: In member function ‘void NText::append(const char*, int, int)’:
ntext.cc:247: error: invalid conversion from ‘const char*’ to ‘char*’
make: *** [ntext.o] Error 1

```I have looked at this part of the code, but can't see a quick fix.  I am pretty sure the code can compile, because this is not a development release.  I believe it's an issue of a newer compiler version and older code (2008 release).  Is there a way to tell the compiler to ignore this error?
That code is broken because the text argument is declared as const char *, but the function changes the content then changes it back to what it was originally.

Here is the Ubuntu patch to fix this fault: [http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg201899.html](http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg201899.html)

A very quick and dirty fix would be:
```

p = (char *) strchr(text, '\n');

```
But applying the patch would be a better way of doing it.

---

### Post by japhyr on 2010-11-11
Thank you.  It took a while to figure out how to apply the patch, but in the end it was a very satisfying learning experience.  I have always programmed alone, so I haven't used patches very much.  Digging into this takes me one step closer to contributing to open source projects.

---

