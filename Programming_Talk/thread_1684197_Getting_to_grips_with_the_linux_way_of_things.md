---
title: "Getting to grips with the linux way of things"
date: 2011-02-08
forum: Programming Talk
---

### Post by thecoshman on 2011-02-08
I have been quite happily programming along with visual studio for some years now, mostly using it for not much more then simple one click compiling. Any hoops, whilst I have no issues with actually programming, I am fecked when it comes to compiling my code on a linux machine!

Can some one hep, or link to, explain to me how to go from source to compiled program I can run on my linux computer?

I have looked into using Anjuta, and it seems all well and good. I can get a simple hello world to run, I can even get SDL and OpenGL to work to the point of spiny graphics of testy goodness. But this is all using a simple 'all in the one file' approach. Any time I try to add in a second file, it all go to pot. It took me a fair while just to get the librarys for openGL included in the project... but worked that one out.

Lets just through out some sort of sample set of files I have for my project.

~/main.cc
~/MyCodeStuff/helper.h
~/MyCodeStuff/helper.cc
~/MyCodeStuff/Graphics/openGLWrap.h
~/MyCodeStuff/Graphics/openGLWrap.cc

From what I gather, .cc is what is normally used to imply a C++ source file on linux.

---

### Post by Milliways on 2011-02-08
> **thecoshman said:**
> I have been quite happily programming along with visual studio for some years now, mostly using it for not much more then simple one click compiling. Any hoops, whilst I have no issues with actually programming, I am fecked when it comes to compiling my code on a linux machine!

Can some one hep, or link to, explain to me how to go from source to compiled program I can run on my linux computer?

I have looked into using Anjuta, and it seems all well and good. I can get a simple hello world to run, I can even get SDL and OpenGL to work to the point of spiny graphics of testy goodness. But this is all using a simple 'all in the one file' approach. Any time I try to add in a second file, it all go to pot. It took me a fair while just to get the librarys for openGL included in the project... but worked that one out.

Lets just through out some sort of sample set of files I have for my project.

~/main.cc
~/MyCodeStuff/helper.h
~/MyCodeStuff/helper.cc
~/MyCodeStuff/Graphics/openGLWrap.h
~/MyCodeStuff/Graphics/openGLWrap.cc

From what I gather, .cc is what is normally used to imply a C++ source file on linux.

Anjuta is a good program, but not the ideal place to start. As you will have discovered, it is quite different from VS.

Firstly you should read the stickies above.

To compile c/c++ on GNU/Linux you NEED a makefile (unless you want to perform each step manually).

I would suggest you try compiling some simple multi file programs from the command line, and try a makefile. For more advanced programming you really need to come to terms with Automake et al.

I started programming c on Ubuntu 12 months ago, so know what you are going through.

I use Geany for most of my development, as it is fast and easy to use, and Anjuta to produce finished projects (using the same source).

---

### Post by worksofcraft on 2011-02-08
> **thecoshman said:**
> I have been quite happily programming along with visual studio for some years now, mostly using it for not much more then simple one click compiling. Any hoops, whilst I have no issues with actually programming, I am fecked when it comes to compiling my code on a linux machine!

Can some one hep, or link to, explain to me how to go from source to compiled program I can run on my linux computer?

I have looked into using Anjuta, and it seems all well and good. I can get a simple hello world to run, I can even get SDL and OpenGL to work to the point of spiny graphics of testy goodness. But this is all using a simple 'all in the one file' approach. Any time I try to add in a second file, it all go to pot. It took me a fair while just to get the librarys for openGL included in the project... but worked that one out.

Lets just through out some sort of sample set of files I have for my project.

~/main.cc
~/MyCodeStuff/helper.h
~/MyCodeStuff/helper.cc
~/MyCodeStuff/Graphics/openGLWrap.h
~/MyCodeStuff/Graphics/openGLWrap.cc

From what I gather, .cc is what is normally used to imply a C++ source file on linux.

I use .cc to indicate a file to compile into an object module and .cpp for files that make an executable

building is then simply a matter of typing at the command prompt:

g++ -c *.cc
g++ *.cpp *.o

or even better if you put your .o files in a software library ;)

---

### Post by thecoshman on 2011-02-09
@worksofcraft

So you advise that, at least to start with, I don't bother with using an IDE; I should manually sort out the compilation using the make file my self.

Well, I would be perfectly fine writing my code with out an IDE, the only feature I would really miss from VS would be the code hinting.

I looked over some of these stikeys, I might have just missed it, but I can't really find anything helping explain how to get to grips with make files, any advice on this front?

---

### Post by johnl on 2011-02-09
The basics of a makefile are rather simple.  You tell make:

1. what you want to make
2. what you need to make it
3. how to make it.

in the format:

