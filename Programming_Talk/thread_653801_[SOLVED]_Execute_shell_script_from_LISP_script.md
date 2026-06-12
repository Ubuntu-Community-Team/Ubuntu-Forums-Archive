---
title: "[SOLVED] Execute shell script from LISP script"
date: 2007-12-30
forum: Programming Talk
---

### Post by x1a4 on 2007-12-30
Hi,

How do I execute a shell script from a LISP script?  I want to execute a script whenever I login to Sawfish.  The place to do it is in ~/.sawfishrc which uses LISP to configure Sawfish.  I now nothing about LISP and googling didn't help. 

Thank you.

---

### Post by wolfbone on 2007-12-30
(system "shell_command")

probably....

---

### Post by x1a4 on 2007-12-30
> **wolfbone said:**
> (system "shell_command")

probably....

Eureka!

---

