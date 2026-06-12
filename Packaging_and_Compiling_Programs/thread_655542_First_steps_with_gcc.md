---
title: "First steps with gcc"
date: 2008-01-01
forum: Packaging and Compiling Programs
---

### Post by cmSthlm on 2008-01-01
I am trying to compile a c++ program with the gcc compiler. I wrote the following program:

#include <iostream>
int main()
{
  std::cout << "Hello";
  return 0;
}


I tried compiling:

$ gcc hello.cpp

and I got:

/tmp/ccyQfgGT.o: In function `__static_initialization_and_destruction_0(int, int)':
hello.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccyQfgGT.o: In function `__tcf_0':
hello.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccyQfgGT.o: In function `main':
hello.cpp:(.text+0x8e): undefined reference to `std::cout'
hello.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccyQfgGT.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


Please help me!

---

### Post by LaRoza on 2008-01-01
See my wiki, the wiki in my sig links to another with Ubuntu programming guides to get you started.

---

### Post by cmSthlm on 2008-01-01
Oh, g**++**
Thank you! Very nice wiki!

---

