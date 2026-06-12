---
title: "Evil makefile removed important files, how the get the files back?"
date: 2009-03-09
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-03-09
I got this makefile:
```

SRCS          = main.cpp graphics.c collisions.c list.c init.c misc.c room.cpp units.cpp game.cpp
APPNAME   = output

CFLAGS    = -g -Wall -pedantic -ffast-math `sdl-config --cflags`
LFLAGS     = `sdl-config --libs` -lSDL -lSDL_image -lSDL_ttf -lSDL_mixer -lGL -lGLU -lpython2.5 -lm
LPATH      = -L/usr/lib/python2.5/config

CC = g++

# No changes below this line are required!

OBJS         = $(SRCS:.c=.o)
DEP_FILE  = .depend

.PHONY: all clean distclean


all: depend $(APPNAME)

$(APPNAME): $(OBJS)
	@echo Makefile - linking $@
	@$(CC) $^ $(LPATH) $(LFLAGS) -o $@

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
See this console output:
```

arho@arho-laptop:~/Projects/C/stacked$ make clean
rm -f **main.cpp** graphics.o collisions.o list.o init.o misc.o **room.cpp** **units.cpp** **game.cpp**

```
It was supposed to delete ONLY .o files! Not the source code! ](*,) :evil: :cry: :-x

AAARRGGHH!!! All that work, gone. Can't find it in trash because it's completely removed. 

And if those bytes still exists in my hard disk, unchanged, how the hell can I recover them?

[s]Until somebody can tell me a program or some way to get the files back, I'll leave this computer running.[/s]

---

### Post by stumbleUpon on 2009-03-09
Well the Makefile was not evil. It did what it was told to do.

make clean would remove all the OBJ files. But the OBJ files are obtained from changing the extension of the '.c' files to '.o'. You have put '.cpp' files in SRCS.

This may be of some use. 

[http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html](http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html)

But i am doubtful if you can recover files deleted with 'rm -f'. Also see this post (it may not be of much use)

[http://ubuntuforums.org/showpost.php?p=2194002&postcount=8](http://ubuntuforums.org/showpost.php?p=2194002&postcount=8)

---

### Post by crazyfuturamanoob on 2009-03-09
All they ask me the hard drive. How can I know it?

There are files like sda, sda1, sda5, sdb1, and so on in /dev. Which is the right one?

---

### Post by stumbleUpon on 2009-03-09
Look at the output of

df -h

Identify the hard-disk (for e.g. by its size) where you had your file and try

grep -i -a -B10 -A100 'main.cpp' /dev/sda1 > file.txt

i am assuming above that /dev/sda1 is the hard-disk you want. If you are lucky, the contents of your lost main.cpp might get written to file.txt

good luck

---

### Post by dwhitney67 on 2009-03-09
> **crazyfuturamanoob said:**
> ...
[/code]
See this console output:
```

arho@arho-laptop:~/Projects/C/stacked$ make clean
rm -f **main.cpp** graphics.o collisions.o list.o init.o misc.o **room.cpp** **units.cpp** **game.cpp**

```
It was supposed to delete ONLY .o files! Not the source code! ](*,) :evil: :cry: :-x
...

Unfortunately I cannot offer any advice on recovering your files.  I can however offer the following Makefile which can be useful for building projects consisting of .cpp and .c files.
```

# Define the name of your executable
BIN       = testing

# Define C++ source files (if any)
CPP_SRCS  = Foo.cpp Poly.cpp Testing.cpp

# Define C source files (if any)
C_SRCS    = Function.c

# Define C++ and C compiler flags
CXXFLAGS  = -Wall -ansi -pedantic
CFLAGS    = -Wall -ansi -pedantic -D_GNU_SOURCE -std=gnu99

# Define header file paths
INCPATH   = -I./

# Define the -L library path(s)
LDFLAGS   =

# Define the -l library name(s)
LIBS      =

# Don't fiddle with these
CPP_OBJS  = $(CPP_SRCS:.cpp=.o)
C_OBJS    = $(C_SRCS:.c=.o)
DEP_FILE  = .depend


.PHONY = all clean distclean


# Main entry point
#
all: depend $(BIN)


# For linking object file(s) to produce the executable
#
$(BIN): $(C_OBJS) $(CPP_OBJS)
	@echo Linking $@
	@$(CXX) $^ $(LDFLAGS) $(LIBS) -o $@


# For compiling source file(s)
#
.cpp.o:
	@echo Compiling $<
	@$(CXX) -c $(CXXFLAGS) $(INCPATH) $<

.c.o:
	@echo Compiling $<
	@$(CC) -c $(CFLAGS) $(INCPATH) $<


# For cleaning up the project
#
clean:
	$(RM) $(CPP_OBJS) $(C_OBJS)

distclean: clean
	$(RM) $(BIN)
	$(RM) $(DEP_FILE)


# For determining source file dependencies
#
depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Generating dependencies in $@
	@-$(CXX) -E -MM $(CXXFLAGS) $(INCPATH) $(CPP_SRCS) >> $(DEP_FILE)
	@-$(CC) -E -MM $(CFLAGS) $(INCPATH) $(C_SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

Btw, always test a new Makefile before use.  Just create a test entry point to verify your Makefile's definitions (i.e. C_OBJS and CPP_OBJS).  For example:
```

testdef:
        @echo C_OBJS = $(C_OBJS)
        @echo CPP_OBJS = $(CPP_OBJS)

all: ...

```

---

### Post by MadMan2k on 2009-03-09
well use [SCons]("http://www.scons.org/") next time ;)

---

### Post by crazyfuturamanoob on 2009-03-09
I definitely need a background application which would backup the files for me.

