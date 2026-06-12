---
title: "C Non-Buffered I/O"
date: 2008-07-04
forum: Programming Talk
---

### Post by solarwind on 2008-07-04
Hey all,

I'm making a program in C which needs non-buffered i/o. For that, I'm using the open() function (which returns an int file descriptor). However, I need to pass it a flag which tells it to open in binary mode. The flag is O_BINARY and it is defined as 0x8000. However, I noticed that this define is in fnctl.h. I was compiling on Windows using MinGW. However, when I tried compiling on BSD, the flag O_BINARY doesn't exist.

1. I was wondering if anyone could tell me more about this O_BINARY flag.
2. Can someone please check their C headers in Ubuntu to check if the O_BINARY flag is defined?

---

### Post by geirha on 2008-07-04
binary mode vs text mode is a windows thing. In unix you always access files in "binary mode".

---

### Post by solarwind on 2008-07-04
> **geirha said:**
> binary mode vs text mode is a windows thing. In unix you always access files in "binary mode".

Thanks!

---

### Post by solarwind on 2008-07-04
Ok, so now since I want my program to compile on all platforms, how do I use ifdefs and defines to do something like:

```
#ifdef WINDOWS
//open statements with O_BINARY
#else
//normal open statements
#endif
```

How would I "define" the flag WINDOWS so that I can use it like the example above?

---

