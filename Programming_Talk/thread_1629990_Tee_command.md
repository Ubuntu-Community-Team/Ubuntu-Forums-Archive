---
title: "Tee command?"
date: 2010-11-24
forum: Programming Talk
---

### Post by urkrnboy90 on 2010-11-24
Can anyone help me with this code? I am to make a C++/C Program that acts as a tee command in linux. 

So for example, the tee command would look like this in the command line:

                ls *.txt | tee txtfiles.txt

And the new utility/program that I made (named "test" just for example) would make the tee command look like this in the command line:

                ls *.txt | test txtfiles.txt

I have performed aclocal, autoconf, ./configure, make, and automake however, when I try to make install, errors come up. This is what my code looks like:

#include <fstream>
      
int main( int argc, const char** argv)
{
      std::ofstream file(argv[1]);
      teestream teeout(std::cout, file);
      teeout << std::cin.rdbuf();
}

And this is the output from trying to run make install:

gcc -DPACKAGE=\"test\" -DVERSION=\"1.0\"  -I. -I.      -g -O2 -c test.c
test.c:1:19: error: fstream: No such file or directory
test.c: In function ‘main’:
test.c:5: error: expected expression before ‘:’ token
test.c:6: error: ‘teestream’ undeclared (first use in this function)
test.c:6: error: (Each undeclared identifier is reported only once
test.c:6: error: for each function it appears in.)
test.c:6: error: expected ‘;’ before ‘teeout’
test.c:7: error: ‘teeout’ undeclared (first use in this function)
test.c:7: error: ‘std’ undeclared (first use in this function)
test.c:7: error: expected ‘;’ before ‘:’ token
make: *** [test.o] Error 1

Anyone...............help?? :(

---

### Post by aromo on 2010-11-24
> **urkrnboy90 said:**
> test.c:1:19: error: fstream: No such file or directory
(

This line should tell you something.

Try ```
#include<fstream.h>
``` instead.

---

### Post by MadCow108 on 2010-11-24
don't do what aromo proposed, fstream is correct, C++ standard headers do not have extensions

> 
gcc -DPACKAGE=\"test\" -DVERSION=\"1.0\"  -I. -I.      -g -O2 -c test.c
test.c:1:19: error: fstream: No such file or directory
test.c: In function &#8216;main&#8217;:
test.c:5: error: expected expression before &#8216;:&#8217; token
test.c:6: error: &#8216;teestream&#8217; undeclared (first use in this function)
test.c:6: error: (Each undeclared identifier is reported only once
test.c:6: error: for each function it appears in.)
test.c:6: error: expected &#8216;;&#8217; before &#8216;teeout&#8217;
test.c:7: error: &#8216;teeout&#8217; undeclared (first use in this function)
test.c:7: error: &#8216;std&#8217; undeclared (first use in this function)
test.c:7: error: expected &#8216;;&#8217; before &#8216;:&#8217; token
make: *** [test.o] Error 1

Anyone...............help?? :(

you are trying to compile C++ code with a C compiler (gcc)
use g++ instead.

In the case of autotools a rename of the file to a c++ extension should suffice.
e.g. test.cpp or test.cxx or test.C or test.cc ...

also you will have to change stuff like *_CFLAGS to *_CXXFLAGS if they are used


is that all your source?
if yes teestream is undefined. you must define it somewhere

---

### Post by spjackson on 2010-11-24
make doesn't work because you are running a C compiler on C++ code. Rename your source to one of the default C++ extensions: .cc .cp .cxx .cpp .CPP .c++ .C

That should get you started. You have faults to fix in your C++ source before your homework is done.

---

### Post by Arndt on 2010-11-24
> **urkrnboy90 said:**
> Can anyone help me with this code? I am to make a C++/C Program that acts as a tee command in linux. 

So for example, the tee command would look like this in the command line:

                ls *.txt | tee txtfiles.txt

And the new utility/program that I made (named "test" just for example) would make the tee command look like this in the command line:

                ls *.txt | test txtfiles.txt

I have performed aclocal, autoconf, ./configure, make, and automake however, when I try to make install, errors come up. This is what my code looks like:

#include <fstream>
      
int main( int argc, const char** argv)
{
      std::ofstream file(argv[1]);
      teestream teeout(std::cout, file);
      teeout << std::cin.rdbuf();
}

And this is the output from trying to run make install:

gcc -DPACKAGE=\"test\" -DVERSION=\"1.0\"  -I. -I.      -g -O2 -c test.c
test.c:1:19: error: fstream: No such file or directory
test.c: In function &#8216;main&#8217;:
test.c:5: error: expected expression before &#8216;:&#8217; token
test.c:6: error: &#8216;teestream&#8217; undeclared (first use in this function)
test.c:6: error: (Each undeclared identifier is reported only once
test.c:6: error: for each function it appears in.)
test.c:6: error: expected &#8216;;&#8217; before &#8216;teeout&#8217;
test.c:7: error: &#8216;teeout&#8217; undeclared (first use in this function)
test.c:7: error: &#8216;std&#8217; undeclared (first use in this function)
test.c:7: error: expected &#8216;;&#8217; before &#8216;:&#8217; token
make: *** [test.o] Error 1

Anyone...............help?? :(

Your program is clearly C++, not C, so #include <fstream> is the proper syntax, but you should compile it with g++, not gcc, and preferably give it a file name ending which reflects the language: not .c, but .cc or .cpp.

---

