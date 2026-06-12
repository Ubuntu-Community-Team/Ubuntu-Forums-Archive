---
title: "C++: How to initiate kernel panic?"
date: 2009-05-09
forum: Programming Talk
---

### Post by camper365 on 2009-05-09
I am trying to write a program that calls the panic() function in c++.
where is the library that does that, or do I need to get the linux-source?

---

### Post by stroyan on 2009-05-09
As you say you are writing c++ code I can be fairly certain that you don't intend to write kernel code.  Code in the kernel is never written in c++.
You can't just call some panic function from user space code to panic a linux system.  If you are writing code that will run as root then you may able to use the sysrq mechanism to trigger a stack trace and shutdown similar to a panic.  See [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key) and the /proc/sysrq and /proc/sysrq-trigger pseudo-files.

---

### Post by monkeyking on 2009-05-09
Why do you want to crash the system?
I'me been trying to avoid that for many years now.

don't know if it helps,
but check this

[http://www.faqs.org/docs/Linux-HOWTO/Linux-Crash-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Linux-Crash-HOWTO.html)

---

### Post by Sinkingships7 on 2009-05-10
This sounds vaguely like you're trying to write a virus of some sort...

---

### Post by cobolt01 on 2009-05-10
Yes, I couldn't imagine any situation that would require you to initiate a kernel panic that isn't malicious.

---

