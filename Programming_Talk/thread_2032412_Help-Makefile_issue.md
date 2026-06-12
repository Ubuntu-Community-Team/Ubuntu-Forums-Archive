---
title: "Help-Makefile issue"
date: 2012-07-23
forum: Programming Talk
---

### Post by pellyhawk on 2012-07-23
I would like learn how to write Makefile and some issues:

```
   objects = foo.o bar.o

    all: $(objects) 

    $(objects): %.o: %.c
            $(CC) -c $(CFLAGS) $< -o $@
```

My questions is:

1)what does "all: %(objects)" mean? without this line, does it still work?
2)%.o equal to "foo.o bar.o", % equal to "foo bar" or *? In others words, % equal to all files? %.c equal to "foo.c bar.c" or "*.c"?

My material about Makefile is very limited, mainly for gcc and g++. Would you please tell me some material which clarifes Makefile in detail?

Thanks!

---

### Post by the_unforgiven on 2012-07-24
> **pellyhawk said:**
> I would like learn how to write Makefile and some issues:

```
   objects = foo.o bar.o

    all: $(objects) 

    $(objects): %.o: %.c
            $(CC) -c $(CFLAGS) $< -o $@
```

My questions is:

1)what does "all: %(objects)" mean? without this line, does it still work?


It tells make to create a target "all" that depends on "**$**(objects)" - i.e. the value of the variable objects that you have defined above. Note, it's a $ and not %.

So, in other words, it's equivalent to ```
all: foo.o bar.o
```
The reason is to simply allow running "make all" and be done with it.

Also, if there is no .DEFAULT target defined, the first target defined will be treated as the default target. So, if you just do "make", it's equivalent of saying "make all".

> **pellyhawk said:**
> 
2)%.o equal to "foo.o bar.o", % equal to "foo bar" or *? In others words, % equal to all files? % equal to "foo.c bar.c" or "*.c"?


No, '%' is not like a '*' wildcard. The rule ```
%.o : %.c
``` is like a template to expand into something like 
```

foo.o : foo.c
      .......

bar.o : bar.c
      ........

```
That is, for every .o file, create a rule with matching .c file as a dependency. Rather, for every .c file found, create a rule like above.

HTH. ;)

---

### Post by pellyhawk on 2012-07-24
Thanks a lot. I have understood what you told me about "%.c". but I am still confused by "%".

If only "%" is used, what dose it mean? Especially  ```
    vpath %.c foo
    vpath %   blish
    vpath %.c bar
```

why "%" is used in line 2 while "%.c" are used in line 1 and 3. I guess these 3 lines mean that all .c files are searched in directories foo, blish and bar. why not use```
    vpath %.c foo
    vpath %.c blish
    vpath %.c bar
```

---

### Post by the_unforgiven on 2012-07-24
> **pellyhawk said:**
> Thanks a lot. I have understood what you told me about "%.c". but I am still confused by "%".

If only "%" is used, what dose it mean? Especially  ```
    vpath %.c foo
    vpath %   blish
    vpath %.c bar
```

why "%" is used in line 2 while "%.c" are used in line 1 and 3. I guess these 3 lines mean that all .c files are searched in directories foo, blish and bar. why not use```
    vpath %.c foo
    vpath %.c blish
    vpath %.c bar
```
Turns out that I was wrong about '%' :) - it is indeed a wildcard.
However, found this piece to be quite helpful about vpath understanding:
[http://www.cmcrossroads.com/ask-mr-make/11088-the-basics-vpath-and-vpath](http://www.cmcrossroads.com/ask-mr-make/11088-the-basics-vpath-and-vpath)

See if it helps you.

---

### Post by spjackson on 2012-07-24
> **pellyhawk said:**
> Thanks a lot. I have understood what you told me about "%.c". but I am still confused by "%".

If only "%" is used, what dose it mean?

You seem to have taken your example from the [GNU Make Manual.]("http://www.gnu.org/software/make/manual/make.html") So '%' means "any sequence of zero or more characters".
> 
 Especially  ```
    vpath %.c foo
    vpath %   blish
    vpath %.c bar
```

why "%" is used in line 2 while "%.c" are used in line 1 and 3. I guess these 3 lines mean that all .c files are searched in directories foo, blish and bar.

The second directive will match **any** file that is being searched for. So if a.s is needed for example, then it will look in the blish directory.
> 
 why not use```
    vpath %.c foo
    vpath %.c blish
    vpath %.c bar
```
In this case, if a.s is needed for example, then it will not look in the blish directory. It will only look there for files whose name ends in .c

---

### Post by Bachstelze on 2012-07-24
```
$(objects): %.o: %.c
    $(CC) -c $(CFLAGS) $< -o $@
```

this is unnecessary (at least in GNU Make), there is an implicit rule for that

```
firas@aoba test % ls
bar.c  foo.c  Makefile
firas@aoba test % cat Makefile 
CC=gcc
CFLAGS=-std=c99 -pedantic -Wall -Wextra -g
OBJECTS=foo.o \
	bar.o

all: $(OBJECTS)
firas@aoba test % make
gcc -std=c99 -pedantic -Wall -Wextra -g   -c -o foo.o foo.c
gcc -std=c99 -pedantic -Wall -Wextra -g   -c -o bar.o bar.c
firas@aoba test % ls
bar.c  bar.o  foo.c  foo.o  Makefile

```

---

### Post by pellyhawk on 2012-07-25
the_unforgiven and spjackson,

Thanks a lot.

Bachstelze,

I am totally confused. In your Makefile, nothing about gcc is called, but why the following commands worked```
gcc -std=c99 -pedantic -Wall -Wextra -g   -c -o foo.o foo.c
gcc -std=c99 -pedantic -Wall -Wextra -g   -c -o bar.o bar.c
```

It is very weird! Would you please clarify it for me? I am new to gcc and Makefile and reading. Many thanks.

---

### Post by the_unforgiven on 2012-07-25
> **pellyhawk said:**
> 
Bachstelze,

I am totally confused. In your Makefile, nothing about gcc is called, but why the following commands worked```
gcc -std=c99 -pedantic -Wall -Wextra -g   -c -o foo.o foo.c
gcc -std=c99 -pedantic -Wall -Wextra -g   -c -o bar.o bar.c
```

It is very weird! Would you please clarify it for me? I am new to gcc and Makefile and reading. Many thanks.
All versions of make generally have built-in rules (called implicit rules) for most commonly used compilation targets - for various languages that are popular at the time.

Check this page from the make manual:
[http://www.gnu.org/software/make/manual/html_node/Implicit-Rules.html](http://www.gnu.org/software/make/manual/html_node/Implicit-Rules.html)

You can print the internal rules database of make using the command:```
make -p
```
The output is quite large, so you may want to pipe it through less/more or dump it into a file for reading later.

HTH ;)

---

### Post by pellyhawk on 2012-07-25
> **the_unforgiven said:**
> All versions of make generally have built-in rules (called implicit rules) for most commonly used compilation targets - for various languages that are popular at the time.

Check this page from the make manual:
[http://www.gnu.org/software/make/manual/html_node/Implicit-Rules.html](http://www.gnu.org/software/make/manual/html_node/Implicit-Rules.html)

You can print the internal rules database of make using the command:```
make -p
```
The output is quite large, so you may want to pipe it through less/more or dump it into a file for reading later.

HTH ;)

Thanks for your help and I shall look through it carefully.:)

---

