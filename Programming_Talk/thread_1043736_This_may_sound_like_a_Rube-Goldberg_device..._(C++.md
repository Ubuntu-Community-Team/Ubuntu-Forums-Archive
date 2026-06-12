---
title: "This may sound like a Rube-Goldberg device... (C++ syntax)"
date: 2009-01-18
forum: Programming Talk
---

### Post by Zorgoth on 2009-01-18
Ok, this sounds ridiculous.  In fact, it is ridiculous.  But I want to pass by reference a pointer, which is to pointers, which are to functions of doubles returning doubles in C++.  I've tried virtually every possible combination of *s, and every time I get a compiler error.  What should I do here?

---

### Post by snova on 2009-01-18
Typedefs are your friend. :)

A function pointer:

[PHP]typedef double (*funcptr)(double);[/PHP]

A pointer to a function pointer:

[PHP]typedef funcptr* funcptrptr;[/PHP]

A function that takes a pointer to a function pointer:

[PHP]double otherfunc(funcptrptr tmp, double y);[/PHP]

Quick example:

[PHP]int main()
{
    funcptr ptr = some_func;
    funcptrptr ptr2 = &ptr;
    double z = other_func(ptr2, 4.2);
    printf("%f\n", z);
}[/PHP]

---

### Post by Zorgoth on 2009-01-18
Thanks!

---

