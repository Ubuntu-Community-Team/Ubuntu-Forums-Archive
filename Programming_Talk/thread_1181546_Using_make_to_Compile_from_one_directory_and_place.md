---
title: "Using make to Compile from one directory and place Object files in another directory"
date: 2009-06-08
forum: Programming Talk
---

### Post by austinium on 2009-06-08
Hi,

I am teaching myself to write makefiles, its been fun so far :)

I am trying to write a makefile(stored in Makefile directory) which will compile source files from Source directory, and place the object files and executables in Objects directory. There is just a single C file for now, i intend to use this setup as i go along doing (hopefully) more serious stuff.

So the directory structure is MyPrj which contains Makefile, Source and Objects.

this is the makefile iam trying to get to work , but it isn't :(

```

CC=gcc

SOURCE_DIR=..\Source
OUTPUT_DIR=..\Objects
.c.o:
        $(CC) $(SOURCE_DIR)\$*.c /Fo$(OUTPUT_DIR)\$*.obj
MyTest: $(OUTPUT_DIR)\*.o
        ld -o $(OUTPUT_DIR)\MyTest $(OUTPUT_DIR)\*.o -lc


```

This gives me the follwing error:
```

make: *** No rule to make target `..\Objects\*.o', needed by `MyTest'.  Stop.

```

shouldn't the prefix rule .c.obj: compile all c files to object files?

iam new to this, help!

thanks

---

### Post by leblancmeneses on 2009-06-08
I'm putting my .o in a bin/ directory

```

%.o: %.c
    @mkdir -p bin
    $(CC) $(CFLAGS) $< ${STATIC_LIBRARIES} -o bin/$@

```

by the way this is the rule for compiling a crap load of executables (unit tests).. if you plan to link your .o files you need to add -c switch.

---

### Post by dwhitney67 on 2009-06-08
I cannot comprehend why you would place the Makefile in its own directory; typically it would reside within the directory containing the Sources directory or within Sources directory itself.

Consider the following directory structure:
```

workspace/
           Project1/
                     Makefile
                     Sources/
                              Sources1/
                                        HelloWorld.c
                              Sources2/
                                        Main.c
                     Objects/
                              Sources1/
                                        HelloWorld.o
                              Sources2/
                                        Main.o

           Project2/
                     ...

```
In the example above, the workspace contains two projects, each of which has a Makefile and a Source and Object directories.  The Source directory contains individual directories itself for related source code files.  This is not always necessary; it depends on the complexity of the project.

Anyhow, any object file(s) that are created are placed into separate directories within Objects.  There is no benefit to this, other than it keeps everything organized.

I did not have too much time to play around with the puzzle that you presented, but I came up with the following Makefile that assumes something similar to the above.  Actually, it assumes that there is a sole source file in Sources.

Here's the Makefile, which I'm sure could be improved...
```

APP     = Hello

SRCDIR  = Sources
OBJDIR  = Objects

SRCS    := $(shell find $(SRCDIR) -name '*.c')
SRCDIRS := $(shell find . -name '*.c' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))

CFLAGS  = -Wall -pedantic -ansi
LDFLAGS =


all: $(APP)

$(APP) : buildrepo $(OBJS)
	$(CC) $(OBJS) $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	$(RM) $(OBJS)

distclean: clean
	$(RM) $(APP)

buildrepo:
	@$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
	mkdir -p $(OBJDIR)/$$dir; \
   done
endef

```

P.S.  I've also attached a tar-ball in case you want the full work area.

---

### Post by Nubilous on 2011-07-21
Not to reopen an old thread, but I found this thread via Google in search for a Makefile sample, and the one given by dwhitney is quite a nice solution, but doesn't work (for me at least) without a few fixes:

```
# Compiler
CC = g++
OPTS = -c -Wall

# Project name
PROJECT = application_name

# Directories
OBJDIR = obj
SRCDIR = src

# Libraries
LIBS = 

# Files and folders
SRCS    = $(shell find $(SRCDIR) -name '*.cpp')
SRCDIRS = $(shell find . -name '*.cpp' | dirname {} | sort | uniq | sed 's/\/$(SRCDIR)//g' )
OBJS    = $(patsubst $(SRCDIR)/%.cpp,$(OBJDIR)/%.o,$(SRCS))

# Targets
$(PROJECT): buildrepo $(OBJS)
	$(CC) $(OBJS) $(LIBS) -o $@

$(OBJDIR)/%.o: $(SRCDIR)/%.cpp
	$(CC) $(OPTS) -c $< -o $@
	
clean:
	rm $(PROJECT) $(OBJDIR) -Rf
	
buildrepo:
	@$(call make-repo)

# Create obj directory structure
define make-repo
	mkdir -p $(OBJDIR)
	for dir in $(SRCDIRS); \
	do \
		mkdir -p $(OBJDIR)/$$dir; \
	done
endef
```

This worked pretty well for me, but I'm by no means an expert on makefiles or shell scripting, so additions are welcome of course :)

---

### Post by strongdrink on 2011-10-23
Here is a little Edit I made.... the SRCDIRS did not work if there were more than one directory... sooooo...

```
SRCDIRS = $(shell find $(SRCDIR) -type d | sed 's/$(SRCDIR)/./g' )
```

---

