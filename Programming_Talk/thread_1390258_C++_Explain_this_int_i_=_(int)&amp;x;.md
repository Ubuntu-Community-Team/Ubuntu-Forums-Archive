---
title: "C++ Explain this: int i = *(int*)&amp;x;"
date: 2010-01-25
forum: Programming Talk
---

### Post by akvino on 2010-01-25
float InvSqrt(float x){
   float xhalf = 0.5f * x;
   int i = *(int*)&x; // store floating-point bits in integer
   i = 0x5f3759d5 - (i >> 1); // initial guess for Newton's method
   x = *(float*)&i; // convert new bits into float
   x = x*(1.5f - xhalf*x*x); // One round of Newton's method
   return x;
}

---

### Post by CHW on 2010-01-25
I think i is the content of x, copied into the integer bit by bit.

More in detail: you take the address of x (&x), and cast that address to a pointer to integer (int*). Then you access the content of this pointer (*).

I hope this is understandable, it's not so easy to explain.

---

### Post by cpplinux on 2010-01-25
It just tries to put the float into an int for manipulation. It use the pointers trick so that the float's decimal part won't be truncated when being put into an int.

---

### Post by MadCow108 on 2010-01-25
very detailed description of the whole thing:
[http://en.wikipedia.org/wiki/Fast_inverse_square_root](http://en.wikipedia.org/wiki/Fast_inverse_square_root)
specific the part you asked about:
[http://en.wikipedia.org/wiki/Fast_inverse_square_root#Aliasing_from_floating_point_to_integer](http://en.wikipedia.org/wiki/Fast_inverse_square_root#Aliasing_from_floating_point_to_integer)

---

### Post by akvino on 2010-01-25
Thanks for the link, thanks for pointer dereferencing insight. O:)

---

### Post by Habbit on 2010-01-25
By the way, C++ has more explicit cast operators called X_cast. They perform a defined operation and have known, specified ways of failing, instead of the unknown "black magic" represented by a C cast. In this particular case, you probably want reinterpret_cast, which unambiguously specifies that you want a certain area of memory to be reinterpreted as of being of another type:
```
float InvSqrt(float x){
    float xhalf = 0.5f * x;
    int i = *reinterpret_cast<int*>(&x); // store floating-point bits in integer
    i = 0x5f3759d5 - (i >> 1); // initial guess for Newton's method
    x = *reinterpret_cast<float*>(&i); // convert new bits into float
    x = x*(1.5f - xhalf*x*x); // One round of Newton's method
return x;
} 
```

---

### Post by akvino on 2010-01-25
So habbit how would you use C++ specific cast?

---

### Post by dwhitney67 on 2010-01-25
> **akvino said:**
> So habbit how would you use C++ specific cast?

:confused:

Look at Habbit's post for an example (of reinterpret_cast).

---

### Post by akvino on 2010-01-26
I was blind and now I see:

int i = *reinterpret_cast<int*>(&x); // store floating-point bits in integer

Thanks :D

dwhitney67 - you know your c and c++ on these forums - I just didn't read his example carefully. Give me a month or two - ;)...

---

