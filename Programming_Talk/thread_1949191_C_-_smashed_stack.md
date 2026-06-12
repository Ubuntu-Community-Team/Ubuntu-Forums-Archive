---
title: "C - smashed stack"
date: 2012-03-29
forum: Programming Talk
---

### Post by cguy on 2012-03-29
How do you debug smashed stacks efficiently? I spent all day and couldn't solve this problem:

Two consecutive frames look like this:
#3 func3 ( param1 = 0x0, param2 = 0xXXXXXXXX )
#4 func4 ( paramA = 0xYYYYYYYY, paramB = 0xZZZZZZZZ )

paramA and paramB are valid pointers to structures.
param1 should be _exactly_ paramA, but is NULL instead.
param2 should be a member of paramB, but points to a nonsense address.

How can this be? If I switch to frame 4, all variables are OK, but in frame 3 they all go haywire. Shouldn't they break somewhere inside frame 4? (because they don't, somehow. They look OK all the way. Only in f3 they don't)

This problem was reproduced only three time in the course of 2 days of intensive testing.

---

### Post by Bachstelze on 2012-03-29
Have you used valgrind to check for abnormal memory accesses ?

---

### Post by cguy on 2012-03-29
No, not yet.
Will Valgrind be useful for that vast majority of cases when the program works fine?

---

### Post by Bachstelze on 2012-03-29
Hard to say without seeing the code, but even if it doesn't, you can make a script to do a thousand runs and output the valgrind log for each one, then grep through them to see what happens when it goes wrong.

---

### Post by Bachstelze on 2012-03-29
P.S.: Valgrind is a tool you should run on *every* C program as part of your testing. The vast majority of invalid memory accesses go unnoticed for a long time.

---

### Post by cguy on 2012-04-02
Just in case someone has a similar trouble as I did: those NULLs were, in fact, optimized values.
The code was built for an embedded platform and that's how GDB displayed them. On the simulator it showed clearly "value optimized out".

---

### Post by cgroza on 2012-04-02
Are you relying on implementation dependent features?

---

