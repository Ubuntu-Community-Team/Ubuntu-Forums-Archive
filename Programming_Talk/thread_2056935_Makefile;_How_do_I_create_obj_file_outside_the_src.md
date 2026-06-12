---
title: "Makefile; How do I create obj file outside the src folder"
date: 2012-09-12
forum: Programming Talk
---

### Post by safarin on 2012-09-12
Hello all.. ):P

I try to create some recursive makefile, playing around with GNU make Makefile but got stuck... Here are my situation...

```

.
&#9500;&#9472;&#9472; include
&#9474;   &#9500;&#9472;&#9472; def.h
&#9474;   &#9492;&#9472;&#9472; h_TmrSbc.h
&#9500;&#9472;&#9472; lib
&#9500;&#9472;&#9472; obj
&#9492;&#9472;&#9472; src
    &#9500;&#9472;&#9472; f_TmrSbc.c
    &#9500;&#9472;&#9472; Makefile
    &#9492;&#9472;&#9472; m_TmrSbc.c

```

I try to run ("$ make") the Makefile inside the src folder but don't want to have object and execution files inside the /src folder.. instead I do need that files located inside the /obj folder...

```

CC = gcc
CFLAGS = -g -Wall
INCL = -I../include
EXEC = TmrSbc
 
$(EXEC): m_TmrSbc.o f_TmrSbc.o
    $(CC) -o $@ $^ 
 
%.o: %.c
    $(CC) $(CFLAGS) -c $< $(INCL)

```

I do need help or keyword to solve this problem... 
I already try to change 

```
%.o: %.c
to
obj/%.o: %.c
```

but the compiler state it could not found the header inside the include folder... 

ohhh.. and is this problem occur have something to do with vpath or patsubst???

P/S: I'm just new to play makefile..

Please help.. Thank you :popcorn:

---

### Post by dwhitney67 on 2012-09-12
This Makefile may be overkill, but it should work for your needs.  If necessary, customize it further.

```

APP      = TmrSbc

OBJDIR   = obj

SRCS    := $(shell find . -name '*.c')
SRCDIRS := $(shell find . -name '*.c' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.c,$(OBJDIR)/%.d,$(SRCS))

DEBUG    = -g
INCLUDES = -I./include
CFLAGS   = $(DEBUG) -Wall -pedantic $(INCLUDES) -c
LDFLAGS  =
LIBS     =

DEPENDS  = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

SHELL    = /bin/bash

.PHONY: all clean distclean


all: buildrepo $(APP)

$(APP): $(OBJS)
<tab>$(CC) $(LDFLAGS) $^ $(LIBS) -o $@

$(OBJDIR)/%.o: %.c
<tab>$(CC) $(CFLAGS) $(DEPENDS) $< -o $@

clean:
<tab>$(RM) -r $(OBJDIR)

distclean: clean
<tab>$(RM) $(APP)

buildrepo:
<tab>@$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
    mkdir -p $(OBJDIR)/$$dir; \
   done
endef

ifneq "$(MAKECMDGOALS)" "distclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```

P.S.  The Makefile above should sit at the same level as 'obj', 'include', and 'src' directories.

---

### Post by dwhitney67 on 2012-09-12
Here's a simpler Makefile that you can keep within the 'src' directory:
```

EXEC   = TmrSbc

OBJDIR = ../obj

SRCS   = $(wildcard *.c)
OBJS   = $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))

CFLAGS = -g -Wall
INCL   = -I../include

$(EXEC): $(OBJS)
<tab>$(CC) -o $@ $^ 

$(OBJDIR)/%.o: %.c
<tab>$(CC) $(CFLAGS) $(INCL) -c $< -o $@

```

---

### Post by safarin on 2012-09-12
> **dwhitney67 said:**
> Here's a simpler Makefile that you can keep within the 'src' directory:
```

...

SRCS   = $(wildcard *.c)
OBJS   = $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))

...

```

Thank you dwhitney67 for your answers..

but I have to question regarding to your answers.. 

1. why use wildcard because already use "* (wildcard)"...
2. what is this function for $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))

P/S: Your overkill Makefile template is really awesome.. Yes, I don't understand it.. but maybe other person could use it in the future.. or maybe me will use it.. Thank you... :guitar:

---

### Post by safarin on 2012-09-12
Other simple solution 

```

CC = gcc
CFLAGS = -g -Wall
INCL = -I../include
EXEC = TmrSbc
OBJ_DIR = ../obj

$(OBJ_DIR)/$(EXEC): $(OBJ_DIR)/m_$(EXEC).o $(OBJ_DIR)/f_$(EXEC).o
	$(CC) -o $@ $^  

$(OBJ_DIR)/%.o: %.c
	$(CC) $(CFLAGS) $(INCL) -c $< -o $@

```

P/S: credit to cboard.cprogramming guys..

---

### Post by dwhitney67 on 2012-09-12
> **safarin said:**
> Thank you dwhitney67 for your answers..

but I have to question regarding to your answers.. 

1. why use wildcard because already use "* (wildcard)"...
2. what is this function for $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))

Answers:

1.  The 'wildcard' word is actually a statement recognized by 'make' to fetch the files using the regex pattern specified.  Without the 'wildcard', 'make' would not know what to do with the specified pattern.

2.  The function is a "pattern substitution" directive; it tells 'make' to take the first part of the .c file name(s) from SRCS, and create a pattern that includes the OBJDIR and same first part of file name.  Something like this:
```

foo.c ===> $(OBJDIR)/foo.o

```

For simple projects that have one, two, or even a handful of .c files, your "simple" Makefile may suffice, but when you have projects with tens or hundreds of files, only the foolhardy or the person with copious amounts of free time would put in the effort to list each and every file in the Makefile.  Thus the rationale for employing the use of 'wildcard' (or the shell 'find' command in my first Makefile example).

---

### Post by safarin on 2012-09-13
> The function is a "pattern substitution" directive; it tells 'make' to take the first part of the .c file name(s) from SRCS, and create a pattern that includes the OBJDIR and same first part of file name.  Something like this:
```

foo.c ===> $(OBJDIR)/foo.o

OBJS    := $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))

```

According to your explanation... Le't me clarify my understanding, all the objects inside the $(OBJDIR) will substitute to the name according to $(SRCS) files... but the different is only the extension of the file.. ".c to .o" am I correct..

> For simple projects that have one, two, or even a handful of .c files, your "simple" Makefile may suffice, but when you have projects with tens or hundreds of files, only the foolhardy or the person with copious amounts of free time would put in the effort to list each and every file in the Makefile.  Thus the rationale for employing the use of 'wildcard' (or the shell 'find' command in my first Makefile example).

I already try your Makefile (1st post makefile example)..
It's is really handy... I'm surprise that I don't need anymore makefile in each subfolder.. The top level Makefile is more than enough.. 

Thanks for that Makefile Magic... I really appreciate

---

