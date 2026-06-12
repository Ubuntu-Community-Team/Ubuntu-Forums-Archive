---
title: "use of header files"
date: 2012-12-10
forum: Programming Talk
---

### Post by IAMTubby on 2012-12-10
Hello,
I am sorry, but I still haven't been able to understand why header files are used, in spite of having read a lot about it.
I understand that if you are using a function from another C file/library, then you use a header file which has the function declaration instead of declaring the function in every C file which uses it. But .. can't this be done even **without** the header file, if all the C files are linked to form the same executable.

Consider these 2 .c files
```

**main.c**
#include <stdio.h>

int main(void)
{
 fun(1);

 return 0;
}

**support.c**
#include <stdio.h>

int fun(int a)
{
 printf("\ninside the other c file, a == %d",a);

}

**build line** : 
gcc *.c
./a.out

```

I'm not using any header for the function called fun, and it still works fine.

Please advise.
Thanks.

---

### Post by steeldriver on 2012-12-10
It probably 'works' because the compiler is implicitly assuming the return type of 'fun' is 'int'

If you turn on compiler warnings you will see that gcc is in fact unhappy about it

```
gcc -Wall ...
```[http://stackoverflow.com/questions/11171120/implicit-int-and-implicit-declaration-of-functions-with-gcc-compiler](http://stackoverflow.com/questions/11171120/implicit-int-and-implicit-declaration-of-functions-with-gcc-compiler)

And no, it doesn't matter that files are *linked* to form a single executable - they are still *compiled* separately

---

### Post by bird1500 on 2012-12-10
The header files are there for the compiler. If the compiler finds a call of a function (say foo(5)) **before** it found the function itself (that is its definition: "void foo(int i) {...}" or its declaration (that is "void foo(int);"), then the compiler fails to compile because the compiler doesn't just compile stuff, but it also does a lot of extra work like optimizations and checking for certain errors. To do this the compiler needs at least the declaration of the function.

Your example probably works because the compiler first sees the file with the definition of the function (support.c) and then the file with the main function, that's why it doesn't require a separate header file or so.

However, later on, the linker will need to find the actual function, be it in a library somewhere or in your binary executable, the linker stage is a different beast.

---

### Post by trent.josephsen on 2012-12-10
Wall of text incoming, more than you wanted to know.

For starters, you don't need to #include <stdio.h> in main.c since main.c doesn't use anything declared there. Also you've declared fun() to return an int but you don't return anything from it.

But in answer to your actual question, you've actually committed a cardinal sin: you called fun() in main.c without a declaration in scope. With warnings enabled, your compiler should let you know that fun() was implicitly declared when you called it in main.c.

When you compile main.c, the compiler doesn't know anything about fun(), like what type it returns or the number and types of its arguments. This kind of information is essential to generating the object code that calls a function. When you call it without a declaration in scope, the compiler has to make assumptions about how it works. For backwards-compatibility, it assumes that the return value is int, and it makes some other assumptions about the arguments based on how you call it. Still nothing is known about the *actual* form of fun().

When the post-compilation object files are linked together (the final step in the process), the linker inserts some extra information into the object code for main() so that main() knows where to find fun(). But you still have a potential issue the linker won't necessarily detect: main() calls fun() based on the *assumptions* the compiler made when you called main.c, and not on how fun() was *actually compiled*. If this goes undetected, you may be able to run the program, but if the compiler assumed wrong all the way back in step 1, main() may inadvertently scribble on your stack or cause fun() to do so, because they're not in agreement on how the stack should be used. When fun() returns you can't necessarily predict what will happen next. Or, in the terms of the C Standard, the behavior is undefined.

In your example, the compiler's assumptions are correct, and so it may work fine. But suppose fun() was defined in support.c to return void, since you don't in fact return anything from it. Then main() might expect fun() to put an int on the stack, but fun() doesn't do it -- after fun() returns, your stack pointer is off by sizeof(int) bytes. And trust me, that's something you *really* don't want. *(N.B. I don't think this would actually happen with gcc on x86 under ordinary conditions, but those are some big assumptions and you could always construct a more complex example that exhibits similar problems.)*

There is a way to solve this problem without header files: declare everything manually. Continuing with the prior example, you could declare fun() in main() and all would be well:

```
/* main.c */
void fun(int); // this is a prototype declaration, which tells the
               // compiler everything it needs to know about how to
               // call fun()
int main(void)
{
    fun(1);
    return 0;
}
```

But if you called fun() from a lot of different files, you might accidentally type int fun(int); instead, and you'd be back to the same problem, except your compiler wouldn't be able to warn you about it since you explicitly gave it the wrong information rather than letting it guess. Furthermore, if you ever saw a need to change the prototype of fun(), you'd have to go through every file that used it and fix the declaration. This is what header files are for. Since fun() is declared in support.c, you'd create support.h as follows:

```
/* support.h */
void fun(int);
```

Then, in every file you use fun(), you just have to #include "support.h" at the beginning and you immediately know they all are using the same function prototype. Furthermore, if you accidentally call fun() with the wrong number of arguments or something, the compiler will warn you with a message along the lines of "incompatible declaration".

But wait! There's one more improvement we can make. What happens if I'm editing support.c and I change the function there? Now support.c and support.h are in disagreement, and I'm back to square 1. Well, just add #include "support.h" at the top of support.c, and now the same declaration is in scope in support.c as in main.c. If I try to change the function's prototype in support.c, the compiler will immediately warn me that the definition conflicts with the declaration in support.h, and I will know I need to change it.

**TL;DR** - header files guarantee that all your object files agree on how functions are to be called.

I suggest calling gcc with -std=c99 -Wall -Wextra to be warned about this and other potentially dangerous mistakes. Use -std=c89 instead for ANSI C and -std=c11 for the newest version of the language (currently experimental).

---

### Post by rnerwein on 2012-12-10
> **IAMTubby said:**
> Hello,
I am sorry, but I still haven't been able to understand why header files are used, in spite of having read a lot about it.
I understand that if you are using a function from another C file/library, then you use a header file which has the function declaration instead of declaring the function in every C file which uses it. But .. can't this be done even **without** the header file, if all the C files are linked to form the same executable.

Consider these 2 .c files
```

**main.c**
#include <stdio.h>

int main(void)
{
 fun(1);

 return 0;
}

**support.c**
#include <stdio.h>

int fun(int a)
{
 printf("\ninside the other c file, a == %d",a);

}

**build line** : 
gcc *.c
./a.out

```I'm not using any header for the function called fun, and it still works fine.

Please advise.
Thanks.
to declare functions is one reason. but think about the typedefs of structures, definition of values, macros, limits and so on. have a look at some header files in /usr/include and i think you will understand what i mean.
cheers

---

### Post by Bachstelze on 2012-12-10
> **IAMTubby said:**
> 
I'm not using any header for the function called fun, and it still works fine.

You should know by now that in C, "it works fine" does not mean it's okay. If you still believe it does, you haven't learned much these past few months... This does not work fine:

```
firas@aoba ~ % cat test.c
#include <stdio.h>

int main(void)
{
    float f = abs(-5.0);
    printf("%f\n", f);
}
firas@aoba ~ % gcc -o test test.c
firas@aoba ~ % ./test 
1.000000
firas@aoba ~ % ./test foo
2.000000


```

And it even changes the value when you pass an argument! This works fine:

```
firas@aoba ~ % cat test.c        
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    float f = abs(-5.0);
    printf("%f\n", f);
}
firas@aoba ~ % gcc -o test test.c
firas@aoba ~ % ./test 
5.000000
firas@aoba ~ % ./test foo
5.000000

```

---

### Post by IAMTubby on 2012-12-10
> **steeldriver said:**
> It probably 'works' because the compiler is implicitly assuming the return type of 'fun' is 'int'

If you turn on compiler warnings you will see that gcc is in fact unhappy about it

```
gcc -Wall ...
```[http://stackoverflow.com/questions/11171120/implicit-int-and-implicit-declaration-of-functions-with-gcc-compiler](http://stackoverflow.com/questions/11171120/implicit-int-and-implicit-declaration-of-functions-with-gcc-compiler)

And no, it doesn't matter that files are *linked* to form a single executable - they are still *compiled* separately
Thanks steeldriver, yes I enabled flags and observed that it gives me warnings.

---

### Post by IAMTubby on 2012-12-10
> **bird1500 said:**
> 
Your example probably works because the compiler first sees the file with the definition of the function (support.c) and then the file with the main function, that's why it doesn't require a separate header file or so.

Thanks bird1500, but the "problem" is, it always works fine. Don't you think it would have been more easy to understand if the compiler reported an error ?

---

### Post by IAMTubby on 2012-12-10
> **trent.josephsen said:**
> 
I suggest calling gcc with -std=c99 -Wall -Wextra to be warned about this and other potentially dangerous mistakes. 
trent.josephsen, this was very very useful.
It gave me the warning
```

main.c: In function âmainâ:
main.c:5: warning: implicit declaration of function âfunâ

```
Thanks a lot for giving me the right flags to understand the concept. But don't you think it would have been better had the compiler reported an error, instead of doing so many things on it's own to get it right ? :)

---

### Post by IAMTubby on 2012-12-10
> **rnerwein said:**
> to declare functions is one reason. but think about the typedefs of structures, definition of values, macros, limits and so on. have a look at some header files in /usr/include and i think you will understand what i mean.
cheers
Thanks rnerwein, I had a look at /usr/include/printf.h and /usr/include/strings.h 
I get what you are saying, that it is not just about function declaration before calling a function, but also has variable declaration/definition, creating new data structures etc.

But don't you think this whole thing is messy and would have been much simpler if the compiler generated an error ?

---

### Post by IAMTubby on 2012-12-10
> **Bachstelze said:**
> You should know by now that in C, "it works fine" does not mean it's okay. 
```
firas@aoba ~ % cat test.c
#include <stdio.h>

int main(void)
{
    float f = abs(-5.0);
    printf("%f\n", f);
}
firas@aoba ~ % gcc -o test test.c
firas@aoba ~ % ./test 
1.000000
firas@aoba ~ % ./test foo
2.000000


```

And it even changes the value when you pass an argument! This works fine:

```
firas@aoba ~ % cat test.c        
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    float f = abs(-5.0);
    printf("%f\n", f);
}
firas@aoba ~ % gcc -o test test.c
firas@aoba ~ % ./test 
5.000000
firas@aoba ~ % ./test foo
5.000000

```
Bachstelze, thanks a lot for the example to demo that everything that gives an output is "not working" :)
I shall get into the practise of adding headers from now on.


