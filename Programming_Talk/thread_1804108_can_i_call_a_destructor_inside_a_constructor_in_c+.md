---
title: "can i call a destructor inside a constructor in c++??"
date: 2011-07-14
forum: Programming Talk
---

### Post by Praveen30 on 2011-07-14
Normally we define the constructor and destructor seperately...i want to know is there any way by which i can call  destructor inside a constructor and if it is possible then what will be the effect on the object??

```

class A
{
int x;
public:

A{
  ~A()  // can i do something like this???
}
};

int main()
{
A obj;  // if this happens then what will be the effect on object???
return 0;
}

```

---

### Post by matt_symes on 2011-07-14
Hi

> can i *call* a destructor inside a constructor in c++??> i want to know is there any method by which we can *define* the destructor inside a constructor

Which one are you trying to do ?

Kind regards

---

### Post by Praveen30 on 2011-07-14
> **matt_symes said:**
> Hi



Which one are you trying to do ?

Kind regards
  
sorry for this confusion...take the first one...i just want to know can a destructor be called inside a constructor??

---

### Post by dwhitney67 on 2011-07-14
> **Praveen30 said:**
> ... is there any way by which i can call  destructor inside a constructor

Umm, why would you want to do this?  I'm not sure if the compiler will allow it, but you can try.

---

### Post by Simian Man on 2011-07-14
Of course you *can*.  C++ lets you do anything you want to no matter how stupid it is.  Consider:
```

#include <iostream>
using std::cout;

class A {
  public:
    A( ) {
      cout << "Starting Constructor\n";
      this->~A( );
      cout << "Leaving Constructor\n";
    }

    ~A( ) {
      cout << "In Destructor\n";
    }
};

int main( ) {
  A a;
  return 0;
}

```

The more important question is *should* you call the destructor in the constructor and the answer is no.  Destructors are automatically called for you and should never be called more than once.  Therefore you should never call it yourself.  See the [C++ FAQ Lite]("http://www.parashift.com/c++-faq-lite/dtors.html") for more info.

---

### Post by Praveen30 on 2011-07-14
> **Simian Man said:**
> Of course you *can*.  C++ lets you do anything you want to no matter how stupid it is.  Consider:
```

#include <iostream>
using std::cout;

class A {
  public:
    A( ) {
      cout << "Starting Constructor\n";
      this->~A( );
      cout << "Leaving Constructor\n";
    }

    ~A( ) {
      cout << "In Destructor\n";
    }
};

int main( ) {
  A a;
  return 0;
}

```The more important question is *should* you call the destructor in the constructor and the answer is no.  Destructors are automatically called for you and should never be called more than once.  Therefore you should never call it yourself.  See the [C++ FAQ Lite]("http://www.parashift.com/c++-faq-lite/dtors.html") for more info.

thanks. ya, i know the question is stupid..but somebody asked me so i just want to know the answer..

---

### Post by dwhitney67 on 2011-07-14
And here is a case where calling the destructor manually leads to disaster:
```

class Foo
{
public:
   Foo()
      : value(new int(10))
   {
      this->~Foo();
   }
   ~Foo()
   {
      delete value;
   }
private:
   int* value;
};

int main()
{
   Foo foo;
}

```
Of course, one can be a little more careful; for instance, setting the pointer to null after it has been deleted.  But typically this is not done within the destructor.

---

