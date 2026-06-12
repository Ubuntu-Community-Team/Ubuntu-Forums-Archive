---
title: "i killed kern.log"
date: 2008-09-29
forum: Programming Talk
---

### Post by cjwang23 on 2008-09-29
I was doing some kernel module development.  I did something wrong and my kernel module crashed.  After that, kern.log stopped logging.

I use printk(KERN_ALERT "....") to display stuff to kern.log.

How do I get it back without reboot my computer?

I tried restart sysklogd and klogd.  klogd seemed touched kern.log, but it won't print my message to the file immediately.  It seemed only flush pending kernel messages when I restart it.

C.J.

---

### Post by meanburrito920 on 2008-09-29
... but I didn't get the deputy!

Sorry, I couldn't resist.
As for your question, is there a reason  why you can't simply reboot?

---

### Post by cjwang23 on 2008-09-29
Reboot takes a long time.  Not an efficient way to debug.  I believe there must be a way to restart daemons.  The kernel was still running perfectly.

If there is any other way for me to see the output of printk, that will work, too.

---

### Post by dribeas on 2008-09-30
I just rechecked that you had already done was I was to propose. No more ideas then :)

---

