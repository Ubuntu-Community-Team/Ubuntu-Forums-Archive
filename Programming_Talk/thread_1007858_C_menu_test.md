---
title: "C menu test"
date: 2008-12-10
forum: Programming Talk
---

### Post by myquidproquo on 2008-12-10
Hi!

I'm trying to use an input file to test my program in c. The program has a simple menu. It's like
 
do { 
gets(stdin);
switch(...) 
}while(1).

In normal execution all works fine. 
But if I try to use "./program < input.txt" it loops infinitly. Anyway to solve this? Thank you.

---

### Post by dwhitney67 on 2008-12-10
You have nothing to break it out of the do-while loop.  Check for eof, using feof() after doing a call to gets().

Btw, you should really use fgets() in lieu of gets(); it is safer because you can avoid buffer overruns.

---

