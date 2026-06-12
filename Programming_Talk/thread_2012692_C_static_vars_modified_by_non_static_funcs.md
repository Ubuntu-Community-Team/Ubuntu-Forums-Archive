---
title: "C: static vars modified by non static funcs"
date: 2012-06-29
forum: Programming Talk
---

### Post by cguy on 2012-06-29
I have seen this:
- declares static global variable
- declares non-static function in the same file; all that function does is change the value of the variable declared at the step above
- uses the non-static function in other files when he wants to change the static global variable

What are the advantages of this method?

---

### Post by satsujinka on 2012-06-29
It's in essence a means of getting private variables. You'd do it for all the same reasons as you would declare a private variable in languages with such a construct.

---

### Post by Bachstelze on 2012-07-01
$10 says the person who wrote that is a Java programmer.

---

### Post by trent.josephsen on 2012-07-01
> **Bachstelze said:**
> $10 says the person who wrote that is a Java programmer.
No takers.

---

### Post by snip3r8 on 2012-07-04
Maybe if you can post the code you saw we could better discern a reason.Though I cant think of any.

---

### Post by steeldriver on 2012-07-04
> **cguy said:**
> I have seen this:
- declares static **global **variable
- declares non-static function in the same file; all that function does is change the value of the variable declared at the step above
- uses the non-static function in other files when he wants to change the static global variable

What are the advantages of this method?

Are you sure it's not declaring a static **external **variable? The keyword **static **in that context is a scope modifier not a lifetime modifier i.e. it makes the variable private to the source file (explicitly **not **a global).

Used in this way it is roughly equivalent to having a C++ class containing a private data member that is modified via a public accessor method, as satsujinka says.

In fact there's a discussion of doing exactly that in K&R's original C book.

---

### Post by snip3r8 on 2012-07-04
> **steeldriver said:**
> Are you sure it's not declaring a static **external **variable? The keyword **static **in that context is a scope modifier not a lifetime modifier i.e. it makes the variable private to the source file (explicitly **not **a global).

Used in this way it is roughly equivalent to having a C++ class containing a private data member that is modified via a public accessor method, as satsujinka says.

In fact there's a discussion of doing exactly that in K&R's original C book.
That seems to be what a good google search turns up.

---

### Post by ofnuts on 2012-07-04
> **Bachstelze said:**
> $10 says the person who wrote that is a Java programmer.Java programmers would use singletons for this, possibly with Spring to initialize the variable. Simplicity is dangerous.

---

### Post by trent.josephsen on 2012-07-04
> **steeldriver said:**
> Are you sure it's not declaring a static **external **variable? The keyword **static **in that context is a scope modifier not a lifetime modifier i.e. it makes the variable private to the source file (explicitly **not **a global).
Well, C doesn't exactly have "global" variables since even variables with external linkage have to be explicitly "imported" (using **extern**) into each file in which they're used. **static** used outside of a function modifies linkage, not scope. (**static** inside a function doesn't affect linkage or scope, just storage duration.)

tl;dr -- you're conceptually right but your terminology might be misleading.

---

