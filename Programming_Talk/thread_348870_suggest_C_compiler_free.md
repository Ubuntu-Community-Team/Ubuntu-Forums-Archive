---
title: "suggest C compiler free"
date: 2007-01-29
forum: Programming Talk
---

### Post by burmanabhay88 on 2007-01-29
can anyone suggest me a free C compiler which can run in ubuntu 6.10.
thank u.

---

### Post by Wybiral on 2007-01-29
Yeah, Gcc.

Type this in the command line: sudo apt-get install build-essential

---

### Post by burmanabhay88 on 2007-01-29
wait.....
> 
RPMs and DEBs are binary packages. Linux is not binary-compatible. One release of Ubuntu is not even binary-compatible with another release of Ubuntu. Everything works fine at the source level.

The distribution provides binary packages for it's releases. If there is no version in the ubuntu repositories, download the source and build it. Don't try to use a foreign binary package.

Most of the software that exists in the free-libre software world is available in the Ubuntu repositories - make sure to enable the universe repo in your sources.list.

i run on a ubuntu 6.10 Edgy

i am new to linux. most of this is braille to me. i can download the source code. but how exactly do i BUILD IT???
secondly. how do i enable universe repo in my sources list???? and what exactly will that do????

one more thing
i've installed GCC. now how do i open it?? i have not worked on any LINUX os b4. so please try to explain in detail

---

### Post by Wybiral on 2007-01-29
Well... You don't open gcc. It's a compiler. You must be thinking of an IDE. I can't help you there (a lot of people would suggest Anjuta though, you can download it from synaptic package manager)

If you have Gcc, do this... Type up a small C program (hello world would be great) and save it somewhere as "hello.c"

Open up a command line, navigate to where you saved that C code. then type...
```
gcc hello.c -o hello
```
Which should compile your "hello.c" program and output the executable "hello"
From the command line, you can execute that executable with...
```
./hello
```

Hope that helps... Once again, you're probably looking for an IDE, you should search for those if you already have a compiler. Compilers don't open, they just compile code.

---

### Post by maubp on 2007-01-29
Do you understand the idea about source code being compiled into binary code (i.e. a program, like a .EXE or .DLL on windows)

> **burmanabhay88 said:**
> i am new to linux. most of this is braille to me. i can download the source code. but how exactly do i BUILD IT???
It sounds like you are quoting some instructions for building / installing some other software from source.  Those instructions should include more steps - e.g. perhaps something like this:

(1) Get the source, uncompressed
(2) open a command prompt
(3) goto the directory where you uncompressed the source
(3) run this command:

./configure

(4) run this command:

make

(5) next they might suggest:

make install

These are generic instructions that might work.  It all depends on the package you are trying to install...

> **burmanabhay88 said:**
> secondly. how do i enable universe repo in my sources list???? and what exactly will that do????
It lets you use the "pre compiled packages" from a larger repository.  Some software you may want might be available in a different repository.  If you add this repository, then extra software becomes available via the apt-get command line tool, or the graphical front ends.

---

### Post by burmanabhay88 on 2007-01-30
the last post went over my head. wait. we have Turbo C/ Visual C compilers in windows. they have a graphical user interface. is there any such compiler for ubuntu 6.10 edgy??????

---

### Post by ansi on 2007-01-30
> **burmanabhay88 said:**
> they have a graphical user interface. is there any such compiler for ubuntu 6.10 edgy??????

They have not GUI. They have IDE. As GUI IDE in Linux you can use, for example, Anjuta or KDevelop. Some prefers Emacs or Vim + makefile only ;).

---

### Post by ghandi69_ on 2007-01-30
> **burmanabhay88 said:**
> the last post went over my head. wait. we have Turbo C/ Visual C compilers in windows. they have a graphical user interface. is there any such compiler for ubuntu 6.10 edgy??????

Ok, so to summarize here.  First things, install the c 'compliler'... by typing..

> sudo apt-get install build-essential

this will give you 'gcc' and 'g++' gcc being the c compiler, and g++ being a c++ compiler.  Note there are no graphical user interfaces for these, you don't open and run them.. you just send them code.  So, lets practice....

sudo nano HelloWorld.c

(Enter you c program competely into this file, save it and exit)

then to use to gcc to compile the code type

> gcc -o Helloworld.exe Helloworld.c

"HelloWorld.exe", can be anything you want.  It is what your are naming the executable file gcc creates...  It could have been written "gcc -o RandomCrap Helloworld.c" and still work.  The 2nd part. HelloWorld.c has to be the same as the .c file is named.

Then to run your porgram using the first example..  you would type

./Helloworld.exe

Assuming there were no errors in your original program.  This is how you use gcc, and I would run through the process a couple times to get a better understanding of how compiling works in linux.  However, what you are probably looking for is an Integrated Development Environment(like VisualC++) or IDE as mentioned here by others.. Again, there are a few to choose from, but I also would recommend Anjuta for C.. You can get this by typing

sudo apt-get install anjuta

into the terminal..  

I hope this helps!!

---

