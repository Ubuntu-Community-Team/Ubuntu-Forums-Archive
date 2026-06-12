---
title: "is it useful to learn writing makefiles ?"
date: 2008-12-15
forum: Programming Talk
---

### Post by mkrahmeh on 2008-12-15
gurus..
i fell into a book about advanced linux programming, 'twas quite interesting to have an idea how linux command lines are being developed, however, i tried a couple of examples my self to write makefiles and thus develop small apps without using an IDE, and my question whether it is useful to acquire such skills ? i mean to work on makefiles rather than fancy IDEs, especially in the market ?

---

### Post by jimi_hendrix on 2008-12-15
delete

---

### Post by jimi_hendrix on 2008-12-15
yes...its not that hard and it saves typing...

also will show you your errors in vim if you use vim when you type :make

you dont need makefiles but i recommend them

with the fancy ideas...thats your choice...but i recommend learning make and stuff first...then use IDE's to automate it for you

---

### Post by DougB1958 on 2008-12-15
If nothing else, understanding what make does and how a makefile works is a good starting point for understanding what your IDE is doing behind the scenes, what more sophisticated build tools (e.g., ant) are about, etc. So I'd recommend learning the basics of makefiles, even if you then go on and do your "serious" programming with an IDE.

---

### Post by jimi_hendrix on 2008-12-15
besides...makefiles arnt that hard...

```

all:
     gcc -o foo foo.c bar.c

```

---

### Post by monkeyking on 2008-12-15
of cause you should use Makefiles.
the learning curve is quite non existing.

A very small example

[PHP]
C=gcc
CC=g++
FLAGS=-Wall -fPIC -ansi -pedantic

all: simple_dep

inner.o: inner.c inner.h
  ${C} -c ${FLAGS} inner.c

simple_dep: inner.o vars.cpp
  ${CC} -o ${FLAGS} mainProg vars.cpp

clean:
  rm -rf *.so mainProg
[/PHP]

If you want to recompile everything with optims then you would simply change the FLAGS and type

make clean;make

It doesn't require special skills to use do it,
it's just a simple tool, not rocket science.

---

### Post by slavik on 2008-12-15
note: makefiles is not only for compiling stuff, you can use make for other things

---

### Post by dwhitney67 on 2008-12-15
> **monkeyking said:**
> of cause you should use Makefiles.
the learning curve is quite non existing.

A very small example

[PHP]
C=gcc
CC=g++
FLAGS=-Wall -fPIC -ansi -pedantic

all: simple_dep

inner.o: inner.c inner.h
  ${C} -c ${FLAGS} inner.c

simple_dep: inner.o vars.cpp
  ${CC} -o ${FLAGS} mainProg vars.cpp

clean:
  rm -rf *.so mainProg
[/PHP]

If you want to recompile everything with optims then you would simply change the FLAGS and type

make clean;make

It doesn't require special skills to use do it,
it's just a simple tool, not rocket science.

It must be rocket science!  I cannot imagine how you would get the Makefile you posted to work.

Please, if you have a working Makefile, then copy/paste that into your post.  The one you provided is non-functional.

---

### Post by jimi_hendrix on 2008-12-15
mine works i think...

i have other working ones that are not accessable right now but i will post later

---

### Post by jimi_hendrix on 2008-12-15
i also got this from the first website i hit with "makefile tutorial" in google...

