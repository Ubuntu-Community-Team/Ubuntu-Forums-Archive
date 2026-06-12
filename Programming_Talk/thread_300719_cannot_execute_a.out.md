---
title: "cannot execute a.out"
date: 2006-11-16
forum: Programming Talk
---

### Post by std03028 on 2006-11-16
hello,

im a new user of ubuntu and i have a problem in executing a.out. :-k 
compiling, linking are done well and a.out is created in the folder... but when i type a.out and hit enter, then it appears "a.out unknown command"
why? :-?  :evil:

---

### Post by llonesmiz on 2006-11-16
In order to execute a program in the current directory you need to prepend "./" before the name of the executable, e.g.:

./a.out

This is because the current directory isn't in the PATH. Anyway I think you should change the executable's name using the option -o in gcc.

gcc -o executable_name source_code_name.c

instead of simply

gcc source_code_name.c

(.c if you are using c but if you are using any other language the extension will be different)

---

