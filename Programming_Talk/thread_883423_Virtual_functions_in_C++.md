---
title: "Virtual functions in C++"
date: 2008-08-07
forum: Programming Talk
---

### Post by Unresolved on 2008-08-07
Let's say base calss A has a virtual function defined as:
```
     virtual void print(){
        cout<<"print in A";};
```
If class B is derived from A directly, and overrides the virtual function in A as:
    ```
 void print(){cout<<"print in B";};
```
Is the function print in B going to be automatically virtual? so that any class that derive from class B will be able to override the function print() in class B? Thanks for the help in advance.

---

### Post by slavik on 2008-08-08
no

---

### Post by dwhitney67 on 2008-08-08
> **Unresolved said:**
> Let's say base calss A has a virtual function defined as:
```
     virtual void print(){
        cout<<"print in A";};
```
If class B is derived from A directly, and overrides the virtual function in A as:
    ```
 void print(){cout<<"print in B";};
```
Is the function print in B going to be automatically virtual? so that any class that derive from class B will be able to override the function print() in class B? Thanks for the help in advance.
Yes it will be; nevertheless it is still good practice to indicate that the method is virtual.  Someone inheriting from class B may not be staring at the definition for the base class (A).

Btw, it wouldn't kill you to write a test program, would it??
[PHP]#include <iostream>

class Base
{
  public:
    virtual void print() { std::cout << "Base::print() called." << std::endl; }
  protected:
    Base() {}
};

class Derived : public Base
{
  public:
    Derived() : Base() {}

    void print() { std::cout << "Derived::print() called." << std::endl; }
};

class BottomFeeder : public Derived
{
  public:
    BottomFeeder() : Derived() {}

    void print() { std::cout << "BottomFeeder::print() called." << std::endl; }
};

int main()
{
  Base *b = new BottomFeeder();

  b->print();

  delete b;

  return 0;
}[/PHP]

---

### Post by Unresolved on 2008-08-08
> **dwhitney67 said:**
> Yes it will be; nevertheless it is still good practice to indicate that the method is virtual.  Someone inheriting from class B may not be staring at the definition for the base class (A).

Btw, it wouldn't kill you to write a test program, would it??
[PHP]#include <iostream>

class Base
{
  public:
    virtual void print() { std::cout << "Base::print() called." << std::endl; }
  protected:
    Base() {}
};

class Derived : public Base
{
  public:
    Derived() : Base() {}

    void print() { std::cout << "Derived::print() called." << std::endl; }
};

class BottomFeeder : public Derived
{
  public:
    BottomFeeder() : Derived() {}

    void print() { std::cout << "BottomFeeder::print() called." << std::endl; }
};

int main()
{
  Base *b = new BottomFeeder();

  b->print();

  delete b;

  return 0;
}[/PHP]

Thanks, that really works. Nice coding btw.

---

