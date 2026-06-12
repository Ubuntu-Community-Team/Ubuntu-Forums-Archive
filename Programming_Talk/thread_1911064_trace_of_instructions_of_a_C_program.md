---
title: "trace of instructions of a C program"
date: 2012-01-18
forum: Programming Talk
---

### Post by chuchi on 2012-01-18
I would like to know if there is a tool to know the trace of instructions of a C program once it has finished. I know I can debug with gdb as the program is executing, but I am using ncurses and it is very difficult.
 

 Thank you very much!

---

### Post by karlson on 2012-01-18
> **chuchi said:**
> I would like to know if there is a tool to know the trace of instructions of a C program once it has finished. I know I can debug with gdb as the program is executing, but I am using ncurses and it is very difficult.
 

 Thank you very much!

You can attach the gdb to a process to see the execution by running ```
gdb -p <pid>
``` in another terminal.

---

