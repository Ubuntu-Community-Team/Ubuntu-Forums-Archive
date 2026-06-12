---
title: "C++ Template Inheritance Performance Benefits Question"
date: 2012-08-09
forum: Programming Talk
---

### Post by akvino on 2012-08-09
Take regular inheritance, if the method is virtual then the method will be looked up in the vtable at run time.


Template inheritance -if the base class is template class and the the child class is template class, article I read suggest this is done at the compile time????? How do I check this????

What happens if the base class is regular non template class, and the child class is template class???? 

Performance gurus, clarifications needed? How does one verify this is correct??? I can dig into assembly code but I am not sure what to look for?

---

### Post by durdenstationer on 2012-08-10
> **akvino said:**
> Take regular inheritance, if the method is virtual then the method will be looked up in the vtable at run time.

Not true. If the type of the object can be determined at compile time or link time any decent compiler will change this into a direct call. Also if the object is a known type, meaning not used through a reference or pointer to a base type, the call will also be optimized. These are pretty basic optimizations that any mainstream compiler does. CFront 1.0 did the latter optimization well back in 1985. Only an extremely primitive optimizer and linker wouldn't have this capability.

> **akvino said:**
> Template inheritance -if the base class is template class and the the child class is template class, article I read suggest this is done at the compile time????? How do I check this????

Look at the disassembly as you would to verify any optimization.

---

### Post by durdenstationer on 2012-08-11
I forgot to add about how you know if dynamic dispatch is optimized out from the disassembly.  [This](http://stackoverflow.com/questions/9995922/how-to-tell-if-a-program-uses-dynamic-dispatch-by-looking-at-the-assembly) Stack Overflow question gives you some pointers on what you'd see if the vtable lookup is used.

---

