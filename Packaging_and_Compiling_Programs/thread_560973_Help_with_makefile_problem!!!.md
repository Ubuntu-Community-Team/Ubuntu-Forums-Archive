---
title: "Help with makefile problem!!!"
date: 2007-09-27
forum: Packaging and Compiling Programs
---

### Post by simbasaurus on 2007-09-27
Hello!

I am trying to write a simple makefile that compiles some C++
sources from ~/testmake/src and places the object files in
~/testmake/obj.

The makefile looks like this:

CC=g++
BASEDIR = ~/testmake
SRC = $(BASEDIR)/src
OBJ = $(BASEDIR)/obj

SOURCES = s1.cpp s2.cpp
OBJECTS = $(SOURCES:.cpp=.o)


vpath %.cpp $(SRC)
vpath %.o $(OBJ)

all: mylib.so $(OBJECTS)

clean:
rm -f $(OBJ)/*.o

$(OBJECTS):\
%.o:%.cpp
$(CC) -c $< -o $(OBJ)/$@

mylib.so: $(OBJECTS)
$(CC) -shared -fPIC -o $@ $^


The output of the make command under Ubuntu 7.04 is

g++ -c s1.cpp -o ~/testmake/obj/s1.o
g++ -c s2.cpp -o ~/testmake/obj/s2.o
g++ -shared -fPIC -o mylib.so s1.o s2.o
g++.real: s1.o: No such file or directory
g++.real: s2.o: No such file or directory
g++.real: no input files
make: *** [mylib.so] Error 1


Can you please tell me what i'm doing wrong?
Shouldn't it find the .o files and create the shared object??

Regards,
Simbasaurus

---

### Post by dwhitney67 on 2007-09-27
Personally I always like to keep my Makefile that compiles the source code at the same level as the source code itself.  Thus, if I had a directory containing the following:

[PHP]Makefile file1.cpp file2.cpp[/PHP]

my Makefile would look like:

[PHP]
SOURCES = file1.cpp \
          file2.cpp

OBJECTS = $(SOURCES:.cpp=.o)

LIB     = libForFun.so


all: $(LIB)

$(LIB): $(OBJECTS)
        @echo building shared library $@
        @$(CXX) -shared -fPIC -o $@ $^

.cpp.o:
        @echo compiling source $<
        @$(CXX) -c $< -o $@

clean:
        $(RM) *.o

distclean: clean
        $(RM) $(LIB)
[/PHP]

Please note that there is no need to define your own CC (which more appropriately should have been CXX) variable within a Makefile,  unless you plan to use a compiler other than the default (which is g++).

Also, RM is automatically defined by Makefile, so the "rm -f" is not needed.

P.S.  I understand you wanted to use the vpath feature so that you can stuff your compiled objects elsewhere, but I have never seen the point of doing that.  I guess everyone has their own preferences.

---

