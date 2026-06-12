---
title: "Could someone please tell me why this C++ wont compile"
date: 2007-01-05
forum: Programming Talk
---

### Post by Jamesbowden on 2007-01-05
```
//

// Program to convert temperature from Celsius degrees

// unit into Fahrenheit degree units:

// Fahrenheit = Celsius * (212 - 32)/100 +32

//

#include <cstdio>

#include <cstdlib>

#include <iostream>

using namespace std;



int  main(int nNumberofargs, char* pszArgs[])

{

// enter temperature in Celsius

int celsius;

cout << "Enter the temperature in Celsius:";

cin >> celsius;



// calculate conversion factor for Celsius 

// into Fahrenheit 

int factor; 

factor = 212 - 32;



// use conversion factor to convert Celsius

// into fahrenheit values

int fahrenheit;

fahrenheit = factor * celsius/100 + 32;



// output the result (followed by a NewLine)

cout << "Fahrenheit value is:";

cout << fahrenheit << endl;



// wait until user is ready before terminating program.

system ("PAUSE");

return 0;

}
```

Can someone please tell me why this program wont compile when i use

```
gcc -o cel2fah cel2fah.cpp
```

I get this output, i compiled just fine under dev-c++ in windows.

```

/tmp/ccPzGUbd.o: In function `__static_initialization_and_destruction_0(int, int)':
cel2fah.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccPzGUbd.o: In function `__tcf_0':
cel2fah.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccPzGUbd.o: In function `main':
cel2fah.cpp:(.text+0x8e): undefined reference to `std::cout'
cel2fah.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
cel2fah.cpp:(.text+0xa1): undefined reference to `std::cin'
cel2fah.cpp:(.text+0xa6): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
cel2fah.cpp:(.text+0xe5): undefined reference to `std::cout'
cel2fah.cpp:(.text+0xea): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
cel2fah.cpp:(.text+0xf8): undefined reference to `std::cout'
cel2fah.cpp:(.text+0xfd): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
cel2fah.cpp:(.text+0x105): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
cel2fah.cpp:(.text+0x10d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccPzGUbd.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

---

### Post by Pluk on 2007-01-05
from:
[http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html#single_source_cpp](http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html#single_source_cpp)

for gcc to understand it is C++ code you have to change your file extension to .cc
or use c++ as your compiler

```
gcc -o cel2fah cel2fah.cc
```

or

```
c++ -o cel2fah cel2fah.cpp
```

---

### Post by Jamesbowden on 2007-01-05
Thanks very much, i have never had to do that before, its strange.

---

### Post by Jucato on 2007-01-05
Actually, no... you don't need to rename .cpp to .cc. You just have to use g++ instead of gcc or gcc with the proper C++ switches. g++ is the GNU C Compiler, g++ uses the same compiler with the proper C++ switches. So your command to compile would be:

```
g++ -o cel2fah cel2fah.cpp
```

---

