---
title: "Help in compiling header files with C++ file using GCC"
date: 2010-07-09
forum: Programming Talk
---

### Post by musex on 2010-07-09
Hi everyone

I need help in compiling c++ files with non standard header files, written by me. The problem is that I don't seem to be able to make gcc compile the programs.So here's an easy program,made of 3 files: main.cpp file.h and file.cpp

main.cpp:
```

#include "file.h"
int main(){
print();
return 0;
}

```file.h:
```

#ifndef FILE_H
#define FILE_H

void print();

#endif
```file.cpp:
```

#include <iostream>

using namespace std;
void print(){
    cout<<"prova";
}

```I tried to compile it using codeblocks or by command line using gcc but nothing seems to work.
can you help me? :)
thanks

---

### Post by ibuclaw on 2010-07-09
If you are not going to '**#include "file.h**"' in the file.cpp source file, then try **extern** void print(); in the header instead.

---

### Post by ibuclaw on 2010-07-09
> **musex said:**
> I tried to compile it using codeblocks or by command line using gcc but nothing seems to work.
can you help me? :)
thanks

D'oh, just re-read the question. Don't use GCC, use G++ instead. :)

---

### Post by musex on 2010-07-09
thanks for your answer

ok I used g++ instead of gcc and here's the error message I get 
```
 
claudio@claudio:~/c++/esempio$ g++ main.cpp -o main
/tmp/cchH0IxH.o: In function `main':
main.cpp:(.text+0x7): undefined reference to `print()'
collect2: ld returned 1 exit status

```

---

### Post by musex on 2010-07-09
while using gcc I get this message

```

claudio@claudio:~/c++/esempio$ gcc main.cpp -o main
/tmp/ccSnGpMj.o: In function `main':
main.cpp:(.text+0x7): undefined reference to `print()'
/tmp/ccSnGpMj.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


```

---

### Post by MadCow108 on 2010-07-09
undefined reference is an error in the linking stage (where the compiled object files get merged together)
it means there is no compiled version of print available to the linker.

you have to compile file.cpp too.
There are many ways:
g++ -c file.cpp -o file.o // -c means compile only, no linking
g++ -c main.cpp -o main.o
g++ main.o file.o -o executablename // now we link

or more convenient all at once:
g++ main.cpp file.cpp -o executablename

internally this does he same as above just that it deletes the temporary object files after its finished (but you can keep them with -fsave-temps)

---

### Post by GeneralZod on 2010-07-09
> **musex said:**
> thanks for your answer

ok I used g++ instead of gcc and here's the error message I get 
<snip>


Using g++ instead of gcc is correct.

Try

```
 
claudio@claudio:~/c++/esempio$ g++ main.cpp file.cpp -o main

```

---

### Post by musex on 2010-07-09
Ok thanks. I used your last command 
```
g++ main.cpp file.cpp -o executablename
```

and it generates the executable file. But when I try to run it doesn't show anything,while it's supposed to print a message.is there an error in the source code?

---

### Post by MadCow108 on 2010-07-09
try adding 
<< endl
or
<< flush
after the output line.

This causes the stdout buffer to be flushed and the message to appear immediately (the first also adds a line break).
Without the line break it will probably appear before the shell prompt.

---

### Post by musex on 2010-07-09
Ok thanks a lot  everyone :D
it works perfectly now.

---

### Post by trent.josephsen on 2010-07-09
As ibuclaw mentioned already, you should #include your header file in the implementation so both files (main.cpp and file.cpp) always see the same declarations.  (I don't think adding extern will change anything, though, because IIRC function declarations always have external linkage.  It's different with objects.)

As for it not printing anything, that could be because you aren't putting a newline at the end (works for me either way, though).

---

