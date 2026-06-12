---
title: "help with using g++ and executing in windows"
date: 2012-07-13
forum: Programming Talk
---

### Post by IlikeMoose on 2012-07-13
hello all,

i'm using g++ to compile a simple "hello world" type program and it executes fine in Ubuntu but i'm trying to send the program to my parents to show them my work but the file won't execute in windows.

is there some flag when executing g++ to compile the gameover.cpp file in order to get it to run in windows?

i'm using the following command to compile my program:

```

g++ -o gameover.cpp gameover

```

thanks in advance

---

### Post by Vaphell on 2012-07-13
[http://stackoverflow.com/questions/182408/manual-for-cross-compile-a-c-application-from-linux-to-windows#182456](http://stackoverflow.com/questions/182408/manual-for-cross-compile-a-c-application-from-linux-to-windows#182456)

---

### Post by IlikeMoose on 2012-07-15
the program compiles just fine and runs in linux here it is:
```
 
// Game Over
// A first C++ program

#include <iostream>
using std::cout;
using std::endl;

int main()

{
        cout << "Game Over!" << endl;
        return 0;
}

```

but when i try this cross compiler i get the following when trying to compile:

```

mike@hackbox:~/C++/game_over$ i586-mingw32msvc-cc main.cpp -o gameover.exe
/tmp/cctVl0kh.o:main.cpp:(.text+0xe): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'
/tmp/cctVl0kh.o:main.cpp:(.text+0x52): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/cctVl0kh.o:main.cpp:(.text+0x8b): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/cctVl0kh.o:main.cpp:(.text+0xd0): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/cctVl0kh.o:main.cpp:(.text+0x121): undefined reference to `std::cout'
/tmp/cctVl0kh.o:main.cpp:(.text+0x126): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/cctVl0kh.o:main.cpp:(.text+0x131): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
/tmp/cctVl0kh.o:main.cpp:(.text+0x137): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/cctVl0kh.o:main.cpp:(.text+0x16a): undefined reference to `std::ios_base::Init::Init()'
/tmp/cctVl0kh.o:main.cpp:(.text+0x1ad): undefined reference to `std::ios_base::Init::~Init()'
collect2: ld returned 1 exit status

```

any ideas?

---

### Post by Vaphell on 2012-07-15
i586-mingw32msvc-g++ instead of i586-mingw32msvc-cc, *cc compiles C

to see what mingw has to offer
```
locate mingw32 | grep compilercache
```

---

### Post by IlikeMoose on 2012-07-16
it works!!!!! THANKS!!!

---

