---
title: "How to set up GCC?"
date: 2005-11-02
forum: Packaging and Compiling Programs
---

### Post by Zingam on 2005-11-02
I've installed GCC 4.0 (breezy) but I still get these error messages when I try to compile the "Helloworld" program:
```

hristo@roccoor:~/Desktop/untitled folder 1$ make
gcc-4.0 -Wall -ansi main.cpp -o startme
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from main.cpp:1:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
/tmp/cc1IvVE3.o: In function `main':
main.cpp:(.text+0x25): undefined reference to `std::cout'
main.cpp:(.text+0x2a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/cc1IvVE3.o: In function `__tcf_0':
main.cpp:(.text+0x47): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc1IvVE3.o: In function `__static_initialization_and_destruction_0(int, int)':
main.cpp:(.text+0x74): undefined reference to `std::ios_base::Init::Init()'
/tmp/cc1IvVE3.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
make: *** [all] Error 1
hristo@roccoor:~/Desktop/untitled folder 1$ make
gcc-4.0 -Wall -ansi main.cpp -o startme
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from main.cpp:1:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
/tmp/ccxe43JY.o: In function `main':
main.cpp:(.text+0x25): undefined reference to `std::cout'
main.cpp:(.text+0x2a): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccxe43JY.o: In function `__tcf_0':
main.cpp:(.text+0x47): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccxe43JY.o: In function `__static_initialization_and_destruction_0(int, int)':
main.cpp:(.text+0x74): undefined reference to `std::ios_base::Init::Init()'
/tmp/ccxe43JY.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
make: *** [all] Error 1
```

---

### Post by stuporglue on 2005-11-02
Did you run ./configure first? 

After re-running configure, make clean, then make again. 

does it fix anything?

---

### Post by niko_ on 2005-11-02
try maybe with older gcc

export CC=/usr/bin/gcc-3.4

and then make

---

### Post by Zingam on 2005-11-02
I've used Synaptic to install GCC and I have both GCC-4.0 and GCC-3.4 installed. I had to install GCC-3.4 for the ATI driver to compile and it did sucessfully.

> Did you run ./configure first?

After re-running configure, make clean, then make again.

does it fix anything?

That's why I don't understand, why I should do what you suggest. I'm not installing it form the sources.

---

### Post by hearty on 2006-02-20
apt-get install build-essential should solve your problem

---

### Post by healychan on 2006-02-20
Follow the link in my signature will solve your problem.

---

### Post by gtm631 on 2007-04-23
With Ubuntu 7.04 after
> sudo apt-get install g++ build-essential

got same
bla-bla undefined reference to `std::ios_base::Init::Init()'
when compiling c++ test. The ugly thing, std lib is there,
but is not referenced in linker invokation. Instead of

gcc -o yourexeResult YourSource.cpp

do

gcc -lstdc++ -o yourexeResult YourSource.cpp

and everything compiles. Looks like a config bug for
whoever configured g++ for Ubuntu.

- Alex

---

### Post by WW on 2007-04-24
If your program is C++, you should use the command **g++** instead of **gcc**.

---

