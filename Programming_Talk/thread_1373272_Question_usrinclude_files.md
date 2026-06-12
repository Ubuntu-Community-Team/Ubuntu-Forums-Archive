---
title: "Question /usr/include files"
date: 2010-01-05
forum: Programming Talk
---

### Post by lewisforlife on 2010-01-05
I know that all of the header files included in programs are in /usr/include.  For instance, I am doing a lot of GTK+ programming right now, and I can go to /usr/include and see all of the GTK+ .h files.  From programming, I know that the functionality for things is not usually in a .h header file, it is normally in a .c source file.  So I have 2 questions:

[LIST=1]
[*]Are there source files that go along with all of these header files or is all of the functionality in the header files?

[*]If there are source files that go along with these header files, where are they located?
[/LIST]

Thanks, I am a little confused about how everything is set up.  :confused:

---

### Post by dwhitney67 on 2010-01-05
Header files (typically) include function prototypes and/or defined constants.

The functions are implemented in source files, either in the C or C++ languages.  These source files are compiled into object files; these object files are then gathered into either a static library or shared-object library file, or both.

When you build with a library, you are using the header file(s) to ensure that you have properly followed the API, and then you are using either the static or shared-object file for your application.  Developers generally do not need to reference the source code of the library.

If you wish to view the source code, then you would need to visit the site where the library is maintained (eg. gnu.org).

P.S.  Not all header files reside in /usr/include; some are in /usr/local/include.  Similarly for the libraries; some are in /usr/local/lib.

---

### Post by lewisforlife on 2010-01-05
That makes since, so the source files are already compiled into object files right?  Is that what the .so files are in /usr/lib and /usr/local/lib?  Is there a difference between a .so and a .o object file?

---

### Post by dwhitney67 on 2010-01-05
> **lewisforlife said:**
> That makes since, so the source files are already compiled into object files right?  Is that what the .so files are in /usr/lib and /usr/local/lib?  Is there a difference between a .so and a .o object file?

An .so is a shared-object library, that consists of relocatable code that came from one or more object (.o) files.  I'm not well-versed on what the 'relocatable' implies, but suffice to say, these libraries will not be built into one's application; they are loaded during runtime.

A static library (.a) contains a collection of object files that were grouped together as an archive (using the 'ar' command).  These object file(s) are no different that the object file(s) one creates when building their application.  These will be included within the application executable, thus making the executable bigger than if shared-object libraries had been used.

---

### Post by lewisforlife on 2010-01-05
Ok, I think I understand as much as I am going to understand right now.  But I have one more question loosely related to this topic.  Say I have a source C file that uses code from the math library, therefore I have

```
#include <math.h>
```

at the top of my source file.  I know when I compile my program I will have to link to the math library, if I am using gcc I might compile like

```
gcc myprog.c -o myprog -lm
```

How does gcc know that "-lm" means find the math library.  Are all of these in a gcc config file somewhere?

---

### Post by iharrold on 2010-01-05
> **lewisforlife said:**
> How does gcc know that "-lm" means find the math library.  Are all of these in a gcc config file somewhere?

The "-l" command tells the linker to look for the file "libm.so" in all the known search locations.  The "lib" and ".so" or ".a" are added to the characters following the "-l" command.

[http://gcc.gnu.org/onlinedocs/gcc-4.4.2/gcc/Link-Options.html#Link-Options](http://gcc.gnu.org/onlinedocs/gcc-4.4.2/gcc/Link-Options.html#Link-Options)

By default "/usr/lib" is included in the search paths.  To increase the search path ... say to /home/iharrold/mylibrary/mine/right/here then i would also include the linker option: 
-L/home/iharrold/mylibrary/mine/right/here

In other words if I had a library file located and called /home/iharrold/mylibrary/mine/right/here/libMyLib.so then the command line would look similar to:

```
gcc myprog.c -o myprog -L/home/iharrold/mylibrary/mine/right/here -lMyLib
```

To see the default search paths on your system (ones that don't require the "-L" option) enter the following command:
[PHP]gcc -print-search-dirs[/PHP]

---

### Post by lewisforlife on 2010-01-05
Thank you, I understand now.  Man... gcc is really a beast!

---

