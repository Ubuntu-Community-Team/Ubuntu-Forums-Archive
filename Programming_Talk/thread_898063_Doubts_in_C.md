---
title: "Doubts in C"
date: 2008-08-22
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-08-22
I have a few doubts n C. If someone can help please

1)How do i compile a program in C when i use the #define command at the beginning. I get an error message when i compile it the normal way. Is there any option that needs to be added.

Can someone give me a list of all the options that can be added when different aspects of C are used. In the sense, there doesn't seem to be a header file by the name <conio.h>???

2) Here we are thought that integer takes in 2 bytes of memory. I am shocked that when i made an array of integers each integer seemed to have taken in 4 memory addresses. Is the definition of an integer different in gcc from that of ANSI C.

One more thing. According to ANSI C we must declare all variables<local> at the beginning of a function. But it seems that we can declare the variables any where in the function just before use. Is gcc a c++ compiler.

3)In the concept of pointers i seem to be a little confused. Actually haven't understood the concept at all. Now when i point a variable to a array, the pointer will store the base memory address of the array, say a[0] for eg. Now if that is the case then what is the need to define a data-type for a pointer. If the amount of memory to be stored is the same(i.e. it has to anyway store only the base address) then what difference will it make when a pointer is assigned a char/int/float data-type. This doubt will be applicable to variables which are not arrays as well.

---

### Post by pmasiar on 2008-08-22
Seems like you have no previous programming experience?

Maybe is not too late for you to switch to Python, to avoid thinking about half of those problems? Check sticky FAQ for advice for beginners and poll.

If not, enjoy your C!

---

### Post by LaRoza on 2008-08-22
> **i.mehrzad said:**
> 
1)How do i compile a program in C when i use the #define command at the beginning. I get an error message when i compile it the normal way. Is there any option that needs to be added.

Can someone give me a list of all the options that can be added when different aspects of C are used. In the sense, there doesn't seem to be a header file by the name <conio.h>???

I don't understand 1.

conio.h is not a standard header. See the C library references in my wiki under C.

> 
2) Here we are thought that integer takes in 2 bytes of memory. I am shocked that when i made an array of integers each integer seemed to have taken in 4 memory addresses. Is the definition of an integer different in gcc from that of ANSI C.

Don't be shocked ;) [http://home.att.net/~jackklein/c/inttypes.html#int](http://home.att.net/~jackklein/c/inttypes.html#int)

> 
One more thing. According to ANSI C we must declare all variables<local> at the beginning of a function. But it seems that we can declare the variables any where in the function just before use. Is gcc a c++ compiler.

What version of C ;) gcc is a bunch of compilers, hence: GNU Compiler Collection.

Remember, C has changed with each standard, and C89 and C99 are commonly used.

---

### Post by LaRoza on 2008-08-22
> **pmasiar said:**
> Seems like you have no previous programming experience?

Maybe is not too late for you to switch to Python, to avoid thinking about half of those problems? Check sticky FAQ for advice for beginners and poll.

If not, enjoy your C!

Already tried to recommend that, but he is learning it in school.

(I wonder why all the Indian schools use C for their intros? At least, all the ones that I have seen. They all ask about conio.h as well)

---

### Post by yabbadabbadont on 2008-08-22
conio.h ...  ah the DOS/Win memories.  Uh oh... make them stop!  :lol:

---

### Post by ghostdog74 on 2008-08-22
> **LaRoza said:**
> (I wonder why all the Indian schools use C for their intros? At least, all the ones that I have seen. They all ask about conio.h as well)

maybe you should stop wondering :). C is perfectly suitable as a study tool for basic programming.

---

### Post by dwhitney67 on 2008-08-22
> **LaRoza said:**
> Already tried to recommend that, but he is learning it in school.

(I wonder why all the Indian schools use C for their intros? At least, all the ones that I have seen. They all ask about conio.h as well)
Perhaps because the educators are probably are trying to prepare their students to assume job roles as embedded s/w developers?  I don't see python being relevant in that particular domain.

---

### Post by xeth_delta on 2008-08-22
> 
1)How do i compile a program in C when i use the #define command at the beginning. I get an error message when i compile it the normal way. Is there any option that needs to be added.

I don't mean to be too picky and I'm sure it's just semantycs right now, but #define is not a command. It's just a definition.

---

### Post by slavik on 2008-08-22
> **xeth_delta said:**
> I don't mean to be too picky and I'm sure it's just semantycs right now, but #define is not a command. It's just a definition.
you mean macro. :-p

---

### Post by xeth_delta on 2008-08-22
> **slavik said:**
> you mean macro. :-p

yeah, fair enough. :p

---

### Post by pmasiar on 2008-08-23
> **ghostdog74 said:**
> C is perfectly suitable as a study tool for basic programming.

Yes, but as OP experience shows, as second language, not the first.

---

### Post by ghostdog74 on 2008-08-23
> **pmasiar said:**
> Yes, but as OP experience shows, as second language, not the first.

that reply was for Laroza's response  on how he wondered why the schools use C for their intro. We are not going to go through this again are we?

---

### Post by Nemooo on 2008-08-23
> **i.mehrzad said:**
> I have a few doubts n C. If someone can help please

1)How do i compile a program in C when i use the #define command at the beginning. I get an error message when i compile it the normal way. Is there any option that needs to be added.

What error message?

> **i.mehrzad said:**
> One more thing. According to ANSI C we must declare all variables<local> at the beginning of a function. But it seems that we can declare the variables any where in the function just before use. Is gcc a c++ compiler.

You can declare variables anywhere in a function, as long as it's done before it's used. Just as you say.

And yes GCC can compile C++ code.

> **i.mehrzad said:**
> 3)In the concept of pointers i seem to be a little confused. Actually haven't understood the concept at all. Now when i point a variable to a array, the pointer will store the base memory address of the array, say a[0] for eg. Now if that is the case then what is the need to define a data-type for a pointer. If the amount of memory to be stored is the same(i.e. it has to anyway store only the base address) then what difference will it make when a pointer is assigned a char/int/float data-type. This doubt will be applicable to variables which are not arrays as well.

Pointers seem confusing at first. Re-read the text concerning them in your book and look around for tutorials ([http://www.cprogramming.com/tutorial/c/lesson6.html](http://www.cprogramming.com/tutorial/c/lesson6.html) - very basic). You should also use them in small programs to test how they're used and how they work.

---

