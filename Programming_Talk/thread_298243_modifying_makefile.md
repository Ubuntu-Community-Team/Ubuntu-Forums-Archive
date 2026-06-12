---
title: "modifying makefile"
date: 2006-11-12
forum: Programming Talk
---

### Post by dexter on 2006-11-12
Hi all,

I'm using quite a big program (Diablo) for my thesis. I don't need to  edit the program myself, i'm just writing frontends for it. Right now, the frontends i'm writing are in the same directory as the big program, this however is a bit clumsy. It would be nicer if a could extract my own code files from the Diablo folder.

This is the situation how i would like it:
- folder prog
- subfolder Diablo
- subfolder with my programs (let's call it test for now)

So I put my code file's in the test folder and the makefile i'm using to compile my program. The problem is that this makefile include's another makefile in the Diablodirectory, this of course thousn't work anymore after moving the makefile.

This is how the makefile looks like:

```
BINARY=simple_frontend

all: $(BINARY)

DIABLOPATH=../Diablo/diablo-pieter/

BIT64=no
FLOWGRAPH_CONFIGURE=--disable-ppc --disable-i386
ANOPT_CONFIGURE=--disable-ppc --disable-i386

include $(DIABLOPATH)Makefile.local

CC=gcc
LD=$(CC)

CFLAGS=$(DIABLO_CFLAGS) -g -Wall -Wno-unused-function -DBIT32ADDRSUPPORT
LIBS=$(DIABLO_LIBS)

clean: diablo_clean
	-rm -f simple_frontend_options.[cho]

distclean: diablo_distclean
	-rm -f $(BINARY)

$(BINARY): simple_frontend.o simple_frontend_options.o
	$(LD) $(LDFLAGS) -o $@ $^ $(LIBS)

#the commannd line options stuff is pretty hairy - I don't think anyone but
# Bruno understands it completely
simple_frontend_options.o: simple_frontend_options.c

simple_frontend_options.c: simple_frontend.opt bin/opt_gen
	bin/opt_gen -d simple_frontend.opt -o simple_frontend_options -a frontend_options -l frontend_option_list -f FrontendOptions

simple_frontend.o: simple_frontend.c simple_frontend_options.c depend_anopt
	

%.o: %.c
	$(CC) -I. -Iinclude -c $(CFLAGS) $< -o $@
```

I made a variable DIABLOPATH to point to the directory of diablo, and changed the include line to include $(DIABLOPATH)Makefile.local.
The problem now is that when he start's executing the instructions in $(DIABLOPATH)Makefile.local, he's in the wrong directory (test), can't find files and stops making. I can't seem to find a way to change to the diablodir before he starts executing the $(DIABLOPATH)Makefile.local, is that possible with only modifying the makefile from the test folder ?

---

### Post by hod139 on 2006-11-12
I'm not sure how to change to the sub directory, but you can probably use the -I flag to add that directory to the include path.

```

$(DIABLO_CFLAGS) += ${DIABLOPATH}

```or something like that.

---

