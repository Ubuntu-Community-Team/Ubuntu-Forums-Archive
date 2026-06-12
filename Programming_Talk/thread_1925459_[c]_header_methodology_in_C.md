---
title: "[c] header methodology in C"
date: 2012-02-14
forum: Programming Talk
---

### Post by PeterP24 on 2012-02-14
Hello,

I am reading a book about introduction in C. I have a question about headers. At some point, the author give some hints about using header files in order to contain only function prototypes while the function definition is contained in another file, with the same name as the header but with extension .c instead of .h. More specifically, there are 3 files like so:

```
/*header.h*/
void fct(int i);
```

```
/*header.c*/
void fct(int i)
{
   printf("Was here:> your number is %d", i);
}
```

```
/*main.c*/
#include "header.h"

int main(void)
{
   int i=2;
   fct(i);
   return 0;
}
```

The problem with the above code is that the compiler complains that it cannot see the fct function from header.c, unless I insert a #include "header.c" line in header.h.
My question is - is it a way to use the code as it is and to avoid inclusion of header.c in header.h or main.c? Maybe some option passed to compiler in order for the compiler to see the definition of fct in the header.c file? I think it would be neat for the header.h file to contain only function prototypes and no #include directives.

---

### Post by Arndt on 2012-02-14
> **PeterP24 said:**
> Hello,

I am reading a book about introduction in C. I have a question about headers. At some point, the author give some hints about using header files in order to contain only function prototypes while the function definition is contained in another file, with the same name as the header but with extension .c instead of .h. More specifically, there are 3 files like so:

```
/*header.h*/
void fct(int i);
```

```
/*header.c*/
void fct(int i)
{
   printf("Was here:> your number is %d", i);
}
```

```
/*main.c*/
#include "header.h"

int main(void)
{
   int i=2;
   fct(i);
   return 0;
}
```

The problem with the above code is that the compiler complains that it cannot see the fct function from header.c, unless I insert a #include "header.c" line in header.h.
My question is - is it a way to use the code as it is and to avoid inclusion of header.c in header.h or main.c? Maybe some option passed to compiler in order for the compiler to see the definition of fct in the header.c file? I think it would be neat for the header.h file to contain only function prototypes and no #include directives.

What commands do you use for compiling and linking the program? You are right in that h files are not supposed to include c files.

gcc -o program main.c header.c

ought to work.

---

### Post by PeterP24 on 2012-02-14
:p it works - just what I wanted. I use Code::Blocks IDE - I don't know where the compiler and linker commands are given inside the IDE - but right now I'll put aside Code::Blocks and work with gcc at the command line. 

Please tell me - why does it work? The header.c it is not included in main.c (header.h is) and header.c does not appear to be compiled as a library than linked sometime in the compilation/linking process. So how does the compiler figure it out that the header.c contains fct?

---

### Post by Arndt on 2012-02-14
> **PeterP24 said:**
> :p it works - just what I wanted. I use Code::Blocks IDE - I don't know where the compiler and linker commands are given inside the IDE - but right now I'll put aside Code::Blocks and work with gcc at the command line. 

Please tell me - why does it work? The header.c it is not included in main.c (header.h is) and header.c does not appear to be compiled as a library than linked sometime in the compilation/linking process. So how does the compiler figure it out that the header.c contains fct?

The compiler compiles both files, and then links them. The command is equivalent to

gcc -c header.c
gcc -c main.c
gcc -o program main.o header.o

The first two lines produce header.o and main.o, respectively. You could now put header.o into a library if you wanted, but that's only a detour when you know that header.o will be needed.

The compiler (or rather, linker, in this role), looks in main.o for undefined symbols, find 'fct', then looks in the next .o file, and finds 'fct' there, so everything is fine.

What happens when you link with a library is essentially the same as listing all the object files of the library on the command line, except that only those files that are actually needed will be used.

In this three-command form I gave now, you will have header.o and main.o afterwards. In the first form, they are maybe removed after use, I'm not sure. In bigger projects, it's a good thing to cut up the building in small parts, so you don't need to recompile everything because only one file was changed.

So I suggest you learn about makefiles next, they help with this.

---

### Post by Arndt on 2012-02-14
I forgot to mention: it's very common for h files to include other h files. For example if foo.h defined the function Foo with the prototype

void Foo(struct Bar *);

and bar.h defined what struct Bar is, it is usual to find

#include bar.h

at the top of foo.h

---

### Post by PeterP24 on 2012-02-14
Thank you - it is clear now!

---

### Post by trent.josephsen on 2012-02-14
If you aren't already, you should be #including header.h in header.c -- not the other way around -- so that you can be sure that if you make any prototype mismatches they'll be caught at compile time.

---

### Post by PeterP24 on 2012-02-14
@trent.josephsen

I don't understand. In the context of the code from the first post, if I include header.h in both main.c and header.c wouldn't that be a problem (since it is included twice)? Or maybe you meant to include header.h in header.c and header.c in main.c?

---

### Post by muteXe on 2012-02-14
You  can stop multiple inclusion with a header guard:
[http://en.wikipedia.org/wiki/Include_guard](http://en.wikipedia.org/wiki/Include_guard)

---

### Post by gateway67 on 2012-02-14
> **PeterP24 said:**
>  In the context of the code from the first post, if I include header.h in both main.c and header.c wouldn't that be a problem...
No, that would not be a problem.  In fact, that is what was suggested, instead of including header.c from within header.h.

Rule of thumb... don't include .c files, only .h files.

Also, you should get into the habit of coding the appropriate pre-processor macros within header files to prevent multiple inclusion.  For example:
```

#ifndef HEADER_H
#define HEADER_H

void fct(int i);

#endif

```

Back to the post describing a situation where you have a Bar.h, imagine if two header files, A.h and B.h both included this file.  In turn, the file with the main() function included both A.h and B.h.  The pre-processor macros would prevent Bar.h from being included twice, thus mitigating the chance of having multiple declarations found.

---

### Post by PeterP24 on 2012-02-14
After reading this thread, I have to clarify something and ask a new question. I said in the first post that I included header.c in header.h only because it didn't compile. It was a beginner workaround. Arndt clarified that I should not do that and offered me an alternative solution. I don't include header.c in header.h anymore. 

I have to ask you - which solution is considered best practice? The one offered by Arndt (in which header.h is not included in header.c) or the one in which header.h is included in both header.c and main.c? Sorry for the being insistent but as I said before, the book I am following only hints at this stuff.

---

### Post by Bachstelze on 2012-02-14
It's a good idea to include it in both files, so that the compiler will warn you if protoypes of the function in your header and source files don't match.

---

### Post by Arndt on 2012-02-15
> **PeterP24 said:**
> After reading this thread, I have to clarify something and ask a new question. I said in the first post that I included header.c in header.h only because it didn't compile. It was a beginner workaround. Arndt clarified that I should not do that and offered me an alternative solution. I don't include header.c in header.h anymore. 

I have to ask you - which solution is considered best practice? The one offered by Arndt (in which header.h is not included in header.c) or the one in which header.h is included in both header.c and main.c? Sorry for the being insistent but as I said before, the book I am following only hints at this stuff.

In both files, yes. What I meant was that header.c should not be included anywhere.

---

