---
title: "system calls in c?"
date: 2012-01-22
forum: Programming Talk
---

### Post by conradin on 2012-01-22
Hi all,
Im sure someone has asked this before, but Im not sure how to say what Im looking for. Im writing a program and I want to use linux commands like stat, inside my C program. Anyone have some pointers for me?

---

### Post by Simian Man on 2012-01-22
> **conradin said:**
> Hi all,
Im sure someone has asked this before, but Im not sure how to say what Im looking for. Im writing a program and I want to use linux commands like stat, inside my C program. Anyone have some pointers for me?

You can invoke generic commands with the "system" function, but it's a much better idea to call the C functions directly if possible.  For stat, for example, you can call system("stat"); but like I said you can call stat directly.  Check out "man 2 stat".  The 2 tells man to give you C programming references instead of the user commands.

---

### Post by conradin on 2012-01-22
Thanks Simian Man, That was pretty helpful looking at man 2 stat. 
Can you tell me just a bit more about making calls to system() in C?
I didnt see a man 2 system, why would I not want to use functional alread compiled code?


> **Simian Man said:**
> You can invoke generic commands with the "system" function, but it's a much better idea to call the C functions directly if possible.  For stat, for example, you can call system("stat"); but like I said you can call stat directly.  Check out "man 2 stat".  The 2 tells man to give you C programming references instead of the user commands.

---

### Post by Bachstelze on 2012-01-22
> **conradin said:**
> 
Can you tell me just a bit more about making calls to system() in C?
I didnt see a man 2 system,

It's in section 3, man 3 system.

> why would I not want to use functional alread compiled code?

Because it makes it harder for you to track what your program does. If you run system(), all the info you have about what the called program does is its exit status. In particular you can't (easily) control its execution, capture its output, or otherwise interact with it. Basically, you lose all control of your program until the called program has terminated.

Now, there is nothing evil in system(), if you don't need to do any of these things, and you are certain the called program works fine, feel free to use it. It's very difficult to be certain of that, though, because you know nothing about the system on which your program might be run.

---

