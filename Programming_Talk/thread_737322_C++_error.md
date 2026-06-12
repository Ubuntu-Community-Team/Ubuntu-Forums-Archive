---
title: "C++ error?"
date: 2008-03-27
forum: Programming Talk
---

### Post by Ryozanpaku Tiger on 2008-03-27
Dear all,

Here is a very simple code:

[COLOR="Blue"]1  #include<stdio.h>
2   int main()
3   {
4    void print(double d)
5   {
6       printf("%f; \n", d);
7   }
8   print(10.);
9
10   return 0;
11 }[/COLOR]

But g++ compiler gives the following:

[COLOR="Blue"]g++ -Wall -c -g listing1.c
listing1.c: In function ‘int main()’:
listing1.c:5: error: a function-definition is not allowed here before ‘{’ token
listing1.c:8: error: ‘print’ was not declared in this scope[/COLOR]

Where is an error? I can't find it! Can anyone help? :( Thank you!

---

### Post by nick_h on 2008-03-27
Try:
```
#include<stdio.h>
void print(double d)
{
	printf("%f; \n", d);
}
int main()
{
	print(10.);
	return 0;
}
```

---

### Post by Ryozanpaku Tiger on 2008-03-27
Thank you very much! It worked! But what is the reason for such an error? I can't define a function within main function, can I?

---

### Post by baumgc on 2008-03-27
> **Ryozanpaku Tiger said:**
> Thank you very much! It worked! But what is the reason for such an error? I can't define a function within main function, can I?

Forgive me if I don't use the correct terminology, but I think it goes something like this:

You can **declare** a function within main, but the **implementation** has to be outside of main.

Amirite?

---

### Post by Jessehk on 2008-03-27
> **Ryozanpaku Tiger said:**
> Thank you very much! It worked! But what is the reason for such an error? I can't define a function within main function, can I?

Nope. :)

---

### Post by Ryozanpaku Tiger on 2008-03-27
I suspected that.:)

But gcc compiler doesn't give error here! Why?

---

### Post by Nemooo on 2008-03-27
Just on a sidenote:

Your C++ code looks more like C to me. In C++ it would look like this:

```
#include <iostream>

void print(double d)
{
    std::cout << d << std::endl;
}

int main()
{
    print(10.)
    return 0;
}
```

---

### Post by Ryozanpaku Tiger on 2008-03-27
**Nemooo,** that's true! It is C code, which is compiled by C++ compiler.

The point is that gcc allows defining functions within main function, while g++ does not! Could you please explain, why does it happen? Thank you!

---

### Post by rye_ on 2008-03-27
defining a function within a function.  that's news to me.

---

### Post by Ryozanpaku Tiger on 2008-03-27
**rye_**, try to compile the following using gcc compiler:

[COLOR="Blue"]#include<stdio.h>
int main()
{
  int maximum(int a, int b) {return a>b ? a : b;}
  int minimum(int a, int b) {return a<b ? a : b;}

  return 0;
}[/COLOR]

gcc has nothing against it, while g++ does. Am I doing something wrong?

---

### Post by Nemooo on 2008-03-27
Both gcc and g++ won't compile the code you just posted. Both with the same error:

a function-definition is not allowed here before &#8216;{&#8217; token

---

### Post by Ryozanpaku Tiger on 2008-03-27
That's weird! :( My gcc compiler compiles it without problems.

gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

This is my makefile:

[COLOR="Blue"]OBJS4 = test.o

CC = gcc
DEBUG = -g
CFLAGS = -Wall -c $(DEBUG)
LFLAGS = -Wall $(DEBUG)

all : test

test : $(OBJS4)
	$(CC) $(LFLAGS) $(OBJS4) -o test
test.o : test.c
	$(CC) $(CFLAGS) test.c

clean:
	rm -f *.o test[/COLOR]

What is wrong?

---

### Post by Nemooo on 2008-03-27
I'm on default setings (how do I see my makefile?). The only parameter I'm using in both cases is -o.

---

### Post by WW on 2008-03-27
Yes, it compiles with gcc.  I have the same compiler version as R. Tiger.  (I called the file "nestedfuncs.c"):
> 
$ gcc -Wall nestedfuncs.c -o nestedfuncs 
$

