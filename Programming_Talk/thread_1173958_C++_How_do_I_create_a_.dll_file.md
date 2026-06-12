---
title: "C++ How do I create a .dll file"
date: 2009-05-30
forum: Programming Talk
---

### Post by PaulM1985 on 2009-05-30
Hi

I am writing a fairly large program and I want to start packaging my files together so that I don't have to link all the files together if I only change one.  Can I create a .dll file for each package so that if I change a file I only have to compile that file, create a dll for that package and then link all the dlls together?

Is this possible.  If so, how do I go about doing it?

Paul

---

### Post by hessiess on 2009-05-30
On Linux they are called .so (shared object) files, you can compile
them using:

```

g++ source_file.cpp -fPIC -o lib(out_put_file_name).so -shared

```

and can be linked into a program by importing the relevant .h files
and adding -l(lib_name) to the command line

```

g++ (source_file.cpp, source2.cpp...) -I /path/to/.so/file -l(so_file_name) -o (output binary name)

```

You may also want to use automake/libtool

---

### Post by PaulM1985 on 2009-05-30
What exactly do you mean by including relevant h files..

My file system:
- Interface
   - Window.cpp <- this uses the library
- Core
   - libCore.so
   - Coord.cpp
   - Coord.h

In the Window file, do I need to do 
#include "../Core/libCore.so/Coord.h", or
#include "Coord.h" or something else.

Thanks

Paul

---

### Post by dwhitney67 on 2009-05-30
hessiess made an error in his post concerning compiling the application.  Typically the library header file(s) do not reside in the same directory as the shared-object file.  But for now (based on the limited information you offered), let's assume he is correct.

Wrt the directory layout:
```

My file system:
- Interface
- Window.cpp <- this uses the library
- Core
- libCore.so
- Coord.cpp
- Coord.h

```
you did not indicate what is in Core, nor Interface.  I'll assume that the file(s) in Core are used to build libCore.so.

Assuming only two files:
```

cd Core
g++ -fPIC -c CoreFile1.cpp
g++ -fPIC -c CoreFile2.cpp
g++ -shared -o libCore.so CoreFile1.o CoreFile2.o

```
Of course, you can compile and build the library in one step, but this is impractical if you are dealing with many files.

Assuming, the Core library has header files CoreFile1.h and CoreFile2.h, and these are required by Window.cpp:

In Window.cpp:
```

#include "CoreFile1.h"   // or use <>
#include "CoreFile2.h"   // or use <>
...

```

Assuming Window.cpp is a self-contained program with a main() function:
```

g++ -I./Core -c Window.cpp
g++ Window.o -L./Core -lCore -o myapp

```

To run myapp:
```

LD_LIBRARY_PATH=./Core myapp

```

P.S.  For good programming practice, you should consider passing the -Wall -pedantic options to GCC when compiling a C or C++ source file.

---

### Post by stroyan on 2009-05-30
There is a how-to on creating archive and shared libraries at
[http://tldp.org/HOWTO/Program-Library-HOWTO/](http://tldp.org/HOWTO/Program-Library-HOWTO/)

There is white paper on how shared libraries work and the best practices for creating them at
[http://people.redhat.com/drepper/dsohowto.pdf](http://people.redhat.com/drepper/dsohowto.pdf)

---

### Post by PaulM1985 on 2009-05-30
Is there a way that I can straight compile the final one where the link is taken place?

I have been trying:

 g++ run.cpp Interface/Window.cpp `pkg-config gtk+-2.0 --libs --cflags` -L./Core -libCore -o run

with errors:
Interface/Window.cpp:4:19: error: Coord.h: No such file or directory
Interface/Window.cpp: In constructor &#8216;Window::Window(int, char**)&#8217;:
Interface/Window.cpp:17: error: &#8216;Coord&#8217; was not declared in this scope
Interface/Window.cpp:17: error: &#8216;aCoord&#8217; was not declared in this scope
Interface/Window.cpp:17: error: expected type-specifier before &#8216;Coord&#8217;
Interface/Window.cpp:17: error: expected `;' before &#8216;Coord&#8217;

but it is as if the Window.cpp cannot find the library.  When I try to compile Window.cpp to an .o file, I use:

 g++ -I./Core -c Interface/Window.cpp `pkg-config gtk+-2.0 --libs --cflags`

and I get the errors:

g++: -lgtk-x11-2.0: linker input file unused because linking not done
g++: -lgdk-x11-2.0: linker input file unused because linking not done
g++: -latk-1.0: linker input file unused because linking not done
g++: -lgdk_pixbuf-2.0: linker input file unused because linking not done
g++: -lm: linker input file unused because linking not done
g++: -lpangocairo-1.0: linker input file unused because linking not done
g++: -lpango-1.0: linker input file unused because linking not done
g++: -lcairo: linker input file unused because linking not done
g++: -lgobject-2.0: linker input file unused because linking not done
g++: -lgmodule-2.0: linker input file unused because linking not done
g++: -ldl: linker input file unused because linking not done
g++: -lglib-2.0: linker input file unused because linking not done

Any advice?

Paul

Ps:

File structure info:

Base folder contains
run.cpp <- runs the program
Interface <- User interface folder
Core <- Contains core system

Interface folder contains:
Window.cpp <- contains references to gtk library
Window.h

Core Folder contains
Coord.cpp <- Coordinating object for the core system
Coord.h
Shape.cpp
Shape.h
Face.cpp
Face.h

---

### Post by PaulM1985 on 2009-05-31
Sorted it.

Thanks everyone

---