```

# This makefile compiles the project listed in the PROJ macro
#
PROJ = project			# the name of the project
OBJS = main.obj io.obj		# list of object files 
# Configuration:
#
MODEL = s			# memory model
CC = bcc			# name of compiler 
# Compiler-dependent section
#
%if $(CC) == bcc		# if compiler is bcc
  CFLAGS = &#8211;m$(MODEL)		# $(CFLAGS) is &#8211;ms
  LDSTART = c0$(MODEL)		# the start-up object file
  LDLIBS = c$(MODEL)		# the library
  LDFLAGS = /Lf:\bc\lib		# f:\bc\lib is library directory
%elif $(CC) == cl		# else if compiler is cl
  CFLAGS = &#8211;A$(MODEL,UC)	# $(CFLAGS) is &#8211;AS
  LDSTART =			# no special start-up
  LDLIBS =			# no special library
  LDFLAGS = /Lf:\c6\lib;	# f:\c6\lib is library directory
%else				# else
% abort Unsupported CC==$(CC)	# compiler is not supported
%endif				# endif 
# The project to be built
#
$(PROJ).exe : $(OBJS)
	tlink $(LDSTART) $(OBJS), $(.TARGET),, $(LDLIBS) $(LDFLAGS) 
$(OBJS) : incl.h 

```

---

### Post by jimi_hendrix on 2008-12-15
it was the last example on the page...so probably the most complex but there you go

---

### Post by monkeyking on 2008-12-15
> **dwhitney67 said:**
> It must be rocket science!  I cannot imagine how you would get the Makefile you posted to work.

Please, if you have a working Makefile, then copy/paste that into your post.  The one you provided is non-functional.

[PHP]C=gcc
CC=g++
FLAGS=-Wall -fPIC -ansi -pedantic

all: simple_dep

inner.o: inner.c inner.h
  ${C} -c ${FLAGS} inner.c

simple_dep: inner.o vars.cpp
  ${CC} -o mainProg ${FLAGS} vars.cpp

clean:
  rm -rf *.so mainProg  [/PHP]

that should do it

---

### Post by dwhitney67 on 2008-12-15
Monkeyking, it appears from the Makefiles you posted that vars.cpp is somehow dependent upon inner.o; perhaps vars.cpp calls a function that is defined in this object file?

Anyhow, when vars.cpp is compiled/linked, there is nothing in the Makefile that would indicate that it should look at inner.o to find any unresolved functions.

Here's a Makefile which I believe is better suited:
[php]
CXX_SRCS = vars.cpp
CC_SRCS = inner.c

EXE = mainProg

FLAGS = -Wall -ansi -pedantic

OBJS  = $(CXX_SRCS:.cpp=.o)
OBJS += $(CC_SRCS:.c=.o)


$(EXE): $(OBJS)
        @echo Linking $^ to build $@
        @$(CXX) $^ -o $@

.cpp.o:
        @echo Compiling $<
        @$(CXX) -c $(FLAGS) $<

.c.o:
        @echo Compiling $<
        @$(CC) -c $(FLAGS) $<

clean:
        $(RM) $(OBJS) $(EXE)
[/php]

---

### Post by dribeas on 2008-12-16
You must know what makefiles are and how they work. On the other hand, I have not written any makefile in a long time. You can use simpler tools (we use cmake) to generate makefiles from a simpler description.

While simple makefile usage is rather easy, more complex tasks are not (as an example automatically defining dependencies from a source tree so that the makefile will create all objects in order). Solutions like CMake, or scons, ant (probably, never used it with c++) are simpler in most cases.

Anyway, you must have an understanding of what makefiles are and how they work.

---

### Post by mkrahmeh on 2008-12-16
but the question still holds: why would i bother to write a makefile while fancy IDE's automatically generate almost everything, i've seen how makefiles generated by eclipse are pretty neat..so what is the point of it, unless am developing from within a CLI loggin ??

in short, does knowing much about makefiles increase my credentials as a programmer ??

---

### Post by nvteighen on 2008-12-16
> **jimi_hendrix said:**
> besides...makefiles arnt that hard...

```

all:
     gcc -o foo foo.c bar.c

```

Writing a Makefile for that would be overkill. Using a Makefile to compile a multi-file C project is usually done by splitting the compilation process into parts and according to dependency rules so you are not recompiling things that weren't touched (and therefore, gaining time...)

> **slavik said:**
> note: makefiles is not only for compiling stuff, you can use make for other things

+1

A Makefile is just a shell-script that's executed by checking dependencies. A .deb package's "rules" file (which creates the internal directory structure) is a Makefile.