> 
If you still believe it does, you haven't learned much these past few months

Sir, I shall try harder in the months to come .
I do not believe it works fine by the way, especially after seeing your example and the flags given by trent.jospehson.

But I'm slightly disappointed that something that people spend so much time on, that is, adding headers etc gives the correct output even without having it.

I feel that C standard should be altered either to :
1) not have it as a warning 
2) then show an error

---

### Post by Vaphell on 2012-12-10
> But I'm slightly disappointed that something that people spend so much time on, that is, adding headers etc gives the correct output even without having it.

adding headers doesn't take much time.
Besides correct output by accident in some obscure cases is wrong no matter how you slice it. Even if it worked correctly 99% of the time it's still bad.

be hardcore - use -Werror flag and have all warnings treated as errors

---

### Post by Bachstelze on 2012-12-10
> **IAMTubby said:**
> 
I feel that C standard should be altered either to :
1) not have it as a warning 
2) then show an error

That is outside the scope of the C standard. The only things the standard defines are the syntax of the language and the behavior of a program that obeys it. If you write a program that does not obey the syntax of the language, then your compiler is free to do whatever it wants. In particular, gcc with its default settings ([font=monospace]-std=gnu89[/font]) compiles a language which is basically C89 (ANSI C) with some GNU additions, and thus may or may not be consistent with the C89 standard.

