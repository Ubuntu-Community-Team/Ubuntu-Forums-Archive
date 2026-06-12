---
title: "Socket Programming"
date: 2008-02-11
forum: Programming Talk
---

### Post by sammmy101 on 2008-02-11
hi, i m newbie to ubuntu, i want to run a socket program, which requires 
#include<stdio.h>
#include<conio.h>
#include<sys/socket.h>
#include<sys/types.h>
#include <netinet/in.h>
Which deb package is required to run the same?


Thanks in advance
Sam

---

### Post by LaRoza on 2008-02-11
That looks like a Windows program, did you write it? conio.h isn't a standard library.

See the stickies for compiling C programs (moving to programming talk)

---

### Post by sammmy101 on 2008-02-11
Actually, i have written C programs in Borland Turbo C compiler in Windows, but now i m trying it in Ubuntu. i want conio.h so that, i can use "getch()" function so as to see output of the program.

Thanks in advance
Sam

---

### Post by sammmy101 on 2008-02-11
i hav UBUNTU 7.10 live CD, is the software/package present in it, so that after installing it, socket program can be compiled succesfully.
If yes, which package should i install ?

---

### Post by LaRoza on 2008-02-11
> **sammmy101 said:**
> Actually, i have written C programs in Borland Turbo C compiler in Windows, but now i m trying it in Ubuntu. i want conio.h so that, i can use "getch()" function so as to see output of the program.

Thanks in advance
Sam

conio.h isn't a standard header.

You don't need to "see the output of the program", if you run it in a terminal.

You can use getchar() instead if you really want to do that. It is in <stdio.h>

---

### Post by yabbadabbadont on 2008-02-11
conio.h is a dos/windows specific header file.  Try stdio.h instead.

Edit: Doh!  Too slow.

---

### Post by LaRoza on 2008-02-11
> **sammmy101 said:**
> i hav UBUNTU 7.10 live CD, is the software/package present in it, so that after installing it, socket program can be compiled succesfully.
If yes, which package should i install ?

Read the stickies on how to compile a C program (The package is on the CD, I am not sure about the networking specific ones though)

---