```

what_to_make: needed objects to_make it     # you can write comments
    rule to make it                         # after hash signs

```

e.g.

```

my_program:  main.c
    gcc main.c -o my_program

```

Save this as a file named 'makefile' (or Makefile, if you're into capitalisation) in your project directory.  Now when you can type 'make' or 'make my_program' to build your program.


of course this will soon get very repetetive and verbose -- luckily make is way smarter than this, and has nifty features like macros, generic rules, and other cool things.

For example you could shorten the above:

```

my_program:  main.c
[B]    gcc $< -o $@    # $< expands to the prerequisite file (main.c)
                    # $@ expands to the target file (my_program)[/B]

```
These shortcuts are super useful because they mean you are not re-typing the same file names over and over again.  Unfortunately you can't use **$<** with a list of prerequisites, because it expands to just one.


Of course usually your makefile is more than one rule.  For example above I am compiling the sources directly to the executable.  If we have a large program we will want to compile objects first, then link so that if we change a single source every single .c file doesn't need to be recompiled.

So we might have a makefile like this:

```

# link all the .o (object files) to create our program
my_program:  main.o util.o gui.o
    gcc main.o util.o gui.o -o $@

# how to make main.o
main.o: main.c
   gcc -c $< -o $@

# how to make util.o
util.o: util.c
   gcc -c $< -o $@


# how to make gui.o
gui.o: gui.c
   gcc -c $< -o $@

```

Of course this is needlessly repetitive.   The rule to make all the .o files from the .c files is the same, so why not combine them? We'll just tell gcc how to make a .o from a .c and list the .o files we need.

```

# link all the .o (object files) to create our program
my_program:  main.o util.o gui.o
    gcc main.o util.o gui.o -o $@

[B]# generic rule on how to make a .o file from a .c file 
# (this is called a suffix rule)
.c.o:
    gcc -c $< -o $@ [/B]

```

Of course we can also use variable names to make things cleaner, and no longer have to list each object file in the rule and prerequisites individually:

```

[B]CC     = gcc
TARGET = my_program
OBJS   = main.o util.o gui.o

$(TARGET): $(OBJS)
    $(CC) $(OBJS)[/B] -o $@

.c.o:
    $(CC) -c $< -o $@ 

```

What if we need to link with some other library? Or we want to pass flags to gcc? Why not add variables for that?

```

CC      = gcc
**CFLAGS  = -Wall -O2 # flags for gcc**
**LDFLAGS = -lcurses # link with the ncurses library**

TARGET  = my_program
OBJS    = main.o util.o gui.o

$(TARGET): $(OBJS)
    $(CC) **$(LDFLAGS)** $(OBJS) -o $@

.c.o:
    $(CC) -c **$(CFLAGS)** $< -o $@ 

```


You can even use pattern substitution to build the object files dynamically from a list of source files:

```

CC      = gcc
CFLAGS  = -Wall -O2 # flags for gcc
LDFLAGS = -lcurses # link with the ncurses library

TARGET  = my_program
[B]
SRCS    = main.c util.c gui.c
OBJS    = $(SRCS.c=.o) # foreach source, replace .c with .o[/B]

$(TARGET): $(OBJS)
    $(CC) $(LDFLAGS) $(OBJS) -o $@

.c.o:
    $(CC) -c $(CFLAGS) $< -o $@ 

```

Hope this helps.

---

### Post by Simian Man on 2011-02-09
> **Milliways said:**
> To compile c/c++ on GNU/Linux you NEED a makefile (unless you want to perform each step manually).

That is *absolutely* incorrect.  Any decent C++ IDE will handle building automatically if you want it to.  Furthermore, there are *many* command-line build systems and nearly *all* of them are better than make.

My favorite build system is called [scons]("http://www.scons.org/").  With scons, you create a file called "Sconstruct" in your project directory with instructions to compile your program and run the scons command to do so.  Here is a sample Sconstruct:
```

# set up the link libraries you want
libraries = ['GL', 'GLU', 'SDL']

# use all files named ".cc" as sources
sources = Glob('*.cc')

# compiler flags
cflags = '-W -Wall -pedantic -g'
env = Environment(CPPFLAGS = cflags)

# build the program
env.Program(target = 'myprogram', source = sources, LIBS = libraries)

```

You just specify the sources, libs, and flags you want and scons will handle the rest.  Unlike make, it is smart enough to figure out the dependencies between files without being told.  Even better, if you add files, or change the relationships between files, you don't need to alter the Sconstruct file like you would a makefile.

I'm glad johnl posted his howto because it demonstrates better than I could how ridiculously complicated make is for what should be a simple task.  It boggles my mind that people willingly write those things!  He even left off the problem of specifying which source files depend on which headers - which scons knows about automatically too.

So NO, you don't "NEED" a makefile to compile on Linux :).

As for IDEs, I wouldn't personally recommend Anjuta.  I like Eclipse with CDT the best, but for getting started quickly, you can look at Code::Blocks which is nice and more similar to Visual Studio.

Have fun!

---

### Post by johnl on 2011-02-09
> **Simian Man said:**
> That is *absolutely* incorrect.  Any decent C++ IDE will handle building automatically if you want it to.  Furthermore, there are *many* command-line build systems and nearly *all* of them are better than make.

My favorite build system is called [scons]("http://www.scons.org/").  With scons, you create a file called "Sconstruct" in your project directory with instructions to compile your program and run the scons command to do so.  Here is a sample Sconstruct:
```

# set up the link libraries you want
libraries = ['GL', 'GLU', 'SDL']

# use all files named ".cc" as sources
sources = Glob('*.cc')

# compiler flags
cflags = '-W -Wall -pedantic -g'
env = Environment(CPPFLAGS = cflags)

# build the program
env.Program(target = 'myprogram', source = sources, LIBS = libraries)

```

You just specify the sources, libs, and flags you want and scons will handle the rest.  Unlike make, it is smart enough to figure out the dependencies between files without being told.  Even better, if you add files, or change the relationships between files, you don't need to alter the Sconstruct file like you would a makefile.

I'm glad johnl posted his howto because it demonstrates better than I could how ridiculously complicated make is for what should be a simple task.  It boggles my mind that people willingly write those things!  He even left off the problem of specifying which source files depend on which headers - which scons knows about automatically too.

So NO, you don't "NEED" a makefile to compile on Linux :).

As for IDEs, I wouldn't personally recommend Anjuta.  I like Eclipse with CDT the best, but for getting started quickly, you can look at Code::Blocks which is nice and more similar to Visual Studio.

Have fun!

IMO if you are developing on Linux you should at least understand how a makefile works and how to write one, since you will invariably come across code that uses it.  You can add 'auto-magic' dependency generation to a Makefile using the -M family of switches to gcc, but that was beyond the scope of my quick writeup :)


