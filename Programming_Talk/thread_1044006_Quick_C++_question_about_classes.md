---
title: "Quick C++ question about classes"
date: 2009-01-19
forum: Programming Talk
---

### Post by jyaan on 2009-01-19
I'm just wondering how I can make a class that does not require instantiation before usage; eg. cout from the iostream class. Or is it that iostream is somehow already instantiated?

---

### Post by Zugzwang on 2009-01-19
> **jyaan said:**
> I'm just wondering how I can make a class that does not require instantiation before usage; eg. cout from the iostream class. Or is it that iostream is somehow already instantiated?

Yep, you got it. Here's an example:

my_class.h:
[PHP]
class Hello {
public:
  void sayHello();
};

extern Hello myHello;
[/PHP]

my_class.cpp:
[PHP]
#include "my_class.h"
#include <iostream>

void Hello::sayHello() {
  std::cout << "Hello everyone!\n";
}

Hello myHello;
[/PHP]

main.cpp:
[PHP]
#include "my_class.h"

int main() {
  myHello.sayHello();
}
[/PHP]

---

### Post by Npl on 2009-01-19
cout and Zugzwang`s example both are global instances, means the constructor of those instances will be called before the "main" function.
So they still get instantiated (and the destructor will be called upon exit), albeit not explicitely through your code.

---

