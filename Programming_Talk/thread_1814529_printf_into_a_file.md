---
title: "printf into a file"
date: 2011-07-29
forum: Programming Talk
---

### Post by roololing on 2011-07-29
Is there a way to make printf print into a file instead of stdout? I've never worked with files before in c/c++, just robots.... A simple helloworld code would be appreciated.

---

### Post by cguy on 2011-07-29
Use fprintf.

eg:
FILE *fp; /*then open the file*/
char *name="John";
fprintf(fp, "Hello, %s!", name)

---

### Post by roololing on 2011-07-29
Thank you for the quick reply!

---

### Post by stchman on 2011-07-30
I gather we can assume you are programming in C?

---

