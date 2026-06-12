---
title: "How to profile C program?"
date: 2007-12-16
forum: Programming Talk
---

### Post by biso on 2007-12-16
Dears,

I developed a C program and I want to measure CPU, memory and IO access of the program? any tool to do that??


Thanks in advance
BISO

---

### Post by slavik on 2007-12-16
look into valgrind

---

### Post by biso on 2007-12-16
Thanks for the tool. 
Is there any built-in tools in unix?

---

### Post by slavik on 2007-12-16
there is time, but it will only tell you the amount of time the process spent running in user mode, the time it spent for doing system calls and the total time it ran. (consider it as a general overview of which your app does most).

---

### Post by Wybiral on 2007-12-16
"gprof" is another option.

---

### Post by Majorix on 2007-12-16
> **biso said:**
> Is there any built-in tools in unix?

I haven't come across any if there is, but it would be great to have one. It could even be built into gcc, which when called with an option like --profile tells you the profile info. Just dreaming :p

---

### Post by jpkotta on 2007-12-16
Take a look at OProfile too.  It profiles the entire system (kernel too) with a kernel module.  You can of course narrow things down to a specific program.

---

### Post by biso on 2007-12-17
> **Wybiral said:**
> "gprof" is another option.

Thanks a lot, gprof is what i need :)

---

### Post by kuscsik on 2008-01-29
Here is a simple example of using gprof

[http://kuscsik.blogspot.com/2007/08/how-to-benchmark-c-code-using-gcc.html](http://kuscsik.blogspot.com/2007/08/how-to-benchmark-c-code-using-gcc.html)

I hope you will find it useful.

---

