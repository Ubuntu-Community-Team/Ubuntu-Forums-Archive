---
title: "Makefile"
date: 2009-04-20
forum: Programming Talk
---

### Post by swappo1 on 2009-04-20
Hello,

I am working on creating a pong game and I will be using a Makefile.  This is the first time I will be using a Makefile and I am not sure if what I have is correct.  I got this from a game whose code I was studying and modified it for my needs.  I only have one file for now(main.cpp) and am using the SDL library.  I compiled it by typing $make(returned no errors) but now I am not sure how to run the program.  I tried $./main.cpp but got permission denied.  If this Makefile is correct, how do I run the file after compiling?
```
CC = g++
CFLAGS = -O2 -Wall -Werror -ansi
LDLIBS = -lSDL_image -lpthread
INCLUDE = .
PROG = Pongclone
NAME = Pongclone
SRCS = main.cpp		
OBJS = main.o

$(PROG): $(OBJS)
		$(CC) -o $(PROG) $(OBJS) $(LDLIBS)
		mv $(PROG) ..

# How to make the object files:

-include deps.mak

deps:
		$(CC) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		rm -f $(OBJS) ../$(PROG)


```

---

### Post by Arndt on 2009-04-20
> **swappo1 said:**
> Hello,

I am working on creating a pong game and I will be using a Makefile.  This is the first time I will be using a Makefile and I am not sure if what I have is correct.  I got this from a game whose code I was studying and modified it for my needs.  I only have one file for now(main.cpp) and am using the SDL library.  I compiled it by typing $make(returned no errors) but now I am not sure how to run the program.  I tried $./main.cpp but got permission denied.  If this Makefile is correct, how do I run the file after compiling?
```
CC = g++
CFLAGS = -O2 -Wall -Werror -ansi
LDLIBS = -lSDL_image -lpthread
INCLUDE = .
PROG = Pongclone
NAME = Pongclone
SRCS = main.cpp		
OBJS = main.o

$(PROG): $(OBJS)
		$(CC) -o $(PROG) $(OBJS) $(LDLIBS)
		mv $(PROG) ..

# How to make the object files:

-include deps.mak

deps:
		$(CC) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		rm -f $(OBJS) ../$(PROG)


```

It looks like the default target (the first one) produces the program "Pongclone". So, to run it, do ./Pongclone

(The variable "NAME" doesn't seem to be used, by the way.)

When you ran "make", it showed what it did, step by step, and the last step should have been the linking step. It's a good idea to look at those commands carefully and learn what they do. Writing larger makefiles becomes much easier if you have a clear idea what commands you want to be executed (although such detailed knowledge isn't needed all the time - that's part of the point with makefile rules).

For example, if you wonder how it gets from .cpp to .o, that's a builtin rule in 'make', and doesn't need to be specified in your makefile, while the final linking so often needs particular linking options that a default rule makes less sense.

---

### Post by dwhitney67 on 2009-04-20
A couple of other notes concerning Makefiles.  CC and CXX are built-in definitions for 'gcc' and 'g++', respectively.  There is no need to define these, unless you require a different compiler (e.g. a cross-compiler for another platform).  If you are compiling C++ files, use the CXX.

Corresponding to the CC and CXX are CFLAGS and CXXFLAGS.

In the Makefile posted by the OP, CC is redefined to 'g++', thus the CFLAGS will not be used when the source file is compiled.  This is probably not what the OP wants.

@ the OP... try the following for your Makefile:
```

CXXFLAGS = -O2 -Wall -Werror -ansi
LDLIBS   = -lSDL_image -lpthread
INCLUDE  = .
PROG     = Pongclone
SRCS     = main.cpp		
OBJS     = $(SRCS:.cpp=.o)

...

```

---

### Post by swappo1 on 2009-04-20
I tried ./Pongclone but it didn't work while in the directory that contains the files.  If I type ./Pongclone in my home directory the program starts but throws a built in exception.  It is not able to load the background image.  If I run main.cpp in its directory using g++ -o main main.cpp -lSDL_image, it runs fine.  So how can I run this from the directory that contains the files and get it to load the background image?  I did change CFLAGS to CXXFLAGS.  Thanks.

---

### Post by dwhitney67 on 2009-04-20
> **swappo1 said:**
> ...
So how can I run this from the directory that contains the files and get it to load the background image?
...
Don't move your program (binary file) up one directory.  In essence, take a look at the 'mv' command and the 'rm' commands in your Makefile.

If you do not have a need to move the binary, then don't; just yank the 'mv' statement out of the Makefile.  When removing the binary, you do not need to look up one folder; it should be in the PWD.

```

...

$(PROG): $(OBJS)
		$(CXX) -o $(PROG) $(OBJS) $(LDLIBS)

# How to make the object files:

-include deps.mak

deps:
		$(CXX) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		$(RM) $(OBJS) $(PROG)

```

---

### Post by swappo1 on 2009-04-20
I just found that putting the background image in /home, the program will run as it should in the home directory.  Where in the Makefile would I put the path to the directory for the files?  For now, I want to run this from its own directory.  Just a thought, If I were to have multiple Makefiles for multiple programs, wouldn't I need to put each of these in separate directories?  How would the compiler know which Makefile to use if there were more than one in a directory?  Thanks.

---

### Post by swappo1 on 2009-04-20
Okay, it runs from its directory now.  Thanks.
```
CXXFLAGS = -O2 -Wall -Werror -ansi
LDLIBS = -lSDL_image -lpthread
INCLUDE = .
PROG = Pongclone
NAME = Pongclone
SRCS = main.cpp		
OBJS = main.o

$(PROG): $(OBJS)
		$(CXX) -o $(PROG) $(OBJS) $(LDLIBS)
		
# How to make the object files:

-include deps.mak

deps:
		$(CXX) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		$(RM) $(OBJS) $(PROG)


```

---

### Post by dwhitney67 on 2009-04-20
> **swappo1 said:**
> I just found that putting the background image in /home, the program will run as it should in the home directory.  Where in the Makefile would I put the path to the directory for the files?  For now, I want to run this from its own directory.  Just a thought, If I were to have multiple Makefiles for multiple programs, wouldn't I need to put each of these in separate directories?  How would the compiler know which Makefile to use if there were more than one in a directory?  Thanks.

Read my last post.... which now it appears you have.

---

### Post by Arndt on 2009-04-20
> **dwhitney67 said:**
> Don't move your program (binary file) up one directory.  In essence, take a look at the 'mv' command and the 'rm' commands in your Makefile.

If you do not have a need to move the binary, then don't; just yank the 'mv' statement out of the Makefile.  When removing the binary, you do not need to look up one folder; it should be in the PWD.



Oops, I missed the "mv" when I replied.

There may arise a need to package the program and associated files into something that can be sent somewhere else. Then add a new target "distrib" or something, which copies (not moves) the files to some convenient place. Another common target is "install", which typically copies the program to /usr/bin and does other things that may be needed.

---

### Post by dwhitney67 on 2009-04-20
> **Arndt said:**
> Oops, I missed the "mv" when I replied.

There may arise a need to package the program and associated files into something that can be sent somewhere else. Then add a new target "distrib" or something, which copies (not moves) the files to some convenient place. Another common target is "install", which typically copies the program to /usr/bin and does other things that may be needed.
+1.

And the proper command to use is '/usr/bin/install', not '/bin/cp'.

---

