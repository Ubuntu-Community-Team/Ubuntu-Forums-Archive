---
title: "g++/gcc show assembler code"
date: 2010-02-05
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2010-02-05
Hello all,

I'm just wondering if any of you know how to view the assembler code after compiling C++ code with g++/gcc.  I can't find information on this any where.

Thanks.

---

### Post by baddog144 on 2010-02-06
```

gcc -S foo.c

```
Note the -S

---

### Post by c0mput3r_n3rD on 2010-02-06
You made my night. Thank you!

---

### Post by baddog144 on 2010-02-06
Hey, no problem :)

---

### Post by MadCow108 on 2010-02-06
you can also use objdump -dS on the compiled binary

---

### Post by c0mput3r_n3rD on 2010-02-06
Thanks madcow that's pretty cool.

---

