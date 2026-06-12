---
title: "C++ data types"
date: 2009-07-21
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-07-21
What C++ data type is appropriate to store a value as large as a trillion? (1,000,000,000,000)

---

### Post by MadCow108 on 2009-07-21
64 bit integers can go up to 18446744073709551616 (2^64)
a trillion fits in there

unfortunatly theres not 64 bit type in c++ standard(yet) but g++ has one defined as long long and studio has it as __int64
so do:
```

#if defined(some_windows_define_i_dont_remeber)
typedef __int64          Long64_t;
typedef unsigned __int64 ULong64_t;
#else
typedef long long          Long64_t;
typedef unsigned long long ULong64_t;
#endif

```

and use Long64_t for portable code.
(or just use long long if you don't care)

note: when declaring add LL (or LLU for unsigned):
Long64_t var = 1000000000**LL**;

for larger numbers consider big integer libraries like CLN

---

### Post by c0mput3r_n3rD on 2009-07-21
Awsome, thank you, I will try it after dinner. :D

---

### Post by jero3n on 2009-07-21
or use a double :)

---

### Post by dribeas on 2009-07-22
> **jero3n said:**
> or use a double :)

Working with doubles is a little bit trickier. You cannot depend on equality to compare two doubles that have gone through different calculation paths, for example. It might or not be appropriate depending on what the user wants to do with the data.

---

### Post by Sockerdrickan on 2009-07-22
or use uint64_t

---

### Post by dribeas on 2009-07-22
> **Tux0r said:**
> or use uint64_t

That is standard C99, but not C++ (the c++ standard is clear in that whenever it deals with 'standard C' it is C89). In the upcoming standard (C++0x) you can use  'long long' which is guaranteed to be at least 64 bits (but no strict size is defined, it could be larger). 

The working draft I have (pre-July meeting) also deals with the <cstdint> header where some more integer types (typedefs in fact) will be defined. To that extent uint64_t (as int64_t and all other types that fix a size) is optional for the compiler vendor. But then again, I guess all vendors will provide them.

---

### Post by Sockerdrickan on 2009-07-22
> **dribeas said:**
> That is standard C99, but not C++ (the c++ standard is clear in that whenever it deals with 'standard C' it is C89). In the upcoming standard (C++0x) you can use  'long long' which is guaranteed to be at least 64 bits (but no strict size is defined, it could be larger). 

The working draft I have (pre-July meeting) also deals with the <cstdint> header where some more integer types (typedefs in fact) will be defined. To that extent uint64_t (as int64_t and all other types that fix a size) is optional for the compiler vendor. But then again, I guess all vendors will provide them.
I'm using C++0x with uint64_t and gcc says nothing with -std=c++0x -pedantic :lolflag:

---

### Post by jero3n on 2009-07-22
> **dribeas said:**
> Working with doubles is a little bit trickier. You cannot depend on equality to compare two doubles that have gone through different calculation paths, for example. It might or not be appropriate depending on what the user wants to do with the data.
Thanks for this clarification, I should have mentioned this, however my intention was to show that the initial question was a bit fuzzy :)

---

### Post by dribeas on 2009-07-22
> **Tux0r said:**
> I'm using C++0x with uint64_t and gcc says nothing with -std=c++0x -pedantic :lolflag:

:) With g++ you won't even need to use the -std::c++0x, or include <cstdint> to get it to work. But that does not mean that it will compile with any other compiler.

I have tried g++-4.1, g++-4.3 in C++98 mode and the compiler will not complain.

---

