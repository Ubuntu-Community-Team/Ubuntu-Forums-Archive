---
title: "Signals and interruption of system calls"
date: 2010-12-27
forum: Programming Talk
---

### Post by dawwin on 2010-12-27
I've got in my program functions, which can be interrupted by signals (select(), recv() etc...). Should I write code, which will restart them in the case of interruption (errno == EINTR) even if I don't expect any signals? In some situations system or other programs can send signal to my program, so I am not sure

---

### Post by dwhitney67 on 2010-12-27
> **dawwin said:**
> I've got in my program functions, which can be interrupted by signals (select(), recv() etc...). Should I write code, which will restart them in the case of interruption (errno == EINTR) even if I don't expect any signals? In some situations system or other programs can send signal to my program, so I am not sure

If you have not set up any signal handlers or if you have not specifically indicated which signal(s) should be ignored, then, AFAIK, one of two possibilities will occur if a signal is sent to your process:

1.  The process will die ungracefully;

2.  The signal will be ignored (because that is the default behavior).

Look at the following man-page for more information on what behavior can be expected based on the signal type.
```

man 7 signal

```

---

### Post by MadCow108 on 2010-12-27
also note that when you define _BSD_SOURCE or _GNU_SOURCE signal handlers use BSD style restarting (SA_RESTART) instead of failing with EINTR

[http://www.gnu.org/s/libc/manual/html_node/Interrupted-Primitives.html](http://www.gnu.org/s/libc/manual/html_node/Interrupted-Primitives.html)

---

