---
title: "what datatype in this c++ problem?"
date: 2010-01-24
forum: Programming Talk
---

### Post by abhilashm86 on 2010-01-24
i've to find highest prime factor of 600851475143, i'm getting error with regard to datatype......

```
long int num = 600851475143; 
```

error is........
```
5.cpp:7: warning: integer constant is too large for ‘long’ type
5.cpp: In function ‘int main()’:
5.cpp:7: warning: overflow in implicit constant conversion

```

i need to use modulus % to find remainder, so what kind of datatype should i be using? if not datatype, should i use array?

---

### Post by Can+~ on 2010-01-24
```
long long
```

2^64 = 18446744073709551616

If I remember right, long is architecture dependant (it's 2^32 in 32-bit, and 2^64 in 64-bit).

---

### Post by Queue29 on 2010-01-24
Works fine on a 64 bit system :KS

You might want to try making it an unsigned long long.

---

### Post by MadCow108 on 2010-01-24
long long would be a 64 bit integer added as extension by gcc
but don't forget the LL or LLU behind the literal:
long long i = 1<<62LL
unsigned long long = 1<<63LLU

you might want to create some typdefs for portability as c++ has no standard 64 bit datatype

---

