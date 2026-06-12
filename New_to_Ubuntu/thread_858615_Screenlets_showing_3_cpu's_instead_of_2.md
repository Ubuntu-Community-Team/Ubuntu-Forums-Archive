---
title: "Screenlets showing 3 cpu's instead of 2?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by kool_kat_os on 2008-07-13
I have a intel p4 hyperthreaded...but when i use a screenlets sensor applet it says i have 3 cpu's instead of 2  (CPU0 CPU1 CPU2) 

right now i selected CPU0 and CPU1 ....are those the correct ones?

---

### Post by descendency on 2008-07-13
edit: I'm an idiot. You have a single core chip (which is why you call it a p4. . .)

It doesn't mean 3 CPUs. It means 3 threads. I'm not sure how you got a 3rd one, though.

---

### Post by johnl on 2008-07-13
CPU1 is your first physical processor and CPU2 is the second.
CPU0 is your 'total' CPU --  ie, the combination of CPU1 and CPU2.

---

### Post by kool_kat_os on 2008-07-13
ah! so it is an average of both theads(as i believe they are called)

---

### Post by johnl on 2008-07-13
> **kool_kat_os said:**
> ah! so it is an average of both theads(as i believe they are called)

Yup, it's the average.  If CPU1 is completely pegged out(100%) and CPU2 is idle, CPU0 will report 50%.

I wouldn't call them 'threads', though.  They're cores or processors -- threads are a different concept :)

---

### Post by kool_kat_os on 2008-07-13
even in hyper threaded processors?

they are still called cores?

---

