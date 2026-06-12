---
title: "examine a program stack and a stack frame"
date: 2010-04-06
forum: Programming Talk
---

### Post by cybo on 2010-04-06
i would like to examine a program stack (let's assume i have a small code) and for that matter each individual stack frame (it would be nice to look into each individual register too). i was always puzzled by mysterious terms like stack frame and program stack and i was recently told that it is possible to examine them but unfortunately not how to do it. can anybody help out with that? i'm not a novice coder but i am, just like most of the programmers, a self taught one. i would appreciate any links to the websites, recommendations for books, gdb commands to use (i've heard of gdb, but really never used it much) or anything else.

any help in this matter is appreciated.

---

### Post by Compyx on 2010-04-06
This should get you started with gdb: [http://beej.us/guide/bggdb/]("http://beej.us/guide/bggdb/").

---

### Post by Wybiral on 2010-04-06
Start learning assembly if you want to learn about stack frames (and learn how C function calls are handled by most compilers).

---

### Post by MadCow108 on 2010-04-06
gdb executable
>break somewhere
>run
(...)
>backtrace
(shows all stack frames, first number is the stack frame number, you are in frame 0)
>frame 3
(you are now in frame 3 (assuming there is one) and can examine it with the usual gdb commands, e.g. list to the current source code position or print to examine variables/registers)

---

### Post by cybo on 2010-04-07
@everyone thank you very much. your input should get me started.

---

