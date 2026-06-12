---
title: "gcc has suddenly gone insane and wont compile anything"
date: 2007-02-04
forum: Programming Talk
---

### Post by Choad on 2007-02-04
```
#include <iostream>

int main() {
	std::cout << "bla bla bla" << std::endl;
	return 0;
	}

```

now unless i have been hit with a rock recently, that is a very reasonable looking c++ program

```
richard@richard-laptop:~/Projects/bla$ gcc main.cpp 
/tmp/ccGPN5by.o: In function `__static_initialization_and_destruction_0(int, int)':
main.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccGPN5by.o: In function `__tcf_0':
main.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccGPN5by.o: In function `main':
main.cpp:(.text+0x8e): undefined reference to `std::cout'
main.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
main.cpp:(.text+0x9b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
main.cpp:(.text+0xa3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccGPN5by.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
richard@richard-laptop:~/Projects/bla$ gedit main.cpp

(gedit:17532): GLib-CRITICAL **: g_string_append: assertion `val != NULL' failed
sys:1: Warning: g_string_append: assertion `val != NULL' failed
[/corichard@richard-laptop:~/Projects/bla$ gcc main.cpp 
/tmp/ccGPN5by.o: In function `__static_initialization_and_destruction_0(int, int)':
main.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccGPN5by.o: In function `__tcf_0':
main.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccGPN5by.o: In function `main':
main.cpp:(.text+0x8e): undefined reference to `std::cout'
main.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
main.cpp:(.text+0x9b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
main.cpp:(.text+0xa3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccGPN5by.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

WHAT IS GOING ON!?!?!

---

### Post by duff on 2007-02-04
comiled with g++ not gcc

---

### Post by Choad on 2007-02-04
oh... duh

i feel dumb now :D

was looking at c tutorial and totally forgot the difference

---

### Post by maddog39 on 2007-02-04
Yeah, you aren't using the actual C++ compiler, I do believe there is an option in gcc to compile for C++ but your supposed to just use g++ instead. Install with:
```

sudo apt-get install g++

```

---