---

### Post by spjackson on 2012-12-10
> **IAMTubby said:**
> I feel that C standard should be altered either to :
1) not have it as a warning 
2) then show an error

C is an old language - over 40 years old. I'm sure that Kernighan and Ritchie had good reasons for allowing implicit declaration of functions returning int. It might not be to everybody's taste (including mine) and if they were starting now, they might have made a different decision. The philosophy of C was "trust the programmer". If you want to do all kinds of dubious casting, C lets you, and many other languages don't.

As C has evolved, maintaining backwards compatibility has been an objective, and support for old constructs has persisted. There is an awful lot of old C code out there that still needs to be compiled.

When C++ came along, it was meant to be as compatible as possible with C. However, this implicit declaration of functions returning int was not preserved in C++. The C99 standard (13 years old) has also removed it.

So, as you want this feature to be removed from C, you can rejoice because it was 13 years ago. However compilers are still permitted to compile code that pre-dates that standard, thankfully.

If you compile with ```
gcc -std=c99
``` you do get a warning (when strictly speaking it should be an error). In order to make it an error you need ```
gcc -std=c99 -pedantic-errors
```

The compiler defaults may not be to your taste (or mine), but part of the craft of programming includes learning to use and tailor your tools (including the compiler) to suit your needs and preferences. Part of that involves deciding what C standard to use, and telling the compiler that that is what you want.

