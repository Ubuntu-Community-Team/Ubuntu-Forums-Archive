---
title: "[C] List files in directory &amp; macro question"
date: 2010-07-23
forum: Programming Talk
---

### Post by SpinningAround on 2010-07-23
Is there a way in a linux environment to list all files in a specific directory? I wonder if it's possible in C and not C++ or C# since I studying for a course.

Macro question:
Could someone explain what this macro do?
[PHP]#define DATA_REG (*(unsigned char *) 0x200 )[/PHP]

---

### Post by dwhitney67 on 2010-07-23
You can use the combination of opendir() and then readdir() to get the contents of a directory.  Don't forget to use closedir() when you are done.

As for your other question, the inner cast is treating the 0x200 as an address, and then the outer '*' is dereferencing the address so that the value at the address can be read (and if permitted, written to).  If for example, the address represents a 16-bit (2-word) register, you could use the macro as such:
```

unsigned short value = DATA_REG;

```

---

### Post by SpinningAround on 2010-07-23
Thanks :D

---

