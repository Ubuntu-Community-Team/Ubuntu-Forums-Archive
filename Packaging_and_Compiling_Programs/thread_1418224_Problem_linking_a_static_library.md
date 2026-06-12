---
title: "Problem linking a static library"
date: 2010-02-28
forum: Packaging and Compiling Programs
---

### Post by rfrutos on 2010-02-28
Hello, I'm trying to compile a program that uses a static library called libThread.a and when I try to link my program I receive the following error:
 
/usr/bind/ld: /media/windows-share/PROGRAMAS/COMUN/LIB: No such file: File format not recognizedd
 
I have succesfully compiled my library at /media/windows-share/PROGRAMAS/COMUN/LIB obtaining the file libThread.a 
 
These are my Makefiles:
 
The one for compiling the library (that works fine):
 
```
 
CC = g++
LIB=$(LIB_COMUN)/libThread.a
SRC = Thread.cc
INCLUDES= -I. -I$(INC_COMUN)
LIBS= -L../ -L$(LIB_COMUN) -lm -lpthread
OBJ = $(SRC:.cc=.o)
$(LIB):$(OBJ)
 @echo lib Makefile - archiving $(LIB)
 @ar rcs $(LIB) $(OBJ)
.cc.o:
 @echo lib Makefile - compiling $<
 @$(CC) $(INCLUDES) $(CXXFLAGS) -c $< -o $@
clean:
 rm -f $(OBJ) $(LIB)

```
 
The one for compiling my program PU_Thread.cc (that gives the error)
 
```
 
CC = g++
LIBS = -lpthread -lThread
CXXFLAGS = -g
INCLUDE = -I$(INC_COMUN)
SRC = PU_Thread.cc
OBJ = $(SRC:.cc=.o)
EXE=PU_Thread
all:$(EXE)
$(EXE): $(OBJ)
 @echo application Makefile - linking $<
 @$(CC)  $^ $(LIB_COMUN) $(LIBS) -o $@
.cc.o:
 @echo application Makefile - compiling $<
 @$(CC) $(INCLUDE) $(CXXFLAGS) -c $< -o $@
clean:
 rm -f $(OBJ) $(EXE)

```
 
Colud anyone help me with this error? I don't understand what does it means...

---

### Post by lloyd_b on 2010-02-28
Basically, you're telling it *where* the library is located, instead of telling it the name of the library.  Make the change below (it's in red), and it should work```
CC = g++
LIBS = -lpthread -lThread
CXXFLAGS = -g
INCLUDE = -I$(INC_COMUN)
SRC = PU_Thread.cc
OBJ = $(SRC:.cc=.o)
EXE=PU_Thread
all:$(EXE)
$(EXE): $(OBJ)
 @echo application Makefile - linking $<
 @$(CC)  $^ $(LIB_COMUN)[COLOR="Red"]/libThread.a[/COLOR] $(LIBS) -o $@
.cc.o:
 @echo application Makefile - compiling $<
 @$(CC) $(INCLUDE) $(CXXFLAGS) -c $< -o $@
clean:
 rm -f $(OBJ) $(EXE)
```

Lloyd B.

---

