---
title: "parallel programming"
date: 2012-03-25
forum: Programming Talk
---

### Post by chmcy on 2012-03-25
hello, i am trying to make a parallel program using threads and i need some help. Actually i've got 2 threads an i want them to add the lines of two arrays and when one of the threads finish, get then next free line and make the calculations. How can i do that?
thanks

---

### Post by r-senior on 2012-03-25
Welcome :)

What language are you working in?

---

### Post by chmcy on 2012-03-25
hi! :)  with c

---

### Post by ofnuts on 2012-03-25
> **chmcy said:**
> hello, i am trying to make a parallel program using threads and i need some help. Actually i've got 2 threads an i want them to add the lines of two arrays and when one of the threads finish, get then next free line and make the calculations. How can i do that?
thanksSince the threads will likely take always more ore less the same time to process a line, why not avoid the problem and make one thread process the even lines and the other the odd ones?

---

### Post by chmcy on 2012-03-26
ok but how do we know that is the same time for each thread? if i have a huge table then there is a possibility the  one of the threads to finish much earlier than the other right?

---

### Post by ofnuts on 2012-03-26
> **chmcy said:**
> ok but how do we know that is the same time for each thread? if i have a huge table then there is a possibility the  one of the threads to finish much earlier than the other right?Not really... I expect the number of instruction executed by each thread to process each line to be identical. If there are large execution time discrepancies between the lines, it means something is making you wait (swapping?) and then being multi-thread is moot... (I assume you want to run full-throttle on all cores... btw you may also want to look at SSE instructions if you haven't done so already).

---

### Post by chmcy on 2012-03-26
yeap u r right..  i actually wanted to try that.. having two threads running and when the one finish, doing the next job bt i think this wont be very effiecient.. :)

---

