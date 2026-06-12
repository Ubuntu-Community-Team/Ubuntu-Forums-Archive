---
title: "crypt_r problem (glibc)"
date: 2014-06-17
forum: Programming Talk
---

### Post by nibal on 2014-06-17
I'm developing a security application, using crypt_r in a multithreaded environment for testing. There are no support links for either crypt or glibc in the man pages, and couldn't find anything in the web :-(

 1) Is the hash returned (as a C-string) malloced or stack-allocated? Or maybe stored in the supplied data structure? Valgrind doesn't report it as a leak if i don't free it...
 2) crypt_r is supposed to be thread safe. However ~30% of the returned hashes are bad, shorter than should be from the protocol. This is independent of text given, 
 but rather time dependent. If i try to hash the same text later, it will produce the correct hash, and therefore won't match the table record. What is this error? Bug or smt
I'm doing wrong?

I just initialize once at start of program:
```
data.initialized = 0
```

data is global. Should it be thread specific and initialized in each thread?

I then call crypt-r as described in man pages.

Any ideas?

---

### Post by nibal on 2014-06-17
> **nibal said:**
> I'm developing a security application, using crypt_r in a multithreaded environment for testing. There are no support links for either crypt or glibc in the man pages, and couldn't find anything in the web :-(

 1) Is the hash returned (as a C-string) malloced or stack-allocated? Or maybe stored in the supplied data structure? Valgrind doesn't report it as a leak if i don't free it...
 2) crypt_r is supposed to be thread safe. However ~30% of the returned hashes are bad, shorter than should be from the protocol. This is independent of text given, 
 but rather time dependent. If i try to hash the same text later, it will produce the correct hash, and therefore won't match the table record. What is this error? Bug or smt
I'm doing wrong?

I just initialize once at start of program:
```
data.initialized = 0
```

data is global. Should it be thread specific and initialized in each thread?

I then call crypt-r as described in man pages.

Any ideas?

 It turns out that indeed result is stored in data and a pointer to it is returned. As such, data, should be allocated and initialized in each thread separately. No need to free returned pointer, as long as data is handled properly...;-)

---

