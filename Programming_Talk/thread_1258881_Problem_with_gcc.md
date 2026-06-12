---
title: "Problem with gcc"
date: 2009-09-05
forum: Programming Talk
---

### Post by bagljash on 2009-09-05
Hi,

I have problem with my gcc compiler. I've tried compiling newly written program but compiler returned weird output. I tried making some changes to my my program so it does work but same output appeared again. So I tried recompiling my existing programs but again same output.

Can someone help me with this because I'm just learning how to program and I'm also new to Ubuntu.

Here's output that gcc keep giving me 
```
bagljash@bagljash:~/Documents$ gcc factorial.cpp 
/tmp/ccC3Lcc3.o: In function `__static_initialization_and_destruction_0(int, int)':
factorial.cpp:(.text+0x1d): undefined reference to `std::ios_base::Init::Init()'
factorial.cpp:(.text+0x22): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccC3Lcc3.o: In function `main':
factorial.cpp:(.text+0x7f): undefined reference to `std::cout'
factorial.cpp:(.text+0x84): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
factorial.cpp:(.text+0x92): undefined reference to `std::cin'
factorial.cpp:(.text+0x97): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
factorial.cpp:(.text+0xc4): undefined reference to `std::cout'
factorial.cpp:(.text+0xc9): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
factorial.cpp:(.text+0xd1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
factorial.cpp:(.text+0xd9): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccC3Lcc3.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

Thank you in advance.

bagljash

---

### Post by Arndt on 2009-09-05
> **bagljash said:**
> Hi,

I have problem with my gcc compiler. I've tried compiling newly written program but compiler returned weird output. I tried making some changes to my my program so it does work but same output appeared again. So I tried recompiling my existing programs but again same output.

Can someone help me with this because I'm just learning how to program and I'm also new to Ubuntu.

Here's output that gcc keep giving me 
```
bagljash@bagljash:~/Documents$ gcc factorial.cpp 
/tmp/ccC3Lcc3.o: In function `__static_initialization_and_destruction_0(int, int)':
factorial.cpp:(.text+0x1d): undefined reference to `std::ios_base::Init::Init()'
factorial.cpp:(.text+0x22): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccC3Lcc3.o: In function `main':
factorial.cpp:(.text+0x7f): undefined reference to `std::cout'
factorial.cpp:(.text+0x84): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
factorial.cpp:(.text+0x92): undefined reference to `std::cin'
factorial.cpp:(.text+0x97): undefined reference to `std::basic_istream<char, std::char_traits<char> >::operator>>(int&)'
factorial.cpp:(.text+0xc4): undefined reference to `std::cout'
factorial.cpp:(.text+0xc9): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
factorial.cpp:(.text+0xd1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
factorial.cpp:(.text+0xd9): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccC3Lcc3.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

Thank you in advance.

bagljash

What does the program look like?

---

### Post by bagljash on 2009-09-05
Oh sorry I forgot to post it.

```
#include <iostream>

using namespace std;

int main(){
        int num;
        int total = 1;

        cout <<"Enter number \n";
        cin >> num;

        for (int i = 1; i <= num; i++)
                total *= i;

        cout << total <<endl;

        return 0;
}

```

---

### Post by MadCow108 on 2009-09-05
your trying to compile a C++ program with gcc which is for C
use g++ instead

---

### Post by bagljash on 2009-09-05
thx now it works, but in the man page of gcc is written that this is GNU project C and C++ compiler, so why did I have problem compiling C++ program with it?

---

### Post by Sockerdrickan on 2009-09-05
You have to specify the language (C++) as an argument for gcc or use g++

---

### Post by dwhitney67 on 2009-09-05
> **Tux0r said:**
> You have to specify the language (C++) as an argument for gcc or use g++

That's correct.  One can use either:
```

gcc factorial.cpp -lstdc++

```
or
```

g++ factorial.cpp

```
Employ the one that you feel most comfortable typing at the command line.

---

