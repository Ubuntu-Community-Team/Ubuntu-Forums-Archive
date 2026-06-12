---
title: "[Makefiles]  Conditioning compiling flags according to target name"
date: 2008-08-09
forum: Programming Talk
---

### Post by nvteighen on 2008-08-09
Hi,

I've the following question. Say I have a project in C with several source files and just **one** (call it "weird.c") of those needs a special compiler flag (e.g. a `pkg-config`). So, my *attempt* in such a case would be:

```

SRC := $(wildcard *.c)
OBJ := $(SRC:.c=.o)
CC := gcc
FLAGS := -Wall -ggdb

.c.o :
ifneq($<,"weird.c")
    FLAGS += `pkg-config --cflags gtk+-2.0` # GTK is a popular example for pkg-config.
endif
    $(CC) -c $< $(FLAGS)

```

OK, if you have experience on Makefiles, you know that won't work: automatic variables can't be used in conditionals because of the way make reads Makefiles.

Of course, we could do something like this:
```

# same variable definitions as above

weird.o : weird.c
    $(CC) -c $< $(FLAGS) `pkg-config --cflags gtk+-2.0`

.c.o : 
    $(CC) -c $< $(FLAGS)

```

But there, we're duplicating code just to satisfy a single case... So, is there a sane way to condition rules according to the source name, without having to duplicate code innecessarily?

Or am I just a structured-programming paranoid? :)

---

