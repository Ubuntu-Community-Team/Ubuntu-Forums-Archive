---
title: "problem with debugger"
date: 2009-05-19
forum: Programming Talk
---

### Post by johnny_b_30 on 2009-05-19
hi guys , i'm using ddd debugger to debug a program in C, but when i try to run it, it aborts with the following message:

"Program exited with code 0176. You can't do that without a process to debug"

What is  that? what i have to do?

Thanks in advance

---

### Post by stroyan on 2009-05-19
I don't have a clear picture of how you started ddd or what you did between starting it and reading that message.  Tell us more.

Perhaps you ran the program and it exited with that result code.

If that is the case you could use a 'b exit' gdb command to set a breakpoint at the exit function.
Then running the program would result in a stop just before exiting.

---

