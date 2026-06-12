---
title: "c++ makefile"
date: 2006-09-29
forum: Packaging and Compiling Programs
---

### Post by houghtonator on 2006-09-29
Just starting to do some C++ development.
Compiling with gcc v3.4, and make using 'makedepend' for multiple file compilation.
Not sure how to direct the compiler to libraries
getting:
makedepend -- -Wall -pedantic-errors -g -- Cell.cpp Mazer.cpp
makedepend: warning:  Mazer.cpp, line 10: cannot find include file "fstream"
        not in /usr/include/fstream

where libraries are in /usr/include/c++/3.4

tried installing gccmakedep
while trying to configure, got:

checking if gcc -E requires -undef... gcc: no input files
gcc: no input files
configure: error: gcc -E defines unix with or without -undef.  I don't know what  to do.

thanks

---

### Post by po0f on 2006-09-29
houghtonator,

Do you have build-essential installed?  If this is not the problem, I am not familiar enough with what makedepend does.  Why not just use a standard makefile for such a (seemingly, only two files) small project?  Hope this helps you out somehow.

---

### Post by houghtonator on 2006-09-29
Installed the build-essential package. Still same errors. The project i'm compiling has 4 source files, and when compiling, gives multiple 'cannot find file' errors.
Just using a makefile supplied from uni, which originally used 'gccmakedep' instead of 'makedepend'
Open for ideas of a simpler makefile, or anything to get the project compiling.
cheers

---

### Post by po0f on 2006-09-29
```
CXX=g++
CXXFLAGS=-Wall -pedantic-errors -g
SOURCES=file1.cpp file2.cpp file3.cpp
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=myprog

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
    $(CXX) -o $@ $(OBJECTS)

clean:
    rm -f $(OBJECTS) $(EXECUTABLE)

.cpp.o:
    $(CXX) $(CXXFLAGS) -c -o $@ $<
```

Any indentation in that should be a tab, not spaces.

---

### Post by houghtonator on 2006-09-29
Much better makefile.
Thanks for the help, off to some C++ forums to fix my code.
cheers

---

