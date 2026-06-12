---
title: "gcc + running an executable"
date: 2012-03-08
forum: Packaging and Compiling Programs
---

### Post by Parzi on 2012-03-08
Here is a novice question.

I wrote a small c program (Test.c) and used gcc to compile it. An executable called "test" was created. But when I tried to execute it (by writing "test" and pressing enter) nothing happened (I got message "Command not found) when I tried to run it. I have allowed the file to be used as an executable. Also clicking the executable in file management causes nothing to happen. What goes wrong?

---

### Post by lisati on 2012-03-08
If you are doing something like this:
```
gcc test.c -o test
```
you can do this to run it:
```
./test
```

---

### Post by Parzi on 2012-03-08
Thank you, it works.

---

