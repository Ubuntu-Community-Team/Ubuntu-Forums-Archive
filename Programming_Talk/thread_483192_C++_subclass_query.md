---
title: "C++ subclass query"
date: 2007-06-24
forum: Programming Talk
---

### Post by WebDrake on 2007-06-24
Suppose I have a class in C++ --- let's call it MyClass --- which has several subclasses, MySub1, MySub2 etc.

Now suppose I want to create a vector or an array whose elements will all be subclasses of MyClass---but not necessarily the *same* subclass.

How would I go about doing this?  Or if it's not possible, is there another way of achieving the same result (e.g. by having 1 class, but following different templates)?

---

### Post by aks44 on 2007-06-24
STL containers are homogenous, you can't store objects belonging to different classes.

To achieve what you want, you can use a std::vector<MyClass*>
However, beware of correctly freeing the pointed-to objects when appropriate.

If you don't want to bother with memory management, a std::vector< boost::shared_ptr<MyClass> > will do the trick.

---

### Post by dempl_dempl on 2007-06-24
> **aks44 said:**
> 
However, beware of correctly freeing the pointed-to objects when appropriate.


Virtual destructor will do the trick.

---

### Post by duff on 2007-06-24
> **dempl_dempl said:**
> Virtual destructor will do the trick.

If you store pointers, you still have to explicitly delete the objects.

---

### Post by dempl_dempl on 2007-06-24
He he , not if you use smart pointers :) ...

---

### Post by WebDrake on 2007-06-25
> **aks44 said:**
> 
To achieve what you want, you can use a std::vector<MyClass*>
However, beware of correctly freeing the pointed-to objects when appropriate.


Ahh! I had not realised that a pointer to the base class can also point to a subclass.  Thank you very much!

I'm mainly a C person so used to freeing memory manually. ;)

---

### Post by aks44 on 2007-06-25
> **dempl_dempl said:**
> He he , not if you use smart pointers :) ...

Just DON'T use a vector of std::auto_ptr. This topic has been discussed numerous times (search comp.lang.c++), and it is very dangerous to do that, as it *won't* do what you expect, whatever you're expecting.

The only (?) safe smart pointer useable in STL containers is boost::shared_ptr. (or any other ref-counted smart ptr)


[COLOR="Red"]> **WebDrake said:**
> Ahh! I had not realised that a pointer to the base class can also point to a subclass.  Thank you very much!
I'm mainly a C person so used to freeing memory manually. ;)
If using raw pointers, you still have to **delete** the object manually. But having a virtual destructor in your base class will then also take care of the derived classes.[/COLOR]

EDIT: just ignore the last paragraph (in red), I misunderstood you.

---

### Post by dempl_dempl on 2007-06-25
> **aks44 said:**
> Just DON'T use a vector of std::auto_ptr. This topic has been discussed numerous times (search comp.lang.c++), and it is very dangerous to do that, as it *won't* do what you expect, whatever you're expecting.

The only (?) safe smart pointer useable in STL containers is boost::shared_ptr. (or any other ref-counted smart ptr)
.

I don't use any auto_ptr. I made my own smart pointers :) . I know ,I'm such a cool geek, all girls love me :)

---

### Post by aks44 on 2007-06-25
> **dempl_dempl said:**
> I don't use any auto_ptr. I made my own smart pointers :) . I know ,I'm such a cool geek, all girls love me :)

But unless it's a ref-counted smart pointer, it will have issues with (at least) STL containers... ;)

---

### Post by dempl_dempl on 2007-06-25
Well, Ive templated arguments for it:

class  Reflinking
{
 ...
}

class RefCounted
{
  ...
}

template <typename StoredType , 
                class ManagementPolicy = RefCounted , ... >  //couple of other stuff
class smartPtrholder :  public ManagementPolicy
{
    ....
}

Found it in a book called something like : "Modern c++ design" , by some Romanian guy.
Best book on c++ , templates , multiple inheitance and design patterns I've ever seen!

---

