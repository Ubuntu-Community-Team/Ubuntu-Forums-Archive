---
title: "[c] malloc, free and multithreading program"
date: 2010-08-04
forum: Programming Talk
---

### Post by dawwin on 2010-08-04
Are malloc() and free() thread-safe? Some people say, they are, others say they aren't and finally I don't know anything about it for sure. Can anyone, who has an experience with threads and memory allocation, tell me how it really is?

---

### Post by vikas.sood on 2010-08-04
> **dawwin said:**
> Are malloc() and free() thread-safe? Some people say, they are, others say they aren't and finally I don't know anything about it for sure. Can anyone, who has an experience with threads and memory allocation, tell me how it really is?

I think current versions of malloc and free implementation should all be thread safe. In general, platforms supporting multi threaded environments should all have thread safe versions.

I remember reading somewhere that with libc 2.0 malloc free along with some other functions are thread safe. I will try to find those links and share here.

---

### Post by MadCow108 on 2010-08-04
they are thread safe in newer versions of glibc
How new I don't know, but probably since quite a long time.

The oldest version I recall using in multithreaded programs without problems is 2.3.6. Probably also much earlier versions  are fine.
But realloc has pretty bad multithreaded performance in that version. This should be better in newer versions.

---

### Post by dawwin on 2010-08-04
I found this in malloc/malloc.c in sources of gnu libc:
```

Thread-safety: thread-safe unless NO_THREADS is defined

```

---

### Post by interval1066 on 2010-08-04
If you link with -pthreads, malloc() will be threadsafe in glibc.

---

