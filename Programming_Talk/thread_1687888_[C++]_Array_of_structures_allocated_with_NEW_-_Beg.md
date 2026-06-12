---
title: "[C++] Array of structures allocated with NEW - Beginner question"
date: 2011-02-14
forum: Programming Talk
---

### Post by abraxyz on 2011-02-14
[FONT=Arial]I was wondering why is this not possible:
[/FONT]
```

struct fish
{
   string kind;
   float weight;
   float length;
};

fish * pt = new fish [3];

**pt[0] = {"Tuna", 7.2, 20.5};**
```So, you have to do this instead:

```
pt[0].kind = "Tuna";
pt[0].weight = 7.2;
pt[0].length = 20.5;
```Thanks...

---

### Post by johnl on 2011-02-14
You can do this with **extended initializer lists**, present in the upcoming C++0x standard.  Compile your code with -std=c++0x and it should work as you have written it.

---

### Post by abraxyz on 2011-02-14
Oh!.. That's exactly what my compiler responded with, but it didn't make much sense to me. Now it does. Thanks!

---

### Post by MadCow108 on 2011-02-14
what you can do in c++98 is this:
```
static fish def = {some values};
fish * pt = new fish[3];
pt[0] = def
```

or use the constructor
```
#include <memory>
pair <fish*,ptrdiff_t> result = get_temporary_buffer<fish>(3);
new (result.first) fish("tuna", 2.3, 23.);

```

---

### Post by abraxyz on 2011-02-14
That did it too!
Thanks, MadCow

The first part that is... I don't understand the rest

---

### Post by MadCow108 on 2011-02-14
sorry it also had a bug.
it should be this:
```
#include <memory>
pair <fish*,ptrdiff_t> result = get_temporary_buffer<fish>(3);
new (result.first) fish("tuna", 2.3, 23.);
new (result.first+1) fish("tuna2", 2.3, 23.);
//do stuff

// free memory, need to explicitly call destructors
result.first[0].~fish();
result.first[1].~fish();
return_temporary_buffer(result.first)
```
or using uninitialized_copy/fill/fill_n

get_temporary_buffer creates a buffer of memory for 3 fish objects but does not initialize it = no default constructor is invoked (it is basically the same as a malloc(sizeof(fish)*n))
then the placement new is used to initialize this memory with a fish object.

this may be more efficient than the other method when the default constructor is expensive
see
[http://www.cplusplus.com/reference/std/memory/](http://www.cplusplus.com/reference/std/memory/)

---

### Post by abraxyz on 2011-02-14
Oh, that looks neat. I'm reading on it.
So, just curious: is it possible to later delete individual array members, or you'd have to delete the whole array?

---

### Post by abraxyz on 2011-02-14
Aaand, this looks creepy:

> abraxyz@abraxyz-P35-DS3R:~/test_coding$ ./a.out 
Tuna
7.2
20.5
*** glibc detected *** ./a.out: munmap_chunk(): invalid pointer: 0x09864024 ***
======= Backtrace: =========
/lib/libc.so.6(+0x6c501)[0x267501]
/lib/libc.so.6(+0x6d77e)[0x26877e]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0x1ba441]
./a.out[0x8048cc1]
/lib/libc.so.6(__libc_start_main+0xe7)[0x211ce7]
./a.out[0x8048991]
======= Memory map: ========
00110000-001ef000 r-xp 00000000 08:03 134744     /usr/lib/libstdc++.so.6.0.14
001ef000-001f3000 r--p 000de000 08:03 134744     /usr/lib/libstdc++.so.6.0.14
001f3000-001f4000 rw-p 000e2000 08:03 134744     /usr/lib/libstdc++.so.6.0.14
001f4000-001fb000 rw-p 00000000 00:00 0 
001fb000-00352000 r-xp 00000000 08:03 928169     /lib/libc-2.12.1.so
00352000-00354000 r--p 00157000 08:03 928169     /lib/libc-2.12.1.so
00354000-00355000 rw-p 00159000 08:03 928169     /lib/libc-2.12.1.so
00355000-00358000 rw-p 00000000 00:00 0 
004cc000-004cd000 r-xp 00000000 00:00 0          [vdso]
00c40000-00c5c000 r-xp 00000000 08:03 928166     /lib/ld-2.12.1.so
00c5c000-00c5d000 r--p 0001b000 08:03 928166     /lib/ld-2.12.1.so
00c5d000-00c5e000 rw-p 0001c000 08:03 928166     /lib/ld-2.12.1.so
00d4f000-00d69000 r-xp 00000000 08:03 917584     /lib/libgcc_s.so.1
00d69000-00d6a000 r--p 00019000 08:03 917584     /lib/libgcc_s.so.1
00d6a000-00d6b000 rw-p 0001a000 08:03 917584     /lib/libgcc_s.so.1
00f5c000-00f80000 r-xp 00000000 08:03 928173     /lib/libm-2.12.1.so
00f80000-00f81000 r--p 00023000 08:03 928173     /lib/libm-2.12.1.so
00f81000-00f82000 rw-p 00024000 08:03 928173     /lib/libm-2.12.1.so
08048000-08049000 r-xp 00000000 08:03 793169     /home/abraxyz/test_coding/a.out
08049000-0804a000 r--p 00001000 08:03 793169     /home/abraxyz/test_coding/a.out
0804a000-0804b000 rw-p 00002000 08:03 793169     /home/abraxyz/test_coding/a.out
09864000-09885000 rw-p 00000000 00:00 0          [heap]
b776b000-b776e000 rw-p 00000000 00:00 0 
b777c000-b777f000 rw-p 00000000 00:00 0 
bff95000-bffb6000 rw-p 00000000 00:00 0          [stack]
AbortedAfter I added:

```
delete pt;
```lol

Edit:
Oh, gee. I should use ***delete [] pt*** here

---

### Post by MadCow108 on 2011-02-14
well you can call the destructor of each element separately but the array itself can only be deleted in one go.

Using this kind of memory management is not recommended for general use as it is far more error prone (e.g. forgetting to call a destructor etc.).
Use only when default construction of objects is really expensive and you really need such a buffer.

to delete each element separately completely you have to use an array of pointers:
```

fish ** p = new fish*[3];
p[0] = new fish(...);
p[1] = new fish(...);
//...
delete p[1];
p[1] = new fish(...);
//..
delete p[0];
delete p[1];
delete [] p;

```

but you have the same issues with more complex memory management.

---

### Post by abraxyz on 2011-02-14
Alright, thanks for your help. It means a lot to me

---