---

### Post by trent.josephsen on 2012-12-10
> **IAMTubby said:**
> But I'm slightly disappointed that something that people spend so much time on, that is, adding headers etc gives the correct output even without having it.
You must hate comments then. :-P

If C were invented today, I doubt header files would exist. GoLang, for instance, has a module-based approach to solving the same problem; IIRC, its compiler analyzes the entire (multi-file) source code of a package at once and I imagine that potential ambiguities on this level are worked out at link time. That's not really possible with C unless you totally abandon the idea of separate compilation for every source file, which would be one heck of a compatibility nightmare.

I picked Go because it's an example of a language heavily influenced by and with many of the same goals as C, but developed in the last decade. The concept of a software "module" like Python's or Java's didn't really exist in 1970.

---

### Post by JKyleOKC on 2012-12-10
While learning, it might be a good idea to add this line to your .bashrc file:```
alias gcc='gcc -std=c99 -pedantic-errors'
```This will force the error messages you want, without requiring all that typing every time. The "alias" command is one of the most, if not **the** most, powerful in the entire system.

---

### Post by Odexios on 2012-12-10
> **Bachstelze said:**
> You should know by now that in C, "it works fine" does not mean it's okay. If you still believe it does, you haven't learned much these past few months... This does not work fine:

```
firas@aoba ~ % cat test.c
#include <stdio.h>

int main(void)
{
    float f = abs(-5.0);
    printf("%f\n", f);
}
firas@aoba ~ % gcc -o test test.c
firas@aoba ~ % ./test 
1.000000
firas@aoba ~ % ./test foo
2.000000


```

And it even changes the value when you pass an argument! This works fine:

```
firas@aoba ~ % cat test.c        
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    float f = abs(-5.0);
    printf("%f\n", f);
}
firas@aoba ~ % gcc -o test test.c
firas@aoba ~ % ./test 
5.000000
firas@aoba ~ % ./test foo
5.000000

```Nice example. Could you please explain why does that happen, or tell me what should I look for to understand it?

I mean, I see what's wrong, but why does test behave in that particular way?

---

### Post by Bachstelze on 2012-12-10
> **Odexios said:**
> Nice example. Could you please explain why does that happen, or tell me what should I look for to understand it?

I mean, I see what's wrong, but why does test behave in that particular way?

What do you mean by "that particular way"?

---

### Post by Odexios on 2012-12-10
> **Bachstelze said:**
> What do you mean by "that particular way"?The fact that passing an argument to main, for example, changes the value returned by abs, or the way it is interpreted, or whatever happens.

I understand that when a behaviour is undefined anything can happen, but I guess there is a reason it fails in this way.

---

