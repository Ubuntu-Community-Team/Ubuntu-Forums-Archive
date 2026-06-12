---
title: "problem compiling C++ on my 64 bit."
date: 2008-09-08
forum: Programming Talk
---

### Post by mrsins on 2008-09-08
hi, ive been unable to compile using my 64bit system. 
on terminal this is what happens:

elias@elias-desktop:~/Documents$ g++ hello.cpp -o hello
hello.cpp:10:2: warning: no newline at end of file
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status
elias@elias-desktop:~/Documents$ 


can anyone help me out? thanks.

---

### Post by kjohansen on 2008-09-08
Can you post your hello.cpp?  Have you compiled this file elsewhere with a 32 bit compiler and know that it works?

I assume this is a code issue and not a compiler bug.

---

### Post by Oldsoldier2003 on 2008-09-08
moved to PT

---

### Post by elmoosecapitan on 2008-09-09
Hi, try this:
```
$ *insert editor name* ~/tmp/helloworld.cpp 
```
Paste:
```
#include <iostream>

int main()
{ 
  std::cout << "Hello, World!" << std::endl;
  return 0;
}
```
Save and try:
```
$ g++ ~/tmp/helloworld.cpp -o ~/tmp/helloworld.exe; ~/tmp/helloworld.exe
```

Depending on what and when something fails one should be able to figure the problem. Yes this program works; I just tried it.

---

### Post by elmoosecapitan on 2008-09-09
This is, of course, assuming that the problem lies with the compiler and not with your code.


> **elmoosecapitan said:**
> Hi, try this:
```
$ *insert editor name* ~/tmp/helloworld.cpp 
```
Paste:
```
#include <iostream>

int main()
{ 
  std::cout << "Hello, World!" << std::endl;
  return 0;
}
```
Save and try:
```
$ g++ ~/tmp/helloworld.cpp -o ~/tmp/helloworld.exe; ~/tmp/helloworld.exe
```

Depending on what and when something fails one should be able to figure the problem. Yes this program works; I just tried it.

---

