---
title: "c++ - launching external application"
date: 2008-01-21
forum: Programming Talk
---

### Post by jondecker76 on 2008-01-21
I"m starting to nose around in c++ again (it has been a long time!)

I'm trying to get an external application to launch from within c++ code.  I have tried system(), but that halts my program. I need to launch an external application, while keeping my originating program still running.

Anybody have any idea?


thanks,

Jon

---

### Post by chenxing on 2008-01-21
Maybe you can add a & to run it background.

---

### Post by LaRoza on 2008-01-21
> **jondecker76 said:**
> I"m starting to nose around in c++ again (it has been a long time!)

I'm trying to get an external application to launch from within c++ code.  I have tried system(), but that halts my program. I need to launch an external application, while keeping my originating program still running.

Anybody have any idea?


thanks,

Jon

Try forking or threading. See my wiki, [http://laroza.pbwiki.com/Specifc](http://laroza.pbwiki.com/Specifc)

---

### Post by ynef on 2008-01-22
What you do in this case is that you use the system calls fork() and one of the exec()-family of system calls. fork() gives you a child process (a copy of your parent process, one big difference being the return value from fork() so you can distinguish them in your code), and one of the exec() functions basically replaces the process that runs it (the child process in your case) with some other process. It isn't too tricky, but takes some getting used to. If you own a UNIX programming book, it would be good to look into it -- or simply google around for it, I suppose.

---

