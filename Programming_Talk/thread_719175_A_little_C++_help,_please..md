---
title: "A little C++ help, please."
date: 2008-03-08
forum: Programming Talk
---

### Post by ErusGuleilmus on 2008-03-08
Hello,

What code would I use in C++ to find what OS the program is running on? 

Thanks, and sorry for wasting your time with a stupid question.

   -Erus

---

### Post by LaRoza on 2008-03-08
Er, if it is compiled and running, you can assume it is running on the OS you compiled it for.

---

### Post by ErusGuleilmus on 2008-03-08
Clarification: Sorry, I meant what version of Ubuntu it is being run on.

---

### Post by LaRoza on 2008-03-08
> **ErusGuleilmus said:**
> Clarification: Sorry, I meant what version of Ubuntu it is being run on.

Parse: /etc/issue.

---

### Post by Martin Witte on 2008-03-09
As alternative for the already mentioned method you can parse the output of command lsb_release -a, or lsb_release -rci

---

