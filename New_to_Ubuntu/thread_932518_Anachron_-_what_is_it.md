---
title: "Anachron - what is it?"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by pucenavel on 2008-09-28
What is anachron?  specifically, what does cron.daily refer to?

---

### Post by t0p on 2008-09-28
I think you mean **anacron**...

```
t0p@ubunty:~$ man anacron

ANACRON(8)                   Anacron Users’ Manual                  ANACRON(8)

NAME
       anacron - runs commands periodically

```

Now maybe you can guess what cron.daily is?

---

### Post by pucenavel on 2008-09-28
OK - got it.  Spelling always helps, natch!

This is something that was showing up in syslog - I was just curious.

It looks like everything in the related files is "defaults" since the modified dates on all are before I reloaded the OS.

---

