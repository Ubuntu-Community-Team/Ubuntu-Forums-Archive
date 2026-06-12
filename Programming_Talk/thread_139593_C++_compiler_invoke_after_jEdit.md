---
title: "C++ compiler invoke after jEdit?"
date: 2006-03-04
forum: Programming Talk
---

### Post by Zdravko on 2006-03-04
I just installed jedit. Now I can produce cpp/h files. But how do I invoke the compiler to compile all of these? I think it is something like "g++ file.cpp -o file", but I am not quite sure. Can you help me?

---

### Post by thumper on 2006-03-04
Yes, you're right.

---

### Post by Zdravko on 2006-03-04
thumper, I hope you are not fooling me :)
Anyway - I installed 2 plugins for jEdit - Project manager and Console Application. The first one groups several files into a single hierarchy. So far so good. The second plugin generates a terminal with some predefined commands, as well as the usual ones. 
If I have a single file I type:
g++ myfile.cpp -o myfile
Then I type:
./myfile
Voila!
But what if I have more cpp/h files? How do I tell the compiler to:
1. Compile every cpp file!
2. Link with appropriate headers/libs?

---

### Post by thumper on 2006-03-04
You can either collate your source files like
```
g++ file1.cpp file2.cpp file3.cpp -o exec_me
```
Or you can compile to object files and then link the executable.

I think that the compile only flag is -c, so
```
 g++ -c file1.cpp -o file1.o
g++ -c file2.cpp -o file2.o
g++ -c file3.cpp -o file3.o
g++ file1.o file2.o file3.o -o exec_me

```
If it is not exactly that, it is something very close.

---

### Post by pharcyde on 2006-03-04
I prefer using gnu make to compile all of my source in one fail swoop.  I do this by writing a make file to compile object files and then link the object all at once at the end of the executable.

Makefile:

```

obj1: file1.cpp misc.h misc2.h
  gcc -c file1.cpp -o file1.o

obj2: file2.cpp misc3.h
  gcc -c file2.cpp -o file2.o

obj3: file3.cpp misc4.h
  gcc -c file3.cpp -o file3.o

program: obj1 obj2 obj3
  gcc file1.o file2.o file3.o -o exec_me

```

To compile everything you would type "make program"

This is nice because make will only recompile the targets that have files in them that have changed.  So for example if you modify misc2.h then only the "obj1" target and "program" targets will be built again because obj1 depends on misc2.h and program depends on obj1.  This is very useful when compiling very large programs that have dependencies on multiple files.

Check out [http://www.gnu.org/software/make/](http://www.gnu.org/software/make/) or type "man make" to find out more information about it.

---

### Post by engla on 2006-03-04
and after all these levels come Autotools.

Autotools are really a whole package of tools to automate configurations, makefiles and lots more around linux and unix-like programming projects... ideally a package created with autotools would compile on any POSIX/unix-like system...

make is a part of autotools and so, and if you are going to make a big project, I suggest that you learn something about autotools.. I don't think it's very hard to learn the basics, but it might be hard to find the right end to start in to learn the basics.. shoot me an icq message if you want to chat about it ;-)

---

### Post by Zdravko on 2006-03-05
Thanks for the reply. I created the following zmake file:
> 
zenvi: zenvi.cpp zenvi.h
	g++ -c zenvi.cpp

zmain: zmain.cpp zmain.h
	g++ -c zmain.cpp

zmath: zmath.cpp zmath.h
	g++ -c zmath.cpp

znode: znode.cpp znode.h
	g++ -c znode.cpp

zpos: zpos.cpp zpos.h
	g++ -c zpos.cpp

zprim: zprim.cpp zprim.h
	g++ -c zprim.cpp

zrand: zrand.cpp zrand.h
	g++ -c zrand.cpp

zsim: zsim.cpp zsim.h
	g++ -c zsim.cpp

program: zenvi zmain zmath znode zpos zprim zrand zsim
	g++ zenvi.o zmain.o zmath.o znode.o zpos.o zprim.o zrand.o zsim.o

I have already created these .h and their corresponding .h files. Now what do I need to do with this file? Is my semantic OK? I couldn't find any exact description of the contents f this make? :(

---

### Post by pharcyde on 2006-03-06
[QUOTE=Zdravko]Thanks for the reply. I created the following zmake file:

I have already created these .h and their corresponding .h files. Now what do I need to do with this file? Is my semantic OK? I couldn't find any exact description of the contents f this make? :([/QUOTE]

I think that looks ok.  Just make sure the file is calld "makefile" and type "make program".  Everythign should compile in the correct order and work.

---

### Post by WelterPelter on 2006-03-06
So you decided to try jEdit after all. Good. I would also recommend the buffer tabs plugin. Makes things easier, especially with a lot of files.

---

