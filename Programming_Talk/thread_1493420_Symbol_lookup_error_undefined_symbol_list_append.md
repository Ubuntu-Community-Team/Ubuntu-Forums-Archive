---
title: "Symbol lookup error: undefined symbol: list_append"
date: 2010-05-25
forum: Programming Talk
---

### Post by y50a7XpWRH66IV on 2010-05-25
Hi everyone,

I am currently writing a GTK program that involves the use of plugins. I have successfully compiled my main program, which is then suppose to load my plugin.

My plugin compiles and loads fine until I start using SimCList for its linked-list functions.

I have copied simclist.h and simclist.c into my plugin's structure as follows:

[LIST]
[*]libmyplugin.c
[*]libmyplugin.h
[*]libplugincallbacks.h
[*]libplugincallbacks.c
[*]simclist.h
[*]simclist.c
[/LIST]

I have included simclist using:
```

#include "simclist.h"

```

My program compiles fine into a .so file.

However, whenever I call something that uses a simclist function, I get an error like this:

```
symbol lookup error: modules/libmyplugin.so: undefined symbol: list_init
```

It is strange that I can call functions within libmyfunctioncallbacks.h without any problems.

The simclist documentation mentions that compiling with the -std=c99 flag is needed. So I have modified my makefile to the following, but it did not make any difference:

```
libmyplugindir= /
libmyplugin_LTLIBRARIES=libmyplugin.la
libmyplugin_la_SOURCES=libmyplugin.c libmyplugincallbacks.c simclist.c
include_HEADERS = libmyplugincallbacks.h simclist.h
libmyplugin_la_LDFLAGS= -lc -lgcc -std=c99 -avoid-version --export-dynamic @PACKAGE_LDFLAGS@
libmyplugin_la_LIBDADD = @PACKAGE_LIBS@
INCLUDES = @PACKAGE_CFLAGS@
```

Any ideas appreciated! :)

---

### Post by dwhitney67 on 2010-05-25
Your Makefile is less than stellar.  I have no idea what the libmyplugin_la_LDFLAGS is used for, but typically (that is, almost always) when I see an LDFLAGS, in a Makefile, it is used for linking.  Yet you have the -std=c99 in there.

The -std=c99 should be used when compiling; if you are programming in C, add this to your CFLAGS, or if you're doing C++, then CXXFLAGS.


P.S.  I appears that you are programming in C.


P.S #2.  There should be no reason why you should not be able to duplicate the issue you are having in a few lines of code; please post some code, how you are compiling/linking it, etc.

---

### Post by y50a7XpWRH66IV on 2010-05-25
Hi!

Thanks for your quick reply. Forgot to mention that the code is in C.

Here's an extract that demonstrates the problem:
```

#include <stdlib.h>
#include <gtk/gtk.h>
#include <stdint.h>
#include <stdio.h>
#include "simclist.h"
#include "libmyplugin.h"

void main(){
    list_t nodes;
    list_init(&nodes);
}

```

list_init will fail when the program is executed.

Regarding the make file: libmyplugin is to be compiled into a .so dynamic library using libtool.

Compilation is done as per the makefile I have posted in my first post. In this situation, where should -std=c99 be placed?

---

### Post by dwhitney67 on 2010-05-25
It's late, and I don't have the time for a journey into an abyss.

The code you posted has one (perhaps five) too many header files included.

Where is 'list_t' and list_init() defined?  This header file should be the only one you need to include.

When compile, screw the libtools and any other black magic you possess.  Just use the command line with gcc.  The -I option is used to specify the location of any non-standard header files that you require, and the -L option is used to specify the location of the library (if any) that you wish to link against.

Say you include "foo.h", and it is located in /left/field.  I would expect that you would compile with something like:
```

gcc -I/left/field MySource.c

```
If you require a libfoo.so to link, then augment the statement above with:
```

gcc -I /left/field MySource.c -L/left/field/lib -lfoo

```
Of course, substitute as necessary the crazy names I demonstrated above.

If you are indeed building a shared-object library, then obviously what I have stated above is not applicable.  First you would need to compile each of your modules, then link them together into a shared-object library.  Typically something like:
```

gcc -c File1.c
gcc -c File2.c
...
gcc -c FileN.c

gcc -shared -o libAllMe.so File1.o File2.o ... FileN.o

```
When compiling each module (ie File1.c), use the -I option if applicable.

---

### Post by y50a7XpWRH66IV on 2010-05-25
Hi again!

The solution to the problem is quite simple. I simply added -std=c99 to PACKAGE_CFLAGS in my configure.ac.

After doing so, automake will give a series of vague "make recursive errors" and an error saying there a libtool version mismatch.

To fix it, just run the following in the project's directory:
```
autoreconf -iv
```

Cheers :)

---

