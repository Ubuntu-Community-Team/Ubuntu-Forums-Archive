---
title: "C++ Equivalent to Java Super (for methods)"
date: 2008-06-17
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-06-17
Is there a C++ equivalent for calling the corresponding method of the parent class?  Say I have a class called Dog that is a subclass of Animal.  There is a virtual method called Walk() implemented in Animal.  I want to have a method called Walk() in dog which then calls the Walk() defined in the animal class, then does some other things.  Any way of doing this in C++?

---

### Post by haTem on 2008-06-18
Yep, just do something along the lines of:

[PHP]void Dog::Walk()
{
     // call the parent class's Walk() method
     Animal::Walk();

     // put your dog-specific code here
}[/PHP]

---

### Post by SNYP40A1 on 2008-06-18
That makes sense.  Animal is specified because C++ allows multiple inheritance while Java does not.  The parent class name is not referenced by Java Super because there is only one possible class that it could be.

---

