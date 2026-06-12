---
title: "[SOLVED] 211 Processes?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-09-06
After installing and running Conky I discovered that I have 211 processes listed. Despite the fact that only a few are actually running, I'm afraid that this number could be too high. As a former Windows user, I usually had 30 processes, 39 tops and 25 after a lot of tweaking.

What should I do to reduce the number of processes if this is not normal?

---

### Post by Sorivenul on 2008-09-06
Is this while the system is idle, or do you have applications open (other than conky)?

How many "tasks" does the command ```
top
``` show?

---

### Post by lovinglinux on 2008-09-06
With system idle the number is just a little bit smaller.


> top - 00:49:42 up 10 min,  3 users,  load average: 0.15, 0.31, 0.21
Tasks: 114 total,   1 running, 113 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.2%us,  4.2%sy,  0.0%ni, 91.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2075688k total,   767508k used,  1308180k free,    22288k buffers
Swap:  2996080k total,        0k used,  2996080k free,   358604k cached

Another question:

Why I have 3 users listed using "top" command?

---

### Post by Sorivenul on 2008-09-07
114 isn't too high.  Right now I'm running 90.  I'm not much help with conky, but posting your config and having others look at it might not hurt, as it seems to be an issue with the way conky is recognizing the processes if I'm interpreting correctly.  As far as "top" showing 3 users, I don't know, I have two: myself and root listed.  Check the name of the third user, is it another user you have created?

---

### Post by sdennie on 2008-09-07
100+ processes seems completely reasonable to me.  The idea of "processes" may not be exactly what you are used to if you are coming from Windows and you probably have dozens (or even most of them) that are things that the kernel spins up to make your hardware work correctly.  These types of things likely exist in Windows as well but, they are not reported to the user or they are aggregated into big processes instead of lots of little small processes.

---

### Post by lovinglinux on 2008-09-07
> **Sorivenul said:**
> 114 isn't too high.  Right now I'm running 90.  I'm not much help with conky, but posting your config and having others look at it might not hurt, as it seems to be an issue with the way conky is recognizing the processes if I'm interpreting correctly.  As far as "top" showing 3 users, I don't know, I have two: myself and root listed.  Check the name of the third user, is it another user you have created?

Thanks. I'm not very concerned about Conky displaying more processes, but the number of processes itself. But I guess I'm within normal range.

I didn't created another user. There are 3 users listed, but in the process list I only see 2, me and root.

---

### Post by Sorivenul on 2008-09-07
+1 to vor's post.  Exactly right, the "process" concept between Windows and Linux is very different.  Good luck!

---

### Post by gletob on 2008-09-07
it lists one user as the gui and one as the terminal under the same account and one as root

---

### Post by lovinglinux on 2008-09-07
> **Sorivenul said:**
> +1 to vor's post.  Exactly right, the "process" concept between Windows and Linux is very different.  Good luck!

I imagined that, but you know how paranoid a former Windows user can be... :biggrin:

> **gletob said:**
> it lists one user as the gui and one as the terminal under the same account and one as root

All right then.

Thank you all.

---

