---
title: "error in My first C++ program......"
date: 2009-08-02
forum: Programming Talk
---

### Post by Dr.AMA on 2009-08-02
[B][COLOR="DimGray"]Hi ....

in my first simple program i have an error i can't solve , and i Hope you guys help me .... :)

the source code is :[/COLOR][/B]

_________________________________________________________________
```

//
//			 
//		Program to convert temperature from Celsius degree
//		units into Fahrenheit degree units:
//		Fahrenheit = Celsius * (212 - 32)/100 + 32
//		Dr.AMA 3-8-2009 

#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

int main(int nNumberofArgs, char* pszArgs[])
{

  // enter the temperature in Celsius
  int celsius;
  cout << " Enter the temperature in Celsius:";
  cin >> celsius;
  // calculate conversion factor for Celsius
  // to Fahrenheit
  int factor;
  factor = 212 - 32;
  // use conversion factor to convert Celsius
  // into Fahrenheit values
  int fahrenheit;
  fahrenheit = factor * celsius/100 + 32;
  // output the results (followed by a NewLine)
  cout << "Fahrenheit value is:";
  cout << fahrenheit << endl;
  // wait until user is ready before terminating program
  // to allow the user to see the program results
  system("PAUSE");
  return 0;
}


```

_____________________________________________________________________

and when i compile it the result was ----->

ama@ama-laptop:~/gcc$ gcc -o test test.cpp
```



/tmp/ccFOUBLj.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x1d): undefined reference to `std::ios_base::Init::Init()'
test.cpp:(.text+0x22): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccFOUBLj.o: In function `main':
test.cpp:(.text+0x78): undefined reference to `std::cout'
test.cpp:(.text+0x7d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
test.cpp:(.text+0x8b): undefined reference to `std::cin'
test.cpp:(.text+0x90): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
test.cpp:(.text+0xcf): undefined reference to `std::cout'
test.cpp:(.text+0xd4): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
test.cpp:(.text+0xe2): undefined reference to `std::cout'
test.cpp:(.text+0xe7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
test.cpp:(.text+0xef): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
test.cpp:(.text+0xf7): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccFOUBLj.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


```

---

### Post by Simian Man on 2009-08-02
Compile with g++ not gcc.  It thinks it is compiling C code, when in fact it's C++.

---

### Post by Dr.AMA on 2009-08-02
[COLOR="DimGray"][B]Thnks .... :D it is work :KS

```


ama@ama-laptop:~/gcc$ ./test
 Enter the temperature in Celsius:40
Fahrenheit value is:104
sh: PAUSE: not found
ama@ama-laptop:~/gcc$ 



```

but the gcc is the same g++  or what ???[/B][/COLOR]

---

### Post by croto on 2009-08-02
Hey Dr., if I may, a couple of comments.

1) F = 5.0/9.0 * C + 32.0

2) I'd recommend using float instead of int for the variables fahrenheit and celcius.

---

### Post by lisati on 2009-08-02
> **Dr.AMA said:**
> [COLOR="DimGray"][B]Thnks .... :D it is work :KS

```


ama@ama-laptop:~/gcc$ ./test
 Enter the temperature in Celsius:40
Fahrenheit value is:104
sh: PAUSE: not found
ama@ama-laptop:~/gcc$ 



```

but the gcc is the same g++  or what ???[/B][/COLOR]
yes and no: gcc is for C, G++ is for c++


btw: the formulae are C= 5/9 x (F - 32) and F=C*9/5+32

---

### Post by Can+~ on 2009-08-02
Another temperature conversion snippet?

:confused:

---

### Post by Cyanidepoison on 2009-08-02
> **Can+~ said:**
> Another temperature conversion snippet?

:confused:
Well, it is more than "hello world".

Also, 
```

system("PAUSE");

```
only does anything on Windows.

---

### Post by Dr.AMA on 2009-08-02
[B][COLOR="DimGray"]thnks All, for Help ....
i start to learn from " C++ for Dummies 5th Edition 2004 " and i think it has many codes that work for Windows Only, i will try to change the Book to anthore one ....[/COLOR][/B]

---

### Post by Cyanidepoison on 2009-08-02
You don't need to do anything to let the user see the output on Linux.  They're already using a terminal, and unlike Windows, it won't disappear when you finish running the program.

---

### Post by JordyD on 2009-08-02
> **Cyanidepoison said:**
> You don't need to do anything to let the user see the output on Linux.  They're already using a terminal, and unlike Windows, it won't disappear when you finish running the program.

It will if you run it from a launcher.
[URL="http://cplusplus.com/forum/beginner/1988/"]
This thread[/URL] has information on how to get the terminal to stay open. It's on another forum, by the way.

---

### Post by Cyanidepoison on 2009-08-02
> **JordyD said:**
> It will if you run it from a launcher.
[URL="http://cplusplus.com/forum/beginner/1988/"]
This thread[/URL] has information on how to get the terminal to stay open. It's on another forum, by the way.
Well, if you really want to start it from a launcher, it is a lot faster just to use getchar();

---

