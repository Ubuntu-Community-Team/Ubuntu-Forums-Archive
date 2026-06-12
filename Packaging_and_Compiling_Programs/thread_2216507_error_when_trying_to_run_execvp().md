---
title: "error when trying to run execvp()"
date: 2014-04-12
forum: Packaging and Compiling Programs
---

### Post by noam2 on 2014-04-12
hi everyone,

i have written a program in C which is supposed to compile and run other C files.
when i call execvp() to i get this error:

**"gcc: error trying to exec 'cc1': execvp: No such file or directory."**

i have no problem compiling and running programs from shell or eclipse for example.
i have looked up the cc1 file and found it in /usr/lib/gcc/x86_64-linux-gnu/4.6

this is my code:
char *args[] = {"gcc","-o","b.out",filePath,NULL};
ret_code = execvp("gcc", args);

any ideas?
thanks

---

