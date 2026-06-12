---
title: "interrupts during system call"
date: 2012-05-07
forum: Programming Talk
---

### Post by nolag on 2012-05-07
I heard that in Unix if there is an interrupt during a system call you will get an exception returned.  Is this true?  If so, is it also true for linux?  Do I need to wrap every system call in a try/catch (and loop if I need an answer)?

---

### Post by dwhitney67 on 2012-05-07
> **nolag said:**
> I heard that in Unix if there is an interrupt during a system call you will get an exception returned.  Is this true?  If so, is it also true for linux?  Do I need to wrap every system call in a try/catch (and loop if I need an answer)?

The information you have is incorrect; system calls do not throw exceptions, under any circumstance.  If a system call is interrupted, then it will return a value (typically -1 or some other value less than 0), and errno will be set to EINTR.

---

### Post by nolag on 2012-05-08
> **dwhitney67 said:**
> The information you have is incorrect; system calls do not throw exceptions, under any circumstance.  If a system call is interrupted, then it will return a value (typically -1 or some other value less than 0), and errno will be set to EINTR.

Ok, but if an interrupt occurs when I make a system call (say to read from a file), will I get back the correct result, or is that not a promise by the kernel?

---

### Post by dwhitney67 on 2012-05-08
> **nolag said:**
> Ok, but if an interrupt occurs when I make a system call (say to read from a file), will I get back the correct result, or is that not a promise by the kernel?

It's hard to answer your question; what do you mean by the "correct" result?  Also, what read function are you using... fread()?

If you have a specific function that you are interested in, then refer to the man-page for that function.  It should offer some insight as to what you can expect to be returned when the function is called.

---