However,
> 
$ gcc -Wall -pedantic nestedfuncs.c -o nestedfuncs
nestedfuncs.c: In function 'main':
nestedfuncs.c:4: warning: ISO C forbids nested functions
nestedfuncs.c:5: warning: ISO C forbids nested functions
$ 

So it is probably not a good idea to nest functions, especially if you will be sharing your code with others.

---

### Post by Ryozanpaku Tiger on 2008-03-27
**Nemooo,** this line works fine for me:

> gcc test.c -o test

Are you working in some IDE?

**WW**, yes, sure it's not a good idea. All these examples are just for practice. I learn C and C++ now, so some interesting things appear.:)

---

### Post by Nemooo on 2008-03-27
D'oh. I forgot to save the file as .c.

Sorry for the mistakes, it compiles now with gcc.

---

### Post by rye_ on 2008-03-27
my c/c++ programming started with c++, then back-tracked to c, so perhaps that's why I never noticed.  But also I don't think I read this in "A book on C", by kernighan and richie.  Is this part of the c language or an oddity with gcc?

---

### Post by LaRoza on 2008-03-27
> **rye_ said:**
> my c/c++ programming started with c++, then back-tracked to c, so perhaps that's why I never noticed.  But also I don't think I read this in "A book on C", by kernighan and richie.  Is this part of the c language or an oddity with gcc?
See:
[quote="man gcc"]
For any given input file, the file name suffix determines what kind of
       compilation is done:

       file.c
           C source code which must be preprocessed.

       file.i
           C source code which should not be preprocessed.

       file.ii
           C++ source code which should not be preprocessed.

       file.m
           Objective-C source code.  Note that you must link with the libobjc
           library to make an Objective-C program work.

       file.mi
           Objective-C source code which should not be preprocessed.

       file.mm
       file.M
           Objective-C++ source code.  Note that you must link with the
           libobjc library to make an Objective-C++ program work.  Note that
           .M refers to a literal capital M.

       file.mii
           Objective-C++ source code which should not be preprocessed.

       file.h
           C, C++, Objective-C or Objective-C++ header file to be turned into
           a precompiled header.

       file.cc
       file.cp
       file.cxx
       file.cpp
       file.CPP
       file.c++
       file.C
           C++ source code which must be preprocessed.  Note that in .cxx, the
           last two letters must both be literally x.  Likewise, .C refers to
           a literal capital C.

       file.mm
       file.M
           Objective-C++ source code which must be preprocessed.

       file.mii
           Objective-C++ source code which should not be preprocessed.

       file.hh
       file.H
           C++ header file to be turned into a precompiled header.

       file.f
       file.for
       file.FOR
           Fixed form Fortran source code which should not be preprocessed.

       file.F
       file.fpp
       file.FPP
           Fixed form Fortran source code which must be preprocessed (with the
           traditional preprocessor).

       file.f90
       file.f95
           Free form Fortran source code which should not be preprocessed.

       file.F90
       file.F95
           Free form Fortran source code which must be preprocessed (with the
           traditional preprocessor).

       file.ads
           Ada source code file which contains a library unit declaration (a
           declaration of a package, subprogram, or generic, or a generic
           instantiation), or a library unit renaming declaration (a package,
           generic, or subprogram renaming declaration).  Such files are also
           called specs.

       file.adb
           Ada source code file containing a library unit body (a subprogram
           or package body).  Such files are also called bodies.

       file.s
           Assembler code.

       file.S
           Assembler code which must be preprocessed.

       other
           An object file to be fed straight into linking.  Any file name with
           no recognized suffix is treated this way.

       You can specify the input language explicitly with the -x option:

       -x language
           Specify explicitly the language for the following input files
           (rather than letting the compiler choose a default based on the
           file name suffix).  This option applies to all following input
           files until the next -x option.  Possible values for language are:

                   c  c-header  c-cpp-output
                   c++  c++-header  c++-cpp-output
                   objective-c  objective-c-header  objective-c-cpp-output
                   objective-c++ objective-c++-header objective-c++-cpp-output
                   assembler  assembler-with-cpp
                   ada
                   f95  f95-cpp-input
                   java
                   treelang
[/quote]

---

### Post by rye_ on 2008-03-28
Sorry LaRoza, I don't quite see what you're showing me.
Can you clarify a bit please (I probably being a bit thick here:))

---

### Post by Sockerdrickan on 2008-03-28
I always name my headers file not file.h when I write C++ code. I read somewhere it's the new standard.

---

