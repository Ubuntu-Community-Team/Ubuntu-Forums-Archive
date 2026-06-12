---
title: "Timer usage in Kernel Module"
date: 2012-03-15
forum: Programming Talk
---

### Post by Kdar on 2012-03-15
How do I write a module that would wake up every X seconds and do some work?

I tried to use timer (setup_timer, mod_timer) but I can't get it to run Continuously.

---

### Post by CynicRus on 2012-03-15
[http://www.makelinux.net/ldd3/chp-7-sect-4]("http://www.makelinux.net/ldd3/chp-7-sect-4")

---

### Post by Kdar on 2012-03-16
I followed this example, Listing 1.

[http://www.ibm.com/developerworks/linux/library/l-timers-list/](http://www.ibm.com/developerworks/linux/library/l-timers-list/)

However, timer seems to expire only once and my_timer_callback is called only once.

How can I make this timer run after it expire (so that it would expire again and call my_timer_callback.. and so on)? do I have to create a new timer?

---
Nevermind, I figured out how to do it.

---

