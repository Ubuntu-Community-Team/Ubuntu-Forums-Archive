---
title: "compiling first c++ problem"
date: 2007-09-02
forum: Programming Talk
---

### Post by malfist on 2007-09-02
I compile a simple program, similar to hello world but it it takes input and does a little something with it and gcc spits this back out at me:
```

gcc readEquation.cc 
/tmp/ccPk2K1e.o: In function `__static_initialization_and_destruction_0(int, int)':
readEquation.cc:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccPk2K1e.o: In function `__tcf_0':
readEquation.cc:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccPk2K1e.o: In function `main':
readEquation.cc:(.text+0x8e): undefined reference to `std::cout'
readEquation.cc:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
readEquation.cc:(.text+0xa3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
readEquation.cc:(.text+0xb3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
readEquation.cc:(.text+0xc1): undefined reference to `std::cin'
readEquation.cc:(.text+0xc6): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
readEquation.cc:(.text+0xd7): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::operator>><char, std::char_traits<char> >(std::basic_istream<char, std::char_traits<char> >&, char&)'
readEquation.cc:(.text+0xe8): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
readEquation.cc:(.text+0xf9): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::operator>><char, std::char_traits<char> >(std::basic_istream<char, std::char_traits<char> >&, char&)'
readEquation.cc:(.text+0x10a): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::operator>><char, std::char_traits<char> >(std::basic_istream<char, std::char_traits<char> >&, char&)'
readEquation.cc:(.text+0x11b): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::operator>><char, std::char_traits<char> >(std::basic_istream<char, std::char_traits<char> >&, char&)'
readEquation.cc:(.text+0x12c): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
readEquation.cc:(.text+0x14f): undefined reference to `std::cout'
readEquation.cc:(.text+0x154): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
readEquation.cc:(.text+0x165): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
/tmp/ccPk2K1e.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```
I've compiled it on windows, and through netbeans IDE (C/C++ addon), but I can't do it by hand, someone help?

Malfist

---

### Post by CptPicard on 2007-09-02
You aren't linking in the standard library. To automatically link after compilation, compile with "g++ source.cpp -o output"

---

### Post by malfist on 2007-09-02
thank you, that fixed it. Needed to use g++ instead of gcc.

---

