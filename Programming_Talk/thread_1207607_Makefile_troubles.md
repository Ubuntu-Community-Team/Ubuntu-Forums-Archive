---
title: "Makefile troubles"
date: 2009-07-08
forum: Programming Talk
---

### Post by swappo1 on 2009-07-08
Hello,

When I make changes to a header file, save and run make, it is saying that the file is already updated.  Yet when I run the program it uses the header file prior to making changes.  It seems that it doesn't know that changes have been made to a header file.  I don't have this problem with .cpp files.  I have already wasted alot of time debugging because I didn't realize this was happening.  How do set up my Makefile so when I make changes to a header file it will see that it needs to recompile?  Here is my Makefile.
```
CXXFLAGS = -O2 -Wall -Werror -ansi
LDLIBS = -lpthread
INCLUDE = .
PROG = find
NAME = find
SRCS = main.cpp find.cpp
OBJS = main.o find.cpp

$(PROG): $(OBJS)
		$(CXX) -o $(PROG) $(OBJS) $(LDLIBS)
		#mv $(PROG) ..

# How to make the object files:

-include deps.mak

deps:
		$(CXX) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		$(RM) $(OBJS) $(PROG)


```

---

### Post by dwhitney67 on 2009-07-08
I strongly recommend that you not name your application "find", since that name has already been taken for another well-known app.

As for the Makefile, yours has a mistake or two.  Here's a corrected Makefile:
```

PROG     = myfind

SRCS     = main.cpp find.cpp

OBJS     = $(SRCS:.cpp=.o)
INCLUDE  = -I./
CXXFLAGS = -O2 -Wall -Werror -ansi -c $(INCLUDE)
LDLIBS   = -lpthread
DEPS     = deps.mak

.PHONY: all clean

all: $(DEPS) $(PROG)

$(PROG): $(OBJS)
        $(CXX) -o $@ $(OBJS) $(LDLIBS)

.cpp.o:
        $(CXX) $(CXXFLAGS) $<

$(DEPS):
        $(CXX) -MM $(CXXFLAGS) $(SRCS) > $@

clean:
        $(RM) $(OBJS) $(PROG) $(DEPS)

ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif

```

---

### Post by fr4nko on 2009-07-08
> **swappo1 said:**
> How do set up my Makefile so when I make changes to a header file it will see that it needs to recompile?
In order to let makefile update the target when an header file changes you have to instruct it by giving, for each object file (extension .o), the list of header files it depends on. If you want to maintain this kind of informations manually it can be painful, A better solution is to let gcc make the work for you. I use this kind of code in my makefile to let gcc generate the dependencies from header files automatically:
```

COMPILE = $(CC) $(CFLAGS) $(DEFS) $(INCLUDES)

DISP_OBJ_FILES := $(MY_SRC_FILES:%.c=%.o)
DEP_FILES := $(DISP_SRC_FILES:%.c=.deps/%.P)

DEPS_MAGIC := $(shell mkdir .deps > /dev/null 2>&1 || :)

%.o: %.c
    @echo '$(COMPILE) -c $<'; \
    $(COMPILE) -Wp,-MMD,.deps/$(*F).pp -c $<
    @-cp .deps/$(*F).pp .deps/$(*F).P; \
    tr ' ' '\012' < .deps/$(*F).pp \
          | sed -e 's/^\\$$//' -e '/^$$/ d' -e '/:$$/ d' -e 's/$$/ :/' \
            >> .deps/$(*F).P; \
    rm .deps/$(*F).pp

# the following line goes at the end of file
-include $(DEP_FILES)

```this code gives the rule to create object files (.o) from source file (.c) and it generates automatically the dependencies informations every time you build the target. The dependencies are generated in the .deps directory and they are included in the Makefile with the last line.

Of course you can define the $(COMPILE) differently if you want. In this case it is defined by using the CC, CFLAGS, DEFS and INCLUDES variables.

Note also that you should define MY_SRC_FILES with the list of source files of your project.

Francesco

---

### Post by dwhitney67 on 2009-07-08
Jeez, that statement to get the dependencies seems ridiculously complex.  There are easier ways to do it.

For example, what the OP presented works, and is probably the easiest form.  Of course, his way would hit a snag if he chose to put his object files in a different directory other than where the source file(s) live.

Another way is like this as shown in this Makefile:
```

APP      = myapp

OBJDIR   = objs

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

INCLUDES = -I./Include
CXXFLAGS = -Wall -pedantic -ansi -c $(INCLUDES)
LDFLAGS  =

.PHONY: all clean distclean

all: buildrepo $(APP)

$(APP) : $(OBJS)
        @echo "Building $@..."
        @$(CXX) $(OBJS) $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.cpp
        @echo "Generating dependencies for $<..."
        @$(call make-depend,$<,$@,$(subst .o,.d,$@))
        @echo "Compiling $<..."
        @$(CXX) $(CXXFLAGS) $< -o $@

clean:
        $(RM) -r $(OBJDIR)

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


# usage: $(call make-depend,source-file,object-file,depend-file)
define make-depend
  $(CXX) -MM -MF $3 -MP -MT $2 $(CXXFLAGS) $1
endef

ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif

```

---

### Post by fr4nko on 2009-07-08
> **dwhitney67 said:**
> Jeez, that statement to get the dependencies seems ridiculously complex.  There are easier ways to do it.

