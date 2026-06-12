---
title: "[SOLVED] Anyone have a site that will explain modular programming in C?"
date: 2008-07-04
forum: Programming Talk
---

### Post by Yes on 2008-07-04
I tried copying and pasting the code here: [http://www.keil.com/support/docs/3198.htm](http://www.keil.com/support/docs/3198.htm), but in file2.c I get the error 'undefined reference to `val`', and in file1.c I get the error 'undefined reference to `myfunc`'. 

Anyone know what's wrong?

Thanks.

---

### Post by pmasiar on 2008-07-05
What are your programming skills? Is C your first language?

---

### Post by nvteighen on 2008-07-05
That code is horrible... but more important, it's written in an outdated fashion of C.

If you haven't seen it yet, [http://crasseux.com/books/ctutorial/](http://crasseux.com/books/ctutorial/), is possibly the best C beginner resource in English out there.

See [http://crasseux.com/books/ctutorial/External-variables.html#External%20variables](http://crasseux.com/books/ctutorial/External-variables.html#External%20variables) about external variables (very short and precise).

But functions just need to be prototyped in each source file before you're able to use them in your code. Of course, writing the same prototypes again and again is useless, so that's why we use header files: write once and #include them where necessary.

Example:
[PHP]
/* header.h */

int myfunc(int); 
/* In each source code that uses this header file, the compiler will know
 * what syntax myfunc() needs: which data type it returns and what it
 * takes (argument names are optional here). That's all what it needs,
 * actually. Definitions are the linker's job in the last compilation 
 * step. */

[/PHP]

[PHP]
/* func.c */

#include "header.h"
/* This #include directive is not necessary here, as its the source file 
 * where the function is defined. But in greater projects, where you're
 * using lots of functions across lots of files, this way you just make 
 * sure your programming will compile... */

int myfunc(int hello)
{
    /* Takes an argument and multiplies it by two if non-zero. This
     * could be more easily done with pointers, but it could lead the
     * discussion to somewhere else to what the OP wants. */

    if(hello != 0)
        hello *= 2;
 
    return hello;
}
[/PHP]

[PHP]
/* main.c - Corrected version! Thanks to dwhitney and Yes!*/

#include "header.h"

int main(void)
{
    /* OK, this is absurd, but should be understandable */

    int arnold = 0;
    int maggie = 3;

    int check = myfunc(arnold - maggie);

    return 0;
}
[/PHP]

This should help, I think.

---

### Post by Yes on 2008-07-05
Thanks, but main.c complains of an undefined reference to myfunc, and func.c complains of an undefined reference to main.  I changed int check = hello(arnold - maggie) to int check = myfunc(arnold - maggie) and added #include "header.h" to the top of both .c files.

@pmasiar, I took a 2-year course on Java in school, and have been teaching myself C for the past couple months.  What do you mean by "skills"?

---

### Post by dwhitney67 on 2008-07-05
Yes -

Edit - You are correct; the main.c is missing a #include "header.h", and instead of a call to hello(), it should be myfunc().

How are you compiling the source files?  For the two examples previously posted, you have two choices:  either 1) compile/link them in one step, or 2) compile each source file separately, then link them together.  Here's how...

1)
```
$ gcc func.c main.c -o myProg
```

2)
```

$ gcc -c func.c -o func.o
$ gcc -c main.c -o main.o
$ gcc func.o main.o -o myProg

```

P.S.  Regarding the link you provided in the OP, I see nothing obsolete with how things were declared.  Typically though, a header file will be used to define the function prototypes,( )and a complementary source file will implement the function(s).  There really is no need to declare a function as extern.  For a global variable, there is the need.  One should attempt to minimize the use of global variables; too many will indicate a bad design.

---

### Post by nvteighen on 2008-07-05
> **dwhitney67 said:**
> Yes -

Edit - You are correct; the main.c is missing a #include "header.h", and instead of a call to hello(), it should be myfunc().

That's what happens when writing code without having slept enough. Horrible mistake, thanks for pointing them out... I've corrected my post above so it should work now. (No, actually, I did it in purpose to prove your skills... ;))

> P.S.  Regarding the link you provided in the OP, I see nothing obsolete with how things were declared.  Typically though, a header file will be used to define the function prototypes,( )and a complementary source file will implement the function(s).  There really is no need to declare a function as extern.  For a global variable, there is the need.  One should attempt to minimize the use of global variables; too many will indicate a bad design.

I think it is a bit outdated: it's using void main() instead of int main(); gcc will output a warning if using the -Wall flag. As you say, the "extern" keyword is not necessary to prototype functions in a header... but why some tutorials (including the GNU C Tutorial I gave the link to) keep using it? "extern" is for external variables and nothing else!

---

### Post by Yes on 2008-07-05
Ah, great!  Thank you.

---

### Post by Yes on 2008-07-05
e: Sorry, didn't mean to double post :(

---

