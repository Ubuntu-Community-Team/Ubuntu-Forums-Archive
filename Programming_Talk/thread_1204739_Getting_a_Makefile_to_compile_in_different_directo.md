---
title: "Getting a Makefile to compile in different directories, can't find build rule"
date: 2009-07-05
forum: Programming Talk
---

### Post by jimmio on 2009-07-05
Hello all,
I wrote a little Makefile for something I've been doing with bash scripts, building, and I can't for the life of me get it to work. I've looked at multiple directory examples, and it doesn't help at all.

```
Sources=main.cpp GUI.cpp
Executable=TwistedGameEngine

CFlags=-c -Wall -g -Iinc
LDFlags=
ObjectDir=obj/
SourceDir=src/
BinDir=bin/

CC=g++
RM=rm

#!!!!!DO NOT EDIT ANYTHING UNDER THIS LINE!!!!!
Objects=$(Sources:.cpp=.o)
CSources=$(addprefix $(SourceDir),$(Sources))
CObjects=$(addprefix $(ObjectDir),$(Objects))
CExecutable=$(addprefix $(BinDir),$(Executable))


$(CExecutable): $(CObjects)
	$(CC) $(LDFlags) $(CObjects) -o $@

%.o: %.cpp
	$(CC) $(CFlags) $< -o $@

clean:
	$(RM) $(CExecutable) $(CObjects)
```

Any input would be great.

Thanks,
Jim

---

### Post by jimmio on 2009-07-05
Sorry for double posting, but I've solved it.

Below is a Makefile that should work for just about every project I ever do :D
```

Sources=main.cpp GUI.cpp
Executable=TwistedGameEngine

CFlags=-c -Wall -g -Iinc
LDFlags=
ObjectDir=obj/
SourceDir=src/
BinDir=bin/

CC=g++
RM=rm

#!!!!!DO NOT EDIT ANYTHING UNDER THIS LINE!!!!!
Objects=$(Sources:.cpp=.o)
CSources=$(addprefix $(SourceDir),$(Sources))
CObjects=$(addprefix $(ObjectDir),$(Objects))
CExecutable=$(addprefix $(BinDir),$(Executable))

all: $(CSources) $(CExecutable)

$(CExecutable): $(CObjects)
	$(CC) $(LDFlags) $(CObjects) -o $@

$(ObjectDir)%.o: $(SourceDir)%.cpp
	$(CC) $(CFlags) $< -o $@

clean:
	$(RM) $(CObjects)
```

Makefiles rule! =D

-Jim

---

### Post by dwhitney67 on 2009-07-05
The only thing your Makefile is missing is the rule to determine dependencies on your source files.

For instance, if you modify a header file, it would be essential for the source file(s) that are dependent upon it to be recompiled, and then of course, your application re-linked.

Unless you have a specific requirement, there is no need to define CC and RM; these are already predefined and known to 'make'.  For C++, you should consider using CXX in lieu of CC, which is typically used for C.

Lastly, your Makefile does not create the ./bin nor the ./obj directories; it should.

I suspect you will re-evaluate your position and realize that you are not done.  :-)

