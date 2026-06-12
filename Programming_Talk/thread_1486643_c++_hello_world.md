---
title: "c++ hello world"
date: 2010-05-18
forum: Programming Talk
---

### Post by l3ecl on 2010-05-18
I've programmed c++ in windows before but in Ubuntu I can't even hello world. 
This is my code
> 
#include <stdio.h>
#include <stdlib.h>
#include <iostream>

using namespace std; 

int main()
{
    cout << "hello world" << endl;
    return 0;
}and this is my error:

```
gg@Ubuntu:~/Desktop$ gcc -g -o hello hello.c
```> hello.c:4:20: error: iostream: No such file or directory
hello.c:6: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;namespace&#8217;
hello.c: In function &#8216;main&#8217;:
hello.c:10: error: &#8216;cout&#8217; undeclared (first use in this function)
hello.c:10: error: (Each undeclared identifier is reported only once
hello.c:10: error: for each function it appears in.)
hello.c:10: error: &#8216;endl&#8217; undeclared (first use in this function)Im also confused about files ending with .c, since in windows it was  either .h or .cpp. Do I treat .c files as the .cpp equivalent of  windows? Help please.

---

### Post by Some Penguin on 2010-05-18
g++

---

### Post by Tony Flury on 2010-05-18
gcc will invoke g++ if it gets a C++ source code.

two things : 

One make sure you have everything installed : 
```

sudo apt-get install g++ build-essential

```

Two - given the code fragment you have - you don't need to include stdio.h - If at any point you need to use the C style functions (fprintf etc) then it is best to include "cstdio".

Three - to make it easy on the compiler - use ".cpp" for C++ source code.

---

### Post by km0r3 on 2010-05-18
> **l3ecl said:**
> Do I treat .c files as the .cpp equivalent of  windows? Help please.

Actually, you *should* call them *.cpp when they're CPP.

Your sole error was using `gcc` which is the C-Compiler, instead of `g++` which is the C++-Compiler.

---

### Post by l3ecl on 2010-05-18
i got it working! thanks alot for the explanations. 

when programming c++ in ubuntu, i hear all you need is vi + gcc + make. i've used vi and gcc but where does 'make' come into play?

also how would you be able to make GUI applications? would you need an IDE or do people actually use vi haha. it would be pretty hardcore if you wrote 900 lines for a Form1.

---

### Post by schauerlich on 2010-05-18
You use make when your program contains a bunch of different files. Basically, make decides which files need to be recompiled based on the last time they were modified, and links the whole project together based on rules that you give it. It keeps you from having to run gcc over and over again every time you change one little thing.

---

### Post by MindSz on 2010-05-18
> **schauerlich said:**
> You use make when your program contains a bunch of different files. Basically, make decides which files need to be recompiled based on the last time they were modified, and links the whole project together based on rules that you give it. It keeps you from having to run gcc over and over again every time you change one little thing.

But in order to use that, you need to create a "Makefile" that contains all the rules for the building of your project.

---

### Post by soltanis on 2010-05-18
> **l3ecl said:**
> it would be pretty hardcore if you wrote 900 lines for a Form1.

My motto is that if you write 900 lines of something, chances are you're doing it wrong.

---

### Post by mmix on 2010-05-18
try anjuta or openldev,
it make Makefile automatically.

---

### Post by TheStatsMan on 2010-05-18
> **soltanis said:**
> My motto is that if you write 900 lines of something, chances are you're doing it wrong.

 They really screwed up with the Linux Kernel, being way bigger than 900 lines and all.

---

### Post by Tony Flury on 2010-05-18
> **l3ecl said:**
> i got it working! thanks alot for the explanations. 

when programming c++ in ubuntu, i hear all you need is vi + gcc + make. i've used vi and gcc but where does 'make' come into play?

also how would you be able to make GUI applications? would you need an IDE or do people actually use vi haha. it would be pretty hardcore if you wrote 900 lines for a Form1.

You can use a GUI designer (like glade) without going anywhere near an IDE. For the most part the two are distinct things - unlike in MS Windows world where the IDE has form designers as part of the production process.

Most GUI frameworks have APIs as well (GTK for instance) - it is perfectly possible to write applications that have full featured gui's using the APIs and not going anywhere near a form designer.

---

### Post by trent.josephsen on 2010-05-18
> **km0r3 said:**
> Actually, you *should* call them *.cpp when they're CPP.

Your sole error was using `gcc` which is the C-Compiler, instead of `g++` which is the C++-Compiler.

Pardon my intrusion, but gcc stands for GNU Compiler Collection, not GNU C Compiler as it once did back in the 1980s.  gcc is a perfectly appropriate tool to compile C++ source files.  The OP's mistake was giving C++ source files a .c extension so gcc assumed they were C and not C++.

---

### Post by DangerOnTheRanger on 2010-05-18
> **soltanis said:**
> My motto is that if you write 900 lines of something, chances are you're doing it wrong.

If that's the case, don't let me start with Windows! :)

Seriously, though, some things *do *go way above 900 lines(Firefox is most likely above that), also, OS kernel go above that(even *Minix does*).

---

### Post by schauerlich on 2010-05-19
> **DangerOnTheRanger said:**
> If that's the case, don't let me start with Windows! :)

Seriously, though, some things *do *go way above 900 lines(Firefox is most likely above that), also, OS kernel go above that(even *Minix does*).

True, but a good rule of thumb is that if a single file or object is pushing 1000 lines, there's probably a better way to modularize/abstract it. This obviously won't be the case all of the time.

---

### Post by Zugzwang on 2010-05-19
> **trent.josephsen said:**
> gcc is a perfectly appropriate tool to compile C++ source files.  The OP's mistake was giving C++ source files a .c extension so gcc assumed they were C and not C++.

Yes and no. For some reason this comment comes up again and again in this forums. While "gcc" is OK for compiling C++ files, for *linking* them it is not so appropriate at you'll need to provide some libraries manually (which is probably more complicated than simply using "g++"). As the OP did both in one step, he/she should really rather use g++ instead.

Here's an example:
```

me@mycomputer:/tmp$ cat test.cpp
#include <iostream>

int main(int argc, const char **args) {
    std::cout << "Hello!" << std::endl;
}
me@mycomputer:/tmp$ gcc test.cpp
/tmp/ccamliJV.o: In function `main':
test.cpp:(.text+0x1c): undefined reference to `std::cout'
test.cpp:(.text+0x21): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
test.cpp:(.text+0x29): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
test.cpp:(.text+0x31): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/ccamliJV.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x60): undefined reference to `std::ios_base::Init::Init()'
test.cpp:(.text+0x65): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccamliJV.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
me@mycomputer:/tmp$ g++ test.cpp
me@mycomputer:/tmp$ gcc -lstdc++ test.cpp
me@mycomputer:/tmp$


```

---

