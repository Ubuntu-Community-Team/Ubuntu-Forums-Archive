---
title: "c++ member initialisation lists"
date: 2009-02-16
forum: Programming Talk
---

### Post by gmclachl on 2009-02-16
Hi, I wondered is it possible to initialise an class member which is a pointer to an object in the member initialisation list. 

class A {
 
public: 
      ....
private:
      SomeObject* obj

}


So if obj was an int I could use 

A::A() : obj(1) 
{

}

but I am not sure how to do this with a pointer.

---

### Post by mriedel on 2009-02-16
Why do you need to do it in the initialization list? Is it const? Otherwise just put it in the constructor.

If it is const, what do you want to initialize it to? If you want to initialize it to the value of a parameter passed to the constructor, that should work fine. If you want to initialize it to a hand-crafted memory address or NULL (a const NULL pointer?)... just don't ;)

*Thou shalt not follow the null pointer, for chaos and madness await thee at its end.*

---

### Post by DougB1958 on 2009-02-16
I haven't tried it, but I would think that

[PHP]A::A() : obj( new SomeObject() )
{

}
[/PHP]
would work....

---

### Post by mriedel on 2009-02-16
> **DougB1958 said:**
> I haven't tried it, but I would think that

[PHP]A::A() : obj( new SomeObject() )
{

}
[/PHP]
would work....

If that pointer is supposed to point to a newly created object, that means it either 

- is const and therefore shouldn't be a pointer but an object from a design point of view or
- should't be in the initialization list but in the constructor from a design point of view

---

### Post by gmclachl on 2009-02-17
Thanks for the replies, I guess the best way is to initialise it in the constructor 

George

---

