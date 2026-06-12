---
title: "[SOLVED] forced float"
date: 2008-02-17
forum: Programming Talk
---

### Post by chris200x9 on 2008-02-17
hi I can't figure out what's wrong with this forced float statement

```
 digit = (num/ pow( float base, numDigits - num);
```

---

### Post by stroyan on 2008-02-17
You didn't say much in your question about your situation.
For example, you didn't mention what language you are coding in. ;-)

I presume you are still coding in C++ as in your previous posts.
And I presume the variables you are using are of type int, resulting in an error like-```
call of overloaded ‘pow(int&, int)’ is ambiguous
```

You need to put the type that you are casting to in parentheses, like
```
digit = (num/ pow( (float) base, numDigits - num);
```

---

### Post by aks44 on 2008-02-18
> **stroyan said:**
> I presume you are still coding in C++ as in your previous posts.
[...]
You need to put the type that you are casting to in parentheses, like
```
digit = (num/ pow( (float) base, numDigits - num);
```

Funnily enough, you assume that the OP uses C++ but advise to use C casts. :-s

In C++, such a cast is done using **static_cast<float>(base)**. Contrary to unchecked old-style C casts, new-style C++ casts are much safer, better take a good habit as early as possible.

As a side note, **double**s are most of the time preferred over **float**s, there is no performance overhead but the precision is greatly enhanced.

---

### Post by popch on 2008-02-18
> **chris200x9 said:**
> hi I can't figure out what's wrong with this forced float statement

```
 digit = (num/ pow( float base, numDigits - num);
```

The number of left parentheses does not match the number of right ones, to start with.

---

### Post by chris200x9 on 2008-02-18
thanks!

---

