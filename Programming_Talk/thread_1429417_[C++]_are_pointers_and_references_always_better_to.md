---
title: "[C++] are pointers and references always better to use than just regular values?"
date: 2010-03-14
forum: Programming Talk
---

### Post by cgb223 on 2010-03-14
are pointers and references always faster than say just using a regular data type. are there cases that they would be less efficient?

---

### Post by asmoore82 on 2010-03-14
Using data structures larger than 32-bits as function parameters will always be
more efficient when passed by reference or pointer. The only "gotcha" is(and it's a doozy)
if you make changes to the data structure and assume it only effects that function's
local copy, disaster and chaos will ensue.

In theory, it could be wasteful to pass a tiny primary data type such as **char** by reference.
But I think in modern practice they are always full 32 bit values internally anyway.

---

### Post by rnerwein on 2010-03-14
> **cgb223 said:**
> are pointers and references always faster than say just using a regular data type. are there cases that they would be less efficient?

hi
i think it's primary not the efficient to deside the using of pointers or regular data types. it
depends on what you want to do.
but for efficent: using a regular data types means ( assembler ) there is only "one" instruction to access the data --> la ( load address ). using a pointer means lh ( load the address into the pointer ) and then reference the data - two steps.
e.g. for sorting data arrays i am only using pointers because i only sort the pointers of the
array instead copying around the whole data.
cia
C is like a razor but without a grip  :-)

---

