---
title: "Can't compile c++ programs using gcc command"
date: 2009-03-19
forum: Programming Talk
---

### Post by sreeyeshns on 2009-03-19
I'm beginning c++ programming. I tried to compile the following program using the command. 

```
gcc -o asd asd.cpp
```I got the following message.

/tmp/ccNZRqsT.o: In function `main':
asd.cpp:(.text+0x1c): undefined reference to `std::cout'
asd.cpp:(.text+0x21): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccNZRqsT.o: In function `__static_initialization_and_destruction_0(int, int)':
asd.cpp:(.text+0x50): undefined reference to `std::ios_base::Init::Init()'
asd.cpp:(.text+0x55): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccNZRqsT.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

But I successfully compiled the program using the command

```
g++ -o asd asd.cpp
```I'm interested to know what's wrong with gcc and if there is something missing in the command 

```
#include<iostream>
int main()
{
        std::cout << "Welcome\n";
        return 0;
}

```

---

### Post by simeon87 on 2009-03-19
gcc is for C, g++ is for C++.

---

### Post by sreeyeshns on 2009-03-19
> **simeon87 said:**
> gcc is for C, g++ is for C++.
Are you sure? I heard gcc is a c/c++ compiler.

---

### Post by jelle_ on 2009-03-19
hello

gcc is the gnu c compiler. like the name said, it compiles c-programs. you are using c++, so you must use g++.

---

### Post by dwhitney67 on 2009-03-19
'gcc' can be used to compile C++ applications, but you need to specify the libstdc++ library when linking.
```

gcc -o asd asd.cpp -lstdc++

```
Of course, nobody likes to type alot, so as others have mentioned, it is easier to use 'g++' instead.

---

### Post by jelle_ on 2009-03-19
gcc is both the gnu c compiler and the gnu compiler collection. this collection contains many different compilers. the compiler for c-code is called gcc, the compiler for c++ is called g++.

---

### Post by sreeyeshns on 2009-03-19
Thank you guys for the information.

---

### Post by sreeyeshns on 2009-03-19
> **dwhitney67 said:**
> 'gcc' can be used to compile C++ applications, but you need to specify the libstdc++ library when linking.
```

gcc -o asd asd.cpp -lstdc++

```
Of course, nobody likes to type alot, so as others have mentioned, it is easier to use 'g++' instead.
That's a good reply. Thank you very much. Are gcc and g++ the same? If not, which one is better?

---

### Post by carml on 2009-03-19
If I'm not wrong,you can install g++ for C++ code and call also gcc to compile a C++ source code,because it's gcc that resolves the links. :)

---

### Post by abhilashm86 on 2009-03-19
> **sreeyeshns said:**
> That's a good reply. Thank you very much. Are gcc and g++ the same? If not, which one is better?

actually when you talk about gcc and g++, they both are compeletely different compilers,
c++ is much higher and extended object oriented language, some also tell c++ extension of c.............
hence you can easily compile c with g++ compiler(bison c++) but can't do vice versa

---

### Post by dwhitney67 on 2009-03-19
> **sreeyeshns said:**
> That's a good reply. Thank you very much. Are gcc and g++ the same? If not, which one is better?

"Same same, but different."  :P

Think of g++ as an extension to gcc, that is used for _linking_ C++ code (and C code).  'gcc' can be used to _compile_ C and C++ code, but if you want to link the C++ code, you will need to specify the -lstdc++.

As stated earlier, it is easier and commonplace to use 'g++' when compiling/linking C++ applications.

---

### Post by sreeyeshns on 2009-03-19
> **dwhitney67 said:**
> "Same same, but different."  :P

Think of g++ as an extension to gcc, that is used for _linking_ C++ code (and C code).  'gcc' can be used to _compile_ C and C++ code, but if you want to link the C++ code, you will need to specify the -lstdc++.

As stated earlier, it is easier and commonplace to use 'g++' when compiling/linking C++ applications.
Ok. Thank you very much for your valuable information.

---

