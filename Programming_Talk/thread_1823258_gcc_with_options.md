---
title: "gcc with options"
date: 2011-08-11
forum: Programming Talk
---

### Post by kevinharper on 2011-08-11
I'm fairly new to gcc - been using it for about a month.

When learning to compile with it, I read somewhere online to compile by typing:
```

gcc -c <filename>.c

```

And link it using:
```

gcc -o <executable_name> <filename>.c

```

In a different thread I was told to use "-std=c99 -pedantic -Wall -Werror" also. That these would catch more errors in my code.

I understand what the options do...

My questions:
Do I have to go through two steps? Can I just type the following?
```

gcc -std=c99 -pedantic -Wall -Werror -o foo foo.c

```

When I was first told, I would compile with all of these options and then link with "-o" only. But I accidentally skipped the "-c" step once and noticed that the program compiled and linked... but there was no object file.

---

### Post by MG&amp;TL on 2011-08-11
Try it and see. You're not going to damage anything. In g++, generally one compiles and links at the same time. At least for small programs.

---

### Post by Bachstelze on 2011-08-11
There are mostly two instances where you would want to "compile only" with -c: when you have a large program with several .c files, and when your .c file is just a collection of functions with no main and you want to make a library out of it, not an executable.

For an executable with just one .c file, skipping -c is perfectly fine.

*EDIT:* oh, also if you want to study the object code, e.g. with a disassembler like objdump.

---

### Post by cgroza on 2011-08-11
The -c switch is useful to avoid the unnecessary recompilation of files in a multiple files project.

I have only seen in being used in Makefiles, it is rarely run at the command line by hand.

---

### Post by kevinharper on 2011-08-11
Awesome.. thanks guys.

It was becoming a bit of a pain to have to -c and -o separately every time.

@Bachstelze Where do I sent you my tuition check? :P You've been an awesome resource. Thanks.

---

### Post by dwhitney67 on 2011-08-12
There's another option available to build a simple project; use the "make" command.

For instance, say you have a program called hello.c; to make the executable, you would run:
```

make hello

```
If you wish to use compiler options, then you could always define CFLAGS (or CXXFLAGS for C++ development).  For example:
```

export CFLAGS='-Wall -Werror -pedantic -std=c99'

```
Put this export declaration in your ~/.bashrc (or comparable file) so that you do not have to enter it every time.


P.S.  It should be noted that there are drawbacks to using "make" without a Makefile.  For more complex applications that require dependencies to be generated, or that require additional header file paths, library paths and librarys, etc., then a proper Makefile should be created.

---

### Post by kevinharper on 2011-08-12
Very cool, dwhitney67. Thanks.

---