With that said, I've used Scons before and I think it's a great system.  I certainly wouldn't argue against using it.

---

### Post by Simian Man on 2011-02-09
> **johnl said:**
> IMO if you are developing on Linux you should at least understand how a makefile works and how to write one, since you will invariably come across code that uses it.

Agreed, but for a beginner I can think of about a hundred things that are more worthwhile and fun to learn :).

---

### Post by thecoshman on 2011-02-09
Ok wow!

Thanks guys.

I have been playing with some simple compiling with files from sub-directories and the like. I also made it put the '.o' files into a separate folder from the source, so that it was all 'neat' and out of the way.

I say a guide in which one of the targets was called "clean" and it basically removed all of the object files. But how can I get make to actually do this?

I've got to say, that whilst it is fairly easy to see what is going on when you have a basic set up, I would love a proper tutorial that takes you from doing things in a simple but 'it works' method all the way up to the more complex things you can do, adding in new ways of doing things. The more advanced make files look like a minefield of mess.

---

### Post by Milliways on 2011-02-09
> **thecoshman said:**
> Ok wow!

Thanks guys.

I have been playing with some simple compiling with files from sub-directories and the like. I also made it put the '.o' files into a separate folder from the source, so that it was all 'neat' and out of the way.

I say a guide in which one of the targets was called "clean" and it basically removed all of the object files. But how can I get make to actually do this?

I've got to say, that whilst it is fairly easy to see what is going on when you have a basic set up, I would love a proper tutorial that takes you from doing things in a simple but 'it works' method all the way up to the more complex things you can do, adding in new ways of doing things. The more advanced make files look like a minefield of mess.

To answer some of your earlier questions there is a GNU Make Manual.
One other respondent gave a good summary.

Below is a simple sample of a Makefile (c with gtk+), which includes a clean target.

I won't buy into the argument of which IDE or tool is the best.
I was commenting on my experience of moving from VS, and to help you get started.

Of course I learn programming before VS, when you had to use make to compile anything.
We thought it was quite cool 30 years ago.

I still think it is worthwhile to understand how the command line works, and the basics of a makefile.

Most GNU/Linux code uses automake, but that is another level of complexity.


[PHP]CC     = gcc
CFLAGS = `pkg-config --cflags gtk+-2.0 gmodule-2.0`
LIBS   = `pkg-config --libs   gtk+-2.0 gthread-2.0 gmodule-2.0`
#DEBUG  = -Wall -g -export-dynamic
DEBUG  = -Wall -g
CPPFLAGS = -DPACKAGE_DATA_DIR=\""/usr/local/share"\"
#LDFLAGS = -Wl,--export-dynamic
LDFLAGS = -Wl

