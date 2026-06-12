---
title: "C++ libc open() vs &quot;my&quot; open()"
date: 2007-10-01
forum: Programming Talk
---

### Post by zoniq on 2007-10-01
Hi,

I have a question with (probably) a simple answer.

I have a class foo with a self defined function called open().
Now I have another function in this class, e.g. called bar().

In the definition of bar() I want to use the libc function open() and not the open()  I defined in my class. How do I tell the compiler to use the libc function open()?

Well, a simple solution would be to rename my function open() to myOpen() or similar. But it would be good to know how it works in general.

Thanks

---

### Post by aks44 on 2007-10-01
> **zoniq said:**
> In the definition of bar() I want to use the libc function open() and not the open()  I defined in my class. How do I tell the compiler to use the libc function open()?

```
[COLOR="Red"]**::**[/COLOR]open(/*...*/);
```(or maybe **std :: open()** depending on what header you include)

FWIW you'd better use **std::fstream**s and forget libc for a moment...

---

