---
title: "problem linking through 'ld'"
date: 2008-06-23
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-23
i just began studying c++ and i started it off on ubuntu.
this program is what i can compile, but cant link through ld:
```

//mn.cpp
#include <cstdlib>
 #include <iostream>
 using namespace std;
 double square(double);
 int main(int argc, char *argv[])
 {
     if (argc != 2) {
         cerr << "Usage: square <number>" << endl;
         return 1;
    }
    double n = strtod(argv[1], 0);
    cout << "The square of " << argv[1] << " is " << square(n) << endl;
    return 0;
 }

```
```

//sq.cpp
double square(double n)
{
return n*n;
}

```
i am compiling these through:
```
g++ -Wall -c <filename> ...which gives a filename.o file
```
now i try linking them through ld:
```

dpak@dpak-server:~/ccpp/qt$ ld mn.o sq.o -o sqr
ld: warning: cannot find entry symbol _start; defaulting to 0000000008048094
mn.o: In function `std::__verify_grouping(char const*, unsigned int, std::string const&)':
mn.cpp:(.text+0xe): undefined reference to `std::string::size() const'
mn.cpp:(.text+0x59): undefined reference to `std::string::operator[](unsigned int) const'
mn.cpp:(.text+0x97): undefined reference to `std::string::operator[](unsigned int) const'
mn.cpp:(.text+0xdf): undefined reference to `std::string::operator[](unsigned int) const'
mn.o: In function `__static_initialization_and_destruction_0(int, int)':
mn.cpp:(.text+0x129): undefined reference to `std::ios_base::Init::Init()'
mn.cpp:(.text+0x131): undefined reference to `__dso_handle'
mn.cpp:(.text+0x145): undefined reference to `__cxa_atexit'
mn.o: In function `__tcf_0':
mn.cpp:(.text+0x176): undefined reference to `std::ios_base::Init::~Init()'
mn.o: In function `main':
mn.cpp:(.text+0x1a4): undefined reference to `std::cerr'
mn.cpp:(.text+0x1a9): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
mn.cpp:(.text+0x1b1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
mn.cpp:(.text+0x1b9): undefined reference to `std::ostream::operator<<(std::ostream& (*)(std::ostream&))'
mn.cpp:(.text+0x1e0): undefined reference to `strtod'
mn.cpp:(.text+0x20b): undefined reference to `std::cout'
mn.cpp:(.text+0x210): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
mn.cpp:(.text+0x21c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
mn.cpp:(.text+0x22c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
mn.cpp:(.text+0x23b): undefined reference to `std::ostream::operator<<(double)'
mn.cpp:(.text+0x243): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
mn.cpp:(.text+0x24b): undefined reference to `std::ostream::operator<<(std::ostream& (*)(std::ostream&))'
mn.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'

```



this turns out to be all gibberish to me...please help me.

---

### Post by nvteighen on 2008-06-23
You're not linking to the Standard Library.

Anyway, you don't need to do through that. This single line will generate the executable "myprogram" (-o flag defines output's name) and link it to what you need.
```

g++ -o myprogram sqr.cpp mn.cpp -Wall

```

But, if you want to do two-stages compiling, you also can do it, with g++ in **both stages**:
```

g++ -c sqr.cpp mn.cpp -Wall

```
That creates sqr.o and mn.o, both object files. Now, we link them with:
```

g++ -o myprogram sqr.o mn.o -Wall

```
Yes: the compiler knows what to do depending on file type! Two-stages compilation has its advantages for big projects, where you can't just rebuild the whole thing just to fix one single source file. By creating intermediate, object files, you just rebuild what you need and relink the final executable (but this is usually done with the "make" utility... not manually).

---

### Post by dexter.deepak on 2008-06-23
thanks a lot.
i am new to c++ , si i would like to ask you some more questions ..
A) in the two step process ...compling and then building...why are we needing the "-Wall" option in the first line (during compilation) as well as the second line (during linking) ?

B) how to use ld here/anywhere ? afterall in the manual page , it has been called the "gnu linker" 

C) (as you pointed out make) what is the difference between ld and make ?

---

### Post by dexter.deepak on 2008-06-23
OO!!
i am very sorry for the A part of my questions....what i thought was that Wall option was meant for "building/linking"...i later on found that it just is an option for listing "all the warnings".
stupid me :mad:

but you can still answer the second and the third questions..

---

### Post by JupiterV2 on 2008-06-23
> **dexter.deepak said:**
> thanks a lot.
i am new to c++ , si i would like to ask you some more questions ..
A) in the two step process ...compling and then building...why are we needing the "-Wall" option in the first line (during compilation) as well as the second line (during linking) ?


You already answered your question, so no need for me to repeat it.

> 
B) how to use ld here/anywhere ? afterall in the manual page , it has been called the "gnu linker" 


It IS the gnu linker but g++ does a lot of the work for you, like linking to the standard libraries, that using ld would require you do manually. I can't really think of a good reason off hand why you would want to use the ld command over g++ to link files.

> 
C) (as you pointed out make) what is the difference between ld and make ?

ld is a linker, gnu make is a utility for helping to build projects. Basically, make is a script that will build a project for you once you have set it up correctly. If you have multiple object files, it will check if they need updating (if the source (.cpp) file is newer than the object file (.o) it will recompile the source file). So, if you have 10 different objects for your project but only one is out of date, it will only recompile the once source and relink them together, saving you a LOT of time.

---

### Post by dexter.deepak on 2008-06-23
thanks a lot !!:)

---

### Post by dwhitney67 on 2008-06-23
> **JupiterV2 said:**
> ...
gnu make is a utility for helping to build projects. Basically, make is a script that will build a project for you once you have set it up correctly. If you have multiple object files, it will check if they need updating (if the source (.cpp) file is newer than the object file (.o) it will recompile the source file). So, if you have 10 different objects for your project but only one is out of date, it will only recompile the once source and relink them together, saving you a LOT of time.
If only it were that easy.  :-)

For instance, there may be a case when a single header file is updated, and one or more source files depend upon it.  Unfortunately these source files will not get rebuilt auto-magically unless there are statements added to the Makefile to generate/check for file dependencies.

---

