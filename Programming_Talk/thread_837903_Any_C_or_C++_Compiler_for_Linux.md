---
title: "Any C or C++ Compiler for Linux?"
date: 2008-06-23
forum: Programming Talk
---

### Post by Papenco on 2008-06-23
Well, I moved to Linux because I know it's more customizable and all tha stuff. A friend also told me that it was a good OS for programmers/Developers, so there must be C or C++ compilers for it.
Which are them and which is the best one?
Thanks in advance.

---

### Post by AndThenWhat on 2008-06-23
There is g++ and gcc which are fine.  Just go in the terminal and type:

```
sudo apt-get install build-essential
```

---

### Post by lisati on 2008-06-23
There's gcc for C and g++ for C++. Depending on how your system is set up you might have to go to the terminal and enter ```
sudo apt-get install build-essential
``` to make sure that they're available

---

### Post by Papenco on 2008-06-23
Thanks.
What exactly build-essential is?
Does it make I can see the packages/repositories needed to install gcc and g++ or does it install this apps?
Are these compilers the best ones?
Again, Thanks.

---

### Post by lisati on 2008-06-23
> **Papenco said:**
> Thanks.
What exactly build-essential is?
Does it make I can see the packages/repositories needed to install gcc and g++ or does it install this apps?
Are these compilers the best ones?
Again, Thanks.
"build-essential" contains necessary parts that are "essential" when you want to "build" your program.

---

### Post by AndThenWhat on 2008-06-23
> **Papenco said:**
> Thanks.
What exactly build-essential is?
Does it make I can see the packages/repositories needed to install gcc and g++ or does it install this apps?
Are these compilers the best ones?
Again, Thanks.

Build essential installs everything you will need to successfully build/compile c/c++ programs from the terminal.  It should already be in your default repositories  Those compilers are the most popular and therefore have the most online documentation in case you run into issues, so I would recommend them.

---

### Post by ad_267 on 2008-06-23
build-essential is a package that installs many other packages required for compiling source code.

Yes g++ and gcc are the best :)

---

### Post by rzrgenesys187 on 2008-06-23
build-essential provides you with the main tools you would need to compile and install programs from source code.  It includes packages such as make, dpkg-dev in addition to the gcc and g++ listed above. (more info can be found here: [http://packages.debian.org/unstable/devel/build-essential](http://packages.debian.org/unstable/devel/build-essential))

These tools should work fine for whatever you are doing since many (if not all) of the ubuntu packages are compiled with these tools

---

### Post by LaRoza on 2008-06-23
The sticky has a how to for all this...

---

### Post by Unix_Slayer on 2008-06-23
Trolltech just came out with a new one. It's called Ct instead of C/C++/C##. It's included in the new Qt4.4.

---

### Post by LaRoza on 2008-06-23
> **Unix_Slayer said:**
> Trolltech just came out with a new one. It's called Ct instead of C/C++/C##. It's included in the new Qt4.4.

A new compiler?

---

### Post by mrsteveman1 on 2008-06-23
> Yes g++ and gcc are the best

mmm probably not, apparently ICC produces faster code.

I've also seen some indications on mailing lists that LLVM-gcc (i think thats what its called) makes code that is almost 30% faster than GCC code.

---

### Post by sonofusion82 on 2008-06-23
> **mrsteveman1 said:**
> mmm probably not, apparently ICC produces faster code.

I've also seen some indications on mailing lists that LLVM-gcc (i think thats what its called) makes code that is almost 30% faster than GCC code.

yeah.. ICC probably generates faster code, but are probably rather processor specific.
but faster code is not the only measurement for a "best" compiler. there are also things like compliance to ANSI C and ISO C++ standards.

---

### Post by Papenco on 2008-06-23
JUst another question, already installed all this I needed. Where are gcc and g++ supposed to be?
I mean, Tetris is in apps -- games -- tetris
But I can't find gcc or g++.
Any help?

---

### Post by lisati on 2008-06-23
> **Papenco said:**
> JUst another question, already installed all this I needed. Where are gcc and g++ supposed to be?
I mean, Tetris is in apps -- games -- tetris
But I can't find gcc or g++.
Any help?

They're usually accessed from the command line (terminal), but with a suitable IDE you might be able to avoid that. (Sorry, can't help with suggestions for an IDE)

---

### Post by dmn_clown on 2008-06-23
> **ad_267 said:**
> Yes g++ and gcc are the best

Only on Linux, on other platforms gcc has some fairly craptastic bugs that make it next to useless.

@Papenco, gcc is cli only.

---

### Post by AndyCee on 2008-06-23
Heh, no-one mentioned this. One might think it relevant:

It's in the command line, as in you run it in terminal.

eg:

```
g++ sourcefile1.cpp sourcefile2.cpp -o myfavoriteprogramname
```

Welcome to linux ;)

There are gui alternatives (netbeans, eclipse), which might be handy for dealing with many source files. I've always used and loved g++, but am learning netbeans at the moment.

---

### Post by Papenco on 2008-06-23
But how am I supposed to create a .gcc file?

---

### Post by lisati on 2008-06-23
> **Papenco said:**
> But how am I supposed to create a .gcc file?

"gcc" is the compiler for C programs (file type .c), and "g++" is for C++ programs which usually have a .cpp file type

For a "C" program, create a .c file with gedit e.g. ```
gedit example.c
``` and then use gcc to compile it.

For a C++ program, create a ".cpp" file e.g. ```
gedit example.cpp
``` and then use g++ to compile it.

---

### Post by Papenco on 2008-06-23
Another newbie thing, how do I compile and run?

---

### Post by LaRoza on 2008-06-23
> **Papenco said:**
> Another newbie thing, how do I compile and run?

As said before, the sticky has a guide for all this. I suggest you explore the links in the sticky.

[http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

---

### Post by AndyCee on 2008-06-23
> **Papenco said:**
> Another newbie thing, how do I compile and run?

Compile:

```
g++ sourcefile1 sourcefile2... -o programname
```
Run:

```
./programname
```

---

### Post by Kadrus on 2008-06-23
in terminal:
```
sudo apt-get update
```
```
sudo apt-get install build-essential
```
gedit:
```