> **mkrahmeh said:**
> but the question still holds: why would i bother to write a makefile while fancy IDE's automatically generate almost everything, i've seen how makefiles generated by eclipse are pretty neat..so what is the point of it, unless am developing from within a CLI loggin ??


Because in future you may need to tweak the compilation process... and you have to know how a Makefile is written. Maybe you don't need to write each Makefile you're going to use... there's GNU Autotools that automates the Makefiles' creation... but knowing what they are and how they work gives the ultimate control to configurate the process to what you need. (And the best way to learn is to write Makefiles :))

---

### Post by dwhitney67 on 2008-12-16
> **nvteighen said:**
> 
...

A Makefile is just a shell-script that's executed by checking dependencies. 

...


+1.

I once wrote a Makefile for building Cross-Compiled Linux From Scratch (CLFS).  This was a step not provided in the CLFS guide-book, but one that is necessary to ensure that everything is built in a particular order, and if something fails, I would not have to start from the beginning to resume the build.

Here's an excerpt from the Makefile I wrote last year; note that it pretty much looks like a shell script:
```

...

# CLFS STAGE 3
.clfs3: .stripped
        @echo "Entering 3rd stage of CLFS build..."
        @sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
        @sh ${OLY_LFS}/sources/scripts/enter-chroot-clfs.sh 3 || exit 1
        @sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
        touch $@


# STRIP CLFS LIBRARIES and BINARIES
.stripped: .clfs2
        @echo "Stripping CLFS libraries and binaries..."
        @sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
        @sh ${OLY_LFS}/sources/scripts/enter-chroot-strip.sh || exit 1
        @sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
        touch $@

# CLFS STAGE 2
.clfs2: .clfs1
        @echo "Entering 2nd stage of CLFS build..."
        @sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
        @sh ${OLY_LFS}/sources/scripts/enter-chroot-clfs.sh 2 || exit 1
        @sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
        touch $@


# CLFS STAGE 1
.clfs1: .tools .mnt-kernel-fs
        @echo "Entering 1st stage of CLFS build..."
        @sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
        @sh ${OLY_LFS}/sources/scripts/enter-chroot-clfs.sh 1 || exit 1
        @sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
        touch $@


# BUILD TEMPORARY SYSTEM (TOOLS)
.tools: .cross-tools
        @echo "Building temporary system..."
        make -C ${OLY_LFS}/sources/build-tools install
        touch $@


# BUILD CROSS-TOOLS
.cross-tools: .setup
        @echo "Building cross-tools..."
        make -C ${OLY_LFS}/sources/build-cross-tools install
        touch $@

...

```

---

### Post by monkeyking on 2008-12-16
> **dwhitney67 said:**
> 
[php]
CXX_SRCS = vars.cpp
CC_SRCS = inner.c

EXE = mainProg

FLAGS = -Wall -ansi -pedantic

OBJS  = $(CXX_SRCS:.cpp=.o)
OBJS += $(CC_SRCS:.c=.o)


$(EXE): $(OBJS)
        @echo Linking $^ to build $@
        @$(CXX) $^ -o $@

.cpp.o:
        @echo Compiling $<
        @$(CXX) -c $(FLAGS) $<

.c.o:
        @echo Compiling $<
        @$(CC) -c $(FLAGS) $<

clean:
        $(RM) $(OBJS) $(EXE)
[/php]

mother-of-all Makefiles this is...

---

### Post by dwhitney67 on 2008-12-16
Yep, it looks complicated, but in reality, how often does one mix C source code and C++?  Generally a project involves one or the other.

Sure there are cases where a C-library is used, which btw, isn't covered in the Makefile example I provided.

Anyhow, I keep a template Makefile handy so that I do not have to repeat the typing each and every time I start a project.  If you look carefully, all that is needed to change in the example I provided is the SRCS, the OBJS, and the EXE.  Everything else can remain untouched.

