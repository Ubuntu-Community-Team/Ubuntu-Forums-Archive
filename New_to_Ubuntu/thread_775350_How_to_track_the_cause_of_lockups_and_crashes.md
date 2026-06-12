---
title: "How to track the cause of lockups and crashes?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Stabilityonitsown on 2008-04-30
Hi guys how do I track the cause of lockups and crashes in applications or just the pc in main.

---

### Post by firefeather on 2008-04-30
The System Log (depends on which variant you're using, but under Ubuntu it's System -> Administration -> System Log ) keeps track of errors and messages. That's where I'd start if I were to try to track something like that down.

---

### Post by Stabilityonitsown on 2008-04-30
Would about file wise? Is there any file I can look at with the log of something or some program.

---

### Post by MONODA on 2008-04-30
the cause of most crashes and lockups is compiz fusion (visual effects), turn them off.

---

### Post by firefeather on 2008-04-30
> **Stabilityonitsown said:**
> Would about file wise? Is there any file I can look at with the log of something or some program.
The system log does read actual files.

As for specific programs, you might try running them from terminal or running in a debug mode to see if they leave any information you might need. There isn't a consistent way besides that to see a program's log.

---

### Post by firefeather on 2008-04-30
> **MONODA said:**
> the cause of most crashes and lockups is compiz fusion (visual effects), turn them off.

I wouldn't say that's true necessarily, but I would agree it can help you to track down a graphics problem if the crashes disappear when you turn off compiz fusion.

---

### Post by martrn on 2008-04-30
/var/log

has log files.
See kernel.log or kern.log for crashes

anyway look through you log directory...

---

### Post by MONODA on 2008-04-30
i say that because i have never had a lockup in ubuntu with compiz turned off. (I am not sure about hardy since I have never used it and dont plan to)

---

### Post by Stabilityonitsown on 2008-04-30
Thx guys, I can use all this information as I am trying to help the community by reporting bugs..

---

### Post by martrn on 2008-04-30
> **Stabilityonitsown said:**
> Thx guys, I can use all this information as I am trying to help the community by reporting bugs..

:KS:KS:KS:KS:KS

Your a star.  I remember reading once, a bug is short as the number of eyeballs.  The more eyeballs we have the better.

---

