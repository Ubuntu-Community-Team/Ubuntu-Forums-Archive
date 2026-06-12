---
title: "Building a library using a *.so library and its *.h header"
date: 2010-06-04
forum: Programming Talk
---

### Post by Zohair08 on 2010-06-04
Hi guys,

The question is : how can build a library using a *.so library (which depends on another installed library) and its *.h header. Im confused whether to use LDFLAGS, LIBADD or LIBS.

Any help please?

Thanks

Zoh

---

### Post by kknd on 2010-06-04
Keeping it simple, for libraries already located at the include / lib path (like /usr/include and /usr/lib), it's just this:

[PHP]
gcc myfile.c -o myprogram -lname_of_the_lib
[/PHP]

or, for a shared library:

[PHP]
gcc -shared myfile.c -o libmyname.so -lname_of_the_lib
[/PHP]

It will link to /usr/lib/libname_of_the_lib.so .

If the library or it's header are outside the configured paths, you need to use like this:

[PHP]
gcc myfile.c -o myprogram -I/usr/unusual/include -L/usr/unusual/lib -lname_of_the_lib
[/PHP]

In Makefiles, by convention, the library parameters, like -Lpath and -lname are stored in a variable named LDFLAGS, and the include path (-I) and other options, like -O, -Wall, etc, are stored in a variable named CFLAGS. No magic here.

I hope that was your question =).

---

### Post by dwhitney67 on 2010-06-04
> **Zohair08 said:**
> Hi guys,

The question is : how can build a library using a *.so library (which depends on another installed library) and its *.h header. Im confused whether to use LDFLAGS, LIBADD or LIBS.

Any help please?

Thanks

Zoh
You do not have to link a library that you are creating; all you have to do is compile each of the individual components (ie modules).  Thus, even if your library is dependent upon, let's say GTk+ and my 57' Chevrolet, all you need to do is specify the "include" paths such that your library compiles.

When the developer (perhaps you?) uses your home-made library, they will need to specify all libraries and include paths which are necessary to create an executable.

Oftentimes, but not always, those who produce a library depend upon other libraries, and they are kind (ie savvy) enough to provide a 'pkg-config' file or something similar which provides the appropriate information of what is necessary to compile and link with this library.

I have developed a library (for socket apps) that relies on nothing else, other than the (Linux) C standard library.  Thus developers who wish to use it, at a minimum, do not need to specify any thing else.

---

### Post by Zohair08 on 2010-06-05
Thanks guy for help. The thing is I was asked to use a specific template that originally doesnt use a library. I will not use the gcc command but will use the aututools and stuff instead and in the makefile there's:

[PHP]grinclude_HEADERS =        \
    XYZ.h
lib_LTLIBRARIES =        \
    mygenerated-library.la

mygenerated_library_la_SOURCES =     \
    XYZ.cc

mygenerated_library_la_LIBADD =    \
    $(GNURADIO_CORE_LA)

mygenerated_library_la_LDFLAGS =    \
    $(NO_UNDEFINED)[/PHP]So, my question was how to modifiy this template to include the library and the dependencies.

Cheers,
Zoh

---

