---
title: "ddd debugger"
date: 2008-02-10
forum: Programming Talk
---

### Post by rob21 on 2008-02-10
in a ddd debugger with my project compiled and all source files loaded unto the GDB console,  whenever I try to set a breakpoint  I get the message "no line 9 in file driver.c" or "no line 10 in file driver.c". It seems that only one or two lines are being acknowledged in my driver.
Help please.
         thanks

---

### Post by hod139 on 2008-02-10
did you enable debugging symbols when you compiled?

```

gcc -g 

```

---

### Post by shaggy999 on 2008-02-10
what is the output of ddd when you give it the list command?

---

