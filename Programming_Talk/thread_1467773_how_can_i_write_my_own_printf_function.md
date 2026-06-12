---
title: "how can i write my own printf function?"
date: 2010-05-01
forum: Programming Talk
---

### Post by Max Destruction on 2010-05-01
hey all, im a new programmer.

i was wondering how you would go about writing the printf function  yourself? it is my understanding that when you call printf you are  calling an already written function and just providing an argument? if  this is the case, is it possible to write that function yourself with  just the bare primitives of the language? i only want to know because i  am curious about how things like that work.

---

### Post by soltanis on 2010-05-01
You can. It wouldn't be my idea of fun. But you can.

You should look into handling variable arguments with the C language.

Try man 3 stdarg.

---

### Post by Max Destruction on 2010-05-01
cool i'll do that now.

i considered having a look for the function itself in the libraries but found all .a files and .o files ..binaries. apparently the gcc compiler is written mostly in c so most like lt all these built in functions are too. i could go scavenge through the gcc source but i wouldn't even know what i was looking at. :D

---

### Post by soltanis on 2010-05-01
As they are the spawn of Stallman, you can of course get the source code (wohoo free software) but yes, it wouldn't be very clear what you were looking at.

Basically, it's complicated. It involves some assembler, some calls to the operating system, all of which I don't think serve the purpose of why you would want to do this, which is build a function which parses a variable number of arguments intelligently. If your aim is instead to explore how C function calls are made in machine language or how the standard library talks to the Linux kernel, you should look at the source.

---

### Post by Max Destruction on 2010-05-01
indeed. i've got ahold of the gcc source. hopefully Stallman has commented it well enough to give me some clues. At least he didnt write it in lisp :p

---

### Post by MadCow108 on 2010-05-01
do you want to write your own output function from scratch?
consider writing a *puts* first.
It is basically output without all the features of printf. But the output primitives (from the kernel) will be the same.

printf is not so simple as it requires variadiac macros and/or compiler builtins in addition to the handling of system calls to get output.
see the old deprecated varargs header, the C99 stdarg header and the __builtin_va_* functions of gcc
thanks to the builtins printf is typesafe in gcc, which is unusual for variadic functions in C (and not required by the standard)

if you only want to just make a personal printf use the vprintf functions which work directly on stdarg's va_list's
man vprintf
man stdarg

---

### Post by nvteighen on 2010-05-01
You're looking at the wrong place. printf is implemented in the GNU C Standard Library (libc.so), not gcc.

The issue is that printf is actually a call to fprintf using stdout as its file. So, what you need is fprintf... No, fprintf uses vfprintf... and then the issue is how Linux creates the standard outputting "file" (this is part of the OS), whose file descriptor is 1, and how the C Standard Library takes access to that "file" and names it "stdout". So, added to the hard problem of implementing how to write to a file, you've got the issue of a very special file used for piping output (be also aware that stdout can be redirected to a file using the > operator in shell!).

Take a look at man stdio (install manpages-dev to get the development manpages). There you'll see the issue is not that much how fprintf/printf works, but rather what stdout is.

---

### Post by Max Destruction on 2010-05-01
> **MadCow108 said:**
> do you want to write your own output function  from scratch?
consider writing a *puts* first.
It is basically output without all the features of printf. But the  output primitives (from the kernel) will be the same.

printf is not so simple as it requires variadiac macros and/or compiler  builtins in addition to the handling of system calls to get output.
see the old deprecated varargs header, the C99 stdarg header and the  __builtin_va_* functions of gcc
thanks to the builtins printf is typesafe in gcc, which is unusual for  variadic functions in C (and not required by the standard)

if you only want to just make a personal printf use the vprintf  functions which work directly on stdarg's va_list's
man vprintf
man stdarg


thank you that is what id almost worked out myself - that a puts function is way simpler.
i didnt think about all the floating point arithmetic and such that would have to be built into printf ..gonna be some pretty complex code. i did find some source-code for a "small" version, but it still has a dependency - putchar. i just wanna get my head around writing code without delegating to other functions. really im just looking for a function that will output a string...

---

### Post by Max Destruction on 2010-05-01
> **nvteighen said:**
> You're looking at the wrong place. printf is implemented in the GNU C Standard Library (libc.so), not gcc.