Here's a Makefile that you could consider using...
```

APP      = TwistedGameEngine

SRCEXT   = cpp
SRCDIR   = src
OBJDIR   = obj
BINDIR   = bin

SRCS    := $(shell find $(SRCDIR) -name '*.$(SRCEXT)')
SRCDIRS := $(shell find . -name '*.$(SRCEXT)' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.$(SRCEXT),$(OBJDIR)/%.o,$(SRCS))

DEBUG    = -g
INCLUDES = -I./inc
CFLAGS   = -Wall -pedantic -ansi -c $(DEBUG) $(INCLUDES)
LDFLAGS  =

ifeq ($(SRCEXT), cpp)
CC       = $(CXX)
else
CFLAGS  += -std=gnu99
endif

.PHONY: all clean distclean


all: $(BINDIR)/$(APP)

$(BINDIR)/$(APP): buildrepo $(OBJS)
	@mkdir -p `dirname $@`
	@echo "Linking $@..."
	@$(CC) $(OBJS) $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.$(SRCEXT)
	@echo "Generating dependencies for $<..."
	@$(call make-depend,$<,$@,$(subst .o,.d,$@))
	@echo "Compiling $<..."
	@$(CC) $(CFLAGS) $< -o $@

clean:
	$(RM) -r $(OBJDIR)

distclean: clean
	$(RM) -r $(BINDIR)

buildrepo:
	@$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
	mkdir -p $(OBJDIR)/$$dir; \
   done
endef


# usage: $(call make-depend,source-file,object-file,depend-file)
define make-depend
  $(CC) -MM       \
        -MF $3    \
        -MP       \
        -MT $2    \
        $(CFLAGS) \
        $1
endef

```
I believe it fulfills your requirements; post back if it does not.

---

### Post by jimmio on 2009-08-17
Hello all,
I realize it's been over a month now, but I just thought I should post back stating what's been going on with this.

> **dwhitney67 said:**
> The only thing your Makefile is missing is the rule to determine dependencies on your source files.

For instance, if you modify a header file, it would be essential for the source file(s) that are dependent upon it to be recompiled, and then of course, your application re-linked.

Unless you have a specific requirement, there is no need to define CC and RM; these are already predefined and known to 'make'.  For C++, you should consider using CXX in lieu of CC, which is typically used for C.

Lastly, your Makefile does not create the ./bin nor the ./obj directories; it should.

I suspect you will re-evaluate your position and realize that you are not done.  :-)

Here's a Makefile that you could consider using...
...
I believe it fulfills your requirements; post back if it does not.

@dwhitney67:
Thank you soo much for that. It works perfectly, other than it rebuilding every time make is called and it deleting the bin directory when you call "make distclean" (I changed that as I have data in the bin directory that mustn't be deleted).

Below is my current Makefile which I use in many places now. As you can see, the current project is a Pong remake xP

```
app = Pong

srcExt = cpp
srcDir = src
objDir = obj
binDir = bin
inc = inc

debug = 1

CFlags = -Wall
LDFlags =
libs =
libDir =


#************************ DO NOT EDIT BELOW THIS LINE! ************************

ifeq ($(debug),1)
	debug=-g
else
	debug=
endif
inc := $(addprefix -I,$(inc))
libs := $(addprefix -l,$(libs))
libDir := $(addprefix -L,$(libDir))
CFlags += -c $(debug) $(inc) $(libDir) $(libs)
sources := $(shell find $(srcDir) -name '*.$(srcExt)')
srcDirs := $(shell find . -name '*.$(srcExt)' -exec dirname {} \; | uniq)
objects := $(patsubst %.$(srcExt),$(objDir)/%.o,$(sources))

ifeq ($(srcExt),cpp)
	CC = $(CXX)
else
	CFlags += -std=gnu99
endif

.phony: all clean distclean


all: $(binDir)/$(app)

$(binDir)/$(app): buildrepo $(objects)
	@mkdir -p `dirname $@`
	@echo "Linking $@..."
	@$(CC) $(objects) $(LDFlags) -o $@

$(objDir)/%.o: %.$(srcExt)
	@echo "Generating dependencies for $<..."
	@$(call make-depend,$<,$@,$(subst .o,.d,$@))
	@echo "Compiling $<..."
	@$(CC) $(CFlags) $< -o $@

clean:
	$(RM) -r $(objDir)

distclean: clean
	$(RM) -r $(binDir)/$(app)

buildrepo:
	@$(call make-repo)

define make-repo
   for dir in $(srcDirs); \
   do \
	mkdir -p $(objDir)/$$dir; \
   done
endef


# usage: $(call make-depend,source-file,object-file,depend-file)
define make-depend
  $(CC) -MM       \
        -MF $3    \
        -MP       \
        -MT $2    \
        $(CFlags) \
        $1
endef
```

---

