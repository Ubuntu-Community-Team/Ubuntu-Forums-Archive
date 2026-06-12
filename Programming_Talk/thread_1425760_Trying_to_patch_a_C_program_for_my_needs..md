---
title: "Trying to patch a C program for my needs."
date: 2010-03-09
forum: Programming Talk
---

### Post by arkashkin on 2010-03-09
Hello,

I have downloaded the source code of glade 3.6.7 and trying to find out where the code begins, the 'main' function... how the compiler knows in which file to look for the main function? Is it usually written some where in the make-file?
I just want to add some very simple code in the place where the program begins...

Thanks.

---

### Post by MadCow108 on 2010-03-09
the main is usually in the main.c file
also in glade:
[http://git.gnome.org/browse/glade3/tree/src/main.c](http://git.gnome.org/browse/glade3/tree/src/main.c)
line 73

a quick recursive grep would also have found it
I also recommend cscope for quick code searching

the compiler does not care if there is a main function or not. It just compiles everything.
The linker (mostly invoked by gcc after compiling) then requires that there is the main symbol in one of the object files passed to it as arguments.
If there isn't it outputs an error.

---

### Post by arkashkin on 2010-03-09
> **MadCow108 said:**
> the main is usually in the main.c file
also in glade:
[http://git.gnome.org/browse/glade3/tree/src/main.c](http://git.gnome.org/browse/glade3/tree/src/main.c)
line 73

a quick recursive grep would also have found it
I also recommend cscope for quick code searching

the compiler does not care if there is a main function or not. It just compiles everything.
The linker (mostly invoked by gcc after compiling) then requires that there is the main symbol in one of the object files passed to it as arguments.
If there isn't it outputs an error.

Thanks a lot.

---

### Post by ssam on 2010-03-09
there is also ack-grep for searching in code (its a wrapper around grep).

```

ack-grep 'main('

```
would find it.

---

