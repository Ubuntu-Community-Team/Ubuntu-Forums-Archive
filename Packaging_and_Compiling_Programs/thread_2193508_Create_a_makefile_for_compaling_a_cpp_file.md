---
title: "Create a makefile for compaling a cpp file"
date: 2013-12-13
forum: Packaging and Compiling Programs
---

### Post by souraklis on 2013-12-13
I am new to Ubuntu development. I want to compile a c++ project which I did in MVSC++. My problem is how to create my make file so as to compile to run and clean project. I put all my cpp and header files in the same directory. For running a cpp file I ve found the following:

```
g++ -ggdb `pkg-config --cflags opencv` -o `basename opencvtest.cpp .cpp` opencvtest.cpp `pkg-config --libs opencv`
```
How can I create a makefile with the above??

Ok I ve changed a little bit the make file to:
```
# I am a comment, and I want to say that the variable CC will be
# the compiler to use.
CC=g++
# Hey!, I am comment number 2. I want to say that CFLAGS will be the
# options I'll pass to the compiler.

all:
	$(CC) -ggdb `pkg-config --cflags opencv` -o `basename opencvtest.cpp .cpp` opencvtest.cpp `pkg-config --libs opencv`	

clean:
	rm -rf *o opencvtest
```
And this file works correct. It was just a single main file. When I ve got several cpp and header files how is it possible to compile them??
I am trying something like that :
```

# I am a comment, and I want to say that the variable CC will be
# the compiler to use.
CC=g++
# Hey!, I am comment number 2. I want to say that CFLAGS will be the
# options I'll pass to the compiler.

all:
	$(CC) -ggdb `pkg-config --cflags opencv` -o `basename main.cpp .cpp` main.cpp `pkg-config --libs opencv`	

main: main.o detection.o prediction.o
	$(CC) main.o detection.o prediction.o -o main

main.o: main.cpp
	$(CC) -c main.cpp -ggdb `pkg-config --cflags opencv` -o `basename main.cpp .cpp` main.cpp `pkg-config --libs opencv`	

detection.o: detection.cpp  -ggdb `pkg-config --cflags opencv` -o `basename main.cpp .cpp` main.cpp `pkg-config --libs opencv`	
	$(CC) -c detection.cpp

prediction.o: prediction.cpp
	$(CC) -c prediction.cpp	 -ggdb `pkg-config --cflags opencv` -o `basename main.cpp .cpp` main.cpp `pkg-config --libs opencv`	

clean:
	rm -rf *o main

```

However, I got error: fatal error: core.hpp: No such file or directory compilation terminated. I ve used the same opencv library in the opencvtest.cpp single file and it was compiled  correctly. In what way have to change my makefile to work??

---

### Post by souraklis on 2013-12-13
Basically I ve got thie makefile
```

all:  
	g++ -ggdb `pkg-config --cflags opencv` -o `basename main.cpp .cpp` main.cpp `pkg-config --libs opencv`

main: main.o detection.o prediction.o
	$(CC) main.o detection.o prediction.o -o main

main.o: main.cpp
	$(CC) -c main.cpp

detection.o: detection.cpp
	$(CC) -c detection.cpp

prediction.o: prediction.cpp
	$(CC) -c prediction.cpp

clean:
	rm -rf *o main

```

I am receiving the message opencv core.hpp doesnt found

---

### Post by steeldriver on 2013-12-13
Have a look at some of the Makefile answers posted by dwhitney67 - they are very good imho - like this one [creating a makefile for C++]("http://ubuntuforums.org/showthread.php?t=2099295")

You basically want to structure it into (1) rules to make object files from source files and (2) a rule to make your final executable target from the object files. The examples from dwhitney67 will show you how to use make's special variables to template that 

The specific error you mention is because your current rules for making objects from source do not include the opencv `pkgconfig --cflags` (the best place for that imho would be in a CXXFLAGS variable)

---

### Post by souraklis on 2013-12-13
I ve changed to:

```

CC=g++
CXXFLAGS = `pkg-config --cflags opencv`
LIBS = `pkg-config --libs opencv`

executable: program.o Detection.o prediction.o
		$(CC) -o executable $(LIBS) program.o Detection.o prediction

program.o: 
		$(CC) $(CXXFLAGS) -c program.cpp 

Detection.o:
		$(CC) $(CXXFLAGS) -c Detection.cpp

prediction.o:
		$(CC) $(CXXFLAGS) -c prediction.cpp

```

I ve followed this tutorial [http://mrbook.org/tutorials/make/](http://mrbook.org/tutorials/make/). I ve changed cflags variable to cxxflags but still I am receiving the same error core.hpp not found.

---

