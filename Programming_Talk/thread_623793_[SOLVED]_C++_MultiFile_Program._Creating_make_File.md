---
title: "[SOLVED] C++ MultiFile Program. Creating make File"
date: 2007-11-26
forum: Programming Talk
---

### Post by TreeFinger on 2007-11-26
I am creating a program for the first time which uses multiple .cpp files. I want to create a make file. Could someone help me out on this topic?

Anyways, I tried creating my makefile but I am getting errors.
Here is 'Makefile'
```

bookinfo.o : bookinfo.cpp bookinfo.h
	g++ -Wall -g -c bookinfo.cpp

cashier.o : cashier.cpp cashier.h
	g++ -Wall -g -c cashier.cpp

invmenu.o : invmenu.cpp invmenu.h
	g++ -Wall -g -c invmenu.cpp

reports.o : reports.cpp reports.h
	g++ -Wall -g -c invmenu.cpp

mainmenu.o : mainmenu.cpp bookinfo.h cashier.h invmenu.h reports.h
	g++ -Wall -g -c main.cpp

bookseller : mainmenu.o reports.o invmenu.o cashier.o bookinfo.o
	g++ -g bookinfo.o cashier.o invmenu.o reports.o mainmenu.o -lm -o bookseller

```

Here is the error:
```

Serendipity Booksellers.02$ make
g++ -Wall -g -c bookinfo.cpp
bookinfo.cpp:9:22: error: bookinfo.h: No such file or directory
make: *** [bookinfo.o] Error 1

```

I assure you I have a bookinfo.h file in the directory

---

### Post by engineer on 2007-11-26
how do your includes look like?

an include statement with "filename.h" as argument makes the compiler search in the same path as the source file.
when using <filename.h> the file is looked up in the standard include directories.
you can add a directory to this list by calling gcc with -I dirname as argument.

---

### Post by TreeFinger on 2007-11-26
at the top of my .cpp files I have 
```

#include <filename.h>

```

so you are saying I need to change that to 
```

#include filename.h

```

---

### Post by SledgeHammer_999 on 2007-11-26
no you should change it to:
```
#include "filename.h"
```

---

### Post by TreeFinger on 2007-11-26
OK, cool. I am eager to get home and compile it :)

My book was not good in explaining compiling multiple file programs. It just said that I may choose to use multi or single file. I chose multi because I believe most projects are multi file programs. Then it said if you select multi file, look in your compilers manual for creating a Makefile.

---

### Post by TreeFinger on 2007-11-26
I made the changes to my .cpp files. Now when I run the makefile g++ runs for the first line of the makefile only. I am only getting the bookinfo.o file.. none others. What is the problem?

---

### Post by SledgeHammer_999 on 2007-11-26
I am no expert with makefiles, I use an IDE for C++ development([code::blocks nightly builds)](http://codeblocks.org/). I think the solution to your problem is this: ```
make bookseller
```

you have to specify which part of the makefile is going to be build by make

---

### Post by xtacocorex on 2007-11-26
In accord with the previous poster, I'd change the line in your makefile
```

bookseller : mainmenu.o reports.o invmenu.o cashier.o bookinfo.o

```
to
```

all : mainmenu.o reports.o invmenu.o cashier.o bookinfo.o

```
This way, when you type make at the command prompt, it'll make everything and you won't have to type the bookseller after make.

---

### Post by TreeFinger on 2007-11-27
```

$ make
make: `bookinfo.o' is up to date.

```

Makefile:
```

bookinfo.o : bookinfo.cpp bookinfo.h
	g++ -Wall -g -c bookinfo.cpp

cashier.o : cashier.cpp cashier.h
	g++ -Wall -g -c cashier.cpp

invmenu.o : invmenu.cpp invmenu.h
	g++ -Wall -g -c invmenu.cpp

reports.o : reports.cpp reports.h
	g++ -Wall -g -c invmenu.cpp

mainmenu.o : mainmenu.cpp bookinfo.h cashier.h invmenu.h reports.h
	g++ -Wall -g -c main.cpp

all : mainmenu.o reports.o invmenu.o cashier.o bookinfo.o
	g++ -g bookinfo.o cashier.o invmenu.o reports.o mainmenu.o -lm -o bookseller

```

I figured it out :) I got my program to compile and run.
Makefile:
```

bookinfo.o : bookinfo.cpp bookinfo.h
	g++ -Wall -g -c bookinfo.cpp

cashier.o : cashier.cpp cashier.h
	g++ -Wall -g -c cashier.cpp

invmenu.o : invmenu.cpp invmenu.h
	g++ -Wall -g -c invmenu.cpp

reports.o : reports.cpp reports.h
	g++ -Wall -g -c reports.cpp

mainmenu.o : mainmenu.cpp bookinfo.h cashier.h invmenu.h reports.h
	g++ -Wall -g -c mainmenu.cpp

all : mainmenu.o reports.o invmenu.o cashier.o bookinfo.o
	g++ -g bookinfo.o cashier.o invmenu.o reports.o mainmenu.o -lm -o bookseller

```

Had to make a few changes to my make file.

I also had to #include all the header files I created in my .cpp file with the main function.

And to make all the files you can not just type 'make' at terminal. I had to type: 'make all'.

---

### Post by dwhitney67 on 2007-11-27
> **xtacocorex said:**
> In accord with the previous poster, I'd change the line in your makefile
```

bookseller : mainmenu.o reports.o invmenu.o cashier.o bookinfo.o

```
to
```

all : mainmenu.o reports.o invmenu.o cashier.o bookinfo.o

```
This way, when you type make at the command prompt, it'll make everything and you won't have to type the bookseller after make.

Actually, the first entry point in a Makefile is called when no arguments are supplied to the "make" call.  Thus had the OP re-ordered his Makefile such that *bookseller: <list of dependencies>* where the first entry in the Makefile, then typing "make" without any parameters would be sufficient to build the project.

---

