---
title: "compiling a program works if i call it something.cpp, and not if i dont"
date: 2011-03-29
forum: Programming Talk
---

### Post by btf18 on 2011-03-29
hi there

so i have been programming for a while and never managed to really be sure i can compile a perfectly written program. I have found only one way. It was when i use code blocks IDE in windows, and i press f9 to compile and run, and i call it anything.cpp

Now if i do exactly the same thing in code blocks but just call it any filename, without .cpp, it will come up with heaps of errors, the first one being no such file. Why is this?

if i try write and compile in anything but code blocks i can forget it, it wont work. itll say errors

Thanks

ps, compiling is my worst nightmare, i always copy and paste perfect code, please someone reveal the mystery to me so i can focus on the programming. Ive wasted many hours.

EDIT: this is using c++

---

### Post by Barrucadu on 2011-03-29
Can you compile things from a terminal? Perhaps you are missing some development libraries.

---

### Post by MadCow108 on 2011-03-29
your editor is probably trying to use gcc for C++ code.
use g++ for C++ code and your file extension can be whatever you like.

if you are using autotools your stuck with either C, cpp, cc or cxx as extension, because it also uses the extension to determine the compiler and as far as I know that cannot be changed (besides setting CC to g++...)

---

### Post by Some Penguin on 2011-03-29
Read page 20 (section 1.11.16) of the manual.

---

### Post by btf18 on 2011-03-29
sorry what manual? thankyou. 
 
Thanks all

---

### Post by safarin on 2011-03-29
What I understand from your statement, when you rename your file to .cpp extension, you can compile the code (eg: foo.cpp), else you cannot (eg: foo).

I think you know that .cpp, .c, .jar or something like that is the language file. This is how you determine what kind of language you use for your programming. How about compiler? Compiler also need to know what kind of language you want to compile. That why you need to give the compiler the exact file name for the compiler to compile. If the compiler know what kind of language you want to compile. The codeblock will choose the suitable compiler for you (eg: gcc or g++).

Without compiler you need to write machine code for computer to understand what you want to do.. Hahaha.. So compiler is your code translator to computer.

:D

---

### Post by Some Penguin on 2011-03-29
> **btf18 said:**
> sorry what manual? thankyou. 
 
Thanks all

The manual of the IDE you're using.  Documentation is written for a reason.

[http://www.codeblocks.org/docs/manual_en.pdf]("http://www.codeblocks.org/docs/manual_en.pdf")

---

### Post by btf18 on 2011-03-29
O real? I thought it was written subconsciously..

---

### Post by 102jon on 2011-03-30
The file extension has to be .cpp. What's the problem if it's not?

---

### Post by slavik on 2011-03-30
Did you bother to read the stickied threads? They are there for a reason. :)

---

### Post by btf18 on 2011-04-01
God no. I have better things to do with my life than read endless pages about compiling this early on in my programming education, when im compiling fine every time in code::blocks and want to learn C++ which requires enough time and effort. This was just out of interest.

---

### Post by slavik on 2011-04-01
then you clearly have better things to do than to learn how to properly program.

---

### Post by btf18 on 2011-04-01
Actually dude, im doing an ICT degree, and its been postponed because of a massive earthquake, it started in february this year and the quake happened on the second day of the degree, 180 people died, and the course will now start this monday in a new campus, and i have been learning bash and reading books on programming to get ahead before we have even started the programming material or started the degree. I think im committed. Thread is solved. Move along.

---

