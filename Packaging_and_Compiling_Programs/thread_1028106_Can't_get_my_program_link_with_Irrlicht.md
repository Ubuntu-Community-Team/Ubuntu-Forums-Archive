---
title: "Can't get my program link with Irrlicht"
date: 2009-01-02
forum: Packaging and Compiling Programs
---

### Post by JannoT on 2009-01-02
So i have been tryng to install irrlicht and use it. But linker can't find the Irrlicht shared lib.
```
janno@janno-laptop:~/test$ make
g++ -O3 -g -Wall -c main.cpp
main.cpp: In function ‘int main()’:
main.cpp:9: warning: unused variable ‘device’
g++ -g -lIrrlicht -o test main.o
/usr/bin/ld: cannot find -lIrrlicht
collect2: ld returned 1 exit status
make: *** [game] Error 1

```
Now before someone says that i don't have the needed lib:
```

/lib
/usr/lib
/usr/local/lib

```
All have these two files:
```
libIrrlicht.so.1 - Link to shared library (application/x-sharedlib)
libIrrlicht.so.1.5 - shared library (application/x-sharedlib) 

```

In Code::Blocks when i add the lib manualy all works. So lib is not corrupted or something. :/

This is my makefile:
```

cc=g++
cflags=-O3 -g -Wall
ldflags=-g -lIrrlicht

test : main.o
		${cc} ${ldflags} -o test main.o
	
main.o : main.cpp
		${cc} ${cflags} -c main.cpp

```
So does somebody have any ideas? Or is there something i can't see. :S

---

### Post by Cracauer on 2009-01-02
Please post the exact location of the libraries, e.g. output from
`find /usr -name \*irrlicht\*so -ls`

---

