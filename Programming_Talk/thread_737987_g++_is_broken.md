---
title: "g++ is broken?"
date: 2008-03-28
forum: Programming Talk
---

### Post by ElTimo on 2008-03-28
I tried to compile something with g++, and got this error```
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib64/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status
```the code i'm trying to compile doesn't even HAVE a 'main' function! it's a class file! this leads me to believe that the error refers to something in g++ itself, which can't be good. any help would be greatly appreciated, as this is for my Coocle Summer of Code application.

---

### Post by schmendrick on 2008-03-28
depends what you want to build. i guess you want to build a library?

your g++/linker tries to build an executable and therefore needs an entry point. thats why he cries that he does not have a main function. 

you have to change the compiler/linker options that you do not want to build an executable but the desired type you want. where you can change that is depending on what IDE you use (i dont think you compile via command line do you).

---

### Post by WW on 2008-03-28
Use the **-c** option.  For example,
> 
$ [color=blue]ls[/color]
empty.cpp
$ [color=blue]cat empty.cpp[/color] 
class empty
    {
    };
$ [color=blue]g++ empty.cpp[/color]
/usr/lib/gcc/x86_64-linux-gnu/4.1.3/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status
$ [color=blue]g++ -c empty.cpp[/color] 
$ [color=blue]ls[/color]
empty.cpp  empty.o
$ 

If you are using an IDE, then you'll have to figure out how to tell it that you are not compiling a main program.  (Perhaps look for an option to compile a library?)

---

### Post by ElTimo on 2008-03-28
First of all, thanks for your help.

Second, here's the thing: I write my programs in Geany, compile them there to see if they work, then compile via the command line in the built-in terminal.

I tried the -c option just now, and it worked. Thank you very much! Boy I feel dumb now. :lolflag:

---

### Post by Luksion Knight on 2011-09-30
Don't know if this was ever figured out but I often got this error when I forgot to save my .cpp file in the editor before compiling.

---

### Post by sisco311 on 2011-09-30
Necromancy. 

Thread Closed.

---

