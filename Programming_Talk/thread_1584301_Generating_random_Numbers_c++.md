---
title: "Generating random Numbers c++"
date: 2010-09-28
forum: Programming Talk
---

### Post by DiegoTc on 2010-09-28
Hi guys I am trying to generate 150 numbers in less than 2 seconds.


```

srand(time(NULL));
opt=rand()%4+1;
QString mes=get_Character(opt);

```

But it is giving me the same numbers :(
I was reading about drand48_r(3) but still I don't get it.Can some one help in  this?

Thanks

---

### Post by NovaAesa on 2010-09-28
Are you calling this snippit 150 times? If that is the case, then you could be seeding to the exact same number each time (if the code runs very quickly, which I'm sure it would).

I would suggest seeding only once then just taking 150 numbers with rand().

---

### Post by worksofcraft on 2010-09-29
Yes as NovaAesa says.
you see srand is a "pseudo random" number generator and while the numbers it produces don't appear to be connected, it is always part of the same and identical sequence. This is often desirable so that it will produce repeatable results.

The reason you use the time function to "seed" the sequence is to start that sequence off in an unpredictable place, but when you seed it again, you may just be resetting it to that same start position :shock:

p.s. I just [googled it for you]("http://manpages.ubuntu.com/manpages/lucid/man3/rand.3posix.html") and it says: "The  rand() function shall compute a sequence of pseudo-random integers in the range [0, {RAND_MAX}] with a period of at least 2**32.

---

