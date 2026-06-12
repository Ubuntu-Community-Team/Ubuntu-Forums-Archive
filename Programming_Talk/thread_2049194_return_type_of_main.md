---
title: "return type of main"
date: 2012-08-28
forum: Programming Talk
---

### Post by IAMTubby on 2012-08-28
1.I've heard that
```
int main(void)
```
is the best way to start main.

So that means that my program returns an integer to gcc ?
Am I returning to gcc ? That's my first question.

2.What does gcc do with these return values.
We normally return 0, 1, -1 right? 
So on what basis does it decide successful/failure of program ?

3.I tried doing
```
int main(float a)
```
just for experimenting, and it still doesn't throw any error.
```
#include <stdio.h>

int main(float a)
{
 printf("\nHello world ");
 printf("%f",a);

 return 0;
}

```
Does it mean that the gcc is implemented such that it can pass variable number of arguments to a program ?

---

### Post by MG&amp;TL on 2012-08-28
> 1.I've heard that
```
int main(void)
```is the best way to start main.
That is *one* way to start main.

> So that means that my program returns an integer to gcc ?No, it's returning a value to the operating system.

> Am I returning to gcc ? That's my first question.GCC's just a compiler. It doesn't have anything to do with actually running the program.

> 2.What does gcc do with these return values.
We normally return 0, 1, -1 right? 
So on what basis does it decide successful/failure of program ?GCC doesn't actually do anything with them...you can return any value, but returning 0 is considered a 'successful' program.

> 3.I tried doing
```
int main(float a)
```just for experimenting, and it still doesn't throw any error.You can pass any variable to main, but normally you'd use:

```
int main(int argc, char **argv)
```so you can use the arguments passed to your program.

> Does it mean that the gcc is implemented such that it can pass variable number of arguments to a program ?Err, not GCC, but yes, you can pass arguments to a program.

---

### Post by spjackson on 2012-08-28
> **IAMTubby said:**
> 
2.What does gcc do with these return values.
We normally return 0, 1, -1 right? 
So on what basis does it decide successful/failure of program ?

The C99 Standard only defines 0, EXIT_SUCCESS and EXIT_FAILURE. Any other value returned from main is implementation defined, i.e. it depends on your compiler and operating system. For gcc on Linux, this effectively means values in the range 0-255. Returning -1 from main is usually a mistake by the programmer.

> 
```
int main(float a)
```just for experimenting, and it still doesn't throw any error.
If you compile with gcc -Wall or gcc -pedantic then you get warnings about this. The C99 standard says
```

int main(void) { /* ... */ }
or
int main(int argc, char *argv[]) { /* ... */ }
or "some other implementation-defined manner."

```

---

### Post by Bachstelze on 2012-08-28
> **spjackson said:**
> The C99 Standard only defines 0, EXIT_SUCCESS and EXIT_FAILURE. Any other value returned from main is implementation defined, i.e. it depends on your compiler and operating system.

What do you mean by that? A value cannot be "implementation-defined", it is what it is. If I return 2 from main, then I will return 2. What is implementation-defined is what the calling process does when it encounters this value, and of course it is, because it has nothing to do with the C language and is thus outside the scope of the C standard. Heck, I could even write a program that considers EXIT_SUCCESS a failure, and I would only violate convention, not a standard.

---

### Post by IAMTubby on 2012-08-28
Sir,
so do all non-negative values come under success ? Just trying to make a pattern.
Will you be able to tell me how it classifies the return values as success/failure.

And although MG&TL has already cleared above, I would like to hear from you as to who receives the return value from a program ? -GCC ? OS ?

Thanks.

---

### Post by Bachstelze on 2012-08-28
> **IAMTubby said:**
> Sir,
so do all non-negative values come under success ? Just trying to make a pattern.
Will you be able to tell me how it classifies the return values as success/failure.

As spjackson said, the values returnes from main() on Linux (and all POSIX systems) are in the range 0-255. There is no negative values. The convention is that 0 indicates success and anything else indicates failure, but this is not an absolute rule. There are a lot of examples of applications that will return some non-zero value even in case of success (for example, if there were warnings). Normally, it should be documented in the program's manual page or other documentation.


> And although MG&TL has already cleared above, I would like to hear from you as to who receives the return value from a program ? -GCC ? OS ?

It is implementation-defined. On POSIX, it is returned to the parent process (via the wait() system call). If you run a program from a shell, this means the shell, and you can access it with the ? special variable:

```
firas@aoba ~ % ls foo*
zsh: no matches found: foo*
firas@aoba ~ % echo $?
1

```

Note the non-zero code, which in this case indicates failure, as is conventional.

---

