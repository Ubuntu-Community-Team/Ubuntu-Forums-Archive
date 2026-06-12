---
title: "function sigaction and &lt;signal.h&gt;"
date: 2008-01-22
forum: Packaging and Compiling Programs
---

### Post by pckong on 2008-01-22
Hi all,

I need help for compiling a file. Somehow I need to use function sigaction(). 
It seems that the function is in <signal.h> library. but when I try to compile it is not loaded, any ideas on how to reinstall <signal.h> library?

Pete

---

### Post by stroyan on 2008-01-22
sudo apt-get install libc6-dev

---

