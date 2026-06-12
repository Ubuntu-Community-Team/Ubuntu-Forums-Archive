---
title: "GCC with Find"
date: 2008-08-07
forum: Programming Talk
---

### Post by ngmachado on 2008-08-07
Hi,

I have a folder with lots of .c files, .pdf files and a makefile.

Each .c file should output an executable. So, if I have 10 .c files, I'll end with 10 binaries.

The name of the binary should be the name of the .c file (without the .c).

The makefile has 2 rules: all and clean. The clean rules is:

```
clean:
	find . \! -name "*.c" -and \! -name "*.pdf" -and \! -name "makefile" -delete
```

It'll remove all the binaries (all the files except .c, .pdf and the makefile itself).

Now I need help writing the "All" rule. It should find all the .c files, and send them to gcc compiler. 

I'm using:

```
all:
	find . -name "*.c" -exec gcc {} \;
```

But it generates only one binary file, it's being rewritten every time. I know I should use the -o option of the GCC but I do I get the filenames of the .c files without the .c and send them to GCC?

Any help would be vastly appreciated.

---

### Post by dwhitney67 on 2008-08-07
I would seriously recommend that you rewrite the 'clean' portion of the Makefile.  Seems very risky!

Why not create a Makefile in each of the sub-directories where your code is at?

For example:
```
SRCS := $(wildcard *.c)
OBJS  = $(SRCS:.c=.o)
EXEC  = $(SRCS:.c=)

CFLAGS = -Wall -pedantic -std=c99


all: $(OBJS)
        @for exe in $(EXEC); do\
                $(CXX) $$exe.o -o $$exe;\
        done

.c.o:
        $(CXX) $(CFLAGS) -c $^ -o $@ 

clean:
        $(RM) *.o

allclean: clean
        $(RM) $(EXEC)
```
Then a top-level Makefile:
```
SUBDIRS = dir1 dir2 dir3 etc

all clean allclean:
        @for dir in SUBDIRS; do\
                make -C $$dir $@;\
        done

```

---

### Post by ngmachado on 2008-08-07
Hey dwhitney67, 

It seems that you a know a lot about makefiles! :)

Well, I tested and carefully analysed your makefile and end up with this one:

```
CXX = GCC
SRCS = $(wildcard *.c)
EXEC = $(SRCS:.c=)

CFLAGS = -Wall -pedantic -std=c99

all: $(OBJS)
	@for exe in $(EXEC); do\
     $(CXX) $$exe.c -o $$exe;\
   done

clean:
	$(RM) $(EXEC)

```

I had to add the CXX = GCC or it'll use the G++. I also removed the creation/deletion of object files since I won't create any library. What do you think?

The code of the "all" rule is bash script? I learned a lot about makefiles, mainly the wildcards, "find and replace" in EXEC. 

Thank you.

---

### Post by dwhitney67 on 2008-08-07
The CXX does not need to be defined.  GCC is smart enough to know which compiler to use.

Also, don't forget to use the CFLAGS when you compile!

---

