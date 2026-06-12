---
title: "Trouble with static linking with MinGW."
date: 2011-12-13
forum: Programming Talk
---

### Post by pheserus on 2011-12-13
I'm trying to statically link libstdc++ with mingw, using (i686-w64-mingw32-gcc).
Though when I use -static-libstdc++ I get a bunch of errors.

```
/tmp/ccbgdkOd.o:str.cpp:(.text+0x12): undefined reference to `___gxx_personality_sj0'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x70): undefined reference to `std::basic_stringstream<char, std::char_traits<char>, std::allocator<char> >::basic_stringstream(std::_Ios_Openmode)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x92): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(unsigned int)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0xa7): undefined reference to `std::basic_stringstream<char, std::char_traits<char>, std::allocator<char> >::str() const'
/tmp/ccbgdkOd.o:str.cpp:(.text+0xc7): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::resize(unsigned int)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0xd2): undefined reference to `std::allocator<char>::allocator()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0xf6): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, std::allocator<char> const&)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x101): undefined reference to `std::allocator<char>::~allocator()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x10c): undefined reference to `std::allocator<char>::allocator()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x130): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(char const*, std::allocator<char> const&)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x13b): undefined reference to `std::allocator<char>::~allocator()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x160): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x175): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x1a1): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x1c5): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x1e2): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x206): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x223): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x247): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x264): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x288): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::push_back(char)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x296): undefined reference to `std::cout'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x2a5): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <char, std::char_traits<char>, std::allocator<char> >(std::basic_ostream<char, std::char_traits<char> >&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x2ad): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x2b5): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x2ca): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x2df): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x2f7): undefined reference to `std::basic_stringstream<char, std::char_traits<char>, std::allocator<char> >::~basic_stringstream()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x323): undefined reference to `std::allocator<char>::~allocator()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x342): undefined reference to `std::allocator<char>::~allocator()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x36b): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x38c): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x3b5): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x3fd): undefined reference to `std::basic_stringstream<char, std::char_traits<char>, std::allocator<char> >::~basic_stringstream()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x430): undefined reference to `___gxx_personality_sj0'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x485): undefined reference to `std::cout'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x491): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <char, std::char_traits<char>, std::allocator<char> >(std::basic_ostream<char, std::char_traits<char> >&, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x499): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x4a1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x4ba): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x4f5): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x519): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccbgdkOd.o:str.cpp:(.text+0x53c): undefined reference to `std::ios_base::Init::Init()'
collect2: ld returned 1 exit status

```These errors go away when I use -lstdc++.
Does this mean that -static-libstdc++ doesnt work? Or am I using it wrong?
Could anyone give me some advice on how to make this work?

---

### Post by dodle on 2011-12-14
I think you need to use [color=blue]i686-w64-mingw32-**g++**[/color]. Try it and see what happens.

I'm using [color=blue]i586-mingw32msvc-g++[/color] and I get the following error:

> :/media/Data/Developing/test$ i586-mingw32msvc-g++ -s -O9 test2.cpp -o test.exe -static-libstdc++
i586-mingw32msvc-g++: unrecognized option '-static-libstdc++'

I know I've been able to statically link before on Windows with MinGW. Is [color=blue]i686-w64-mingw32-gcc[/color] 64bit?

**----- EDIT -----**

Here is the conclusion that I have come to: In the version of MinGW on my system there is no longer an option for [color=blue]-static-libstdc++[/color], linking of libstdc++ depends on how libgcc is linked. So if [color=blue]-static-libgcc[/color] is used then libstdc++ will be linked statically as well. It also appears that my version of MinGW is statically linking by default. I have to use the option [color=blue]-shared-libgcc[/color] if I want dynamic linking.

---

