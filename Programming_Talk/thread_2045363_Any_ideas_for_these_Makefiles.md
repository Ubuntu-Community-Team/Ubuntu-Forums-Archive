---
title: "Any ideas for these Makefiles?"
date: 2012-08-21
forum: Programming Talk
---

### Post by outofsync on 2012-08-21
I have a library whose code is split in several directories. The code is multiplatform, and I can compile for several architectures from a single host (for example, when on Linux I can compile for the following architectures: Motif/Linux, wxWidgets/Linux, and wxWidgets/Win32).

My plan is that each code directory will have a subdirectory for each architecture.

I googled for info about this, and I think I have an idea on how to compile for all architectures from a single make invocation, by using loops, and variables in targets (targets and dependencies will have the "architecture variable", so the arch subdirectory is automatically prefixed when building for each architecture in the loop.

However, for convenience, I'd also be able to build for all architectures from a single make invocation when I'm on one of the library directories.

I mean, if the hierarchy is like this:

mylibmaindir
  -mathcode
  -guicode
  -audiocode
  -gfxcode

I'd like all architectures to be built when I hit "make" not only on 'mylibmaindir', but also when I'm on 'gfxcode' for example (although in the later case, only the 'gfxcode' dir will be rebuilt, of course).

How would you do this? As I said, I only know how to do the arch loop from the first-level Makefile, no idea for the subdirs Makefiles...

---

### Post by ofnuts on 2012-08-21
> **outofsync said:**
> I have a library whose code is split in several directories. The code is multiplatform, and I can compile for several architectures from a single host (for example, when on Linux I can compile for the following architectures: Motif/Linux, wxWidgets/Linux, and wxWidgets/Win32).

My plan is that each code directory will have a subdirectory for each architecture.

I googled for info about this, and I think I have an idea on how to compile for all architectures from a single make invocation, by using loops, and variables in targets (targets and dependencies will have the "architecture variable", so the arch subdirectory is automatically prefixed when building for each architecture in the loop.

However, for convenience, I'd also be able to build for all architectures from a single make invocation when I'm on one of the library directories.

I mean, if the hierarchy is like this:

mylibmaindir
  -mathcode
  -guicode
  -audiocode
  -gfxcode

I'd like all architectures to be built when I hit "make" not only on 'mylibmaindir', but also when I'm on 'gfxcode' for example (although in the later case, only the 'gfxcode' dir will be rebuilt, of course).

How would you do this? As I said, I only know how to do the arch loop from the first-level Makefile, no idea for the subdirs Makefiles...

Just make the targets for all architectures dependencies for your default target.

---

### Post by dwhitney67 on 2012-08-21
For building sub-directories, something like this is easy to implement:
```

DIRS = subdir1 subdir2 subdir3

all clean:
        @ for dir in $(DIRS); do \
                $(MAKE) -C $$dir $@; \
        done

```
The Makefile above presupposes that you have separate Makefiles within each sub-directory.  One could look like:
```

LIBNAME  = libmotifStuff.so

CFLAGS  += -Wall -fPIC
LDFLAGS += -lX11 -lXm

SRCS     = $(wildcard *.c)
OBJS     = $(SRCS:.c=.o)

$(LIBNAME) : $(OBJS)
       $(CC) -shared -o $@ $^ $(LDFLAGS) 

```
No doubt you are using a different compiler for building the Window's library, thus define CC to equal the name of that compiler.  For example:
```

LIBNAME = myStuff.dll

CC = mingw-gcc

...

```

If your source code appears in multiple directories within each sub-directory, then you could search for all these using the 'find' command (instead of wildcard); for example:
```

...

OBJDIR   = objs

SRCS     = $(shell find . -name '*.c')
SRCDIRS  = $(shell find . -name '*.c' -exec dirname {} \; | uniq)
OBJS     = $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))

# macro: make object file repo
#
define make-repo
       for dir in $(SRCDIRS); \
       do \
            mkdir -p $(OBJDIR)/$$dir; \
       done
endef


$(LIBNAME): buildrepo $(OBJS)
        $(CC) -shared -o $@ $^

buildrepo:
        @ $(call make-repo)

$(OBJDIR)/%.o: %.c
        $(CC) $(CFLAGS) -c $< -o $@

```
There's so much more that one can do with Makefiles, however I will leave that research up to you.  If you have other specific questions, let us know.

---

### Post by outofsync on 2012-08-22
Thanks a lot for all your advice! Summing it up, I think it's best to always build from the root directory, because I prefer not to have Makefiles in the object code directories, but just on source code dirs.

For example, if a source code dir is 'mathdir', when building three object code subdirs will be created in it (ie: motif-linux, wx-linux, and wx-win32). Given that the compilers variables and settings differ for each of these builds, I believe each build requires a different make execution, and while I find it straightforward to do this loop from the root directory, it would be complicated to do from each source code dir (unless I place a Makefile on each object code subdir of course, but I find that too complicated).

The reason for trying the multibuild to run not only from the root directory but also from each source code dir is for convenience (it's possible that sometimes one source code dir might be temporarily broken, or that you simply prefer to rebuild one dir), but I think I can also live building always from the library root directory.

Thanks!

---

