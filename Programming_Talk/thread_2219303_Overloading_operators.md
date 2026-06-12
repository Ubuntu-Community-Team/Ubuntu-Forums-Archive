---
title: "Overloading operators"
date: 2014-04-23
forum: Programming Talk
---

### Post by bikewrecker on 2014-04-23
Hi guys. I have a question about overloading the << operator in c++. All I'm trying to do is be able to print out two ints in a fraction object, but I can't even compile my code because my overloading syntax must be off. 

Here is my header file where I try to overload <<
```
  3 //
  4 #ifndef Fraction_H
  5 #define Fraction_H
  6 
  7 #include<iostream>
  8 #include<stdexcept>
  9 
 10 class Fraction
 11 {
 12         private:
 13         int x,y;
 14  
 15         public: 
 16                 Fraction(void);     
 17                 Fraction(int, int);
 18                 Fraction(const Fraction& frac);
 19                 ~Fraction(void) {}
 20         friend std::ostream& operator << ( std::ostream& output, const Fraction& frac )
 21         {
 22                 output << frac.x << " / " << frac.y; return output;
 23         }
 24 };
 25 #endif
                                                                                                                        25,6          Bot

```

Here is the program that includes this header file:

```

  1 //
  2 //Fraction.cpp
  3 //
  4 #include <iostream>
  5 #include "Fraction.h"
  6 #include <cmath>
  7 #include <stdio.h>
  8 #include <stdexcept>
  9 using namespace std;
 10 
 11 int find_gcd (int n1, int n2);
 12 
 13 int main()
 14 {
 15 /*
 16         std::ostream& operator<<( std::ostream &output, const Fraction &frac )
 17         {
 18               output << frac.x << " / " << frac.y;
 19         }
 20 */
 21 
 22                         int gcd, x = 5, y = 15;
 23                         gcd = find_gcd(x, y);
"Fraction.cpp" 59L, 1246C written                                                   10,0-1        Top


```

And here are my error messages:
```

gcc Fraction.cpp -Wall -o Fraction.out
/tmp/ccLzjxqU.o: In function `main':
Fraction.cpp:(.text+0x64): undefined reference to `std::cout'
Fraction.cpp:(.text+0x69): undefined reference to `std::ostream::operator<<(int)'
Fraction.cpp:(.text+0x79): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
Fraction.cpp:(.text+0x89): undefined reference to `std::ostream::operator<<(int)'
Fraction.cpp:(.text+0x91): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
Fraction.cpp:(.text+0x99): undefined reference to `std::ostream::operator<<(std::ostream& (*)(std::ostream&))'
Fraction.cpp:(.text+0xe2): undefined reference to `std::cout'
Fraction.cpp:(.text+0xe7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char)'
Fraction.cpp:(.text+0xf7): undefined reference to `std::ostream::operator<<(int)'
Fraction.cpp:(.text+0x107): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
Fraction.cpp:(.text+0x117): undefined reference to `std::ostream::operator<<(int)'
Fraction.cpp:(.text+0x11f): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
Fraction.cpp:(.text+0x127): undefined reference to `std::ostream::operator<<(std::ostream& (*)(std::ostream&))'
Fraction.cpp:(.text+0x138): undefined reference to `std::cout'
Fraction.cpp:(.text+0x13d): undefined reference to `std::ostream::operator<<(int)'
Fraction.cpp:(.text+0x14d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
Fraction.cpp:(.text+0x15d): undefined reference to `std::ostream::operator<<(int)'
Fraction.cpp:(.text+0x165): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
Fraction.cpp:(.text+0x16d): undefined reference to `std::ostream::operator<<(std::ostream& (*)(std::ostream&))'
/tmp/ccLzjxqU.o: In function `__static_initialization_and_destruction_0(int, int)':
Fraction.cpp:(.text+0x1ce): undefined reference to `std::ios_base::Init::Init()'
Fraction.cpp:(.text+0x1e5): undefined reference to `std::ios_base::Init::~Init()'
collect2: error: ld returned 1 exit status
[drmcb@pc14 Homework1]$ 


```

Any help would be greatly appreciated. I'm sure I'm just doing something dumb, but I've already spent hours trying to fix this and I haven't been able to make any progress.

---

### Post by steeldriver on 2014-04-23
Most of those undefined reference (linker) errors are likely due to trying to compile C++ with **gcc** instead of **g++**

---

### Post by spjackson on 2014-04-23
Those error messages are nothing to do with your operator overload. Try:
```

g++ Fraction.cpp -Wall -o Fraction.out

```

---

### Post by bikewrecker on 2014-04-23
> **steeldriver said:**
> Most of those undefined reference (linker) errors are likely due to trying to compile C++ with **gcc** instead of **g++**

... You have to be kidding me. I'm so freaking dumb!

Switched to compiling with "c++" and it compiled perfectly. 

Thank you for your help!

---

