---
title: "C++ Editor"
date: 2009-04-12
forum: Programming Talk
---

### Post by G_man on 2009-04-12
Is there an editor that compiles your program and run it without the need to do it manually in the terminal?

It is kinda boring to write:
g++ XX.cpp -o XX.out
./XX.out

while you can do it easily by pressing F9 in Dev-C++

---

### Post by cguy on 2009-04-12
Code::Blocks

---

### Post by _Purple_ on 2009-04-12
> **G_man said:**
> Is there an editor that compiles your program and run it without the need to do it manually in the terminal?

It is kinda boring to write:
g++ XX.cpp -o XX.out
./XX.out

while you can do it easily by pressing F9 in Dev-C++

You can try anjuta. Install it by typing in terminal:
```
sudo apt-get install anjuta

```

---

### Post by Jiraiya_sama on 2009-04-12
I learned this the other day, but a shortcut for "g++ xxx.cpp -o xxx" is "make xxx". Also, eclipse will do it for you quick.

---

### Post by namegame on 2009-04-12
> **Jiraiya_sama said:**
> I learned this the other day, but a shortcut for "g++ xxx.cpp -o xxx" is "make xxx". 

I'm pretty sure that only works if you have a makefile.

---

### Post by Can+~ on 2009-04-12
Both anjuta and code::blocks are for medium-big projects, the OP wants something to compile smaller things.

I suggest Geany, it's pretty much like DevC++ on windows.

> **Jiraiya_sama said:**
> I learned this the other day, but a shortcut for "g++ xxx.cpp -o xxx" is "make xxx". Also, eclipse will do it for you quick.

It's not a "shortcut". Make is a way of reducing the compile process to a single command. You manually define a makefile in which you set the sources, and then add compiling/linking rules and hand it to gcc to do it's work.

In other words, you could say that "make" is a wrapper for gcc, but definitely not a shortcut, as you have to define your makefile or have an automated tool (e.g. eclipse does it by itself).

---

### Post by Jiraiya_sama on 2009-04-12
It may just be a quirk of my distro (I'm running arch), but it does not require any makefile.

---

### Post by jimi_hendrix on 2009-04-12
> **Jiraiya_sama said:**
> It may just be a quirk of my distro (I'm running arch), but it does not require any makefile.

no it is not

make is smart enough to do one liners like that for small programs

---

### Post by Can+~ on 2009-04-12
> **Jiraiya_sama said:**
> It may just be a quirk of my distro (I'm running arch), but it does not require any makefile.

Eclipse throws it's makefile inside the Debug/ and Release/ folders btw.

---

### Post by sujoy on 2009-04-12
eclipse CDT, netbeans, codeblocks ... take your pick!

i'd say netbeans (but then i use it for java mainly)

---

### Post by namegame on 2009-04-13
> **Jiraiya_sama said:**
> It may just be a quirk of my distro (I'm running arch), but it does not require any makefile.

I'm on arch as well. Unless you have a makefile in the directory "make" will throw an error.

To be exact:
[PHP][namegame@arch ~]$ make
make: *** No targets specified and no makefile found.  Stop.
[/PHP]

---

### Post by bs_one on 2009-04-13
I personally use Netbeans for Java, C++ and C. I think it does its job quite good and it's really easy to handle.
But it's your decision.

---

### Post by Sinkingships7 on 2009-04-13
I think Geany is exactly what you're looking for.

---

### Post by Jiraiya_sama on 2009-04-13
> **namegame said:**
> I'm on arch as well. Unless you have a makefile in the directory "make" will throw an error.

To be exact:
[PHP][namegame@arch ~]$ make
make: *** No targets specified and no makefile found.  Stop.
[/PHP]

Try this.

[PHP]lufthanza@ignitius Sun Apr 12 11:25:54pm 
~/ touch test.c
lufthanza@ignitius Sun Apr 12 11:26:01pm 
~/ make test
cc     test.c   -o test
/usr/lib/gcc/i686-pc-linux-gnu/4.3.3/../../../crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make: *** [test] Error 1
[/php]

---

### Post by ashmew2 on 2009-04-13
Code::Blocks ftw!

But then again ..Linux is all about choice..

---

### Post by krazyd on 2009-04-13
I use kate now that it has vi input mode.

---

### Post by nvteighen on 2009-04-13
> **namegame said:**
> I'm pretty sure that only works if you have a makefile.

No, make is a "shell", so if you give it a target, it will try to build that target first looking at any Makefile script (which just passes arguments to make), then using the implicit rules and if fails, it will return error.

---

### Post by benj1 on 2009-04-13
if youre looking for a text editor rather than an ide have a look at geany (it is more of an ide but very light).

---

### Post by namegame on 2009-04-13
> **nvteighen said:**
> No, make is a "shell", so if you give it a target, it will try to build that target first looking at any Makefile script (which just passes arguments to make), then using the implicit rules and if fails, it will return error.

Thanks for correcting me/informing me of my Bogo emission. :P

Yay for misinformed Computer Science professors telling me things that they themselves don't know.

---

### Post by dribeas on 2009-04-13
> **namegame said:**
> I'm on arch as well. Unless you have a makefile in the directory "make" will throw an error.

To be exact:
[PHP][namegame@arch ~]$ make
make: *** No targets specified and no makefile found.  Stop.
[/PHP]

```

$ ls
test.cpp
$ make test
g++ test.cpp -o test

```

Just test it. As it was posted before, make is able to perform simple compilations like that for one-file executables. Even if you have more than one simple app in the directory you can 'make' each one of them. I use it daily with simple test programs. I used it with ubuntu 7.04, 7.10, 8.04, debian etch, redhat rhel4, rhel5 and macosx... I'd say it is a widely available feature of GNU make...

---

### Post by rich1939 on 2009-04-13
> **cguy said:**
> Code::Blocks

+1 for CODE::BLOCKS!

---

### Post by rich1939 on 2009-04-13
> **cguy said:**
> Code::Blocks

+1 for CPDE::BLOCKS!

---

