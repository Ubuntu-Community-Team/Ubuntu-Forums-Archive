---
title: "Command substitution in Makefile, how?"
date: 2007-09-04
forum: Programming Talk
---

### Post by jonasmattsson on 2007-09-04
Hello!

I was wondering, is it possible to have command substitution in a Makefile? 
kind of like the one in bash or sh, you know:   
># FOO=`ls /`
># echo $FOO
bin boot cdrom dev etc home initrd ...

I have a program that generates a list of files from a vcproj-file and i want to use this list in my makefile. So i need the list to be done before i enter the rules.

---

### Post by Wybiral on 2007-09-04
Yes, in fact its very common for C and C++ makefiles to use something like:

```

CC = gcc
$(CC) *** use c compiler here ***

```

---

### Post by Compyx on 2007-09-04
Perhaps this is what you mean (taken from a makefile I used to play with Gtk+):
```

compyx@gutsy:~$ cat projects/hw/c/hw-gtk.make 
# set syn=make ts=8 sw=8 sts=8 noet
CC = gcc
LD = gcc

CFLAGS = -Wall -Wextra -g `pkg-config --cflags gtk+-2.0`
LDFLAGS = `pkg-config --libs gtk+-2.0` 

PROG = hw-gtk
OBJS = hw-gtk.o

all: $(PROG)

$(PROG): $(OBJS)
        $(LD) $(LDFLAGS) hw-gtk.o -o $(PROG)

hw-gtk.o: hw-gtk.c
        $(CC) $(CFLAGS) -c hw-gtk.c


clean:
        rm -f $(OBJS) $(PROG)

```

The backticks cause command substitution.

---

### Post by bogolisk on 2007-09-04
> **jonasmattsson said:**
> Hello!

I was wondering, is it possible to have command substitution in a Makefile? 
kind of like the one in bash or sh, you know:   
># FOO=`ls /`
># echo $FOO
bin boot cdrom dev etc home initrd ...

I have a program that generates a list of files from a vcproj-file and i want to use this list in my makefile. So i need the list to be done before i enter the rules.

```

FOO=$(shell ls /)

show_files:
[INDENT]echo $FOO[/INDENT]

```

---

### Post by jonasmattsson on 2007-09-04
> **bogolisk said:**
> ```

FOO=$(shell ls /)
```


Yeah!  thats what I'm talking about.
thank you all for your replies, but this was the one i was looking for.

---

