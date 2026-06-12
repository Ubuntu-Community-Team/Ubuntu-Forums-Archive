---
title: "Difficulties with multiple inheritance (C++)"
date: 2007-04-13
forum: Programming Talk
---

### Post by aquavitae on 2007-04-13
Hi

I've got a tricky programming problem (or at least, I find it tricky :) )  I have the following situation:

```

template<typename T> class Container {
   public:
      T& at(int);
};

class BaseClass {
   public:
      virtual BaseClass* at(int) const = 0;
};
      
class A: public Container<B*>, public BaseClass {...};

class B: public Container<C*>, public BaseClass {...};

class C: public BaseClass {...};

B* instanceofa = new B();


```

The idea is to create a generic interface I can use for A, B or C, that allows me to use certain functions from Container without having to reimplement them.  However, I get the following error from the complier for the last line of code:
```

error: cannot allocate an object of type `B'
error:   because the following virtual functions are abstract:
 error:  virtual const BaseClass* BaseClass::at(int) const

```

I'm not even sure if this is the best way of doing it (apparently not, as it doesn't work!) so if anyone has any suggestions I'd be grateful.

---

### Post by IronAvatar on 2007-04-13
I'd say that it's because your BaseClass is an abstract class (it contains pure virtual methods) and so for any class that directly derives from it, you would have to also implement the pure methods (see below);

```

template<typename T> class Container {
   public:
      T& at(int);
};

class BaseClass {
   public:
      virtual BaseClass* at(int) const = 0;
};
      
class A: public Container<B*>, public BaseClass 
{
virtual BaseClass* at(int) const;
};

class B: public Container<C*>, public BaseClass 
{
virtual BaseClass* at(int) const;
};

class C: public BaseClass 
{
virtual BaseClass* at(int) const;

}


B* instanceofa = new B();

```

---

### Post by aquavitae on 2007-04-13
I was hoping I'd be able to get it to use Container::at(int) in the inherited class.  Is there a way to do that, or even a better way of designing the problem?  I suppose I could reimplement it and refer to Container::at(int):
A::at(int i) {
   return Container::at(i);
}
but I'm feeling lazy.

---

### Post by Dancingwllamas on 2007-04-13
You should be able to do it if you remove the "= 0" from the end of the prototype in BaseClass. Without that, child classes should be able to use the function from the parent class.

---

