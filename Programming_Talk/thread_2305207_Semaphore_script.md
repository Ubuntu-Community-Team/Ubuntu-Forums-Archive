---
title: "Semaphore script"
date: 2015-12-03
forum: Programming Talk
---

### Post by Rovio on 2015-12-03
Hello, i have problem with a semaphore script. There must be 3 printers and we have 7 books to print which have 7 chapters each.
Printing times each chapter:
Ch1 => 5 seconds
Ch2 => 6s
Ch3 => 7s 
Ch4 => 4s
Ch5 => 5s
Ch6 => 6s
Ch7 => 3s
 
Any ideas how to write script and solve this problem as fastes we can ? It must be C language

---

### Post by QIII on 2015-12-03
Have you consulted with your instructor?

---

### Post by Rovio on 2015-12-03
Its must be something like this:

[TABLE="width: 500"]
[TR]
[TD]TIME[/TD]
[TD][/TD]
[TD]PRINTERS[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]START[/TD]
[TD]1[/TD]
[TD]2[/TD]
[TD]3[/TD]
[/TR]
[TR]
[TD]5s[/TD]
[TD]Ch1 (5s)[/TD]
[TD]Ch2(6s)[/TD]
[TD]Ch3(7s)[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]
If printer is free then it stars printing next chapter

---

### Post by mystics on 2015-12-03
I'm not during your homework for you! You can easily learn about basic semaphore functions with the following man pages:

```

man 3 sem_init
man 3 sem_wait
man 3 sem_post

```

Beyond that, there are a lot of tutorials online about some basic semaphore usage, how to solve concurrency problems, and how to avoid situations like deadlock. You don't need us to do your homework for you. There's more than enough information out there to help you figure out how to do it yourself.

---

### Post by QIII on 2015-12-03
While we are glad to help with minor sticking points, Ubuntu Forums is not a homework service.

Closed.

---