Thank you very much for the 'ridicoulous', I was just trying to be helpful and my method works perfectly.

In any case, I've to admit that you are true, there are easier ways to do the job.

In the glib library they are using something like that:
```

.c.o:
    $(COMPILE) -MT $@ -MD -MP -MF $(DEPDIR)/$*.Tpo -c -o $@ $<
    mv -f $(DEPDIR)/$*.Tpo $(DEPDIR)/$*.Po
```
which look even simpler than your example.

Francesco

---

### Post by swappo1 on 2009-07-08
dwhitney67, I get the following error and I am not sure what the problem is.
> Makefile:16: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.

```
PROG     = myfind

SRCS     = main.cpp find.cpp

OBJS     = $(SRCS:.cpp=.o)
INCLUDE  = -I./
CXXFLAGS = -O2 -Wall -Werror -ansi -c $(INCLUDE)
LDLIBS   = -lpthread
DEPS     = deps.mak

.PHONY: all clean

all: $(DEPS) $(PROG)

$(PROG): $(OBJS)
        $(CXX) -o $@ $(OBJS) $(LDLIBS) [COLOR="Red"]line 16[/COLOR]

.cpp.o:
        $(CXX) $(CXXFLAGS) $<

$(DEPS):
        $(CXX) -MM $(CXXFLAGS) $(SRCS) > $@

clean:
        $(RM) $(OBJS) $(PROG) $(DEPS)

ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
```

---

### Post by dwhitney67 on 2009-07-08
At the line you indicated, you need to preface the statement with a tab-space, not 8-spaces.

You may encounter similar errors on other lines.  Just fix them the same.

---

### Post by fr4nko on 2009-07-16
> **dwhitney67 said:**
> 
```

%.o: %.c
    @echo '$(COMPILE) -c $<'; \
    $(COMPILE) -Wp,-MMD,.deps/$(*F).pp -c $<
    @-cp .deps/$(*F).pp .deps/$(*F).P; \
    tr ' ' '\012' < .deps/$(*F).pp \
          | sed -e 's/^\\$$//' -e '/^$$/ d' -e '/:$$/ d' -e 's/$$/ :/' \
            >> .deps/$(*F).P; \
    rm .deps/$(*F).pp

```Jeez, that statement to get the dependencies seems ridiculously complex.  There are easier ways to do it.

I've come back to this question and I've found that actually the sed instructions are important to remove from the dependency files the reference to system wide header files, like <math.h> or <stdio.h>. This is logical because these files are not supposed to change because of your activity in the local folder and keeps the dependencies clean.

Francesco

---

### Post by dwhitney67 on 2009-07-17
The sed is not necessary; it is (highly) probable that you are passing the incorrect gcc (or g++) options.

Here's the output of my dependency file (for a very simple application):
```

.srcobjs/./main.o: main.cpp Include/FunctionOne.h Include/FunctionTwo.h

Include/FunctionOne.h:

Include/FunctionTwo.h:

```

I call this function in my Makefile:
```

# usage: $(call make-depend,SourceFile,ObjectFile, DependFile)
define make-depend
  $(CXX) -MM -MF $3 -MP -MT $2 $(CXXFLAGS) $1
endef

```
See the comment above for the API to this function.
$1 = SourceFile
$2 = ObjectFile
$3 = DependFile

I lifted the statement above from a Makefile tutorial, for which unfortunately I do not have a bookmark for anymore.

In the days when I would develop applications where I placed my generated object file(s) and dependency file in the same directory as the source code, I would use this dependency statement(s):
```

# For determining source file dependencies
#
depend: $(DEP_FILE)
        @touch $(DEP_FILE)

$(DEP_FILE):
        @echo Generating dependencies in $@
        @-$(CXX) -E -MM $(CXXFLAGS) $(INCPATH) $(CPP_SRCS) >> $(DEP_FILE)

```

---

### Post by fr4nko on 2009-07-17
> **dwhitney67 said:**
> In the days when I would develop applications where I placed my generated object file(s) and dependency file in the same directory as the source code, I would use this dependency statement(s):
```

# For determining source file dependencies
#
depend: $(DEP_FILE)
        @touch $(DEP_FILE)

$(DEP_FILE):
        @echo Generating dependencies in $@
        @-$(CXX) -E -MM $(CXXFLAGS) $(INCPATH) $(CPP_SRCS) >> $(DEP_FILE)

```
May be I will try your method even if my own works perfectly, its only problem is that the tr/sed instructions are a little bit complicated and ugly. I was just wondering if your method can be used to generate dependencies as a side-effects when compiling the code instead of doing an explicit 'make depend'. My code generates the depencies automatically at each compilation and I think this is very convenient.

Francesco

---

### Post by dwhitney67 on 2009-07-17
My style works very well, however you are correct in assessing that it takes me two-steps to generate a file's dependency and then compile the file.

Btw, earlier I was stating that perhaps you have an incorrect gcc option.  I noticed you used -MMD, which I am not familiar with.  The -MM (which is what I use) stipulates that no system include files will be listed as a dependency.  Subsequently, if you want to pass the generated dependencies to a particular file, then -MF can be used.  In my previous post, I merely redirected the standard-output to a file.

---

