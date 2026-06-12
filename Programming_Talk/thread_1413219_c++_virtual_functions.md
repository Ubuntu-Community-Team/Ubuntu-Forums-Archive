---
title: "c++ virtual functions"
date: 2010-02-22
forum: Programming Talk
---

### Post by night_fox on 2010-02-22
In this code, "Base" is an abstract class, and "Derived" inherits from it. say_hello is a pure virtual function which means it must be overridden. I think I'm overriding it in "Derived", but g++ tells me something different.

Why wont this compile

```
class Base {
    public:
    virtual void say_hello (void) const = 0;
};


class Derived : public Base {
    public:
    void say_hello (void);
};


int main (void) {

    Derived *d = new Derived;

}
```

Compiler errors:

```
virt.cc: In function ‘int main()’:
virt.cc:16: error: cannot allocate an object of abstract type ‘Derived’
virt.cc:7: note:   because the following virtual functions are pure within ‘Derived’:
virt.cc:3: note: 	virtual void Base::say_hello() const
```


But Base::say_hello() isn't a function in Derived. I overrode it. Whats going on? Why wont this compile?

---

### Post by night_fox on 2010-02-22
Solved.

```
class Base {
    public:
    virtual void say_hello (void) const = 0;
};


class Derived : public Base {
    public:
    void say_hello (void) const;
};


int main (void) {

    Derived *d = new Derived;

}
```

compiles but obviously doesn't link because theres no implementation.

---

### Post by dribeas on 2010-02-22
The constantness of the method is part of the signature. To override a virtual function you need to provide the same exact interface [*].

```

struct base {
   virtual void method() const = 0;
};
struct derived : public base {
   void method() const;
};

```

As a side note, unlike C, in C++ the 'void' argument definition is completely optional, and most often discarded.

The interface of the function does not need to be exactly the same, you are allowed to use covariant return types (if 'base::f' returns a reference or pointer to 'type', then 'derived::f' must return a reference or pointer to either a 'type' or a class publicly derived from 'type'. All of the arguments (including the implicit 'this' pointer) must be of the same exact type. Access specifiers (public/protected/private) have no effect on the signatures.

---

