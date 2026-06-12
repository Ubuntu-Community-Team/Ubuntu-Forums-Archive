---
title: "Simple C++ code....lots of errors."
date: 2010-03-09
forum: Programming Talk
---

### Post by Neezer on 2010-03-09
I wrote some code to A) Play with some c++ cause I took the class a while ago and want to start programming again. and B) I read something on xkcd.com and wanted to check it out....

for some reason, I can't get this to compile at all! I don't have any idea why.

Here is my code just checking syntax and stuff. clearly I am missing something.

```

#include <iostream>

using namespace std;

int main()
{
  long int x,y,z;
  cout << "enter x" << endl;
  cin >> x;
  y = x/2;
  z = 3*x + 1;

  cout <<  "x = " << x << endl << "y = " << y << endl << "z = " << z << endl;
  return 0;
}

```

And here is the screen of text that I get when I try gcc collatz.cpp


```

nathan@lappy:~$ gcc collatz.cpp
/tmp/ccxkYcJ2.o: In function `main':
collatz.cpp:(.text+0xf): undefined reference to `std::cout'
collatz.cpp:(.text+0x14): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
collatz.cpp:(.text+0x19): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
collatz.cpp:(.text+0x21): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
collatz.cpp:(.text+0x2d): undefined reference to `std::cin'
collatz.cpp:(.text+0x32): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(long&)'
collatz.cpp:(.text+0x6b): undefined reference to `std::cout'
collatz.cpp:(.text+0x70): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
collatz.cpp:(.text+0x7b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(long)'
collatz.cpp:(.text+0x80): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
collatz.cpp:(.text+0x88): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
collatz.cpp:(.text+0x95): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
collatz.cpp:(.text+0xa4): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(long)'
collatz.cpp:(.text+0xa9): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
collatz.cpp:(.text+0xb1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
collatz.cpp:(.text+0xbe): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
collatz.cpp:(.text+0xcd): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(long)'
collatz.cpp:(.text+0xd2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
collatz.cpp:(.text+0xda): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccxkYcJ2.o: In function `__static_initialization_and_destruction_0(int, int)':
collatz.cpp:(.text+0x10d): undefined reference to `std::ios_base::Init::Init()'
collatz.cpp:(.text+0x112): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccxkYcJ2.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


```

Can someone help me out here? I don't have any idea what is going wrong here.

---

### Post by lisati on 2010-03-09
Try g++ instead of gcc

---

### Post by Neezer on 2010-03-09
Wow! thanks...I knew it was something really small and stupid like that.

Thanks a lot!

---

### Post by puntigamer on 2010-11-03
I had the same problem, thanks for the answer!
This small things, waah:D

---

