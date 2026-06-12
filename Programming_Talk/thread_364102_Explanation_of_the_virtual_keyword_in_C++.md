---
title: "Explanation of the virtual keyword in C++"
date: 2007-02-17
forum: Programming Talk
---

### Post by rekahsoft on 2007-02-17
Hi all, i am learning C++ and have been reading my C++ book but am a little hung up on the virtual keyword. I do not totaly understand its point...Could somone thoroughly explain why the virtual keyword is used and what exactly it does. Thanks

---

### Post by Mirrorball on 2007-02-17
Let's say you have a class A:
```

class A {
  public:
  void hello() { std::cout << "Hello from A." << std::endl; }
};

```And a derived class B:
```

class B : public A
{
};

```You can create a B object and call the hello method.
```

B b;
b.hello();

```The output will be "Hello from A." But you want to override the hello method. You'll write:
```

class B : public A
{
  public:
  void hello() { std::cout << "Hello from B." << std::endl; }
};

```Now the output of b.hello() will be "Hello from B." But one of the advantages of inheritance is that you can pass a B object to a funcion that expects a pointer to A.
```

void say_hello(A* a)
{
  a->hello();
}
say_hello(&b); // It's OK to do this.

```The output will be "Hello from **A**," because A's hello function is being called. However, if A's hello function were virtual:
```

class A
{
  public:
  virtual void hello() { std::cout << "Hello from A." << std::endl; }
};

```Then the output of say_hello(&b) would have been "Hello from **B**." Think of virtual functions as pointer to functions that can be overridden by derived classes and will work even when the derived object is passed (as a pointer) to a function that expects an object from the base class.

---

### Post by rekahsoft on 2007-02-17
ok, thanks...forums and IRC are great :D

---

### Post by Yaspoon on 2011-01-07
> **Mirrorball said:**
> Let's say you have a class A:
[code]
class A {
  public:
  void hello() { std::cout << "Hello from A." << std::endl; }
};


Thanks Mirror ball that made it all simple :)

---

### Post by worksofcraft on 2011-01-07
> **Yaspoon said:**
> Thanks Mirror ball that made it all simple :)

Oh kewl... WTF :confused: Post before that was dated 2007 :P

---

