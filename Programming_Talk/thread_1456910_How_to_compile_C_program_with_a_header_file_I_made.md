---
title: "How to compile C program with a header file I made?"
date: 2010-04-17
forum: Programming Talk
---

### Post by rchan0021 on 2010-04-17
Hey all, how would I compile a C program I made which includes a header file I also made.

when I use,  gcc -o myprogram myprogram.c

it can't find any of the functions I defined in the header file.



Thanks so much!

---

### Post by renkinjutsu on 2010-04-17
I'm no programmer, but i've had a fair share of trying to get unmaintained programs to compile on my machine..

i think you can include it by putting ```
include headerfile.h
``` in your code and putting the header file in the same directory

---

### Post by rchan0021 on 2010-04-17
That's how I have it set up now, hasn't been working.



Thanks for the reply though.

---

### Post by pconroy on 2010-04-17
The syntax is

#include "myheader.h"
#include <system_header_like_stdio.h>

If it still cannot find your header file, something is odd.
Make sure your *in* the directory where your .c and .h files are.

Last resort pass "-I/home/me/mydir/" into gcc to specify the location of the header file.

---

### Post by rchan0021 on 2010-04-17
I think my Ubuntu is just broken, none of the methods are working. I'm going just a little bonkers here, I'm trying to finish up my project, and this problem has had me stuck for 2 hours now.

Gaahhh lol....


Someone please help.

---

### Post by pconroy on 2010-04-17
Start with the basics:
Can you compile and run helloworld?
#include <stdio.h>
int main (int argc, char *argv[])
{
   put( "It works!" );
}

Are you using an IDE or straight gcc?

---

### Post by rchan0021 on 2010-04-17
Yes, HelloWorld compiles and runs, and I am using just gcc, no IDE.

---

### Post by Some Penguin on 2010-04-17
Might want to clarify whether the functions declared in the header file are actually defined in 'myprogram.c' or whether they're defined somewhere else.  Also, actual error messages might be useful.

---

### Post by pconroy on 2010-04-18
> **Some Penguin said:**
> Might want to clarify whether the functions declared in the header file are actually defined in 'myprogram.c' or whether they're defined somewhere else.  Also, actual error messages might be useful.


I agree - post the .c and .h files.
along with the output of gcc.

---

