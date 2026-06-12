---
title: "problems with cc"
date: 2006-07-06
forum: Programming Talk
---

### Post by wr3cktangle on 2006-07-06
at school, I used a telnet client (putty) from Windows XP to connect to a Unix machine on which we coded and compiled our c++ programs.

we had to use cc to compile and link our programs, and so after just starting to use linux, i tried to compile a simple "Hello World" program using cc, but i recieved these errors (the dev directory is my own in my home directory):

user@ubuntu:~/dev$ cc test.cpp
/tmp/ccUJnO2n.o: In function `main':
test.cpp:(.text+0x25): undefined reference to `std::cout'
test.cpp:(.text+0x2a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
test.cpp:(.text+0x35): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
test.cpp:(.text+0x3b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccUJnO2n.o: In function `__tcf_0':
test.cpp:(.text+0x59): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccUJnO2n.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x86): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccUJnO2n.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


using Anjuta, the same file (test.cpp) compiles and executes no problem.

here is the code, just to help rule out the code being the problem

#include <iostream>

using namespace std;

int main()
{
 cout << "Hello World" << endl;

 return 0;
}


any suggestions would be appreciated.

i'm using Ubuntu 5.10 for the time being until i get my 6.06 cds.

---

### Post by Randomskk on 2006-07-06
Try iosteam.h, or perhaps gcc or g++ would work better?
I remember having a similar problem, and I fixed it with one of those three things :/

---

### Post by wr3cktangle on 2006-07-06
g++ worked.

i had tried gcc (from reading the man cc pages), but i didn't catch that g++ would also compile.

thank you for the help.

---

### Post by Max Luebbe on 2006-07-07
g++ is for c++ programs
gcc is for c and depending on configuration, sometimes objective-c

---

