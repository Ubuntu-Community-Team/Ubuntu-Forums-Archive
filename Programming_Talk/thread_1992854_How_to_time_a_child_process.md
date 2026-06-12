---
title: "How to time a child process?"
date: 2012-06-01
forum: Programming Talk
---

### Post by MaximusGlory on 2012-06-01
Hi. Could anyway please show me the way to retrieve the timing statistics of a child process, in a C program, after it has terminated? What I am looking for is a way, or an example, on how to obtain the CPU time used (both user and system time) as well as the real time it took for the child process to execute. 

Any response is much appreciated. Thanks.

---

### Post by ofnuts on 2012-06-01
getrusage() ?

---

### Post by MaximusGlory on 2012-06-01
Hi. Thanks. It is not a problem anymore, I have figured it out.

---

### Post by Trumusiate on 2012-06-01
Hi!
Could you explain how you did it?

---

