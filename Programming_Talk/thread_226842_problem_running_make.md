---
title: "problem running make"
date: 2006-07-31
forum: Programming Talk
---

### Post by tiger99 on 2006-07-31
Hi all
I am new programming in unix environment. I am trying to run a simple "hello world" program

my .cpp file is:
#include <iostream>
int main(){
	std::cout << "Hello, world!" << std::end;
	return 0;
}

my Makefile is:
ch0-0.o: ch0-0.cpp
	gcc -cpp ch0-0.cpp

when I run :make, I got the following error message
:!make  2>&1| tee /tmp/v394799/2
gcc -cpp ch0-0.cpp
make: gcc: Command not found
make: *** [ch0-0.o] Error 127
(1 of 3): gcc -cpp ch0-0.cpp    

Any idea how I can resolve the problem? I put all my files in my home directory. Is it a good place to put all my source code files?

Thanks

---

### Post by Daverz on 2006-07-31
Looks like you're missing gcc.  Try:

sudo aptitude install build-essential

Also, you should use g++ to compile C++ source files.

---

