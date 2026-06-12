---
title: "Problems compiling &quot;Hello World&quot; (C++) in Ubuntu 12.10 using CodeBlocks"
date: 2013-03-11
forum: Programming Talk
---

### Post by Niles M on 2013-03-11
Hi

I have finished installing Ubuntu 12.10 and CodeBlocks from the Software Center. I haven't worked with Linux before. I have the following C++ script in CodeBlocks:

```

#include <iostream>

using namespace std;

int main()
{
    cout << "Hello world!" << endl;
    return 0;
}

```

When I press F9 (build and run), CodeBlocks gives me the message: 

||=== asd, Debug ===|
obj/Debug/main.o||In function `main':|
/home/niles/asd/main.cpp|7|undefined reference to `std::cout'|
/home/niles/asd/main.cpp|7|undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'|
/home/niles/asd/main.cpp|7|undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'|
/home/niles/asd/main.cpp|7|undefined reference to `std::ostream::operator<<(std::ostream& (*)(std::ostream&))'|
obj/Debug/main.o||In function `__static_initialization_and_destruction_0':|
/usr/include/c++/4.7/iostream|75|undefined reference to `std::ios_base::Init::Init()'|
/usr/include/c++/4.7/iostream|75|undefined reference to `std::ios_base::Init::~Init()'|
||=== Build finished: 6 errors, 0 warnings ===|

The compiler is g++. I don't really understand what is going on, the namespace is correct. Thanks for any help in advance.

---

### Post by dwhitney67 on 2013-03-11
Does this look familiar... from the command line:
```

$ gcc foo.cpp 
/tmp/ccMeBXOS.o: In function `main':
foo.cpp:(.text+0xa): undefined reference to `std::cout'
foo.cpp:(.text+0xf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
foo.cpp:(.text+0x14): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
foo.cpp:(.text+0x1c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccMeBXOS.o: In function `__static_initialization_and_destruction_0(int, int)':
foo.cpp:(.text+0x4a): undefined reference to `std::ios_base::Init::Init()'
foo.cpp:(.text+0x4f): undefined reference to `std::ios_base::Init::~Init()'
collect2: ld returned 1 exit status

```
CodeBlocks is using 'gcc', not 'g++.

---

### Post by Niles M on 2013-03-11
> **dwhitney67 said:**
> Does this look familiar... from the command line:
```

$ gcc foo.cpp 
/tmp/ccMeBXOS.o: In function `main':
foo.cpp:(.text+0xa): undefined reference to `std::cout'
foo.cpp:(.text+0xf): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
foo.cpp:(.text+0x14): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
foo.cpp:(.text+0x1c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccMeBXOS.o: In function `__static_initialization_and_destruction_0(int, int)':
foo.cpp:(.text+0x4a): undefined reference to `std::ios_base::Init::Init()'
foo.cpp:(.text+0x4f): undefined reference to `std::ios_base::Init::~Init()'
collect2: ld returned 1 exit status

```
CodeBlocks is using 'gcc', not 'g++.


I just double-checked, and my CodeBlocks is set to use g++ for C++, gcc for C.

---

### Post by dwhitney67 on 2013-03-11
Check you system to ensure that you do indeed have 'g++' installed.
```

sudo apt-get install g++

```
If it is installed, then I suppose it's a CodeBlock issue.

---

### Post by SledgeHammer_999 on 2013-03-11
Maybe CodeBlocks thinks that this is a C source file and tries to compile it with gcc. Somewhere in the project settings you should be able to switch it to C++.

---

### Post by Niles M on 2013-03-11
> **dwhitney67 said:**
> Check you system to ensure that you do indeed have 'g++' installed.
```

sudo apt-get install g++

```
If it is installed, then I suppose it's a CodeBlock issue.

I tried this and it says "g++ is already the newest version"




> **SledgeHammer_999 said:**
> Maybe CodeBlocks thinks that this is a C source file and tries to compile it with gcc. Somewhere in the project settings you should be able to switch it to C++.

Good point. I solved the problem: The linker was set to GCC, but I changed in to g++ (the C++ compiler was already g++). It works now, thanks to both of you.

Best,
Niles.

---

