---
title: "undefined reference to `std::cout'"
date: 2008-12-14
forum: Programming Talk
---

### Post by Bucephalus01 on 2008-12-14
Hi

I'm trying to set my netbeans environment for cpp programming and I'm having trouble running a simple hello  world program. It seems that it can't recognise::: 
 
```

// For construction of filebuffers for cout, cin, cerr, clog et. al.
static ios_base::Init __ioinit;

```

in the iostream  header file.
Here is my code followed by the output.
```

#include <iostream>

int main(int argc, char**argv) {
    // Prints welcome message...
    std::cout << "Hello World" << std::endl;
    return 0;
}

```
 
Running "/usr/bin/make  -f Makefile CONF=Debug" in /home/david/NetBeansProjects/Welcome_1

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/david/NetBeansProjects/Welcome_1'
/usr/bin/make  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/welcome_1
make[2]: Entering directory `/home/david/NetBeansProjects/Welcome_1'
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/welcome.o.d
gcc    -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/welcome.o.d -o build/Debug/GNU-Linux-x86/welcome.o welcome.cc
mkdir -p dist/Debug/GNU-Linux-x86
gcc     -o dist/Debug/GNU-Linux-x86/welcome_1 build/Debug/GNU-Linux-x86/welcome.o  
build/Debug/GNU-Linux-x86/welcome.o: In function `main':
/home/david/NetBeansProjects/Welcome_1/welcome.cc:46: undefined reference to `std::cout'
/home/david/NetBeansProjects/Welcome_1/welcome.cc:46: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/home/david/NetBeansProjects/Welcome_1/welcome.cc:46: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
/home/david/NetBeansProjects/Welcome_1/welcome.cc:46: undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
build/Debug/GNU-Linux-x86/welcome.o: In function `__static_initialization_and_destruction_0':
/usr/include/c++/4.3/iostream:77: undefined reference to `std::ios_base::Init::Init()'
/usr/include/c++/4.3/iostream:77: undefined reference to `std::ios_base::Init::~Init()'
build/Debug/GNU-Linux-x86/welcome.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/welcome_1] Error 1
make[2]: Leaving directory `/home/david/NetBeansProjects/Welcome_1'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/david/NetBeansProjects/Welcome_1'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.

Any ideas please???
Thanks.

---

### Post by geirha on 2008-12-14
Based on the output, it's using gcc (the c compiler) to compile, and not g++ (the c++ compiler) ...

---

### Post by Bucephalus01 on 2008-12-14
Hey

I changed over to g++ and it worked.
Thanks for your help.

---

