---
title: "Issues with gcc"
date: 2014-08-04
forum: New to Ubuntu
---

### Post by dan128 on 2014-08-04
I've been trying to compile some C++ programs on my ubuntu laptop, but every time I try I get errors like this:

$ gcc helloworld.cpp 
/tmp/ccFNdzd1.o: In function `main':
helloworld.cpp.text+0x14): undefined reference to `std::cout'
helloworld.cpp.text+0x19): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std:: operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
helloworld.cpp.text+0x21): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
helloworld.cpp.text+0x29): undefined reference to `std:ostream: operator<<(std ostream& (*)(std:: ostream&))'
/tmp/ccFNdzd1.o: In function `__static_initialization_and_destruction_0(int, int)':
helloworld.cpp.text+0x51): undefined reference to `std::ios_base::Init::Init()'
helloworld.cpp.text+0x68): undefined reference to `std::ios_base::Init::~Init()'
collect2: error: ld returned 1 exit status

I've installed the build-essential package and run updates, but past that I can't think of anything else I can try. Any ideas?

---

### Post by steeldriver on 2014-08-04
Hello and welcome to the forums

If your source code is **C++**, you should use **g++** instead of gcc - among other things, it will automatically link the missing C++ standard libraries

---

