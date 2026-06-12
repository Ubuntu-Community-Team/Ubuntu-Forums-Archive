---
title: "Source code of C rand function"
date: 2011-01-20
forum: Programming Talk
---

### Post by mecrazycoder on 2011-01-20
hi,
  Please let me know where can I get the source code of actually implementation of C rand() function. I checked in coreutils but it is not there. Thanks in advance

---

### Post by geirha on 2011-01-20
It's in the standard C library, so:
```
apt-get source libc6
```

You'll have to dig a little to find the actual code, but eglibc-2.11.1/stdlib/rand.c should be a good start.

---

### Post by geirha on 2011-01-20
It's in the standard C library, so:
```
apt-get source libc6
```

You'll have to dig a little to find the actual code, but eglibc-2.11.1/stdlib/rand.c should be a good start.

---

### Post by mecrazycoder on 2011-01-21
> **geirha said:**
> It's in the standard C library, so:
```
apt-get source libc6
```You'll have to dig a little to find the actual code, but eglibc-2.11.1/stdlib/rand.c should be a good start.
Thank you

---

### Post by Arndt on 2011-01-21
You may want to look at 'random' and 'drand48', too.

---

### Post by Simian Man on 2011-01-21
The rand function included in libc is actually pretty bad.  I don't know what you are asking for, but there are much better implementations out there on the net.

---

### Post by psusi on 2011-01-21
If you want cryptographically strong random numbers, you want /dev/random.  If you don't care THAT much, then rand() is just fine.

---

### Post by Arndt on 2011-01-21
> **psusi said:**
> If you want cryptographically strong random numbers, you want /dev/random.  If you don't care THAT much, then rand() is just fine.

As a blanket statement, no, not really, but if you first determine what kind of properties are important for your application and test 'rand' for those to your satisfaction, then all will be fine.

---

