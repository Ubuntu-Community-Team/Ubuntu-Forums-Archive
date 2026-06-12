---
title: "c++ multiple inheritance casting (binding to c)"
date: 2009-09-03
forum: Programming Talk
---

### Post by aanderse on 2009-09-03
i have a few c++ classes (multiple inheritance) lets say:

```

class A { ... }
class B { ... }
class C : public A, public B { ... }

```

and lets say i want to export these to c so i make some functions

```

// aclass.h
typedef void CA;
typedef void CB;
typedef void CC;

#ifdef __cplusplus
extern "C" {
#endif

CA *function_from_a_class (CA *self);

// aclass.cpp

CA *function_from_a_class (CA *self)
{
A *actual_object = .... ? // cast the object to A class

actual_object->function_from_a_class_impl ();

return .... ? // return the object
}

```

i never payed too much attention to multiple inheritance hell in the past but i have this code i would like to interface with c, so can anyone here answer me which black magic casting of void * to A, B, and C?

thank you

---

### Post by johnl on 2009-09-03
Hi,

I don't believe you can use a dynamic_cast<> directly in this case since self is a void*.  I would try using reinterpret_cast<A*>(self) And see if you get a valid 'A' object.  At that point you might be able to use dynamic_cast<> to downcast from A to C.

This is just conjecture, play around with it and see what happens.

---

### Post by WitchCraft on 2009-09-03
It's difficult enough, I would try C-Style typecasts first. 

Once you got it working, you can still rewrite them as C++ typecasts.

I had to typecast function pointers for an aimbot in C++.

It wasn't possible to do it directly, so I had to typecast from source functionpointer via unsinged long to the destination function pointer...

---

### Post by Habbit on 2009-09-03
Short answer is: it's not possible to do it in C, because the exact layout of the "C" object is unspecified by the C++ standard, and only the compiler knows it. Thus, when you ask the compiler to static_cast<B*>(&c_obj), where c_obj is of type C, it looks up such details in its internal tables, and returns you a pointer which is offset the required number of bytes from the base address of c_obj. On the other hand, dynamic_cast does the same but using runtime type information (that is hidden from the programmer), and can also cast through virtual base classes. However, C pointer casts behave as reinterpret_cast, and thus perform no offsetting, nor use any type layout information (mainly because C doesn't know about it).

---

### Post by aanderse on 2009-09-04
Thanks for your responses!

---

