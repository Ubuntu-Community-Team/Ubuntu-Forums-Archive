---
title: "Compiling Classes"
date: 2010-02-26
forum: Programming Talk
---

### Post by Dromar on 2010-02-26
Hi everybody,

I'm new at programming with Linux, so I wanted to make a very simple application with a class. I looks something like this:

//file: main.cpp
#include <stdio.h>
void main(){
   readbugs *rb = new readbugs();
   return;
}

// file: readbugs.h
#pragma once
#include <stdio.h>
class readbugs{
   readbugs();
   ~readbugs();
};

// file: readbugs.cpp
#include "readbugs.h"
readbugs::readbugs(){ }
readbugs::~readbugs(){ }

As you see it's as simple as possible, but still when I want to compile it with:
     qmake -project main.cpp; qmake; make
I get the following error:
     In file included From readbug.cpp:2:
     readbug.h:3: error: expected constructor, destructor, or type conversion before ';'  
     token

Can you please, tell me what I'm missing, or maybe recommend me another compiler than the QT compiler. (Please not a whole development environment, cause I want to program with the command line :P)

thx for your help

---

### Post by dwhitney67 on 2010-02-26
I recommend that you refresh yourself with C++ before delving into Qt development.

You have an issue with your class declaration; both the constructor and destructor are declared by default, as private.  Presumably you want these declared public, thus you require a "public:" statement within the class.

Second, you need to include your readbug.h file within the main module; otherwise the class declaration will not be known to the compiler.

Third, in C++, typically one uses <iostream> for I/O; not <stdio.h>.  If you must use the C library's stdio.h, then you should include <cstdio>.

Lastly, for such a simple program, you really do not need Qt's qmake.  Just use the command line:
```

g++ main.cpp readbugs.cpp -o myapp

```

---

### Post by Dromar on 2010-02-26
thx, now I can comple it with the g++ compiler, but still not with qmake... do you know the comand for it?

---

