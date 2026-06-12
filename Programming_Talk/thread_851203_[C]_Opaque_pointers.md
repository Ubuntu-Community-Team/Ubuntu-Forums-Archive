---
title: "[C] Opaque pointers"
date: 2008-07-06
forum: Programming Talk
---

### Post by nvteighen on 2008-07-06
Hi there!
I've been experimenting a bit with data encapsulation and opaque pointers in C and have a theorical question on how that actually works. I mean, I do know how to use them, but would like to understand why we can use declare incomplete data types with a typedef statement. How can the compiler accept something it doesn't know anything about? How is the data type definition accessed if it's in another module? Or does the typedef keyword "declare" the data type, similar to declaring a variable without initializing it?

Thanks!

---

### Post by stroyan on 2008-07-06
Opaque pointers are useful for enforcing modular design.  An opaque
pointer type is only able to be passed around and compared for equality
to another pointer.  A compiler can do that without any additional
information.  The compiler can also type check to enforce that the right
opaque data type is passed into function calls.

  Any allocation or dereferencing of such pointers is limited to
code in modules that can see the full definition of the data type.

---

### Post by nvteighen on 2008-07-06
Thanks, I know that. What I'd like to understand is why the compiler doesn't need any additional information, as you say. I hope this helps to make my question clearer.

---

### Post by stroyan on 2008-07-06
Since the operations are so limited the compiler doesn't need to know
anything about the type that an opaque pointer points to.  It can treat
it just like a (void *) type except for the addition of type checking
for parameter passing and assignments.
With a full definition the compiler would see these additional attributes-
[LIST]
[*]size
[*]alignment requirements
[*]field names, types, and offsets
[/LIST]

  But with no allocation, no pointer math, and no dereference those are
not needed.

---

