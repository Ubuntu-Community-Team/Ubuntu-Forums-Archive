---
title: "Assembly launguage"
date: 2009-04-21
forum: Programming Talk
---

### Post by TCSnyder on 2009-04-21
i am taking assembly launguage class in school and was wondering if there is any way to test/run my code in ubuntu

---

### Post by Zugzwang on 2009-04-21
> **TCSnyder said:**
> i am taking assembly launguage class in school and was wondering if there is any way to test/run my code in ubuntu

It depends. For a more detailed answer, please answer the following questions:

[LIST]
[*]For what processor(s) are you writing code? 
[*]For what operating system (if applicable)? 
[*]Which assembler are you using in class?
[/LIST]

---

### Post by TCSnyder on 2009-04-21
we are writing for .586 architechture
we are not writing operating system specific code, just moving things in and out of memory and doing arithmetic.

if you need more information i will have to look it up

---

### Post by Simian Man on 2009-04-21
If you are writing MIPS code, which is usually taught in Universities, you can use [PCSpim]("http://pages.cs.wisc.edu/~larus/spim.html") to run the code.

You could also do what I do and setup gcc, binutils and libc for your target architecture, but that is much more difficult.

<edit>Nevermind</edit>

---

### Post by Zugzwang on 2009-04-21
> **TCSnyder said:**
> we are writing for .586 architechture
we are not writing operating system specific code, just moving things in and out of memory and doing arithmetic.

if you need more information i will have to look it up

I guess you will also "print" stuff to the console since you will otherwise need a debugger to check if your program does something it should. That's however OS-dependent, again.

Also, there's the real-mode vs. protected-mode issue that might affect you. Look up these terms on Wikipedia, if necessary. 

Finally, assemblers use different syntax for administrative work, which is really a hassle. In effect you might be forced to use precisely the same assembler as in class.

The whole point of this post is to warn you that the answer to your original question is not unlikely to be "no" (unless you're doing Linux assembly in class anyway). For MIPS assembly, as already mentioned, this would not have been a problem, but for X86 assembly, things are quite different in Linux, even if you just write some functions for calling them from C/C++ programs since calling conventions are usually different.

---

### Post by Arndt on 2009-04-21
> **TCSnyder said:**
> i am taking assembly launguage class in school and was wondering if there is any way to test/run my code in ubuntu

These links may be helpful:

[http://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html](http://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html)

[http://en.wikipedia.org/wiki/GNU_Assembler](http://en.wikipedia.org/wiki/GNU_Assembler)

and the program 'as', which perhaps comes with gcc (I have it, but I don't know how it got there). I'm not sure what the difference between 'as' and 'gas' is, maybe just two names for the same thing.

---

### Post by Npl on 2009-04-21
AFAIK as is the unix-equivalent, gas is the GNU-Implementation which is compatible to as.
I also think that as (and cc, make, etc) are required for the POSIX-Standard... which pretty much means the same thing as UNIX-Compatible.

---