> **stumbleUpon said:**
> Look at the output of

df -h

Identify the hard-disk (for e.g. by its size) where you had your file and try

grep -i -a -B10 -A100 'main.cpp' /dev/sda1 > file.txt

i am assuming above that /dev/sda1 is the hard-disk you want. If you are lucky, the contents of your lost main.cpp might get written to file.txt

good luck

Thanks. Any idea how long will this take? Size of that partition is 320Gb.

> **dwhitney67 said:**
> Unfortunately I cannot offer any advice on recovering your files.  I can however offer the following Makefile which can be useful for building projects consisting of .cpp and .c files.
```

# Define the name of your executable
BIN       = testing

# Define C++ source files (if any)
CPP_SRCS  = Foo.cpp Poly.cpp Testing.cpp

# Define C source files (if any)
C_SRCS    = Function.c

# Define C++ and C compiler flags
CXXFLAGS  = -Wall -ansi -pedantic
CFLAGS    = -Wall -ansi -pedantic -D_GNU_SOURCE -std=gnu99

# Define header file paths
INCPATH   = -I./

# Define the -L library path(s)
LDFLAGS   =

# Define the -l library name(s)
LIBS      =

# Don't fiddle with these
CPP_OBJS  = $(CPP_SRCS:.cpp=.o)
C_OBJS    = $(C_SRCS:.c=.o)
DEP_FILE  = .depend


.PHONY = all clean distclean


# Main entry point
#
all: depend $(BIN)


# For linking object file(s) to produce the executable
#
$(BIN): $(C_OBJS) $(CPP_OBJS)
	@echo Linking $@
	@$(CXX) $^ $(LDFLAGS) $(LIBS) -o $@


# For compiling source file(s)
#
.cpp.o:
	@echo Compiling $<
	@$(CXX) -c $(CXXFLAGS) $(INCPATH) $<

.c.o:
	@echo Compiling $<
	@$(CC) -c $(CFLAGS) $(INCPATH) $<


# For cleaning up the project
#
clean:
	$(RM) $(CPP_OBJS) $(C_OBJS)

distclean: clean
	$(RM) $(BIN)
	$(RM) $(DEP_FILE)


# For determining source file dependencies
#
depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Generating dependencies in $@
	@-$(CXX) -E -MM $(CXXFLAGS) $(INCPATH) $(CPP_SRCS) >> $(DEP_FILE)
	@-$(CC) -E -MM $(CFLAGS) $(INCPATH) $(C_SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

Btw, always test a new Makefile before use.  Just create a test entry point to verify your Makefile's definitions (i.e. C_OBJS and CPP_OBJS).  For example:
```

testdef:
        @echo C_OBJS = $(C_OBJS)
        @echo CPP_OBJS = $(CPP_OBJS)

all: ...

```

Thanks. I was just going to ask for that.

> **MadMan2k said:**
> well use [SCons]("http://www.scons.org/") next time ;)

What does scons do better than make?

---

### Post by dwhitney67 on 2009-03-09
> **crazyfuturamanoob said:**
> ...
What does scons do better than make?

I just looked at the [Scons User Guide]("http://www.scons.org/doc/1.2.0/HTML/scons-user/book1.html").  After a few minutes perusing the guide, it does seem to make everything much easier to use than a Makefile, and the SConstruct file is portable, which may be of use to many developers.  When I return home today, I will definitely give it a try.

+1 to MadMan2k for mentioning Scons.

---

### Post by crazyfuturamanoob on 2009-03-09
Blah.. tons of files called "main.cpp" in my hard disk, can't find the one I want. That grep thing finds loads of unreadable ascii mess, 

firefox bookmarks xml file, some random strings like "Copyright (c) Microsoft Corporation", but nothing of my game's source code.

This is just useless waste of time. I start coding it all over again. :???: Stupid makefile...

And grep can't find the other source files, room.cpp, units.cpp, and game.cpp.

---

### Post by wmcbrine on 2009-03-09
> **crazyfuturamanoob said:**
> I definitely need a background application which would backup the files for me.Use source control. Then, if you accidentally delete a source file, you can check it back out again. It's not automatic, but it's better, since you can record each set of changes, along with a note to explain.

Example with git:

git init
git add .
git commit

[time passes]

edit main.cpp
git commit -a

[time passes]

rm main.cpp

[oops!]

git checkout main.cpp

[all better!]

---

### Post by uljanow on 2009-03-09
Mount the partition read-only and try recovering the files with debugfs. Alternatively every good text editor should have made backups. E.g. vim options:
```
set backup
set backupdir=~/.vim/backup
```

---

### Post by crazyfuturamanoob on 2009-03-09
I can't remove the hard drive because this is a laptop.

And can't unmount or mount it as read-only, because it is the root partition. Ubuntu's system files are on it.



If I remove a file with nautilus, it goes to trash. (~/.local/share/Trash/files)

But if I remove a file with **rm**, why it doesn't go to trash?

---

### Post by wmcbrine on 2009-03-09
> **crazyfuturamanoob said:**
> I can't remove the hard drive because this is a laptop.I assure you, laptop hard drives are also removable. It may not be easy, but it can be done. :)

> *And can't unmount or mount it as read-only, because it is the root partition. Ubuntu's system files are on it.*You can either boot into single-user mode, or boot from a Live CD.

> [i]If I remove a file with nautilus, it goes to trash. (~/.local/share/Trash/files)

But if I remove a file with **rm**, why it doesn't go to trash?[/i]The Trash is a bolted-on concept, only recently imported from Mac/Windows. It only exists as part of Gnome, not part of the OS. (Although it doesn't work from the command line for Mac OS X or Windows either.) rm is much older.

---