TARGET = gtree
OBJECTS = $(TARGET).o gtree_store.o gtree_disk.o gtree_view.o gtree_key.o gtree_tag.o gtree_cmd.o gtree_display.o gtree_copy.o

all: $(TARGET)

$(TARGET): $(OBJECTS)
	$(CC) $(LDFLAGS) $(LIBS) $(OBJECTS) -o $@

# compile
$(OBJECTS): %.o: %.c gtree.h
	$(CC) $(DEBUG) $(CFLAGS) $(CPPFLAGS) -c $< -o $@

.PHONY: clean

# clean all "built" files
clean :
	rm -f *.o $(TARGET)
[/PHP]

---

### Post by kev17 on 2011-02-13
> **johnl said:**
> The basics of a makefile are rather simple.  You tell make:

1. what you want to make
2. what you need to make it
3. how to make it.

in the format:

```

what_to_make: needed objects to_make it     # you can write comments
    rule to make it                         # after hash signs

```e.g.

```

my_program:  main.c
    gcc main.c -o my_program

```Save this as a file named 'makefile' (or Makefile, if you're into capitalisation) in your project directory.  Now when you can type 'make' or 'make my_program' to build your program.


of course this will soon get very repetetive and verbose -- luckily make is way smarter than this, and has nifty features like macros, generic rules, and other cool things.

For example you could shorten the above:

```

my_program:  main.c
[B]    gcc $< -o $@    # $< expands to the prerequisite file (main.c)
                    # $@ expands to the target file (my_program)[/B]

```These shortcuts are super useful because they mean you are not re-typing the same file names over and over again.  Unfortunately you can't use **$<** with a list of prerequisites, because it expands to just one.


Of course usually your makefile is more than one rule.  For example above I am compiling the sources directly to the executable.  If we have a large program we will want to compile objects first, then link so that if we change a single source every single .c file doesn't need to be recompiled.

So we might have a makefile like this:

```

# link all the .o (object files) to create our program
my_program:  main.o util.o gui.o
    gcc main.o util.o gui.o -o $@

# how to make main.o
main.o: main.c
   gcc -c $< -o $@

# how to make util.o
util.o: util.c
   gcc -c $< -o $@


# how to make gui.o
gui.o: gui.c
   gcc -c $< -o $@

```Of course this is needlessly repetitive.   The rule to make all the .o files from the .c files is the same, so why not combine them? We'll just tell gcc how to make a .o from a .c and list the .o files we need.

```

# link all the .o (object files) to create our program
my_program:  main.o util.o gui.o
    gcc main.o util.o gui.o -o $@

[B]# generic rule on how to make a .o file from a .c file 
# (this is called a suffix rule)
.c.o:
    gcc -c $< -o $@ [/B]

```Of course we can also use variable names to make things cleaner, and no longer have to list each object file in the rule and prerequisites individually:

```

[B]CC     = gcc
TARGET = my_program
OBJS   = main.o util.o gui.o

$(TARGET): $(OBJS)
    $(CC) $(OBJS)[/B] -o $@

.c.o:
    $(CC) -c $< -o $@ 

```What if we need to link with some other library? Or we want to pass flags to gcc? Why not add variables for that?

```

CC      = gcc
**CFLAGS  = -Wall -O2 # flags for gcc**
**LDFLAGS = -lcurses # link with the ncurses library**

TARGET  = my_program
OBJS    = main.o util.o gui.o

$(TARGET): $(OBJS)
    $(CC) **$(LDFLAGS)** $(OBJS) -o $@

.c.o:
    $(CC) -c **$(CFLAGS)** $< -o $@ 

```
You can even use pattern substitution to build the object files dynamically from a list of source files:

```

CC      = gcc
CFLAGS  = -Wall -O2 # flags for gcc
LDFLAGS = -lcurses # link with the ncurses library

TARGET  = my_program
[B]
SRCS    = main.c util.c gui.c
OBJS    = $(SRCS.c=.o) # foreach source, replace .c with .o[/B]

$(TARGET): $(OBJS)
    $(CC) $(LDFLAGS) $(OBJS) -o $@

.c.o:
    $(CC) -c $(CFLAGS) $< -o $@ 

```Hope this helps.


I found the above helpful. Thanks a lot.:):D=D>

---

### Post by DuneSoldier on 2011-02-14
If you have any interest in learning automake, autoconf, etc. I recommend this book:

[http://www.amazon.com/Autotools-Practioners-Autoconf-Automake-Libtool/dp/1593272065/ref=sr_1_1?ie=UTF8&qid=1297718056&sr=8-1](http://www.amazon.com/Autotools-Practioners-Autoconf-Automake-Libtool/dp/1593272065/ref=sr_1_1?ie=UTF8&qid=1297718056&sr=8-1)

It got me up to the level where I can set up a new project quick and easy using automake and autoconf.

---

