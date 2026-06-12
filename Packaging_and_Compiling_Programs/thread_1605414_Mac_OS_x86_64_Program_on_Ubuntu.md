---
title: "Mac OS x86_64 Program on Ubuntu"
date: 2010-10-25
forum: Packaging and Compiling Programs
---

### Post by biometrics on 2010-10-25
HI Everyone,

I have a code developed under the OS X. Since I don't have access to Mac system, I have to compile it under ubuntu system. However, the following errors show up,

g++ -MM -MT src/lib/IO.o -MF src/lib/IO.d -Wextra -Wall -pedantic-ercdrors -arch x86_64 -O3 -fopenmp  -I/usr/local/include -Isrc/lib src/lib/IO.cc
g++: x86_64: No such file or directory
cc1plus: error: unrecognized command line option "-pedantic-ercdrors"
make: *** [src/lib/IO.o] Error 1

The code needs opencv library. And I have already installed the opencv and g++.  Experiments with other codes show that both opencv and g++ works fine on ubuntu. The makefile from OS X code is listed as reference,

# Paths
OPENCV_PATH=/usr/local

# Programs
CC=
CXX=g++

# Flags
ARCH_FLAGS=-arch x86_64
CFLAGS=-Wextra -Wall -pedantic-ercdrors $(ARCH_FLAGS) -O3 -fopenmp
LDFLAGS=$(ARCH_FLAGS)
DEFINES=
INCLUDES=-I$(OPENCV_PATH)/include -Isrc/lib
LIBRARIES=-L$(OPENCV_PATH)/lib -lopencv_core -lopencv_highgui -lopencv_imgproc -lopencv_objdetect -lgomp

I don't what are the reasons of the failure. Maybe it is because the code is developed under X86_64 and I am using 32 bit system of ubuntu?  Sorry to bother you guys. I am relatively new to the ubuntu system. But I am in a hurry to compile this code successfully under ubuntu system. 

I really appreciate your guys help. THanks.

---

### Post by SevenMachines on 2010-10-25
>  cc1plus: error: unrecognized command line option "-pedantic-ercdrors"should be -pedantic-errors, assuming you want all complaints from gcc to be turned into errors, if you only want them as warnings use -pedantic

If you really need to cross compile for x86_64 on i386 you'll probably need to add at least some 64 bit libraries, search for lib64 on synaptic, the gcc-multilib package will install the basics. 

If you can just use the i386 build instead of cross compiling you'll probably find that a lot easier, -pedantic instead of -pedantic-errors is generally what i'd use too. Often they're not big mistakes but things you might want to tidy up/improve at some point rather than have the whole build fail. Quite handy when you're actively in the process of developing something and its very much a 'work in progress'

[EDIT] from man gcc
> -pedantic
           Issue all the warnings demanded by strict ISO C and ISO C++; reject
           all programs that use forbidden extensions, and some other programs
           that do not follow ISO C and ISO C++.
..
.. 
Strict is the very apt word here, with -pedantic-errors your build will fail with an error if any 'strict' rules are broken

---

### Post by biometrics on 2010-10-25
Thanks for your reply. I really appreciate your advice. BUT after I use only -pedanti as the option, it still gives me the following errors,

g++ -MM -MT src/lib/IO.o -MF src/lib/IO.d -Wextra -Wall -pedantic -arch x86_64 -O3 -fopenmp  -I/usr/local/include -Isrc/lib src/lib/IO.cc
g++: x86_64: No such file or directory
make: *** [src/lib/IO.o] Error 1

MY GNU version is i686 GNU/Linux. One thing that bothers me is that I have already installed the g++ and can compile other c++ code without errors. But in this case, the g++ can not be located. Is that because  the code is developed under X86_64, which causes the problem? 

THanks.

---

### Post by SevenMachines on 2010-10-26
Its probably not that its developed on 64, its that you're cross compiling to 64 from 32 in this case. Made a mistake before, you'll need
$ sudo apt-get install g++-multilib
not gcc, as i mentioned before

I dont do a lot of this thing so this may be wrong but you i dont think its -arch for this but -m64. For a simple example

hello.cpp:
> int main(int args, char ** argv){
    return 0;
}
# 32 compile
$ g++  -o hello hello.cpp 
$ readelf -h hello|grep Machine
  Machine:                           Intel 80386

# 64 compile
$ g++ -m64  -o hello hello.cpp 
$ g++ -m64  -o hello hello.cpp 
$ readelf -h hello|grep Machine
  Machine:                           Advanced Micro Devices X86-64

I would add, unless you especially need to cross compile for a different target machines, stick with the native 32 bit ( remove arch flags). Its likely you'll need to manually setup some 64 bit libraries on your 32 bit machines otherwise. Not too difficult but extra work :)

---