There is one thing though that is missing from the Makefile... the means to collect the dependencies that a particular file may have.  With the dependencies collected, a project can be successfully rebuilt if say, one were to change a header file or an individual source file.  The Makefile I demonstrated would indicate that the project is "built" even though I may have made a change to inner.h.

Here's a "templated" Makefile I typically use for C++ projects:
```

EXE       = testing
SRCS     := $(wildcard *.cpp)
OBJS      = $(SRCS:.cpp=.o)
CXXFLAGS  = -Wall -pedantic
INCPATH   =
LIBPATH   =
LIBS      =
DEP_FILE  = .depend

# Nothing below this line need be changed (barring of course any improvements!)


.PHONY = all clean distclean


# Main entry point
#
all: depend $(EXE)


# For linking object file(s) to produce the executable
#
$(EXE): $(OBJS)
	@echo Linking $@
	@$(CXX) $^ $(LIBPATH) $(LIBS) -o $@


# For compiling source file(s)
#
.cpp.o:
	@echo Compiling $<
	@$(CXX) -c $(CXXFLAGS) $(INCPATH) $<

# For cleaning up the project
#
clean:
	$(RM) $(OBJS)

distclean: clean
	$(RM) $(EXE)
	$(RM) $(DEP_FILE)


# For determining source file dependencies
#
depend: $(DEP_FILE)
	@touch $(DEP_FILE)

$(DEP_FILE):
	@echo Generating dependencies in $@
	@-$(CXX) -E -MM $(CXXFLAGS) $(INCPATH) $(CPP_SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```
Note that in some projects, the LIBPATH and the LIBS can be combined into one define statement.  For instance
```

LIBS = `pkg-config foopkg --libs`

```
Similarly for the CXXFLAGS:
```

CXXFLAGS = -Wall -pedantic `pkg-config foopkg --cflags`

```

I do not consider myself an expert with Makefiles; I use them to the extent of my needs, and I always keep my eye open for nifty tricks that simplify my needs.  For instance, I have learned that it is not necessary to define CC or CXX (or RM or MAKE, etc), because 'make' knows these; I also know that CFLAGS is known by 'make'; I'm not sure about CXXFLAGS.  Anyhow, if you need to deviate from the 'make' defaults, then yes, it is necessary to define specifically what is needed.

Anyhow, now that is is late, and I have a clear mind to think about the question posed by the OP, I will go on the record to state that learning to write Makefiles is *not* that important for everyone; it's analogous to a project where many s/w developers use a database, but only one individual is the actual DBA.  Makefiles are generally developed by one person on a team, or perhaps by an IDE (sigh), and are used by the others on the team.

Now, will one's "stock value" increase by knowing how to develop Makefiles?... Damn skippy!!  That's an easy question!  An IDE, just like a bitchin' computer, can't do a man's (or woman's) work.

---

### Post by monkeyking on 2008-12-27
hey dwhitney,

I've been looking into your makefiles in the last days.


You mention you don't need to have the CC macro, makes know this.
I've written this extremely small Makelife.

[PHP]
all:
	@echo ${CXX}
	@echo ${CC}
	@echo ${C}
	@echo ${CX}
[/PHP]
This gives
[PHP]
std:$ make
g++
cc


[/PHP]
g++ is called CXX and gcc is called cc.

ubuntu recognizes cc which symlinks to /etc/alternatives,
which then again symlinks to /usr/bin/gcc.
g++ symlinks to /usr/bin/g++-4.2

So do you have any experience using Makefiles with other compilers icc, I'm problems making make use icc 
```
make CXX=icc cc=icc
```
gives

[PHP]
src$ make cc=icc CXX=icc
icc
cc





[/PHP]


thanks

---

### Post by dwhitney67 on 2008-12-27
If you require to use a different compiler than GCC, then yes, you can specify which to use via CXX or CC.  I've used this feature before when cross-compiling with a different compiler than the system default compiler.

As for the anomaly you had, it is probably because you specified "cc" on the command line, in lieu of "CC".

Try this with your Makefile:
```

make CXX=icc CC=icc

```

---

