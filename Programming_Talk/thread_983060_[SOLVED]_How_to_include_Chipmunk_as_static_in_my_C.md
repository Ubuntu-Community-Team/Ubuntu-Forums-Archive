---
title: "[SOLVED] How to include Chipmunk as static in my C program?"
date: 2008-11-15
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-15
I downloaded chipmunk, compiled/installed it, and now I got a folder full of chipmunk stuff.

How can I include chipmunk in my program as a static library?

---

### Post by nvteighen on 2008-11-15
Well, static libraries are named lib*blah*.a, and they consist in an archive of object files (yes, the very same .o files) just conveniently packaged into one single file (with a linkable symbols' index).

So, you use .a files the same way as when you want .o files to be linked together:
```

gcc -c myprog.c -Wall
gcc myprog.o libblah.a -Wall

```

Just an advice on static linking: Have you read the library's License? Remember that your program will become a Derivative Work of/from the library.

---

### Post by crazyfuturamanoob on 2008-11-15
> **nvteighen said:**
> Well, static libraries are named lib*blah*.a, and they consist in an archive of object files (yes, the very same .o files) just conveniently packaged into one single file (with a linkable symbols' index).

So, you use .a files the same way as when you want .o files to be linked together:
```

gcc -c myprog.c -Wall
gcc myprog.o libblah.a -Wall

```

Just an advice on static linking: Have you read the library's License? Remember that your program will become a Derivative Work of/from the library.

How can I do that with my makefile?

```
CC = gcc -Wall -ansi
LIBRARIES = 

all:
	$(CC) -o output main.c -I/usr/include/python2.5/ -lpython2.5 -lGL -lGLU `sdl-config --cflags --libs` -lSDL_image

clean:
	@echo Cleaning up...
	@rm output
	@echo Done.
```

---

### Post by nvteighen on 2008-11-15
I'd write the Makefile this way:

```

C = gcc -Wall -ansi
PYTHON = -I/usr/include/python2.5/ -lpython2.5
SDL = -lGL -lGLU `sdl-config --cflags --libs` -lSDL_image
LIBRARIES = libxxx.a # if in the same directory

output: main.o
	$(CC) -o $@ $< $(LIBRARIES) $(PYTHON) $(SDL)

main.o: main.c
	$(CC) -c $<

.PHONY: clean

clean:
	@echo Cleaning up...
	@rm output
	@echo Done.

```

I really dislike the 'all' construct... Separate stuff into dependencies and variables, use the automatic variables ($@, $<, etc.)... There are idioms that allow, for example, to take all .c files in a directory and compile them into .o automatically.

Also, when creating "phony dependencies", include them as source for .PHONY (.PHONY:...) so Make doesn't get confused if you happen to have a file called "clean".

---

### Post by crazyfuturamanoob on 2008-11-15
> **nvteighen said:**
> I'd write the Makefile this way:

```

C = gcc -Wall -ansi
PYTHON = -I/usr/include/python2.5/ -lpython2.5
SDL = -lGL -lGLU `sdl-config --cflags --libs` -lSDL_image
LIBRARIES = libxxx.a # if in the same directory

output: main.o
	$(CC) -o $@ $< $(LIBRARIES) $(PYTHON) $(SDL)

main.o: main.c
	$(CC) -c $<

.PHONY: clean

clean:
	@echo Cleaning up...
	@rm output
	@echo Done.

```

I really dislike the 'all' construct... Separate stuff into dependencies and variables, use the automatic variables ($@, $<, etc.)... There are idioms that allow, for example, to take all .c files in a directory and compile them into .o automatically.

Also, when creating "phony dependencies", include them as source for .PHONY (.PHONY:...) so Make doesn't get confused if you happen to have a file called "clean".

That makefile does not work, and I can't understand how to use it.

Actually I don't know anything about makefiles I just copied that from an example makefile.

---

### Post by nvteighen on 2008-11-15
It should work... if you use 'make', not 'make all'

Be sure to copy the static library to the same directory and replace **LIBRARIES = libxxx.a** to fit the library's name.

A nice introduction to Makefiles: [http://crasseux.com/books/ctutorial/Writing-a-makefile.html](http://crasseux.com/books/ctutorial/Writing-a-makefile.html)

---

### Post by dwhitney67 on 2008-11-15
> **nvteighen said:**
> It should work... if you use 'make', not 'make all'

Be sure to copy the static library to the same directory and replace **LIBRARIES = libxxx.a** to fit the library's name.

A nice introduction to Makefiles: [http://crasseux.com/books/ctutorial/Writing-a-makefile.html](http://crasseux.com/books/ctutorial/Writing-a-makefile.html)
I can see a problem with the Makefile you presented.

First, you should separate the include-paths from the library paths.  When main.c is compiled, you are not providing the included-path (for python).  Not that it is required for this case; but in general the include-paths should be used when compiling.  Include paths are not needed when linking.

Here's a Makefile that should be able to be used (but I have not tested it):
```

SRCS      = main.c
APPNAME   = output

CFLAGS    = -Wall -pedantic `sdl-config --cflags`
LFLAGS    = `sdl-config --libs` -lchipmunk
LPATH     = -L./

# No changes below this line are required!

OBJS      = $(SRCS:.c=.o)
DEP_FILE  = .depend

.PHONY: all clean distclean


all: depend $(APPNAME)

$(APPNAME): $(OBJS)
        @echo Makefile - linking $@
        @$(CC) $(LPATH) $(LFLAGS) $^ -o $@

.c.o:
        @echo Makefile - compiling $<
        @$(CC) $(CFLAGS) -c $< -o $@

clean:
        $(RM) $(OBJS)

distclean: clean
        $(RM) $(APPNAME)
        $(RM) $(DEP_FILE)

depend: $(DEP_FILE)
        @touch $(DEP_FILE)

$(DEP_FILE):
        @echo Makefile - building dependencies in: $@
        @$(CC) -E -MM $(CFLAGS) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

---

### Post by crazyfuturamanoob on 2008-11-16
> **nvteighen said:**
> It should work... if you use 'make', not 'make all'

Be sure to copy the static library to the same directory and replace **LIBRARIES = libxxx.a** to fit the library's name.

A nice introduction to Makefiles: [http://crasseux.com/books/ctutorial/Writing-a-makefile.html](http://crasseux.com/books/ctutorial/Writing-a-makefile.html)

Tried it with this makefile:
> C = gcc -Wall -ansi
PYTHON = -I/usr/include/python2.5/ -lpython2.5
SDL = -lGL -lGLU `sdl-config --cflags --libs` -lSDL_image
LIBRARIES = libchipmunk.a # if in the same directory

output: main.o
	$(CC) -o $@ $< $(LIBRARIES) $(PYTHON) $(SDL)

main.o: main.c
	$(CC) -c $<

.PHONY: clean

clean:
	@echo Cleaning up...
	@rm output
	@echo Done.

And this is the output:
> arho@ohra-laptop:~$ make
cc -c main.c
main.c:35:17: error: SDL.h: No such file or directory
main.c:36:23: error: SDL_image.h: No such file or directory
In file included from main.c:39:
lib/graphics.c:2: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
lib/graphics.c: In function ‘LoadTexture’:
lib/graphics.c:80: error: ‘SDL_Surface’ undeclared (first use in this function)
lib/graphics.c:80: error: (Each undeclared identifier is reported only once
lib/graphics.c:80: error: for each function it appears in.)
lib/graphics.c:80: error: ‘TexIMG’ undeclared (first use in this function)
lib/graphics.c:92: error: ‘SDL_SRCALPHA’ undeclared (first use in this function)
main.c: At top level:
main.c:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘event’
main.c:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
main.c: In function ‘initSDL’:
main.c:78: error: ‘SDL_INIT_VIDEO’ undeclared (first use in this function)
main.c:78: error: ‘SDL_INIT_AUDIO’ undeclared (first use in this function)
main.c:86: error: ‘videoInfo’ undeclared (first use in this function)
main.c:96: error: ‘SDL_OPENGL’ undeclared (first use in this function)
main.c:97: error: ‘SDL_GL_DOUBLEBUFFER’ undeclared (first use in this function)
main.c:98: error: ‘SDL_HWPALETTE’ undeclared (first use in this function)
main.c:99: error: ‘SDL_RESIZABLE’ undeclared (first use in this function)
main.c:103: error: ‘SDL_HWSURFACE’ undeclared (first use in this function)
main.c:105: error: ‘SDL_SWSURFACE’ undeclared (first use in this function)
main.c:109: error: ‘SDL_HWACCEL’ undeclared (first use in this function)
main.c:115: error: ‘surface’ undeclared (first use in this function)
main.c: At top level:
main.c:131: error: expected ‘)’ before ‘*’ token
main.c: In function ‘main’:
main.c:222: error: ‘event’ undeclared (first use in this function)
main.c:227: error: ‘SDL_ACTIVEEVENT’ undeclared (first use in this function)
main.c:236: error: ‘SDL_VIDEORESIZE’ undeclared (first use in this function)
main.c:238: error: ‘surface’ undeclared (first use in this function)
main.c:249: error: ‘SDL_KEYDOWN’ undeclared (first use in this function)
main.c:254: error: ‘SDL_MOUSEMOTION’ undeclared (first use in this function)
main.c:259: error: ‘SDL_QUIT’ undeclared (first use in this function)
make: *** [main.o] Virhe 1
arho@ohra-laptop:~$ 

And I have a folder called "lib" which contains the other .c & .h files, which main.c includes and uses.

---

### Post by crazyfuturamanoob on 2008-11-16
BTW what is object code file .o? How does it differ from executables or source code files?

And what is 'linking'? I made another makefile which makes a bunch of .o files then it builds an executable from them,
but it says *"gcc: libchipmunk.a: linker input file unused because linking not done"*. How can I link the files?

---

### Post by dwhitney67 on 2008-11-16
When building a C/C++ application, you need to compile the source code first; this step can, if requested, produce an object file (i.e. the .o file).  When building simple applications (e.g. "hello world" program), you probably never generated the .o file; you probably instructed gcc to compile and link.

When dealing with many modules (or even just one) and with a Makefile handy, it is convenient to produce individual .o files.  The rationale for doing this is simple; you do not want to recompile all files if a change is made to just one source file.  Of course, a change could force all files to be recompiled, and that is where the need to generate dependencies comes into play.

Anyhow, after you have compiled all of your file(s) successfully, you can then link them together to form the executable application.  Oftentimes, complex applications require that you link in external object files that are stored within a static-library (-ies), or link with a shared-library (-ies) that will be accessed by the application during runtime.

I do not familiar with SDL, but it appears that it is present on your system as a collection of shared-libraries and header (.h) files.

Header files typically reside directly within /usr/include or within a subdirectory within that area.  If the latter, then you may want to specify in your source code something like #include <SDL/SDL.h>.

But since you are relying on 'sdl-config', specifying #include <SDL.h> should suffice.  However, you will then be required to pass the include-path of the SDL header files to the gcc compiler when you compile.  You are currently not performing this step.

To pass the include-path to gcc, the -I (uppercase "eye") option needs to be used.  "sdl-config" provides that information, along with other C compiler flags that you will require.

In your Makefile, I suggest that you create a definition for CFLAGS that resembles the following:
```

CFLAGS = -Wall -pedantic `sdl-config --cflags`

```
Then in the statement where you compile your code, use the CFLAGS:
```

main.o: main.c
        $(CC) $(CFLAGS) -c $@

```

After you have completed generating your .o files, then focus on linking.  You will be required to link in libraries.  I am not sure where your libchipmunk.a library is located at, so I will assume in the same working directory as your project.

The first thing to do is set up LFLAGS and LPATH in the Makefile:
```

LFLAGS = `sdl-config --libs` -lchipmunk
LPATH  = -L./

```

Then to link your object file(s) to produce the executable:
```

output: main.o
        $(CC) $^ $(LPATH) $(LFLAGS) -o $@

```
The ordering of the libraries in the step above is important.  Thus if you have a unresolved errors, it could mean that libchipmunk.a needs to be specified before the SDL library dependencies.  If this happens, just modify LFLAGS.

Earlier I had provided a Makefile that is fairly complete.  I would suggest to copy/paste it and edit it to add your project specific stuff to it.  Let me know if you have further questions.

P.S.  Sorry for the lengthy post.

---

### Post by nvteighen on 2008-11-16
> **dwhitney67 said:**
> I can see a problem with the Makefile you presented.

First, you should separate the include-paths from the library paths.  When main.c is compiled, you are not providing the included-path (for python).  Not that it is required for this case; but in general the include-paths should be used when compiling.  There are not needed when linking.

Yup, you're right. My mistake there.

> **crazyfuturamanoob said:**
> 
And I have a folder called "lib" which contains the other .c & .h files, which main.c includes and uses.

Your output is gcc failing. Possibly because of my error of misplacing $(PYTHON)... but as you say you have other source files you want to include into the compilation... so, let's try with this:

(Please, dwhitney67, could you review this? I'm not sure how to deal with object files when they're placed on a different folder)
```

C = gcc -Wall -ansi
INCLUDE = -I/usr/include/python2.5/ `sdl-config --cflags`
LIBS = libchipmunk.a `sdl-config --libs` -lGL -lGLU -lSDL_image -libpython2.5

SRCS = $(wildcard *.c) $(wildcard lib/*.c) # Hmm... I'm not sure on this
OBJS = $(SRCS:.c=.o)

.PHONY: clean

output: $(OBJS)
	$(CC) -o $@ $^ $(LIBS)

$(OBJS): $(SRCS)
	$(CC) -c $< $(INCLUDE)

clean:
# Usually, 'clean' is used to cleanup temporary stuff, not the application.
	@echo Cleaning up...
	@rm *.o lib/*.o
	@echo Done.

```

> **crazyfuturamanoob said:**
> BTW what is object code file .o? How does it differ from executables or source code files?

And what is 'linking'? I made another makefile which makes a bunch of .o files then it builds an executable from them,
but it says *"gcc: libchipmunk.a: linker input file unused because linking not done"*. How can I link the files?

Ok... The C (and also the C++) compiler works on four stages, of which the first three are performed on each file separately.

1. Preprocessing: The preprocessor looks at the # directives, so it expands macros, include headers, etc.
2. Compiling: The compiler takes the preprocessed source and transforms it into Assembly code.
3. Assembling: The assembler takes the compiled Assembly and generates the binary Object Code. This code is just a binary translation of the input source file.
4. Linking: All input object files are linked together and also to the shared/static libraries you specify. Also the Standard Library is linked.

Only the linking stage makes you an executable, as object files don't include anything defined outside the corresponding source file... not even a reference where to look at (they only know the names of stuff). A trivial Hello World program using printf() wouldn't even work because the code for printf() is in /usr/lib/libc6.so. This also implies some adjustment on references to memory addresses.

---

### Post by dwhitney67 on 2008-11-16
> **nvteighen said:**
> ...

(Please, dwhitney67, could you review this? I'm not sure how to deal with object files when they're placed on a different folder)
```

C = gcc -Wall -ansi
INCLUDE = -I/usr/include/python2.5/ `sdl-config --cflags`
LIBS = libchipmunk.a `sdl-config --libs` -lGL -lGLU -lSDL_image -libpython2.5

SRCS = $(wildcard *.c) $(wildcard lib/*.c) # Hmm... I'm not sure on this
OBJS = $(SRCS:.c=.o)

.PHONY: clean

output: $(OBJS)
	$(CC) -o $@ $^ $(LIBS)

$(OBJS): $(SRCS)
	$(CC) -c $< $(INCLUDE)

clean:
# Usually, 'clean' is used to cleanup temporary stuff, not the application.
	@echo Cleaning up...
	@rm *.o lib/*.o
	@echo Done.

```

The setup of SRCS will indeed work just fine.

As for the setup of C, specifying gcc is not required.  But what is worse is that you are not using C, which btw, really should be defined as CFLAGS, when you compile the source file(s).

I would also recommend that you specify $(OBJS) in the 'clean' section when removing the object files.  A little typo and you could potentially delete all the files in your project directory.

Take a look at the Makefile I posted earlier.  When developing a Makefile, it is helpful to "templatize" it such that it can be used again and again for different projects, with minimal changes.

P.S.  The addition of libchipmunk.a to LIBS still bothers me.  It seems to me that it should be -lchipmunk.  Either way, it might not be needed if the object files in ./lib are for the chipmunk library.

---

### Post by crazyfuturamanoob on 2008-11-16
> **dwhitney67 said:**
> blahblahblah :D makefile 

You should use tabs instead of spaces before command lines.

Here's a quote from [GNU C Programming tutorial]("http://crasseux.com/books/ctutorial/Rule-Introduction.html#Rule%20Introduction")
> 
Please note: you need to put a tab character at the beginning of every command line! This is a common mistake that even experienced makefile writers can make.


edit: How to include chipmunk then? I tried **#include "chipmunk.h"** and **#include <chipmunk.h>** but doesn't work. I every file in the same folder.

---

### Post by nvteighen on 2008-11-16
> **dwhitney67 said:**
> The setup of SRCS will indeed work just fine.

Thanks.

> As for the setup of C, specifying gcc is not required.  But what is worse is that you are not using C, which btw, really should be defined as CFLAGS, when you compile the source file(s).

You mean the variable called C. That's surely a typo, it should be CC.

> I would also recommend that you specify $(OBJS) in the 'clean' section when removing the object files.  A little typo and you could potentially delete all the files in your project directory.

That was because of haste, I usually do that... But thanks for pointing it out.

> Take a look at the Makefile I posted earlier.  When developing a Makefile, it is helpful to "templatize" it such that it can be used again and again for different projects, with minimal changes.

Of course... The problem is that I, maybe this was a mistake, tried to simplify my "template" for this thread...

> P.S.  The addition of libchipmunk.a to LIBS still bothers me.  It seems to me that it should be -lchipmunk.  Either way, it might not be needed if the object files in ./lib are for the chipmunk library.

Well, the OP should tell us where he has placed the library. But, anyway, maybe using -L./ would be better.

> **crazyfuturamanoob said:**
> 
edit: How to include chipmunk then? I tried **#include "chipmunk.h"** and **#include <chipmunk.h>** but doesn't work. I every file in the same folder.

If the header file is in the ./lib subfolder, then, use #include "lib/chipmunk.h"... The < > are used for system-wide installed headers.

---

### Post by crazyfuturamanoob on 2008-11-16
> **nvteighen said:**
> 
If the header file is in the ./lib subfolder, then, use #include "lib/chipmunk.h"... The < > are used for system-wide installed headers.

I got now everything in one and the same folder. No subfolders.
libchipmunk.a is in that folder. With main.c and makefile and everything.

main.c line 39
```
#include "chipmunk.h"
```
Output of "make" in terminal:
```
main.c:39:22: error: chipmunk.h: No such file or directory
```

Makefile:
```
[color=#19177C]SRCS[/color]      [color=#666666]=[/color] main.c
[color=#19177C]APPNAME[/color]   [color=#666666]=[/color] output

[color=#19177C]CFLAGS[/color]    [color=#666666]=[/color] -Wall -pedantic [color=#BA2121]`[/color]sdl-config --cflags[color=#BA2121]`[/color]
[color=#19177C]LFLAGS[/color]    [color=#666666]=[/color] [color=#BA2121]`[/color]sdl-config --libs[color=#BA2121]`[/color] -lchipmunk -lGL -lGLU -lSDL_image
[color=#19177C]LPATH[/color]     [color=#666666]=[/color] -L./

[color=#408080][i]# No changes below this line are required!
[/i][/color]
[color=#19177C]OBJS[/color]      [color=#666666]=[/color] [color=#008000]**$(**[/color]SRCS:.c[color=#666666]=[/color].o[color=#008000]**)**[/color]
[color=#19177C]DEP_FILE[/color]  [color=#666666]=[/color] .depend

.PHONY: all clean distclean


all: depend [color=#008000]**$(**[/color]APPNAME[color=#008000]**)**[/color]

[color=#008000]**$(**[/color]APPNAME[color=#008000]**)**[/color]: [color=#008000]**$(**[/color]OBJS[color=#008000]**)**[/color]
	@echo Makefile - linking [color=#19177C]$@[/color]
	@[color=#008000]**$(**[/color]CC[color=#008000]**)**[/color] [color=#008000]**$(**[/color]LPATH[color=#008000]**)**[/color] [color=#008000]**$(**[/color]LFLAGS[color=#008000]**)**[/color] [color=#19177C]$^[/color] -o [color=#19177C]$@[/color]

.c.o:
	@echo Makefile - compiling [color=#19177C]$<[/color]
	@[color=#008000]**$(**[/color]CC[color=#008000]**)**[/color] [color=#008000]**$(**[/color]CFLAGS[color=#008000]**)**[/color] -c [color=#19177C]$<[/color] -o [color=#19177C]$@[/color]

clean:
	[color=#008000]**$(**[/color]RM[color=#008000]**)**[/color] [color=#008000]**$(**[/color]OBJS[color=#008000]**)**[/color]

distclean: clean
	[color=#008000]**$(**[/color]RM[color=#008000]**)**[/color] [color=#008000]**$(**[/color]APPNAME[color=#008000]**)**[/color]
	[color=#008000]**$(**[/color]RM[color=#008000]**)**[/color] [color=#008000]**$(**[/color]DEP_FILE[color=#008000]**)**[/color]

depend: [color=#008000]**$(**[/color]DEP_FILE[color=#008000]**)**[/color]
	@touch [color=#008000]**$(**[/color]DEP_FILE[color=#008000]**)**[/color]

[color=#008000]**$(**[/color]DEP_FILE[color=#008000]**)**[/color]:
	@echo Makefile - building dependencies in: [color=#19177C]$@[/color]
	@[color=#008000]**$(**[/color]CC[color=#008000]**)**[/color] -E -MM [color=#008000]**$(**[/color]CFLAGS[color=#008000]**)**[/color] [color=#008000]**$(**[/color]SRCS[color=#008000]**)**[/color] >> [color=#008000]**$(**[/color]DEP_FILE[color=#008000]**)**[/color]

[color=#BC7A00]ifeq (,$(findstring clean,$(MAKECMDGOALS)))
[/color][color=#BC7A00]ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
[/color][color=#BC7A00]-include $(DEP_FILE)
[/color][color=#BC7A00]endif
[/color][color=#BC7A00]endif
[/color]
```

And I really want to include chipmunk as static in the executable, 
because nearly nobody has chipmunk compiled and installed, 
so the executable wouldn't need it from outside, this is a must.

---

### Post by dwhitney67 on 2008-11-16
> **crazyfuturamanoob said:**
> I got now everything in one and the same folder. No subfolders.
libchipmunk.a is in that folder. With main.c and makefile and everything.

main.c line 39
```
#include "chipmunk.h"
```
Output of "make" in terminal:
```
main.c:39:22: error: chipmunk.h: No such file or directory
```

Check your current working directory.  Is there a file called 'chipmunk.h'?  The compiler is telling you that it cannot find it.  Perhaps you misspelled the file name?

As for linking your application with the libchipmunk.a, your Makefile is specifying the library correctly.

I assume the libchipmunk.a was created using the 'ar' command (for archiving objects files into a library).  Can you please confirm if this is true?

P.S.  I am well aware that command statements in Makefiles need to be preceded with a tab.

---

### Post by crazyfuturamanoob on 2008-11-16
> **dwhitney67 said:**
> Check your current working directory.  Is there a file called 'chipmunk.h'?  The compiler is telling you that it cannot find it.  Perhaps you misspelled the file name?

As for linking your application with the libchipmunk.a, your Makefile is specifying the library correctly.

I assume the libchipmunk.a was created using the 'ar' command (for archiving objects files into a library).  Can you please confirm if this is true?

P.S.  I am well aware that command statements in Makefiles need to be preceded with a tab.

I just took a copy of libchipmunk.a from Chipmunk-4.1.0/src/libchipmunk.a. I just guessed it could be a static pre-compiled library I can use.

If not, then what is it? How? No chipmunk.h in the same folder.

> P.S. I am well aware that command statements in Makefiles need to be preceded with a tab.
Ok, sorry. For some reason when I copy-pasted I got 8 spaces, not tabs.
Might also be my special-configured Scite, which has it's indentation settings
always on 4 spaces instead of tabs. Maybe it automatically converted tabs to spaces?

---

### Post by dwhitney67 on 2008-11-16
> **crazyfuturamanoob said:**
> I just took a copy of libchipmunk.a from Chipmunk-4.1.0/src/libchipmunk.a. I just guessed it could be a static pre-compiled library I can use.

If not, then what is it? How? No chipmunk.h in the same folder.

Ok, in your Makefile, setup LPATH to be something like, where <path> is the folder where Chipmunk-4.1.0 resides:
```

...
LPATH = -L<path>/Chipmunk-4.1.0/src
...

```
And hence the local copy of libchipmunk.a will not be needed.

As for the chipmunk.h header file, is it located in <path>/Chipmunk-4.1.0/src?  If so, then add the path to the CFLAGS.  For instance:
```

...
CFLAGS    = -Wall -pedantic `sdl-config --cflags` -I<path>/Chipmunk-4.1.0/src
...

```


> **crazyfuturamanoob said:**
> 
Ok, sorry. For some reason when I copy-pasted I got 8 spaces, not tabs.
Might also be my special-configured Scite, which has it's indentation settings
always on 4 spaces instead of tabs. Maybe it automatically converted tabs to spaces?
Probably an Ubuntu Forum thing; it probably stripped away my tabs and replaced them with spaces.

---

### Post by crazyfuturamanoob on 2008-11-16
What can I do about these warnings?
```

arho@ohra-laptop:~/Työpöytä/C$ make
Makefile - compiling main.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL.h:44,
                 from /usr/include/SDL/SDL_image.h:28,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from /usr/include/SDL/SDL_image.h:30,
                 from main.c:35:
/usr/include/SDL/begin_code.h:93:8: warning: C++ style comments are not allowed in ISO C90
/usr/include/SDL/begin_code.h:93:8: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:62,
                 from main.c:39:
Chipmunk-4.1.0/src/cpVect.h: In function ‘cpv’:
Chipmunk-4.1.0/src/cpVect.h:31: warning: initializer element is not computable at load time
Chipmunk-4.1.0/src/cpVect.h:31: warning: initializer element is not computable at load time
In file included from Chipmunk-4.1.0/src/chipmunk.h:62,
                 from main.c:39:
Chipmunk-4.1.0/src/cpVect.h:102:38: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpVect.h:102:38: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:63,
                 from main.c:39:
Chipmunk-4.1.0/src/cpBB.h: In function ‘cpBBNew’:
Chipmunk-4.1.0/src/cpBB.h:30: warning: initializer element is not computable at load time
Chipmunk-4.1.0/src/cpBB.h:30: warning: initializer element is not computable at load time
Chipmunk-4.1.0/src/cpBB.h:30: warning: initializer element is not computable at load time
Chipmunk-4.1.0/src/cpBB.h:30: warning: initializer element is not computable at load time
In file included from Chipmunk-4.1.0/src/chipmunk.h:63,
                 from main.c:39:
Chipmunk-4.1.0/src/cpBB.h:52:54: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpBB.h:52:54: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:64,
                 from main.c:39:
Chipmunk-4.1.0/src/cpBody.h:28:2: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpBody.h:28:2: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:65,
                 from main.c:39:
Chipmunk-4.1.0/src/cpArray.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpArray.h:22:1: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:66,
                 from main.c:39:
Chipmunk-4.1.0/src/cpHashSet.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpHashSet.h:22:1: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:67,
                 from main.c:39:
Chipmunk-4.1.0/src/cpSpaceHash.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpSpaceHash.h:22:1: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:69,
                 from main.c:39:
Chipmunk-4.1.0/src/cpShape.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpShape.h:22:1: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:70,
                 from main.c:39:
Chipmunk-4.1.0/src/cpPolyShape.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpPolyShape.h:22:1: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:70,
                 from main.c:39:
Chipmunk-4.1.0/src/cpPolyShape.h: In function ‘cpPolyShapeContainsVertPartial’:
Chipmunk-4.1.0/src/cpPolyShape.h:87: warning: ISO C90 forbids mixed declarations and code
In file included from Chipmunk-4.1.0/src/chipmunk.h:72,
                 from main.c:39:
Chipmunk-4.1.0/src/cpArbiter.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpArbiter.h:22:1: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:73,
                 from main.c:39:
Chipmunk-4.1.0/src/cpCollision.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpCollision.h:22:1: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:75,
                 from main.c:39:
Chipmunk-4.1.0/src/cpJoint.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpJoint.h:22:1: warning: (this will be reported only once per input file)
In file included from Chipmunk-4.1.0/src/chipmunk.h:75,
                 from main.c:39:
Chipmunk-4.1.0/src/cpJoint.h: At top level:
Chipmunk-4.1.0/src/cpJoint.h:32: warning: comma at end of enumerator list
In file included from Chipmunk-4.1.0/src/chipmunk.h:77,
                 from main.c:39:
Chipmunk-4.1.0/src/cpSpace.h:22:1: warning: C++ style comments are not allowed in ISO C90
Chipmunk-4.1.0/src/cpSpace.h:22:1: warning: (this will be reported only once per input file)
In file included from main.c:42:
graphics.c: In function ‘LoadTexture’:
graphics.c:91: warning: ISO C90 forbids mixed declarations and code
Makefile - linking output
arho@ohra-laptop:~/Työpöytä/C$ 

```
They are all about // comments which gcc doesn't like. Only /* comments */ don't give warnings.
And I am too lazy to replace every comment tags in SDL & Chipmunk source code.
Can I somehow make gcc silent about comment warnings?

And why it reports the same warning 200 times?

Edit:
And for some reason, it still says ```
*main.c:(.text+0x809): undefined reference to `cpInitChipmunk'*
```

Edit2:
I found a pre-compiled static chipmunk library from [[COLOR="Blue"]here[/COLOR]]("http://aerosol.googlecode.com/files/ChipmunkStaticLib1.tar.gz") It's surely the correct one.

How can I use it in my app? That file contains libChipmunk.a and headers for everything.

---

### Post by dwhitney67 on 2008-11-16
Add this to your CFLAGS:  -std=gnu99

This will force gcc to use the GNU version of the 1999 C standards, which permits the // style of comments amongst other things.

Concerning your other issue with respect to the undefined reference, that is telling you that the function cpInitChipmunk() cannot be found.  Did you perhaps misspell the function name?  Try to see if that function exists in the Chipmunk source code.

Edit..

I just took a look at the precompiled Chipmunk library you posted via the link.  The function cpInitChipmunk() does indeed exist.

The header files for Chipmunk are located in ChipmunkStaticLib1/headers.  Thus this would need to be correctly specified with your CFLAGS with -I<path>/ChipmunkStaticLib1/headers.

As for the library, the LPATH will need to be modified to have something like -L<path>/ChipmunkStaticLib1.

In both cases above, replace <path> with the subdirectory where you placed ChipmunkStaticLib1.

---

### Post by dwhitney67 on 2008-11-16
Update...

I just tried to compile/link a simple program with the static Chipmunk library.  Apparently gcc was unhappy with it; maybe it is for a different architecture?

Here's the program:
[php]
#include <chipmunk.h>

int main()
{
  cpInitChipmunk();
  return 0;
}
[/php]

For the Makefile, I set up these flags:
```

APP       = chiptest
CFLAGS    = -Wall -pedantic -std=gnu99 -I/home/whitney/Download/ChipmunkStaticLib1/headers
LIBS      = -lChipmunk
LIBPATH   = -L/home/whitney/Download/ChipmunkStaticLib1

```
This is the error I received:
```

/home/whitney/Download/ChipmunkStaticLib1/libChipmunk.a: file not recognized: File format not recognized

```

---

### Post by crazyfuturamanoob on 2008-11-16
> **dwhitney67 said:**
> Update...

I just tried to compile/link a simple program with the static Chipmunk library.  Apparently gcc was unhappy with it; maybe it is for a different architecture?

Here's the program:
[php]
#include <chipmunk.h>

int main()
{
  cpInitChipmunk();
  return 0;
}
[/php]

For the Makefile, I set up these flags:
```

APP       = chiptest
CFLAGS    = -Wall -pedantic -std=gnu99 -I/home/whitney/Download/ChipmunkStaticLib1/headers
LIBS      = -lChipmunk
LIBPATH   = -L/home/whitney/Download/ChipmunkStaticLib1

```
This is the error I received:
```

/home/whitney/Download/ChipmunkStaticLib1/libChipmunk.a: file not recognized: File format not recognized

```

Okey dokey... I have used Chipmunk before with Python, and it works. 
It should be cross-platform, as many other people have used it on Linux, with C, Python, and Ruby.

That libChipmunk.a was precompiled, probably on mac, because slembcke, the guy who is developing chipmunk, uses mac, as I know.
I wasn't aware of that when I found the link.

But I got another libchipmunk.a, which I compiled on my Ubuntu 8.04, from chipmunk source code.
I made an archive containing headers and libchipmunk.a: [chipmunk.zip]("http://host-a.net/crazyfuturamafreak/chipmunk.zip") (Select "save to disk" instead of "open with package manager" when the pop-up comes)

---

### Post by dwhitney67 on 2008-11-16
I downloaded and tested with the chipmunk.tar.gz package you posted.

The libchipmunk.a is indeed missing the cpInitChipmunk() function.  The function prototype however is provided in chipmunk.h.

Could you have possibly obtained a bad build?  Did you build it yourself?

P.S.  All you provided are the header files and the library.  Do you have the source code (.c or .cpp files) for chipmunk?

---

### Post by crazyfuturamanoob on 2008-11-16
> **dwhitney67 said:**
> I downloaded and tested with the chipmunk.tar.gz package you posted.

The libchipmunk.a is indeed missing the cpInitChipmunk() function.  The function prototype however is provided in chipmunk.h.

Could you have possibly obtained a bad build?  Did you build it yourself?

P.S.  All you provided are the header files and the library.  Do you have the source code (.c or .cpp files) for chipmunk?

I'd like to try rebuilding it, but I don't know how to uninstall it.

Should I delete some previously linked stuff? Or just the Chipmunk-X.X.X folder?

---

### Post by dwhitney67 on 2008-11-16
> **crazyfuturamanoob said:**
> I'd like to try rebuilding it, but I don't know how to uninstall it.

Should I delete some previously linked stuff? Or just the Chipmunk-X.X.X folder?
If it is all sitting in your Chipmunk-X.X.X folder, then deleting it is a cinch.  Just remove the directory.
```

rm -rf Chipmunk-X.X.X

```
Then re-obtain the source code and rebuild it (per the instructions).

---

### Post by crazyfuturamanoob on 2008-11-16
I got this:
```
arho@ohra-laptop:~/Tiedostot/Chipmunk-4.1.0$ cmake CMakeLists.txt 
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.6)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so - found
-- Looking for gethostbyname
-- Looking for gethostbyname - found
-- Looking for connect
-- Looking for connect - found
-- Looking for remove
-- Looking for remove - found
-- Looking for shmat
-- Looking for shmat - found
-- Looking for IceConnectionNumber in ICE
-- Looking for IceConnectionNumber in ICE - found
-- Found X11: /usr/lib/libX11.so
libglut found. /usr/include /usr/lib/libglut.so;/usr/lib/libXmu.so;/usr/lib/libXi.so
libGL found. /usr/include /usr/lib/libGLU.so;/usr/lib/libGL.so;/usr/lib/libSM.so;/usr/lib/libICE.so;/usr/lib/libX11.so;/usr/lib/libXext.so
-- Configuring done
CMake Warning (dev) at Demo/CMakeLists.txt:48 (ADD_EXECUTABLE):
  Policy CMP0003 should be set before this line.  Add code such as

    if(COMMAND cmake_policy)
      cmake_policy(SET CMP0003 NEW)
    endif(COMMAND cmake_policy)

  as early as possible but after the most recent call to
  cmake_minimum_required or cmake_policy(VERSION).  This warning appears
  because target "../chipmunk_demos" links to some libraries for which the
  linker must search:

    GL, glut

  and other libraries with known full path:

    /home/arho/Tiedostot/Chipmunk-4.1.0/src/libchipmunk.a

  CMake is adding directories in the second list to the linker search path in
  case they are needed to find libraries from the first list (for backwards
  compatibility with CMake 2.4).  Set policy CMP0003 to OLD or NEW to enable
  or disable this behavior explicitly.  Run "cmake --help-policy CMP0003" for
  more information.
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Generating done
-- Build files have been written to: /home/arho/Tiedostot/Chipmunk-4.1.0
arho@ohra-laptop:~/Tiedostot/Chipmunk-4.1.0$ make
Scanning dependencies of target chipmunk
[  2%] Building C object src/CMakeFiles/chipmunk.dir/chipmunk.o
[  5%] Building C object src/CMakeFiles/chipmunk.dir/cpArbiter.o
[  8%] Building C object src/CMakeFiles/chipmunk.dir/cpArray.o
[ 11%] Building C object src/CMakeFiles/chipmunk.dir/cpBB.o
[ 14%] Building C object src/CMakeFiles/chipmunk.dir/cpBody.o
[ 17%] Building C object src/CMakeFiles/chipmunk.dir/cpCollision.o
[ 20%] Building C object src/CMakeFiles/chipmunk.dir/cpHashSet.o
[ 23%] Building C object src/CMakeFiles/chipmunk.dir/cpJoint.o
[ 26%] Building C object src/CMakeFiles/chipmunk.dir/cpPolyShape.o
[ 29%] Building C object src/CMakeFiles/chipmunk.dir/cpShape.o
[ 32%] Building C object src/CMakeFiles/chipmunk.dir/cpSpace.o
[ 35%] Building C object src/CMakeFiles/chipmunk.dir/cpSpaceHash.o
[ 38%] Building C object src/CMakeFiles/chipmunk.dir/cpVect.o
Linking C shared library libchipmunk.so
[ 38%] Built target chipmunk
Scanning dependencies of target chipmunk_static
[ 41%] Building C object src/CMakeFiles/chipmunk_static.dir/chipmunk.o
[ 44%] Building C object src/CMakeFiles/chipmunk_static.dir/cpArbiter.o
[ 47%] Building C object src/CMakeFiles/chipmunk_static.dir/cpArray.o
[ 50%] Building C object src/CMakeFiles/chipmunk_static.dir/cpBB.o
[ 52%] Building C object src/CMakeFiles/chipmunk_static.dir/cpBody.o
[ 55%] Building C object src/CMakeFiles/chipmunk_static.dir/cpCollision.o
[ 58%] Building C object src/CMakeFiles/chipmunk_static.dir/cpHashSet.o
[ 61%] Building C object src/CMakeFiles/chipmunk_static.dir/cpJoint.o
[ 64%] Building C object src/CMakeFiles/chipmunk_static.dir/cpPolyShape.o
[ 67%] Building C object src/CMakeFiles/chipmunk_static.dir/cpShape.o
[ 70%] Building C object src/CMakeFiles/chipmunk_static.dir/cpSpace.o
[ 73%] Building C object src/CMakeFiles/chipmunk_static.dir/cpSpaceHash.o
[ 76%] Building C object src/CMakeFiles/chipmunk_static.dir/cpVect.o
Linking C static library libchipmunk.a
[ 76%] Built target chipmunk_static
Scanning dependencies of target chipmunk_demos
[ 79%] Building C object Demo/CMakeFiles/../chipmunk_demos.dir/Demo1.o
[ 82%] Building C object Demo/CMakeFiles/../chipmunk_demos.dir/Demo2.o
[ 85%] Building C object Demo/CMakeFiles/../chipmunk_demos.dir/Demo3.o
[ 88%] Building C object Demo/CMakeFiles/../chipmunk_demos.dir/Demo4.o
[ 91%] Building C object Demo/CMakeFiles/../chipmunk_demos.dir/Demo5.o
[ 94%] Building C object Demo/CMakeFiles/../chipmunk_demos.dir/Demo6.o
[ 97%] Building C object Demo/CMakeFiles/../chipmunk_demos.dir/Demo7.o
[100%] Building C object Demo/CMakeFiles/../chipmunk_demos.dir/main.o
Linking C executable ../chipmunk_demos
[100%] Built target ../chipmunk_demos
arho@ohra-laptop:~/Tiedostot/Chipmunk-4.1.0$ 
```
Did I do it correctly?

---

### Post by dwhitney67 on 2008-11-16
I'm not a chipmunk, but based on this statement, and the others, I would say that yes, you built it correctly.
```

[ 41%] Building C object src/CMakeFiles/chipmunk_static.dir/chipmunk.o

```

---

### Post by crazyfuturamanoob on 2008-11-17
How can I link/include/add it to my program then?

Also, I found this thing from Chipmunk-1.4.0/Demo/build.sh:
```
gcc -O3 -std=gnu99 -ffast-math ../src/cp*.c ../src/chipmunk.c ./*.c -I../src -lGL -lglut -o chipmunk_demos
```
It obviously compiles the example program.

---

### Post by dwhitney67 on 2008-11-17
Sorry to get back so late; it's been a busy day.

I'm not sure how your system is set.  This is what I had to do to build libchipmunk.

1.  wget [ChipmunkLatest.tgz]("http://files.slembcke.net/chipmunk/release/ChipmunkLatest.tgz")
2.  tar xzvf ChipmunkLatest.tgz
3.  cd Chipmunk-4.1.0
4.  sudo apt-get install cmake
5.  sudo apt-get install freeglut-dev
6.  cmake .
7.  make

You may be able to skip Steps 4 and 5 if you already have the required packages that Chipmunk requires.

When done, libchipmunk.a and the header files will be located in  the src directory.

When specifying the path within your project's Makefile to reference the header files and to the library, you need to specify the entire path.  So if Chipmunk-4.1.0 is located in your home-directory, then these entries in your Makefile should contain:

```

...
CFLAGS    = -Wall -pedantic -std=gnu99 -I$(HOME)/Chipmunk-4.1.0/src
LIBS      = -lchipmunk
LIBPATH   = -L$(HOME)/Chipmunk-4.1.0/src
...

```

I also found an error in the Makefile you are using; this was my fault.  Pay careful attention to the third line below, and fix accordingly in your Makefile:
```

$(APPNAME): $(OBJS)
        @echo Makefile - linking $@
        @$(CC) $^ $(LPATH) $(LFLAGS) -o $@

```

If you still have problems after this, then your system is defying the laws of physics and sanity.

---

### Post by crazyfuturamanoob on 2008-11-18
Edit: 
Had another problem with makefile but figured it out myself, miss spelled a directory's name.

It works now, thanks :)

---

