---
title: "undefined reference to `std::cout'"
date: 2006-11-11
forum: Programming Talk
---

### Post by Blario on 2006-11-11
I've been compiling downloaded software for months now, with little problems.  I went to compile some homework of mine a second ago and got this error,```
In function `main':test.cpp:(.text+0xa): undefined reference to `std::cout'
```, along with a following error for ever other similar reference.  

gcc -v outputs ```
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
```.  

The code of what I was trying to compile is ...

[INDENT]```
#include <iostream>
using namespace std;

int main ()
{
        cout << "this was a test\n";
        return 0;
}
```[/INDENT]

I have the build-essential package installed, and even removed and re-installed it to see if that would help - no success.  Why is it not finding header file iostream?

---

### Post by Blario on 2006-11-11
Answered my own question.  I really didn't want to google myself first but I   ended up doing it afterwards.  I forgot that g++ is the command to be used to compile c++ code. You're supposed to use that.

GCC is today the _G_NU _C_ _C_ollection, which includes gcc (the program) which is GNU C Compiler, and also includes g++, which is the program to be used to compile C++ code.

```
#dpkg -l g++

||/ Name           Version        Description
+++-==============-==============-===========================
ii  g++            4.0.3-1        The GNU C++ compiler
```
```
#dpkg -l gcc

||/ Name           Version        Description
+++-==============-==============-===========================
ii  gcc            4.0.3-1        The GNU C compiler
```

I always forget that when it's been a long time since I actually wrote some code.

---

### Post by ikr1sse on 2008-01-06
Thanks, I had exactly the same problem, hadn't it been for this I'd searched on forever...

---

### Post by abisxir on 2008-08-21
hi
use g++ rather than gcc
or add -lstdc++ to gcc --> gcc -lstdc++ -o test test.cpp

---

### Post by jinksys on 2008-08-21
> **abisxir said:**
> hi
use g++ rather than gcc
or add -lstdc++ to gcc --> gcc -lstdc++ -o test test.cpp

I smell zombies...

It's good you want to help, but it's generally not good to revive posts that are so old.  8 months ago was the last post, and it is a solved post no less.

---

### Post by feyafe on 2009-11-09
> **jinksys said:**
> I smell zombies...

It's good you want to help, but it's generally not good to revive posts that are so old.  8 months ago was the last post, and it is a solved post no less.
yes, maybe you smell zombies, but maybe zombies have good ideas, the post by **abisxir** is pretty useful for some else has the headache of this problem, it is more info no less.

---

### Post by jinksys on 2009-11-09
> **feyafe said:**
> yes, maybe you smell zombies, but maybe zombies have good ideas, the post by **abisxir** is pretty useful for some else has the headache of this problem, it is more info no less.

Blario solved this problem two years ago.
Zombies eat brains, not grow them.

---

### Post by cariboo on 2009-11-10
This thread is really old. It is closed.

---

