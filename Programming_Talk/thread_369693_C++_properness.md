---
title: "C++ properness"
date: 2007-02-24
forum: Programming Talk
---

### Post by rekahsoft on 2007-02-24
Hi all, i am wondering if it is proper for a C++ program to define temporary variables in a source file that is defining functions from a header file. For example:
Header File:```
#ifndef __TEST_H
#define __TEST_H

#include <string>
#include <iostream>

class test {
     public:
          void tester() const;
};
#endif
```Source file:```
#include "test.h"
using std::cout;
using std::endl;
using std::string;
void test::tester() const {
     string var;
     cin >> var;
     cout << var << endl;
}
```I know it is a pointless example but it shows what i mean...also i get a warning from g++ when i return a local variable...is it improper to do so? Should ALL variables be defined in the header? Even variables that are temporary to specific functions?

---

### Post by hod139 on 2007-02-24
You shouldn't #include anything in the header file that you absolutely do not need.  In this example, neither include belongs.

> 
Hi all, i am wondering if it is proper for a C++ program to define temporary variables in a source file that is defining functions from a header file
If I understand your question yes; but where else could you declare/instantiate them?

> 
also i get a warning from g++ when i return a local variable...is it improper to do so?
This is very bad.  When you allocate a temporary in a method, it is allocated on the stack.  When you return from the function call, the area is marked as reclaimable.  If nothing else happens between the time the method returns and you access that data location, then the value is probably still there.  That's a lot of ifs/maybes though.  This is very unsafe.

> 
Should ALL variables be defined in the header? Even variables that are temporary to specific functions?
No.  Define variables when you need them, not sooner.

---

### Post by rekahsoft on 2007-02-24
I figured out why i was getting the warning...lol...my mistake...i was returning a reference to a variable i defined localy...so after returning the reference the variable is deleted so i am laft with a hanging reference...ok...so in the case of creating a temporary variable local to the function i cannot return it as a reference and it is not good to return a variable of class type because it is not optimal so what is the best thing to do in a circumstance like that?

---

### Post by hod139 on 2007-02-24
If I am understanding your question, you have two options.  You can create a  temporary object and return a copy

```

myObject doSomething(void)
{
  myObject returnMe;
  //do stuff to returnMe
  return returnMe;
}

```


or you can have the method take the output as a parameter (using pass by reference)
```

void doSomething(myObject &outObject)
{
  //do stuff to outObject
}

```

---

### Post by Mirrorball on 2007-02-24
I would return it by value unless I know it's a class with a lot of data. If it is, you can, depending on the circumstances:
1. Return a pointer/reference to a static variable in your function.
2. Add a member (static or not) to your class of the appropriate type and return a pointer/reference to it.
3. Create a new object with **new** and return the pointer/reference. Don't forget to delete it later.
4. Get a pointer to an object as an argument and do what you want with it.
I think these are all the options. Oh, you could return a reference/pointer to a global variable, but global variables are usually bad.

---

