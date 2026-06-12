---
title: "c++ program refuses to compile with g++ on Ubuntu 12.04"
date: 2012-06-01
forum: Packaging and Compiling Programs
---

### Post by zayid on 2012-06-01
Hello, I'm trying to compile a program & though the code seems to be ok, it has refused to compile, it keeps showing errors! The problem is the same code actually did run successfully on windows devc++ application. I saved the program on Desktop as "calc3.cpp", changed directory of terminal to Desktop, then i used this command "gcc calc3.cpp -o calc3" but i get errors.  Below is the program code & also errors

CODE:

```
/* A calculator program without error recovery*/
#include <iostream>
using namespace std;
int main(int argc, char* argv[])
{
    int numerator =1;
    cout << "Pls enter the numerator=";
    cin >>  numerator;
    int denominator =1;
    cout << "Pls enter the denominator=";
    cin >> denominator;
    int DivResult = (numerator/denominator);
    cout << " the answer is =" << DivResult << endl;
    char exitcharacter;
    cout << endl << "press a key + enter=";
    cin >> exitcharacter;
    return 0;
}
```ERRORS:

[HTML]/tmp/ccUf8nqF.o: In function `main':
calc3.cpp:(.text+0x1c): undefined reference to `std::cout'
calc3.cpp:(.text+0x21): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
calc3.cpp:(.text+0x30): undefined reference to `std::cin'
calc3.cpp:(.text+0x35): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
calc3.cpp:(.text+0x4c): undefined reference to `std::cout'
calc3.cpp:(.text+0x51): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
calc3.cpp:(.text+0x60): undefined reference to `std::cin'
calc3.cpp:(.text+0x65): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
calc3.cpp:(.text+0x8d): undefined reference to `std::cout'
calc3.cpp:(.text+0x92): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
calc3.cpp:(.text+0xa2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
calc3.cpp:(.text+0xaa): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
calc3.cpp:(.text+0xb2): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
calc3.cpp:(.text+0xba): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
calc3.cpp:(.text+0xc1): undefined reference to `std::cout'
calc3.cpp:(.text+0xc6): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
calc3.cpp:(.text+0xd6): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
calc3.cpp:(.text+0xe5): undefined reference to `std::cin'
calc3.cpp:(.text+0xea): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::operator>><char, std::char_traits<char> >(std::basic_istream<char, std::char_traits<char> >&, char&)'
/tmp/ccUf8nqF.o: In function `__static_initialization_and_destruction_0(int, int)':
calc3.cpp:(.text+0x112): undefined reference to `std::ios_base::Init::Init()'
calc3.cpp:(.text+0x117): undefined reference to `std::ios_base::Init::~Init()'
collect2: ld returned 1 exit status
[/HTML]Thank you very much.

---

### Post by ksprasad on 2012-06-01
> **zayid said:**
> Hello, I'm trying to compile a program & though the code seems to be ok, it has refused to compile, it keeps showing errors! The problem is the same code actually did run successfully on windows devc++ application. I saved the program on Desktop as "calc3.cpp", changed directory of terminal to Desktop, then i used this command "gcc calc3.cpp -o calc3" but i get errors.
 
If you had used gcc to compile, then it is wrong. You have to use g++ to compile cpp files
 
Regards,
ksprasad

---

### Post by TheFu on 2012-06-01
Looks like you didn't include the std C++ library in your makefile for linking.
$ gcc calc3.cpp -o calc3 -lstdc++ 

You probably want to enable all warnings too -Wall does that.

You might need to add a -L with the library path as well. It has been awhile since I did any C/C++ development.

MS probably automatically added those libs for you ... so you didn't have to learn this yourself.  I consider that a bad practice - YOU should have to know the libraries included in your output program.
I'm pretty certain that gcc will compile C++ code - and has for years.  

This [http://stackoverflow.com/questions/172587/what-is-the-difference-between-g-and-gcc](http://stackoverflow.com/questions/172587/what-is-the-difference-between-g-and-gcc) has a better explanation of the gcc/g++ differences.  It appears that g++ automatically adds libstdc++ to your link for you.

---

### Post by youknowme on 2012-06-01
try using g++ rather than gcc.
infact, g++ (the c++ compiler) will not be installed unless you have installed it in the first place.!

---

### Post by zayid on 2012-06-01
Thanks ksprasad worked like a charm

---

