---
title: "Reading/Writing INI files in C?"
date: 2008-11-19
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-19
How to read INI files in C?

Is there a library for that?

Or do I have to write one?

---

### Post by cb951303 on 2008-11-19
[http://ndevilla.free.fr/iniparser/](http://ndevilla.free.fr/iniparser/)

---

### Post by crazyfuturamanoob on 2008-11-19
> **cb951303 said:**
> [http://ndevilla.free.fr/iniparser/](http://ndevilla.free.fr/iniparser/)

How to include it with my program?

As readme says, I should do **#include "iniparser.h"**, and link libiniparser.a with **-liniparser.a**, but it doesn't work.

Can't find iniparser.h.

---

### Post by snova on 2008-11-19
Well, first you have to build and install the library. This is C after all, no nice interpreted modules.

---

### Post by crazyfuturamanoob on 2008-11-19
> **snova said:**
> Well, first you have to build and install the library. This is C after all, no nice interpreted modules.

I did it. Ran make & other stuff in terminal. All the stuff install.txt told to do.

---

### Post by snova on 2008-11-19
This library looks familiar...

Add a -I/place/where/the/header/is to the compiler command line along with a -L/place/where/the/library/is when linking.

I looked at the installation instructions, they don't specify how to install. I suggest you copy the libraries manually, to /usr/local/lib and the headers to /usr/local/include. (I prefer installing them into my home directory, but that's just a preference.)

---

### Post by crazyfuturamanoob on 2008-11-20
> **snova said:**
> This library looks familiar...

Add a -I/place/where/the/header/is to the compiler command line along with a -L/place/where/the/library/is when linking.

I looked at the installation instructions, they don't specify how to install. I suggest you copy the libraries manually, to /usr/local/lib and the headers to /usr/local/include. (I prefer installing them into my home directory, but that's just a preference.)

If I put the files in /usr/local/something do I need to link anymore? Can I then use the libraries just as they were stdio.h or something?

Like **#include <iniparser.h>** and no need for linking?

If not, how can I do that then?

And I'd like to include the libraries as static, save them into the executable.

---

### Post by snova on 2008-11-20
You *do* have to link with the code behind stdio.h. It's just that libc is so crucial to doing next to anything at all (and I do mean **anything**), GCC links it in automatically unless you specify otherwise. (Note that ld, which is the linker proper, does not.)

Yes, you will have to link it. The Makefile appears to build both shared and static libraries, so you might have to specify the which one you want with a full pathname- /usr/local/lib/libiniparser.a or whatever it's installed as (no -l this time).

You know, instead of going to the bother with libraries at all, just copy the files into your project and build them the way you do everything else. Much simpler. (This is also the way I first came across this library, included in another program.)

---

### Post by olejorgen on 2008-11-20
[http://www.gtk.org/api/2.6/glib/glib-Key-value-file-parser.html](http://www.gtk.org/api/2.6/glib/glib-Key-value-file-parser.html)

---

