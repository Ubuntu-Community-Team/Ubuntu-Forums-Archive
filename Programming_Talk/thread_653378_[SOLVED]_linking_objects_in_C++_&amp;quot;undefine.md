---
title: "[SOLVED] linking objects in C++: &amp;quot;undefined reference&amp;quot;"
date: 2007-12-29
forum: Programming Talk
---

### Post by Andruk Tatum on 2007-12-29
Hi, I'm learning C++, and the book I have has me building a CLI calculator.

I keep getting an "undefined reference" error when I build/compile my project with g++ as follows:

```
g++ calc.cc
```

This is the exact output:

```
/tmp/ccisJFOE.o: In function `main':
calc.cc:(.text+0x10f): undefined reference to `(anonymous namespace)::init()'
calc.cc:(.text+0x17b): undefined reference to `(anonymous namespace)::flag()'
collect2: ld returned 1 exit status
```

I'm using Anjuta to code it out, and that had the same result (expected, as I think Anjuta uses g++).

I have also tried building the author's code, which resulted in the same errors, but it had his namespace, not the "anonymous namespace".

The relevant files are attached, but here's the rundown:
calc.cc - the main part of the program
err.cc & err.h - the error handling implementation and header
prompt.cc & prompt.h - the UI implementation and header

I've looked it over (perhaps too much) and rewritten it several times, and nothing has worked.  Do I have a typo somewhere?  What am I doing wrong?

I'm sure I'll look back on this and cringe.

---

### Post by loell on 2007-12-29
i don't think you have a typo on your program as it compiled successfully , you just need to build this in a proper c++ project in anjuta or know how to make the basic makefiles

---

### Post by Andruk Tatum on 2007-12-29
What do I have to do in Anjuta to build it (other than "Build" the project)?  It is an actual project, but I my have screwed something up when debugging it.

And, if I write my own makefile, will Anjuta overwrite it when I build (if you know)?

Thanks for the example stuff!

---

### Post by geirha on 2007-12-29
Your problem is with the #ifndef #define stuff.

In err.h for instance, you have ```
#define err
```

This conflicts with ```
namespace err
```, as err will be replaced by nothing before the code is compiled. Change those defines to something that will not conflict with your code. **#define ERR_H** for example.

If you do that, your program should compile and link with ```
g++ *.cc
``` or with the compiling and linking seperated:
```
for file in *.cc; do 
  g++ -c $file; #compiling each .cc-file to a object(.o) file
done
g++ -o calc *.o # linking
./calc # running
```
This is something you usually use make for, so read up on that :)

---

### Post by Andruk Tatum on 2007-12-29
Ah, thank you!

---

