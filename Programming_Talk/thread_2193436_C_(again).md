---
title: "C (again)"
date: 2013-12-12
forum: Programming Talk
---

### Post by wingnut2626 on 2013-12-12
Thanks for the help guys on the last one.  I really appreciate it. 

Here is my current problem:

```
printf("The length of my name is %d\n\n",strlen("Charles Barkley"));
```

It doesn't print the number of characters.  What am I doing wrong?

---

### Post by trent.josephsen on 2013-12-12
Works for me, but notice that strlen() returns a size_t while %d expects an int. You should use the %zu specifier instead when printing a size_t. Running gcc with the -Wall flag will warn you about format mismatches.

---

