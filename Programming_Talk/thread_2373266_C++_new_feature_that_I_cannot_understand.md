---
title: "C++ new feature that I cannot understand"
date: 2017-10-04
forum: Programming Talk
---

### Post by erotavlas on 2017-10-04
Hi,
I have a question about a C++ new (I suppose) feature that I cannot understand and cannot find the documentation about it.
I found a project in which there is a class defined in a couple of classA.h and classA.cpp files as usual and there is another file classB.cpp in which is included classA.h and there is the following code:
```

classA::i()->methodA() // methodA is public, there is not any instance of the class classA

```
I never saw this. Is it a sort of resolution operator that can be used in order to access the class member without creating an instance of it? Is it something similar to static class of Java? Where can I find the documentation regarding this?
Thank you

---

### Post by norobro on 2017-10-04
[FONT=monospace][COLOR=#000000]I'd say i() is a static member function of classA that creates an instance of classA on the heap and returns a poin[/COLOR]ter to the instance. 

Something like this:
[/FONT]```
[FONT=monospace][COLOR=#000000]#include <iostream>[/COLOR]

class classA{
public:
    static classA * i() { return new classA; }
    void methodA() { std::cout << "methodA\n"; }
};

class classB {
public:
    classB() { classA::i()->methodA(); }
};

int main() {
    classB b;
}
[/FONT]
```

---

### Post by erotavlas on 2017-10-04
> **norobro said:**
> [FONT=monospace][COLOR=#000000]I'd say i() is a static member function of classA that creates an instance of classA on the heap and returns a poin[/COLOR]ter to the instance. 

Something like this:
[/FONT]```
[FONT=monospace][COLOR=#000000]#include <iostream>[/COLOR]

class classA{
public:
    static classA * i() { return new classA; }
    void methodA() { std::cout << "methodA\n"; }
};

class classB {
public:
    classB() { classA::i()->methodA(); }
};

int main() {
    classB b;
}
[/FONT]
```

Thank you for your fast reply. I thought the same as you at the beginning, however I checked and the classA does not have any method called i() and this class is not a derived class.
So what could it be?

---

### Post by spjackson on 2017-10-04
> **erotavlas said:**
> I thought the same as you at the beginning, however I checked and the classA does not have any method called i() and this class is not a derived class.
So what could it be?
Without the context of the call and without the relevant headers, all anybody can do is guess... and what's the point of that? If you want something explaining, then please show us all the relevant code.

---

### Post by erotavlas on 2017-10-04
> **spjackson said:**
> Without the context of the call and without the relevant headers, all anybody can do is guess... and what's the point of that? If you want something explaining, then please show us all the relevant code.

You are right, the project is quite big and I cannot report all here. However, I think there is something that I'm missing.

---

### Post by dwhitney67 on 2017-10-09
Perform a google search on "singleton design pattern C++".  Maybe then you will be enlightened as to the inner workings of the code your are dealing with.

---

