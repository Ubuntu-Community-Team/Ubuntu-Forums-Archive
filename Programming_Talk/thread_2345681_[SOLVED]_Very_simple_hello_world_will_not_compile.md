---
title: "[SOLVED] Very simple hello world will not compile"
date: 2016-12-06
forum: Programming Talk
---

### Post by mjpin1 on 2016-12-06
I am very new to using ubuntu and was looking to compile a very simple hello world c program, but when i do i get the error:
gcc test.c -o test
gcc: error: test.c: No such file or directory
gcc: fatal error: no input files
compilation terminated.
I am in the directory that the file is in and i have tried reinstalling gcc and build essential and all that jazz. Why is this not working?

---

### Post by TheFu on 2016-12-06
> gcc: error: test.c: No such file or directory

Are you sure?  All Unix systems are case sensitive and need specific permissions for a userid to read the input file(s) and write to the directory.
Please post the output in the directory of **ls -alF** for more specific help, if needed.

---

### Post by kpatz on 2016-12-06
Make sure your source file is really named test.c and not Test.c or test.C or TEST.C.  Linux like other Unix variants use case sensitive file/directory names.

---

### Post by mjpin1 on 2016-12-07
I figured it out, I just assumed the file was saved as "test.c" as it was a c program file, but it just saved as "test". Thank you for the help

---

### Post by TheFu on 2016-12-07
Best not to hide extensions on any OS. This is an important security setting, especially for that "other" OS.

---

