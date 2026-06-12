---
title: "makefile for any extention main.c .cpp .C .cc etc..."
date: 2012-04-15
forum: Packaging and Compiling Programs
---

### Post by scu-ba-de-buntu on 2012-04-15
How do you make a Makefile be able to use any of the various c/c++ filename extensions (.c, .C, .c++, .cpp, etc...), provided they all start with "main" but not "main.h" and still name the compiled binary as "./main"?

---

### Post by r-senior on 2012-04-15
Traditional make used suffix rules to do this but these days it's implicit rules:

[http://www.gnu.org/software/make/manual/make.html#Implicit-Rules](http://www.gnu.org/software/make/manual/make.html#Implicit-Rules)

The .c, .C, .cpp and .cc rules are already there. You'd just need to add to them for anything else you want.

For example:

```
$ cat hello1.C
#include <iostream>

int main()
{
	std::cout << "Hello" << std::endl;
}
$ cp hello1.C hello2.cc
$ cp hello2.cc hello3.cpp
$ make hello1 hello2 hello3
g++     hello1.C   -o hello1
g++     hello2.cc   -o hello2
g++     hello3.cpp   -o hello3
$ ls
hello1  hello1.C  hello2  hello2.cc  hello3  hello3.cpp

```

Note there's no Makefile here. These are compiled with the implicit rules that already exist in GNU make.

---

