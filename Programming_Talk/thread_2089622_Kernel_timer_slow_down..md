---
title: "Kernel timer slow down."
date: 2012-11-29
forum: Programming Talk
---

### Post by cdang_2000 on 2012-11-29
Hi all,
 
I am sorry if this is right place to post this.
I have a driver runs fine on Ubuntu 9.04 (kernel 2.6.28).  It has a timer set to tick at 1ms.
 
I just updated my box to Ubuntu 12.10 (kernel 3.5.0-17) and the timer in my driver slow down 4 times.  I googled and see that Ubuntu 12.10 set the kernel timer to 250Hz instead of 1000Hz.  My questions are:
 
1. What is the last Ubuntu version that has the kernel timer still set to 1000Hz?
2. What is the reason it is set to slow down?
3. If I want to stay with Ubuntu 12.10, but speed the kernel timer to 1000Hz, what do I need to do?  Rebuild the kernel?  What else?
 
Thanks,
cdang_2000

---

