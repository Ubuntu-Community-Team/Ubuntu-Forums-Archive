---
title: "Error linking to libgmp with g++4.6?"
date: 2012-01-07
forum: Programming Talk
---

### Post by DonkeySalami on 2012-01-07
Hello,

I'm writing a small application which uses libgmp for arbitrary precision integer arithmetics. I'm using the standard Ubuntu g++-4.6 packages because I'm using the new C++11 features. For some reason I get lots of undefined symbol errors during the linking step:

$ g++-4.6 -lgmpxx -lgmp ...
....o: In function `__gmpz_neg':
/usr/include/gmp-i386.h:1783: undefined reference to `__gmpz_set'
....o: In function `__gmp_binary_plus::eval(__mpz_struct*, __mpz_struct const*, __mpz_struct const*)':
/usr/include/gmpxx.h:72: undefined reference to `__gmpz_add'
....o: In function `__gmp_binary_multiplies::eval(__mpz_struct*, __mpz_struct const*, __mpz_struct const*)':
/usr/include/gmpxx.h:320: undefined reference to `__gmpz_mul'
...

I was very surprised to find out that it links fine with g++-4.4! So at the moment I'm compiling with g++-4.6 and linking with g++-4.4. Works, but isn't very satisfactory.

The libraries are located in /usr/lib and the missing symbols are definitely there:

$ locate libgmp
/usr/lib/libgmp.a
/usr/lib/libgmp.la
/usr/lib/libgmp.so
/usr/lib/libgmp.so.10
/usr/lib/libgmp.so.10.0.1
/usr/lib/libgmp.so.3
/usr/lib/libgmp.so.3.5.2
/usr/lib/libgmpxx.a
/usr/lib/libgmpxx.la
/usr/lib/libgmpxx.so
/usr/lib/libgmpxx.so.4
/usr/lib/libgmpxx.so.4.2.1

$ objdump -T /usr/lib/libgmp.so|grep __gmpz_set
...
0001f3a0 g    DF .text  00000096  Base        __gmpz_set
...

:confused::confused:

---

### Post by MadCow108 on 2012-01-07
this is wrong:
```
g++-4.6 -lgmpxx -lgmp ... 
```

it should be
```
g++-4.6 ... -lgmpxx -lgmp
```

---

### Post by DonkeySalami on 2012-01-08
Yes, indeed! Thank you!

---