### Post by Bachstelze on 2012-12-10
> **Odexios said:**
> The fact that passing an argument to main, for example, changes the value returned by abs, or the way it is interpreted, or whatever happens.

I understand that when a behaviour is undefined anything can happen, but I guess there is a reason it fails in this way.

Actually if you run the program with two or three arguments you will notice that what gets printed is just the value of argc. Also, it fails that way only on 64 bit systems (more precisely, on x86-64). On x86 (32 bits) it always prints zero. What happens is simply that float and int arguments are passed differently. You can imagine that there is a "float" box and an "int" box where caller functions put arguments and called functions get them. The main function puts the argument for abs() in the "float" box, and abs() get it from the "int" box. Since there is no argument in the "int" box (the argument was put in the "float" box), abs() just takes whatever happens to be in the "int" box and does its thing. And apparently, that thing happens to be the value of argc on 64-bit machines, and zero on 32-bit ones.

Adding the header stdlib.h where abs() is defined tells the main function that abs() expects an int, so it will put the argument into the "int" box (after converting it from float to int, of course).

---

### Post by rnerwein on 2012-12-11
> **IAMTubby said:**
> Hello,
I am sorry, but I still haven't been able to understand why header files are used, in spite of having read a lot about it.
I understand that if you are using a function from another C file/library, then you use a header file which has the function declaration instead of declaring the function in every C file which uses it. But .. can't this be done even **without** the header file, if all the C files are linked to form the same executable.

Consider these 2 .c files
```

**main.c**
#include <stdio.h>

int main(void)
{
 fun(1);

 return 0;
}

**support.c**
#include <stdio.h>

int fun(int a)
{
 printf("\ninside the other c file, a == %d",a);

}

**build line** : 
gcc *.c
./a.out

```I'm not using any header for the function called fun, and it still works fine.

Please advise.
Thanks.
hi
and last not least: you can belive me --> C is like a razor but without a grip !
cheers

---

### Post by IAMTubby on 2012-12-12
> **Vaphell said:**
> adding headers doesn't take much time.
Besides correct output by accident in some obscure cases is wrong no matter how you slice it. Even if it worked correctly 99% of the time it's still bad.
:) ok shall get into the practice of adding headers

Thanks.

---

### Post by IAMTubby on 2012-12-12
> **Bachstelze said:**
> That is outside the scope of the C standard. The only things the standard defines are the syntax of the language and the behavior of a program that obeys it. If you write a program that does not obey the syntax of the language, then your compiler is free to do whatever it wants. In particular, gcc with its default settings ([font=monospace]-std=gnu89[/font]) compiles a language which is basically C89 (ANSI C) with some GNU additions, and thus may or may not be consistent with the C89 standard.
Thanks a lot Sir, I understand.

---

### Post by IAMTubby on 2012-12-12
[RIGHT][/RIGHT]> **trent.josephsen said:**
> You must hate comments then. :-P
Haha :D. 

> If C were invented today, I doubt header files would exist.
Thank you Sir, clears things for me.

> 
GoLang, for instance, has a module-based approach to solving the same problem; IIRC, its compiler analyzes the entire (multi-file) source code of a package at once and I imagine that potential ambiguities on this level are worked out at link time.

I shall look into the features of Go in my free time.

> 
That's not really possible with C unless you totally abandon the idea of separate compilation for every source file, which would be one heck of a compatibility nightmare.