### Post by spjackson on 2012-08-28
> **Bachstelze said:**
> What do you mean by that? A value cannot be "implementation-defined", it is what it is. If I return 2 from main, then I will return 2. What is implementation-defined is what the operating system does when it encounters this value, and of course it is, because it has nothing to do with the C language and is thus outside the scope of the C standard. Heck, I could even write an OS that considers EXIT_SUCCESS a failure, and I would only violate convention, not a standard.
What I mean by that is that a return from main is equivalent to a call to exit() and
the status passed to exit is defined thus:

ISO/IEC 9899:1999 (E), 7.20.4.3 The exit function, Paragraph 5
"Finally, control is returned to the host environment. If the value of status is zero or
EXIT_SUCCESS, an implementation-defined form of the status successful termination is
returned. If the value of status is EXIT_FAILURE, an implementation-defined form
of the status unsuccessful termination is returned. Otherwise the status returned is
implementation-defined."

There is no guarantee from the standard that 2 returned from main will be returned as 2 to the operating system. However, an implementation may make that guarantee. As I understand it on Linux (and most Unixes probably), the least significant 8 bits of the status argument is passed to the OS as the exit status.

---

### Post by IAMTubby on 2012-08-28
> **Bachstelze said:**
> As spjackson said, the values returnes from main() on Linux (and all POSIX systems) are in the range 0-255. There is no negative values. The convention is that 0 indicates success and anything else indicates failure, but this is not an absolute rule. There are a lot of examples of applications that will return some non-zero value even in case of success (for example, if there were warnings). Normally, it should be documented in the program's manual page or other documentation.




It is implementation-defined. On POSIX, it is returned to the parent process (via the wait() system call). If you run a program from a shell, this means the shell, and you can access it with the ? special variable:

```
firas@aoba ~ % ls foo*
zsh: no matches found: foo*
firas@aoba ~ % echo $?
1

```

Note the non-zero code, which in this case indicates failure, as is conventional.
Thank you so much for this example. I tried it out and was really helpful.
Just a small query : Why does it return 1 for you and 2 for me on failure. Does that vary from system-to-system ?

---

### Post by Bachstelze on 2012-08-28
Because there are different kinds of failure. ;) As I said, it should be documented in the manual page. Indeed, [font=monospace]man ls[/font] says:

```
   Exit status:
       0      if OK,

       1      if minor problems (e.g., cannot access subdirectory),

       2      if serious trouble (e.g., cannot access command-line argument).

```

Sometimes there are a lot of possible exit codes (see [font=monospace]man e2fsck[/font]).

---

### Post by IAMTubby on 2012-08-28
Thank you, it's now clear.
Can I wait for some time, ponder about it, and then mark the thread as solved tomorrow ? (It's night in this part of the world)

1 more question : 
Is there a possibility that I, ls something that causes ls to stop working(instead of handling it and returning 1 or 2 like in the example above). In that case, what does it return ?

---

### Post by Bachstelze on 2012-08-28
It depends what you mean by "stop working". In general, a process never "stops working". The only case where it can look like it does is when it is stuck in an infinite loop, or it makes a system call that for some reason keeps blocking. In that case it will never exit, and you will never get your shel back. Try for example

```
sleep 10
```

and imagine that instead of exiting after 10 seconds, it never does.

---

### Post by IAMTubby on 2012-08-28
Okay. I mean something like a Segmentation Fault.
Suppose a string that I pass results in a Segmentation Fault to ls, what would the return value be ?

That's like an unhandled case right ?

---

### Post by MG&amp;TL on 2012-08-28
> **IAMTubby said:**
> Okay. I mean something like a Segmentation Fault.
Suppose a string that I pass results in a Segmentation Fault to ls, what would the return value be ?

That's like an unhandled case right ?

Nope, someone else's program cleans up your program's mess. :)

[http://www.slac.stanford.edu/BFROOT/www/Computing/Environment/Tools/Batch/exitcode.html](http://www.slac.stanford.edu/BFROOT/www/Computing/Environment/Tools/Batch/exitcode.html)

---

### Post by IAMTubby on 2012-08-28
MG&TL,
Thanks for that. Shall go through the document and reply. But I kind of get what you are trying to tell me even without going through the document.

---

### Post by Bachstelze on 2012-08-28
> **IAMTubby said:**
> Okay. I mean something like a Segmentation Fault.
Suppose a string that I pass results in a Segmentation Fault to ls, what would the return value be ?

That's like an unhandled case right ?

You could have tested that yourself. ;)

```
firas@aoba ~ % cat test.c 
int main(void)
{
        char t[50];
        int i=0;
        for (;;) {
                t[i++] = 0;
        }
}
firas@aoba ~ % gcc -o test test.c
firas@aoba ~ % ./test 
zsh: segmentation fault (core dumped)  ./test
firas@aoba ~ % echo $?
139

```

It's probably OS-dependent though.

---

