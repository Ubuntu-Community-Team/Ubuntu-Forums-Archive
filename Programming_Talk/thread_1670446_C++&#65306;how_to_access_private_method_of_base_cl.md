---
title: "C++&#65306;how to access private method of base class"
date: 2011-01-18
forum: Programming Talk
---

### Post by koala114 on 2011-01-18
```

#include <iostream>

namespace my{
class A {

public:
        void OUTPUT();
};

class B: private A{
public:
    B(){std::cout<<"hi ford";}
    //using A::OUTPUT;
    void OUTPUT();
};
class C: private B{
    public:
        C(){std::cout<<"hi C";}
        //using my::B::OUTPUT;
        void xxx();
};
}

``````
#include "heritance.h"

void my::A::OUTPUT(){
std::cout<< "hhhhh";
}

void my::B::OUTPUT(){
A::OUTPUT();
}

void xxx(){
//OUTPUT();
}

```
```
#include "heritance.h"

int main(){
  using namespace my;
  B b;
  b.OUTPUT();
  return 0;
}

```
debian:~/src# g++ main.cpp
/tmp/ccSXkBAc.o: In function `main':
main.cpp:(.text+0x7f): undefined reference to `my::B::OUTPUT()'
collect2: ld returned 1 exit status

---

### Post by worksofcraft on 2011-01-18
> **koala114 said:**
> ```

#include <iostream>

namespace my{
class A {

public:
        void OUTPUT();
};

class B: private A{
public:
    B(){std::cout<<"hi ford";}
    //using A::OUTPUT;
    void OUTPUT();
};
class C: private B{
    public:
        C(){std::cout<<"hi C";}
        //using my::B::OUTPUT;
        void xxx();
};
}

``````
#include "heritance.h"

void my::A::OUTPUT(){
std::cout<< "hhhhh";
}

void my::B::OUTPUT(){
A::OUTPUT();
}

void xxx(){
//OUTPUT();
}

```
```
#include "heritance.h"

int main(){
  using namespace my;
  B b;
  b.OUTPUT();
  return 0;
}

```
debian:~/src# g++ main.cpp
/tmp/ccSXkBAc.o: In function `main':
main.cpp:(.text+0x7f): undefined reference to `my::B::OUTPUT()'
collect2: ld returned 1 exit status

you need to also compile and link the module that contains my::B::OUTPUT... i.e. the second code window there what ever it is called

---

### Post by koala114 on 2011-01-19
Can I call the private method of base class with public heritance.

---

### Post by worksofcraft on 2011-01-19
> **koala114 said:**
> Can I call the private method of base class with public heritance.

Your OUTPUT method is public in both A and B classes. The purpose of making things private is to get a compiler error message if you should accidentally try to use them from outside that class...

so no, if you make it private then you can't access it.

Personally I don't find it that useful except to make copy constructors and assignments illegal and to make sure I don't change members that have interdependencies that must be maintained. Otherwise I just make everything public... until I find some reason to change it ;)

---

