---
title: "Good C++ Compiler for Ubuntu 9.04??"
date: 2009-09-28
forum: Programming Talk
---

### Post by D3mon_Spawn on 2009-09-28
I'm looking for a C++ compiler that abides by the universal standards and runs well under Ubuntu 9.04. I'm new to programming so I don't really want to use an IDE. I figured it would be better to start just using the terminal (also because my proggrams wont be that complex). Any suggestions??

---

### Post by falconindy on 2009-09-28
g++ is the gnu c++ compiler. You can get it by installing the "build-essential" package.

---

### Post by phrostbyte on 2009-09-28
Install [this]("apt://build-essential").

Also you may be interested in [this]("apt://geany"). It's called Geany, it's something between a "heavy" full blown IDE and a simple text editor.

Anyway to compile in command line use
g++ source.cpp -o output

where source.cpp is your source file, and output is your output executable

---

### Post by Can+~ on 2009-09-28
Too bad that the apt:// links don't work on Firefox 3.5.1 (or Shiretoko), nor Chromium 3.

---

### Post by credobyte on 2009-09-29
[GNU Compiler]("http://gcc.gnu.org/") ( available from Ubuntu repositories as gcc/g++ ).[URL="http://gcc.gnu.org/"]
[/URL]

---

### Post by phrostbyte on 2009-09-29
> **Can+~ said:**
> Too bad that the apt:// links don't work on Firefox 3.5.1 (or Shiretoko), nor Chromium 3.

It does in Karmic, I guess they are too lazy to fix it in Jaunty. :confused:

---

### Post by Viva on 2009-09-29
> **Can+~ said:**
> Too bad that the apt:// links don't work on Firefox 3.5.1 (or Shiretoko), nor Chromium 3.

You need to install gnome support for firefox-3.5

```
sudo apt-get install firefox-3.5-gnome-support
```

---

### Post by MadCow108 on 2009-09-29
just to give some choice:
you can also install the the intel c++ compiler which is free for non commercial use
[http://software.intel.com/en-us/articles/non-commercial-software-download/](http://software.intel.com/en-us/articles/non-commercial-software-download/)

but gcc is totally fine except you have a program which greatly benefits from the advantages of the intel compiler (better vectorization and better optimizations for intel chips)
But this should rarely be the case as gcc is near as good nowadays

---

### Post by SeanHodges on 2009-09-29
> **Viva said:**
> You need to install gnome support for firefox-3.5

```
sudo apt-get install firefox-3.5-gnome-support
```

+1

Works for me with Firefox 3.5 and Gnome support.

---

### Post by fiddler616 on 2009-09-29
> **phrostbyte said:**
> Install [this]("apt://build-essential").

Also you may be interested in [this]("apt://geany"). It's called Geany, it's something between a "heavy" full blown IDE and a simple text editor.

Anyway to compile in command line use
g++ source.cpp -o output

where source.cpp is your source file, and output is your output executable

If we still had thanks buttons, I would thank you just for the use of aptURLs. This trend needs to take off.

---

### Post by Can+~ on 2009-09-29
> **Viva said:**
> You need to install gnome support for firefox-3.5

```
sudo apt-get install firefox-3.5-gnome-support
```

Funny, I tried to install some extensions, other packages, but missed that one.

Thank you.

---

### Post by Jekshadow on 2009-09-30
g++?

This in a terminal

```

USAGE:
g++ -o [OUTPUT FILE] [INPUT FILES]

EXAMPLE:
g++ -o helloworld hello.cpp world.cpp main.cpp

```

---

### Post by Clopin on 2009-10-01
> **Jekshadow said:**
> g++?

This in a terminal

```

USAGE:
g++ -o [OUTPUT FILE] [INPUT FILES]

EXAMPLE:
g++ -o helloworld hello.cpp world.cpp main.cpp

```

Only tried g++, and I must admit it works fine for my needs.
Can only recommend it.

I could use some explanation though, for what to do if you got various source code files like: main.cpp, main.h, init.cpp, init.h and so on.
Any help?

---

### Post by MadCow108 on 2009-10-01
you could compile it like this:
```

g++ -c main.cpp -o main.o
g++ -c init.cpp -o init.o
g++ main.o init.o -o result.o

```
the -c flags tells the compiler only to compile the files and don't link anything. The last step then links the objects together to an executable.
(This is just one way, you can also do it in various other command line combinations with the same result)

bigger projects are usually compiled with so called Makefiles.
These include all rules necessary for compilation, so you only have to type *make* in the folder where the makefile lies.
[http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

these makefiles can also be created with tools like autotools or cmake
These tools also allow you to have a platform independent build process.
[http://sourceware.org/autobook/autobook/autobook_toc.html](http://sourceware.org/autobook/autobook/autobook_toc.html)

---

### Post by Clopin on 2009-10-01
Thanks a lot mate!

---

### Post by grayrainbow on 2009-10-01
Don't won't to scare you, but when you got to more complex topics check g++ version and preferably go and get latest one. g++ is notoriously problematic with templates, but I guess(and hope) that's in the past

---

