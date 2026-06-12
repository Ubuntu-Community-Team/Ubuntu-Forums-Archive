---
title: "compiling in c"
date: 2008-02-05
forum: Programming Talk
---

### Post by rob21 on 2008-02-05
whenever I compile two files in a program named driver in a gnu compiler with the following "gcc -g -o driver driver.c list.c",  I get the message "driver not a file or directory". Help, what can I do.
                                                thanks

---

### Post by lnostdal on 2008-02-05
could you paste the output of running ls in your project directory and your call to gcc .. and include the output of gcc please?

---

### Post by jrothwell97 on 2008-02-05
Try putting your source files before the switches, such as -g and -o. IE:

```
gcc driver.c list.c -o driver -g
```

---

