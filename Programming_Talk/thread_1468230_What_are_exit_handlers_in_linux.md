---
title: "What are exit handlers in linux ?"
date: 2010-05-01
forum: Programming Talk
---

### Post by youralibaba on 2010-05-01
I want to know about exit handler. They are reportedly cal when exit() is made in the c binary code. With them IO cleanup routines are also caled.. and there are thirty two exit handlers.
Plz tell me about these. What do those exit handlers do ?

---

### Post by MadCow108 on 2010-05-01
libc:
[http://www.gnu.org/software/libc/manual/html_node/Program-Termination.html#Program-Termination](http://www.gnu.org/software/libc/manual/html_node/Program-Termination.html#Program-Termination)

kernel:
[http://www.informit.com/articles/article.aspx?p=370047&seqNum=4](http://www.informit.com/articles/article.aspx?p=370047&seqNum=4)
(don't know if that article is still up to date)

---

### Post by Compyx on 2010-05-01
> **youralibaba said:**
> I want to know about exit handler. They are reportedly cal when exit() is made in the c binary code. With them IO cleanup routines are also caled.. and there are thirty two exit handlers.
Plz tell me about these. What do those exit handlers do ?

The C standard guarantees a conforming C program can register at least 32 exit handlers. That doesn't mean there are 32 handlers, you have to provide them yourself with the atexit(3) call. If you don't provide any, there won't be any. The standard does guarantee that when exit() is called or when returning from main, all open streams are flushed and closed. This is different with _Exit(3) (std C) and _exit(3) (POSIX) which terminate immediately without cleaning up.

You can examine the number of exit handlers a program can declare with sysconf(3), a POSIX extension.

---