#include<iostream>
using namespace std;
int main()
{
cout<<"Test"<<endl;
return 0;
}

```
save test.cpp
terminal:
```
g++ test.cpp
```
```
./a.out
```
and the program should run.

---

### Post by AndThenWhat on 2008-06-23
If you are struggling with compiling from the terminal, then you may want to try an IDE (Integrated Development Environment).  For simplicity and ease of use, you can try Geany:

You should be able to find it in Synaptic, or if not then go to the terminal and enter:

```
sudo apt-get install geany
```

---

### Post by LaRoza on 2008-06-23
> **AndThenWhat said:**
> If you are struggling with compiling from the terminal, then you may want to try an IDE (Integrated Development Environment).  For simplicity and ease of use, you can try Geany:

You should be able to find it in Synaptic, or if not then go to the terminal and enter:

```
sudo apt-get install geany
```

I disagree. An IDE (especially Geany) isn't flexible. To use the C compiler, learn to use it first, then use tools to abstract the process if you feel like it, but don't substitute it for knowledge.

---

### Post by nvteighen on 2008-06-23
> **LaRoza said:**
> I disagree. An IDE (especially Geany) isn't flexible. To use the C compiler, learn to use it first, then use tools to abstract the process if you feel like it, but don't substitute it for knowledge.
LaRoza's right.

You must understand what is going on with your program, specially on languages like C and C++, which are meant to teach and use the internal workings of a computer. If you don't learn how the compiler works and what it does, you won't be able to customize it according to your needs (e.g., you want to build a shared library... or static link to all libraries... or only get object files to re-compile your project partially... whatever).

It's probably more useful to learn how to use makefiles than to use a certain IDE, I think...

---

### Post by tornado89 on 2008-06-23
I Agree With And Then What
Geany Is A Great IDE to start with...
but you need to learn how to the linker for your compiler works to
be able to link it with shared libs and objects in future..

---