This is a really good point Sir. I was hoping that my link would fail when I link my fails separately on calling a function in support.c from main.c and without using a header in support.c(basically the same question we are discussing, the only difference being that object files are generated separately and linked rather than doing gcc *.c. But no it still gives me the correct output. :(
This is the makefile I used
```

exe : main.o support.o
        gcc -o exe main.o support.c

main.o : main.c
        gcc -c main.c

support.o : support.c
        gcc -c support.c

``` 
Probably, this reminds me of what steeldriver said earlier in the thread. Look below.
> **steeldriver said:**
> 
And no, it doesn't matter that files are *linked* to form a single executable - they are still *compiled* separately




Thanks a lot Sir for your valuable inputs.

---

### Post by IAMTubby on 2012-12-12
> **JKyleOKC said:**
> While learning, it might be a good idea to add this line to your .bashrc file:```
alias gcc='gcc -std=c99 -pedantic-errors'
```
JkyleOKC, thanks a lot for this. I shall do this and adding it as an alias will keep me away from being lazy to add the necessary flags every time.

> **Vaphell said:**
> 
be hardcore - use -Werror flag and have all warnings treated as errors
Vaphell, yes shall add the flag

And how about this
-std=c99 -Wall -Wextra (this is to give a warning right ?)

But can you tell me if these two flags mean the same or are they different.

---

### Post by IAMTubby on 2012-12-12
> **rnerwein said:**
> hi
and last not least: you can belive me --> C is like a razor but without a grip !
cheers
rnerwein, haha :D, I still love it :)

---

### Post by IAMTubby on 2012-12-12
> **Bachstelze said:**
> In particular, gcc with its default settings ([font=monospace]-std=gnu89[/font]) compiles a language which is basically C89 (ANSI C) with some GNU additions, and thus may or may not be consistent with the C89 standard.
I get it Sir.

---

### Post by trent.josephsen on 2012-12-12
-Wall turns on a bunch of warnings. -Wextra turns on some more warnings. It's generally advisable to use both. -Werror makes warnings into errors instead. For more details I suggest [the GNU documentation for your version of gcc](http://gcc.gnu.org/onlinedocs/index.html#dir), specifically the section on [warning options](http://gcc.gnu.org/onlinedocs/gcc-4.7.2/gcc/Warning-Options.html#Warning-Options).

---

### Post by Bachstelze on 2012-12-12
-Werror is only useful if you have a really large program and compiling it produces a lot of output, it may make warnings difficult to spot and -Werror fixes that since then you can't miss them. Other than that, its only use is psychological (it forces you to fix all warnings before you get your executable, so you can't say "I'll fix it later").

---

### Post by kevinharper on 2012-12-12
Bachstelze still owning C threads... I've learned more from you (and others at the Ubuntu Forums) about C, and general programming practices, than any book or tutorial I've read.

Thanks to everyone for your responses. It's been very educational.

---

### Post by Odexios on 2012-12-14
> **Bachstelze said:**
> Actually if you run the program with two or three arguments you will notice that what gets printed is just the value of argc. Also, it fails that way only on 64 bit systems (more precisely, on x86-64). On x86 (32 bits) it always prints zero. What happens is simply that float and int arguments are passed differently. You can imagine that there is a "float" box and an "int" box where caller functions put arguments and called functions get them. The main function puts the argument for abs() in the "float" box, and abs() get it from the "int" box. Since there is no argument in the "int" box (the argument was put in the "float" box), abs() just takes whatever happens to be in the "int" box and does its thing. And apparently, that thing happens to be the value of argc on 64-bit machines, and zero on 32-bit ones.

Adding the header stdlib.h where abs() is defined tells the main function that abs() expects an int, so it will put the argument into the "int" box (after converting it from float to int, of course).Thanks for the explanation.

I guess that until the day I learn a little bit of assembly and of how C code is compiled and executed I won't be able to really grasp how C works.

---

### Post by JKyleOKC on 2012-12-14
> **Odexios said:**
> I guess that until the day I learn a little bit of assembly and of how C code is compiled and executed I won't be able to really grasp how C works.I said almost those exact words in another thread here. If you think of C as an only slightly simplified assembly language you won't be all that far off the mark, and many things that now appear to be frozen mysteries (such as the apparent equivalence between pointers and arrays) will become much more clear.

---

### Post by Bachstelze on 2012-12-14
> **Odexios said:**
> Thanks for the explanation.

I guess that until the day I learn a little bit of assembly and of how C code is compiled and executed I won't be able to really grasp how C works.

Actually no, because the whole point of C is to be portable, meaning assembly does not matter. What you will be able to do, however, is find out how bad code fails on that particular machine, which can also be fun. ;)

---

