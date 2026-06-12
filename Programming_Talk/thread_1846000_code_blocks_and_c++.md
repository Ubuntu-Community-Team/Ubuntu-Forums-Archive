---
title: "code blocks and c++"
date: 2011-09-18
forum: Programming Talk
---

### Post by med linux on 2011-09-18
hello 

I use code Blocks  and c++  in ubuntu 10.04 
 iused this code 
```
#include <iostream>

using namespace std;

int main()
{
    cout << "Hello world!" << endl;
    return 0;
}

```
and It won't work 

the build log shows 
```


-------------- Build: Debug in aa ---------------

Compiling: main.cpp
Linking console executable: bin/Debug/aa
obj/Debug/main.o: In function `main':
/home/user/Desktop/aa/main.cpp:7: undefined reference to `std::cout'
/home/user/Desktop/aa/main.cpp:7: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/home/user/Desktop/aa/main.cpp:7: undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
/home/user/Desktop/aa/main.cpp:7: undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
obj/Debug/main.o: In function `__static_initialization_and_destruction_0':
/usr/include/c++/4.4/iostream:72: undefined reference to `std::ios_base::Init::Init()'
/usr/include/c++/4.4/iostream:72: undefined reference to `std::ios_base::Init::~Init()'
obj/Debug/main.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 0 seconds)
7 errors, 0 warnings
 


```

what should i do ?? :!::?

---

### Post by dwhitney67 on 2011-09-18
Try compiling the code as a C++ project, not a C project.  If you don't know how to do this, refer to the Code Blocks documentation.

---

### Post by med linux on 2011-09-18
ok i have found the solution 
the solution 
go to settings/compiler and debbugers/tollchain executables 
and replace gcc by g++  in c++ compiler and linker for dynamic libs 
thats all ^^

thnks for all

---

