---
title: "Quick question about the stack"
date: 2008-11-28
forum: Programming Talk
---

### Post by Stoodle on 2008-11-28
I'm learning assembly using "Programming from the Ground Up" and it said when space for variables needs to be reserved on the stack, the base pointer gets pushed down. The book says that you'd subtract from the base pointer to do that but wouldn't that move to the top of the stack?

Also, how exactly does pushing the base pointer work? Wasn't sure where it'd move to if the stack is filled sequentially. There'd be no empty spaces for it right?

---

### Post by slavik on 2008-11-29
stack grows from the end, so the stack grows towards the lower numbers.

on x86, the stack pointer is stored in SP (ESP for 32bit?), you push that and the general purpose registers when entering a function. then you move the stack pointer (sub from SP) the number of bytes you want to reserve for local variables. then you undo everything in reverse order (except no need to add to SP, since it gets restored from stack).

---

### Post by Stoodle on 2008-11-29
However, when you allocate space on the stack by moving the base pointer back, what if there's already data where you move the base pointer back to? Also, when you move off into function, do local variables always get pushed into the stack? Is the stack linear? I don't believe that the book addresses these questions.

---

