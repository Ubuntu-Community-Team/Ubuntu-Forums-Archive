---
title: "Can't compile code in linux"
date: 2010-03-07
forum: Programming Talk
---

### Post by fasoulas on 2010-03-07
i have a problem compiling a very simple c++ in linux.

Basically i have written ,compiled and run the program in Microsoft visual studio 2008 and it runs flawlessly but the same code on linux doesn't compile.

I tried with geany , codeblocks and the command line but i get the same error every time

the program is consisted by 3 files the main.cpp math.h and math.cpp
the main.cpp is the file tha includes the main function

i get this when i try to compile main.cpp
main.cpp:(.text+0xa): undefined reference to `menu()'
main.cpp:(.text+0x83): undefined reference to `square_of_number(double)'
main.cpp:(.text+0xfe): undefined reference to `sum_of_numbers(double, double)'
main.cpp:(.text+0x179): undefined reference to `product_of_numbers(double, double)'

and this when i try to compile math.cpp
start.S:115: undefined reference to `main'

---

### Post by lisati on 2010-03-07
Are you able to show us some code?
If you do, put [noparse]```
[/noparse] at the start and [noparse]
```[/noparse] at the end

---

### Post by Sim &amp; Co. on 2010-03-07
```
g++ main.cpp math.h math.cpp -o main
```

-- or simply add an include statement in main.cpp.

---

### Post by fasoulas on 2010-03-07
> **Sim & Co. said:**
> ```
g++ main.cpp math.h math.cpp -o main
```

-- or simply add an include statement in main.cpp.

if i put this in terminal it doesn't show the error messages,what does this mean? How can i run the program to see if it works?

Sorry if i make a lot of questions but i mainly program on visual studio but i also want to learn on linux

By the way thanks both for replying

---

### Post by Sim &amp; Co. on 2010-03-07
No error messages - possible ( most of the bugs doesn't show off just like that ) success.

```
./main
```

** Execute it from the directory you were in when you compiled your application.

---

### Post by fasoulas on 2010-03-07
> **Sim & Co. said:**
> No error messages - possible ( most of the bugs doesn't show off just like that ) success.

```
./main
```

** Execute it from the directory you were in when you compiled your application.

It worked.Thanks a lot

But do you know a way to do this in geany?

---

### Post by Sim &amp; Co. on 2010-03-07
> **fasoulas said:**
> It worked.Thanks a lot

But do you know a way to do this in geany?

[Wikipedia]("http://en.wikipedia.org/wiki/Header_file") know how to :)

---

### Post by fasoulas on 2010-03-07
> **Sim & Co. said:**
> [Wikipedia]("http://en.wikipedia.org/wiki/Header_file") know how to :)

OK i will search and find.

thanks again

---

### Post by MadCow108 on 2010-03-07
A header file won't solve the linking problem
undefined reference is an error in the linking stage, not the compile stage.

What the compiler did in Sim's line is following:
gcc -c math.cpp -o math.o //compile math.cpp to object file
gcc -c main.cpp -o main.o //compile main.cpp to object file
gcc main.o math.o -o math // link main.o and math.o to math executable


so far I know geany has no (yet) got a good way to do this without makefiles.
A makefile is a file containing all the build rules executed with the command make
[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

---

### Post by Sim &amp; Co. on 2010-03-07
> **fasoulas said:**
> OK i will search and find.

thanks again

What are you going to search for ? The link points to a specific section and all you need to do is read and understand it :p

---

### Post by MadCow108 on 2010-03-07
unfortunately you're leading him at the wrong track
the above errors have nothing to do with header files

---

### Post by fasoulas on 2010-03-07
> **MadCow108 said:**
> A header file won't solve the linking problem
undefined reference is an error in the linking stage, not the compile stage.

What the compiler did in Sim's line is following:
gcc -c math.cpp -o math.o //compile math.cpp to object file
gcc -c main.cpp -o main.o //compile main.cpp to object file
gcc main.o math.o -o math // link main.o and math.o to math executable


so far I know geany has no (yet) got a good way to do this without makefiles.
A makefile is a file containing all the build rules executed with the command make
[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

i am using header files because of a programming course i am currently taking at university.

The exersice i had to do was mainly for windows but i tried compiling the code on linux just to learn, and i don't really know what a makefile is,but i will try to learn

---

### Post by fasoulas on 2010-03-07
Can you suggest another linux IDE that can help,except the command line?

---

### Post by MadCow108 on 2010-03-07
> **fasoulas said:**
> i am using header files because of a programming course i am currently taking at university.

The exersice i had to do was mainly for windows but i tried compiling the code on linux just to learn, and i don't really know what a makefile is,but i will try to learn

this is the advantage of the command line.
IDE's hide how the process of building a program actually works.
Using the command line teaches you a lot about that.

Of course it can be debatable if this knowledge is useful when you have a professional IDE at your disposal which handles all that for you.
I personally consider it something one should at least have a look at especially if you want to develop in linux.
It also helps a lot when something in the IDE does not work how its supposed to work.

I have little experience with free linux IDE's but the most suggested are Netbeans, Eclipse and code::blocks but as all more complex IDE's they have a bit of a learning curve.
I mostly use geany for its simplicity and speed or just the editor vim for quick hacking.

---

### Post by matthew.ball on 2010-03-07
> **fasoulas said:**
> Can you suggest another linux IDE that can help,except the command line?
Honestly, why are people so scared of the command line?

Most IDEs just hide their compilation, but they are all working at the command line. The debugging too.
As a user, the difference is we're given this in a widget as opposed to white text on a black background (or whatever colour scheme you're using).

It just means we'll probably have to read a bit more. But really, if we're interested in software development, we won't get far if we're not willing to read much, we could consider it training for later.

Just as MadCow has said, I honestly feel programmers should start with the command line first - I'm not saying IDEs are useless; quite the opposite in fact.
But it's important to understand what it is an IDE is doing.

I would strongly suggest using Emacs. Learn gdb, and learn about Makefiles too. I wouldn't recommend these unless there was a reason to use them.

There's a learning curve to using the above tools - and I don't mention this to scare you off, but rather so you'll keep at it. Just go through the Emacs tutorial (which comes with Emacs) and then keep using Emacs, after less then a week you'll be comfortable.

---

### Post by fasoulas on 2010-03-09
> **matthew.ball said:**
> Honestly, why are people so scared of the command line?

Most IDEs just hide their compilation, but they are all working at the command line. The debugging too.
As a user, the difference is we're given this in a widget as opposed to white text on a black background (or whatever colour scheme you're using).

It just means we'll probably have to read a bit more. But really, if we're interested in software development, we won't get far if we're not willing to read much, we could consider it training for later.

Just as MadCow has said, I honestly feel programmers should start with the command line first - I'm not saying IDEs are useless; quite the opposite in fact.
But it's important to understand what it is an IDE is doing.

I would strongly suggest using Emacs. Learn gdb, and learn about Makefiles too. I wouldn't recommend these unless there was a reason to use them.

There's a learning curve to using the above tools - and I don't mention this to scare you off, but rather so you'll keep at it. Just go through the Emacs tutorial (which comes with Emacs) and then keep using Emacs, after less then a week you'll be comfortable.

I followed your advise.I played a little with the terminal and the g++ compiler and it seems very easy to use and it's also very fast.

---

