---
title: "compiling for other OS's"
date: 2008-04-08
forum: Programming Talk
---

### Post by phoenix5002 on 2008-04-08
I am using Ubuntu.
But, I'm wondering if it's possible to compile a .exe that could be run on windows (or with wine).

---

### Post by LaRoza on 2008-04-08
> **phoenix5002 said:**
> I am using Ubuntu.
But, I'm wondering if it's possible to compile a .exe that could be run on windows (or with wine).

Yes.

[http://ubuntuforums.org/showthread.php?t=161605](http://ubuntuforums.org/showthread.php?t=161605)

---

### Post by scragar on 2008-04-08
[http://ubuntuforums.org/showpost.php?p=4342027&postcount=5](http://ubuntuforums.org/showpost.php?p=4342027&postcount=5)

---

### Post by WW on 2008-04-08
Yes, it's called cross-compiling.  There is an example in this thread: [http://ubuntuforums.org/showthread.php?t=724495](http://ubuntuforums.org/showthread.php?t=724495)

---

### Post by phoenix5002 on 2008-04-08
I tried this:
[b]sudo apt-get install mingw32
sudo apt-get install mingw32-binutils
sudo apt-get install mingw32-runtime[/b]

then I tried to compile it with:
**i586-mingw32msvc-gcc test.cpp -o test.exe**
I get a bunch of errors, output:
```
/tmp/ccKJ6EqV.o:test.cpp:(.text+0xe): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'
/tmp/ccKJ6EqV.o:test.cpp:(.text+0x52): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/ccKJ6EqV.o:test.cpp:(.text+0x8b): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/ccKJ6EqV.o:test.cpp:(.text+0xd0): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[](unsigned int) const'
/tmp/ccKJ6EqV.o:test.cpp:(.text+0x121): undefined reference to `std::cout'
/tmp/ccKJ6EqV.o:test.cpp:(.text+0x126): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccKJ6EqV.o:test.cpp:(.text+0x158): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccKJ6EqV.o:test.cpp:(.text+0x19b): undefined reference to `std::ios_base::Init::~Init()'
collect2: ld returned 1 exit status

```

***EDIT: I should mention that the program is a simple "hello world" program in C++***

I'm assuming this is because it's not finding the library.  I'm just using
**#include <iostream>**

---

### Post by LaRoza on 2008-04-08
> **phoenix5002 said:**
> I tried this:
[b]sudo apt-get install mingw32
sudo apt-get install mingw32-binutils
sudo apt-get install mingw32-runtime[/b]

then I tried to compile it with:
**i586-mingw32msvc-gcc test.cpp -o test.exe**

***EDIT: I should mention that the program is a simple "hello world" program in C++***

I'm assuming this is because it's not finding the library.  I'm just using
**#include <iostream>**

Does that work with C++? If it works like gcc, you will have to specify the language.

---

### Post by phoenix5002 on 2008-04-09
got it :)

just did:
**i586-mingw32msvc-g++ test.cpp -o test.exe**
instead.  changed it from **gcc** to **g++**

thanx

---

