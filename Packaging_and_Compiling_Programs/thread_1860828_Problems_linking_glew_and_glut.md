---
title: "Problems linking glew and glut"
date: 2011-10-15
forum: Packaging and Compiling Programs
---

### Post by zJulien on 2011-10-15
Hello everyone, I am very frustrated now after 8 hours of trying to get my opengl program to work. I am writing glsl program and need to link against glew and glut. It used to compile and work just fine, but everything got broken after I upgraded to ubuntu 11.10 today. I don't know what happened exactly, but I now get linking errors such as:

/home/fan/CS480/BAK/Pong-1/Pong/example1.cpp:65: undefined reference to `glutMainLoop'
example1.o: In function `display()':
/home/fan/CS480/BAK/Pong-1/Pong/example1.cpp:71: undefined reference to `glClear'
/home/fan/CS480/BAK/Pong-1/Pong/example1.cpp:72: undefined reference to `glDrawArrays'
/home/fan/CS480/BAK/Pong-1/Pong/example1.cpp:73: undefined reference to `glFlush'
example1.o: In function `Initialize(int, char**)':
/home/fan/CS480/BAK/Pong-1/Pong/example1.cpp:124: undefined reference to `glewExperimental'
/home/fan/CS480/BAK/Pong-1/Pong/example1.cpp:125: undefined reference to `glewInit'
/home/fan/CS480/BAK/Pong-1/Pong/example1.cpp:132: undefined reference to `glewGetErrorString'

As you can see it seems like linker can't find glew and glut.

 ALl required packages are installed on my system because I no longer get errors such as -lGLEW is not found.

Here is my makefile:

GCC_OPTIONS=-Wall -pedantic -I /include 
 
LIBS =  -L/usr/lib -lGLEW -lglut -lGL -lGLU -lXext -lXmu -lX11 -lm
 
INCS =  -I/usr/include
 
 
#.cpp: 
#        $(CC)  $@.cpp $(LDLIBS) -o $@ 
 
 
.cpp:  
    g++ $@.cpp ../Common/initShader.o $(GCC_OPTIONS) -o $@   
 
exec:    example1.o InitShader.o 
    g++ $(LIBS) $(INCS) -o exec example1.o InitShader.o $(GCC_OPTIONS) -g 
 
InitShader.o:    Common/InitShader.cpp include/Angel.h 
    g++ -c Common/InitShader.cpp -g 
     
example1.o:    example1.cpp include/Angel.h 
    g++ -c example1.cpp -g 
 
clean:     
    rm *.o 
cleanAll: 
    rm *.o exec


Maybe I am specifying wrong paths for shared libraries with -L option ?

Please help I am goind to sleep a bit now, hopefully someone responds by tomorrow.

Thanks in advance, I value your time.

---

### Post by MadCow108 on 2011-10-15
```
g++ $(LIBS) $(INCS) -o exec example1.o InitShader.o $(GCC_OPTIONS) -g
```
LIBS needs to go behind the objects as 11.10 uses ld --as-needed by default.
this is the usual correct ordering
```
g++ $(INCS) $(GCC_OPTIONS) -g -o exec example1.o InitShader.o  $(LIBS)
```

---

### Post by zJulien on 2011-10-15
MadCow, did you know that you are life savior. I would never in my life think about reordering in linking command. Why did that happen with new ubuntu? I thought libraries have to be very first so then they can be referenced by programs?

Thanks again, you probably saved me a full day of figuring it out on my own :)

---

### Post by MadCow108 on 2011-10-15
objects needing symbols must always be placed before the objects providing the symbols with gcc/ld
This is a common pitfall when linking static libraries.
For shared library this is not needed unless you link with --as-needed.

The --as-needed flag is default in ubuntu now because, as the name implies, it only links those libraries which are really needed instead of all listed on the command line.
It will just drop all libraries whos symbols are not needed from left to right on the command line.
The gain are reduced dependencies between packages.

---

