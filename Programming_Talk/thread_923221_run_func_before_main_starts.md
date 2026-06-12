---
title: "run func before main starts?"
date: 2008-09-18
forum: Programming Talk
---

### Post by StOoZ on 2008-09-18
Is is possible to run something , I would like for example , to load an ini configuration file , before 'main' function (C++) starts , I program in linux , is it possible?

---

### Post by fballem on 2008-09-18
> **StOoZ said:**
> Is is possible to run something , I would like for example , to load an ini configuration file , before 'main' function (C++) starts , I program in linux , is it possible?

You're taking me back a few years, but I'm pretty sure that the answer is 'no' - main is the starting point of the program. If you want to configure the program before you do any serious work, then do the configuration as the first steps in the program, then continue working.

---

### Post by screech on 2008-09-18
It is possible.
You could create a new class, where you do something in the 
constructor. 
If you create a global object, the code is executed before main.

some example code:
```

#include <iostream>
#include <string>
using namespace std;

class Before {
    string msg;
public:
    Before(const string&);
};

Before::Before(const string& m) : msg(m) {
    cout << "my msg is: " << msg << endl;
}

Before before("I am first");

int main() {
    cout << "Entering main" << endl;

    return 0;
}

```

---

### Post by fballem on 2008-09-18
Thanks - I learned something new to-day!

---

### Post by dwhitney67 on 2008-09-18
If you only require one instance of the class to hold your configuration information, consider defining a singleton class.

For example:
[PHP]#include <iostream>

class Foo
{
  public:
    static Foo & instance()
    {
      static Foo theInstance;
      return theInstance;
    }

    // data accessor method(s)

  private:
    Foo()
    {
      std::cout << "Foo() called..." << std::endl;
    }

    // Defined, but not implemented.
    Foo( const Foo & );
    Foo & operator=( const Foo & );
};

Foo & foo = Foo::instance();

int main()
{
  std::cout << "main() called..." << std::endl;

  // ...

  return 0;
}[/PHP]

---

### Post by screech on 2008-09-18
You should declare a private copy-constructor for a singleton.
private:
    Foo(Foo&);

---

### Post by dwhitney67 on 2008-09-18
> **screech said:**
> You should declare a private copy-constructor for a singleton.
private:
    Foo(Foo&);

You are correct.  I updated code.

---

### Post by dribeas on 2008-09-18
> **screech said:**
> It is possible.
You could create a new class, where you do something in the 
constructor. 
If you create a global object, the code is executed before main.


Beware of static initialization issues: you cannot instruct the compiler with the order of initialization, so that if you create two static objects as shown above there is no guarantee on which of the objects will be constructed first. That is as much as saying that you should not static initialize any object that might depend on your .ini being parsed...

Also note that any exception raised and not caught inside your constructor will kill your application... kind of funny end to a program that did not even start...

---

