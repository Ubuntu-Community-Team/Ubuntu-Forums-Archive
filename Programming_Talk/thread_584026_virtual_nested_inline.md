---
title: "virtual nested inline"
date: 2007-10-20
forum: Programming Talk
---

### Post by spamalot on 2007-10-20
hi,

i posted this somewhere else but could not quite get a clean answer so i'm trying my luck here. 

a) does it make any difference to D::f() that B's
member functions are inlined? 
b) does the answer depend on whether i use D.f() or A*->f()?

class B{
  inline  void func(){/*definition*/}
};//concrete class

class A{
public:
 virtual void f()=0;

}

class D: public A{
public:
 virtual void f(){b.func();}
private:
 B b; 
};


by the way, i'm aware that virtual obliterates inline and that inline is only a suggestion to the compiler. i'm interested in this specific example where inline is nested *within* a virtual function definition: is inline *always* superfluous in this case?

---

### Post by aks44 on 2007-10-20
There is one case where D::f() could be inlined (depending on the compiler's good will). It is when it knows *for sure* that you're calling D::f():

```
A* aptr = /*...*/; // base class pointer
aptr->f(); // not inlined

D& dref = /*...*/; // reference, no way to tell if dref really is a D
dref.f(); // not inlined
dref.D::f(); // we know what we're really calling, can be inlined

D dobj; // a real D object
dobj.f(); // we know what we're really calling, can be inlined
```


BTW even for non-inlined virtual functions the exact same rules apply to determine whether the virtual mechanism indirection is used, or if it can be optimized out and replaced by a direct (and more efficient) function call. Inlining is just a special case of the "direct call" option.

EDIT: and also, the inlining decision is based on "is D::f() inlineable?". If B::func() was not inline, D::f() could still be inlined as a call to b.func().

---

