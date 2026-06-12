---
title: "[SOLVED] C question"
date: 2008-09-18
forum: Programming Talk
---

### Post by zksailor534 on 2008-09-18
I program in fortran and matlab, but a solver library I'm using is written in C (i think).  I'm pasting in the series of commands I'm interested in, but things I don't understand are the +=, *, and *=.  I'm trying to re-write this little routine in matlab, but I don't fully understand those parts.

Thanks for any help in advance.

    t1 = N/nprocs;
    t2 = N - t1 * nprocs;

    if ( proc >= t2) t2 += (proc * t1);
    else {
      t1++;
      t2    = proc*t1;
    }
    *N_update = t1*chunk;
    t2   *= chunk;

    for (i = 0; i < *N_update; i++) (*update)[i] = i + t2;
  }

---

### Post by mike_g on 2008-09-18
the += operator adds the righthand value to the lefthand variable. IE: a = a + b would be the same as a += b

*= is the same only for multiplication. You can also do /= -= %= >>= <<= ^= &= and |=

The * symbol can have a different meaning dependant on context. It is trhe multiplication operator, but is also used to signify a pointer. For example on this line:
```
*N_update = t1*chunk;
```
The content of the address that **N_update** points to will be set to **t1** multiplied by **chunk**

Hope that clears things up for you.

---

