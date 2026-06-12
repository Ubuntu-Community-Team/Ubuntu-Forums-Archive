---
title: "[SOLVED] having trouble with gcc"
date: 2008-03-04
forum: Programming Talk
---

### Post by vikasmk on 2008-03-04
here is a piece of code i tried to execute but it wont```
vikasmk@vikasmk:~$ gcc vikas.cpp
/tmp/ccTd1Wsq.o: In function `__static_initialization_and_destruction_0(int, int)':
vikas.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccTd1Wsq.o: In function `__tcf_0':
vikas.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccTd1Wsq.o: In function `main':
vikas.cpp:(.text+0x8e): undefined reference to `std::cout'
vikas.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccTd1Wsq.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status[CODE]

 
 heres the c++ code
 [CODE]#include<iostream>
using namespace std; 
int main()
{ cout<<"printing stuff";
  
  }
```
 can any one tell me whats wrong

---

### Post by Adnarim on 2008-03-04
Just use g++ direct for compiling C++ apps instead of the gcc-wrapper and everything works fine.

greets

---

### Post by vikasmk on 2008-03-04
ok it worked , geez i'm feelin really stupid:)

---

