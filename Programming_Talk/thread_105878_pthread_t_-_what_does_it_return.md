---
title: "pthread_t - what does it return?"
date: 2005-12-19
forum: Programming Talk
---

### Post by scorpio2002 on 2005-12-19
Hi there!
Here's my question. When I do a printf() on a variable of the pthread_t type I expect to get a TID. But I'm getting a negative very long integer. is that normal? What is that negative integer? How do I get the correct thread ID?

---

### Post by thumper on 2005-12-19
pthread_t is an opaque type.  While it is often represented by an int or long, you cannot guarantee the value.  Solaris seems to use incrementing integer values using 1 for the main thread and increasing values there after.  Linux however does not use a method like that.  You can be guaranteed that the value is unique for your current process, but that is about it.

---

