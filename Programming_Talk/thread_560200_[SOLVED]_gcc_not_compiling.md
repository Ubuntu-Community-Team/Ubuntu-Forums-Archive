---
title: "[SOLVED] gcc not compiling"
date: 2007-09-26
forum: Programming Talk
---

### Post by bskafh on 2007-09-26
hi i am trying to compile a simple C program using the "gcc filename.c" command, and i am getting this error:

hello.c:1:20: error:  stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
hello.c:4: warning: return type of ‘main’ is not ‘int’

i ttried re-installing gcc, and after going over some of the posts, i re-installed the "build-essential" library. and i am still getting the same error. please any help!

---

### Post by dwhitney67 on 2007-09-26
It might help if you posted your code.  I presume you are including stdio.h using the following syntax:
[FONT="Courier New"]
#include <stdio.h>[/FONT]

Some folks make a newbie error and in lieu of the <> for system include files, they use "" (double-quotes).

---

### Post by bskafh on 2007-09-26
#include <stdio.h>

void main()
{
    printf("\nHello World\n");
    
}

here is the code. i can also find the stdio library in /usr/include.

---

### Post by Compyx on 2007-09-26
> **bskafh said:**
> #include <stdio.h>

void main()
{
    printf("\nHello World\n");
    
}

here is the code. i can also find the stdio library in /usr/include.

First of all, main() returns int, say so. If you declare main() to take no arguments, be explicit about it.

So:
```

#include <stdio.h>

int main(void)
{
    printf("\nHello World!\n");
    return 0;
}

```

But apart from those errors, it should compile and not complain about a missing stdio.h.

What kind of editor did you use? Perhaps you've somehow saved the file in a character-set GCC doesn't recognize?

---

### Post by bskafh on 2007-09-26
it did work! i am new to C but i dont understand what does the stdio.h library have to do with that? well thanks a lot anyway

---

### Post by dwhitney67 on 2007-09-26
The stdio.h is not a library; it is a header file that provides function prototypes and other definitions that are common for standard input, output, and error related I/O.

I could very well be wrong, but I believe the library that does provide the implementation of printf() and other functions is in /lib/libc.so.6.

Btw, I have to ask:

I tried to compile the exact code you posted.  I received a warning about the main() function not being declared to return an "int", just as Compyx pointed out.

However, I did not have any problems referencing stdio.h.  Did you by chance change your code before posting it, or perform some other step to acquire the development tools (i.e. apt-get install build-essential)?

---

### Post by Compyx on 2007-09-26
The stdio library contains, amongst many others, the printf() function. It's a variadic function, that is: it takes an unspecified number of arguments. When you don't #include <stdio.h> the compiler assumes printf() takes a const char *, since you've passed a string literal. At the same time, the compiler is smart enough to know that prototype is incompatible with the actual prototype of printf() declared in stdio.h, which is:
```

int printf(const char *format, ...)

```

I suggest you get a good book on C: "The C Programming Language, Second Edition", by Brian W. Kernighan and Dennis M. Ritchie, commonly referred to by programmers as 'K&R2'.

Don't try to learn C from reading tutorials on the web, nearly all of them are horrible (such as the abomination 'void main()' which is an error in a hosted environment).

HTH.

---

### Post by LaRoza on 2007-09-26
> **Compyx said:**
> 
Don't try to learn C from reading tutorials on the web, nearly all of them are horrible (such as the abomination 'void main()' which is an error in a hosted environment).


Some are good, most are free. I have attempted to gather the most useful tutorials in my wiki. Also, there are free books and software.

---

### Post by bskafh on 2007-09-26
well anyways, thanks a lot guys.

---