The issue is that printf is actually a call to fprintf using stdout as its file. So, what you need is fprintf... No, fprintf uses vfprintf... and then the issue is how Linux creates the standard outputting "file" (this is part of the OS), whose file descriptor is 1, and how the C Standard Library takes access to that "file" and names it "stdout". So, added to the hard problem of implementing how to write to a file, you've got the issue of a very special file used for piping output (be also aware that stdout can be redirected to a file using the > operator in shell!).

Take a look at man stdio (install manpages-dev to get the development manpages). There you'll see the issue is not that much how fprintf/printf works, but rather what stdout is.

hmmm. ok! :D

---

### Post by nvteighen on 2010-05-01
> **Max Destruction said:**
> hmmm. ok! :D

Without having looked to the code, I guess all the C Std. Library does is to interpret the format string and send it to the file. How that file responds and how writing to a file is implemented is the OS's issue.

---

### Post by Max Destruction on 2010-05-01
I found this ... but it still uses two #includes so it kinda defeats the intellectual purpose of the exercise but i think i understand that an ellipsis is used for a variable number of arguments 

```
#include <stdio.h>
#include <stdarg.h>

char *convert(unsigned int, int);

main()
{
void myprintf(char *,...);
char * convert(unsigned int, int);
int i=65;
char str[]="not printed with printf :D";
myprintf("\nMessage = %s%d%x",str,i,i);
}

void myprintf(char * frmt,...)
{
char *p;
int i;
unsigned u;
char *s;
va_list argp;
va_start(argp, frmt);
p=frmt;
for(p=frmt; *p!='\0';p++)
{
if(*p!='%')
{
putchar(*p);continue;
}
p++;
switch(*p)
{
case 'c' : i=va_arg(argp,int);putchar(i);break;
case 'd' : i=va_arg(argp,int);
if(i<0){i=-i;putchar('-');}puts(convert(i,10));break;
case 'o': i=va_arg(argp,unsigned int); puts(convert(i,8));break;
case 's': s=va_arg(argp,char *); puts(s); break;
case 'u': u=va_arg(argp, unsigned int); puts(convert(u,10));break;
case 'x': u=va_arg(argp, unsigned int); puts(convert(u,16));break;
case '%': putchar('%');break;
}
}
va_end(argp);
}
char *convert(unsigned int num, int base)
{
static char buff[33];
char *ptr;
ptr=&buff[sizeof(buff)-1];
*ptr='\0';
do
{
*--ptr="0123456789abcdef"[num%base];
num/=base;
}while(num!=0);
return(ptr);
} 
```

---

### Post by Justin Thunder on 2010-05-02
so.... you want your own printf function from the ground?

then try assembly.
it can`t be that hard.

Read arguments from the stack.
Build string.
Call the right interruption.

just a thought..... im a newbie too, so im not very sure if im right.

---

### Post by Jesdisciple on 2010-05-02
> **Justin Thunder said:**
> then try assembly.
it can`t be that hard.O.O  I've never written assembly, but I have seen it (refer to Wikipedia) and I think your second statement above is way off the mark.

---

### Post by phrostbyte on 2010-05-02
By default, all C code you compile with gcc links to the C Standard Library, also known as libc.

You can build C applications without linking to libc. You will lose the ability to use standard C functions (including printf). In addition malloc/free and other important functions are implemented in libc, so say goodbye to that.

You can however still use syscalls (direct calls to the kernel), but without libc you have write the required assembly code to initiate a software interrupt, this is a free service you lose out on if you don't use libc.

There is some advantages of not using libc, namely a smaller binary size, but it's nothing major. It's worth noting that libc gets pumped into memory very early on in the boot process, so not linking to it isn't going to save you any memory unless you have  already been working down to the metal (eg: embedded OS).

For info on not linking to libc:
[http://blog.ksplice.com/2010/03/libc-free-world/](http://blog.ksplice.com/2010/03/libc-free-world/)

printf uses the varadic function contracts to allow a function with variable parameters. It has access to some kind of parser to understand the format string. The syscall it uses in the backend is probably some call to write() or a variant thereof. If you are interested in this kind of stuff download the source code for the glibc. If you are interested in syscalls download the Linux kernel source code.

Good luck. :D

---

### Post by soltanis on 2010-05-03
I think the OP was talking about implementing a varargs function that interpreted the format string. As I said before, he's barking up the wrong tree if he wants to understand the internals behind the actual I/O operation.

If it's just implementing a variadic function then stdarg is the ticket. If it's rewriting a kernel, well, he better get started.

---

