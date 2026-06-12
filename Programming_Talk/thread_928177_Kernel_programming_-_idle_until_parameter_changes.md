---
title: "Kernel programming - idle until parameter changes"
date: 2008-09-23
forum: Programming Talk
---

### Post by scheissmann on 2008-09-23
Greetings,

I'm trying to make a program that takes a command line paramter (say foo). After it gets loaded into the kernel, it would wait until I supply a value 1 to the paramter using echo 1 > parameter, and then execute the subsequent codes. Which is the best way to do it? I came across the function wait_event(), but it seems like that it only works with device drivers and so on that supply the queue for the function. Thank you!

Kurt

---

