---
title: "What is memory management in programming"
date: 2009-11-21
forum: Programming Talk
---

### Post by hoboy on 2009-11-21
In programming what is What is memory management ?
How do I do it ?

---

### Post by A_Fiachra on 2009-11-21
A number of languages do most of the memory management for you -- e.g. Java, Python, Perl, Ruby.  It is a feature of these languages that you don't usually have to worry about memory management.

In the C and C++ world, however, the programmer has to manage memory.

An obvious example in C is allocating a block of memory and freeing it when done.

```

void myFunction(void) {
    void * buffer = maloc (sizeof(void*)*10000);
    if ( buffer != NULL) {
         /* do something with buffer */
    }
    
    /* comment the next line and you create a memory leak */
    free(buffer);
}

```

At the OS level, every program has a heap and a stack.  I'd start out by looking at the definition of those.  Then, look at the difference between static and automatic memory.  Look at automatic variables, references and scope.

Kernigan and Richie's book on C explains a lot of this.

---

### Post by ownaginatious on 2009-11-21
That's a low level thing that only more primitive languages like C, C++ and assembly support. Basically what it does is lets you directly access the memory to make space for variables and such. Higher level languages like Java, C# and Visual Basic do it automatically (although arguably not as well).

If you'd like to learn about it, you should look into getting a book or finding a website online to learn C. Pretty much the starting point of memory management is learning about "pointers".

---

### Post by A_Fiachra on 2009-11-21
> **ownaginatious said:**
> That's a low level thing that only more primitive languages like C, C++ and assembly support. Basically what it does is lets you directly access the memory to make space for variables and such. Higher level languages like Java, C# and Visual Basic do it automatically (although arguably not as well).

If you'd like to learn about it, you should look into getting a book or finding a website online to learn C. Pretty much the starting point of memory management is learning about "pointers".


In higher level languages you can still preallocate memory and set objects to be garbage-collected to deal with allocation performance issues.  You can also learn to avoid pitfalls like trying to return local objects from a subroutine, forcing a data structure to keep reallocating memory (instead of preallocating, where possible), passing by reference when called for, invoking garbage collection needlessly, and so forth.

Although C and C++ allow you to natively examine memory by address, they are not the only programming languages that requires insight into memory management.  Consider System.gc and finalize in Java.

---

### Post by matthew.ball on 2009-11-21
> **ownaginatious said:**
> That's a low level thing that only more primitive languages like C, C++ and assembly support. Basically what it does is lets you directly access the memory to make space for variables and such. Higher level languages like Java, C# and Visual Basic do it automatically (although arguably not as well).

If you'd like to learn about it, you should look into getting a book or finding a website online to learn C. Pretty much the starting point of memory management is learning about "pointers".
You can use #unsafe region in C# to use pointers/references I believe, Java probably has some equivalent.

---

### Post by grayrainbow on 2009-11-21
Magic! You can not learn it, it has to be inside you!
You can read how other people do it, with good C book or book on OS kernel design, both are different aspects and one should start with the former.

---

### Post by nvteighen on 2009-11-21
Memory management is what the name itself tells. There are two types: automatic and manual (I lie, there's also semiautomatic, but let's leave that for now). Automatic memory management is what all modern high-level languages do: you don't have to do anything about memory because it's managed by the platform (e.g. Python, Java, C#, Javascript, Perl, Lisp, etc.). Manual memory management makes you explicitly tell the computer what to do with each memory block you allocate.

C and C++ use automatic memory management for stack variables and manual for heap variables (malloc()/new and free()/delete). This gives a lot of optimization power and also allows you to economize memory so you just use what's exactly needed. But, it opens the risk of introducing memory leakage (forgetting to release some memory you don't use anymore or losing the pointer to that region) and also introduces a lot of low-level programming. 

In general, you should avoid manual memory management unless you really need it. In most situations, it's more a cost than a benefit, because you can do exactly the same without worring for those issues by using a higher-level language.

Anyway, you should learn about this if you want to be a programmer.

---

### Post by dwhitney67 on 2009-11-21
One other aspect to memory management has to do with limiting an application to how much memory it can allocate.  There are systems where *requirements* stipulate that no more than, say, 90% of memory on the system can be used.

Regardless of the language one chooses, the memory management problem involves the same features.  The memory manager would pre-allocate one or more pools of memory, from which the rest of the application can obtain memory for its needs, thus negating the need for the application to request additional memory from the OS.

This type of memory management in generally used in embedded systems, thus typically the language chosen would be C and/or C++.  But Java has also been used in embedded systems, so it is conceivable that a Java app can also use a memory manager.

P.S.  I find it hilarious that C/C++ are not considered high-level languages.  How quickly do people forget that in the ol' days, assembly was the low-level language, and that C was considered a high-level language.

Today, C/C++ are still widely used.  Embrace it!

---

### Post by CptPicard on 2009-11-21
These are not the old days anymore, dwhitney, old chap :p

---

### Post by grayrainbow on 2009-11-21
> C and C++ use automatic memory management for stack variables and manual for heap variables (malloc()/new and free()/delete). This gives a lot of optimization power and also allows you to economize memory so you just use what's exactly needed. But, it opens the risk of introducing memory leakage (forgetting to release some memory you don't use anymore or losing the pointer to that region) and also introduces a lot of low-level programming. And every Scheme interpreter is build with this "automatic" stack stuff :D
Just for clarity: malloc/free are functions, new/delete(new[]/delete[]) are C++ operators, that's are two exstreamly different things!



> One other aspect to memory management has to do with limiting an application to how much memory it can allocate. There are systems where requirements stipulate that no more than, say, 90% of memory on the system can be used.
 
 Regardless of the language one chooses, the memory management problem involves the same features. The memory manager would pre-allocate one or more pools of memory, from which the rest of the application can obtain memory for its needs, thus negating the need for the application to request additional memory from the OS.
 
 This type of memory management in generally used in embedded systems, thus typically the language chosen would be C and/or C++. But Java has also been used in embedded systems, so it is conceivable that a Java app can also use a memory manager.
You have that limitation on your PC as well, the kernel can not be swapped out :) And just to add, on embedded systems one may deal directly with physical memory.

> P.S. I find it hilarious that C/C++ are not considered high-level languages. How quickly do people forget that in the ol' days, assembly was the low-level language, and that C was considered a high-level language.
 
 Today, C/C++ are still widely used. Embrace it!
I use C/C++ every day, but I still will call Java/C# high level, every higher level probably script, assembly low level, and C/C++ will call...hm, just C/C++

---

### Post by lisati on 2009-11-21
In a nutshell: Memory management is about managing the use of your computer's memory. 

BTW, in discussing languages and programming environments, don't forget [microcode]("http://en.wikipedia.org/wiki/Microcode"). (Note: I'm thinking of *really* low level programming here, not what some of us here at the forums would refer to as [firmware]("http://en.wikipedia.org/wiki/Firmware"))

---

