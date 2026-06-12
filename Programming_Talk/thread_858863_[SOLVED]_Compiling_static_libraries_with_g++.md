---
title: "[SOLVED] Compiling static libraries with g++"
date: 2008-07-14
forum: Programming Talk
---

### Post by ceclauson on 2008-07-14
I'm interested in compiling a static library with g++.  Can anyone tell me how?  Also, is there any way to control what variables/functions/classes have external linkage?

Thanks,
Cooper

---

### Post by samjh on 2008-07-14
What do you mean by "compiling a static library"?

If you mean you want to compile a program and link it statically to a pre-existing library, you'll need to consult the library's documentation on how that is done.  A lot of libraries need to be compiled for static linking before you can link them to your program statically.  If the library documentation doesn't specify anything about that, then try passing the "-static" option to gcc when compiling.

---

### Post by Zugzwang on 2008-07-14
There is one library I know that compiles to a library that a program using it has to statically link against: [CUDD]("http://vlsi.colorado.edu/~fabio/CUDD/"). Have a look at its Makefiles to find out how to perform your task. I suggest that you look at "obj/Makefile" since that one works without configurations. They seem to use the "ar" tool and "ranlib" for actually building the .a file.

---

### Post by ceclauson on 2008-07-16
Thanks for your replies.

I was able to find the answer online:
[http://publib.boulder.ibm.com/infocenter/lnxpcomp/v8v101/index.jsp?topic=/com.ibm.xlcpp8l.doc/proguide/ref/compiling_static.htm](http://publib.boulder.ibm.com/infocenter/lnxpcomp/v8v101/index.jsp?topic=/com.ibm.xlcpp8l.doc/proguide/ref/compiling_static.htm)

If anyone else is interested, you compile the translation units to object files, and then use the archiving utility ar to archive them in to a library.

Thanks,
Cooper

---

