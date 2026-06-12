---
title: "generate random numbers"
date: 2009-03-18
forum: Programming Talk
---

### Post by veda87 on 2009-03-18
can anyone tell me a function or a command to generate a **64 bit** random number.....

i used rand() function but it is generating a 32 bit random number but i need a 64 bit number.....

---

### Post by abhilashm86 on 2009-03-18
you could create by wrapping any 32-bit RNG and rolling it twice each time you need
to generate a 64-bit value.

```
//rand32 could be any 32-bit random generator
unsigned long rand32();

unsigned long long rand64()
{
        return ( static_cast<unsigned long long>( rand32() ) << 32 ) |
rand32();
}
```

try wrapping method.......this must work

---

