---
title: "Print commands in the 'at' queue"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by decktrio on 2013-02-07
Hey everyone, I've got a noob Linux question.  I'm trying to figure out how I can see the command to an at job that's in the queue. I know that 'atq' will list the queue by job number, but does anyone know where I can see what that job is?

---

### Post by Krytarik on 2013-02-08
> **decktrio said:**
> I know that 'atq' will list the queue by job number, but does anyone know where I can see what that job is?
Run this command on the job number you get there:
```
at -c <job-number>
```Regards.

---

### Post by decktrio on 2013-02-12
Thanks!

---

