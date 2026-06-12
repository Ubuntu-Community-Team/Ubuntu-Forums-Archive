---
title: "how to create a semaphore for student thread and virtuoso thread respectively?"
date: 2018-11-30
forum: Programming Talk
---

### Post by christ1128 on 2018-11-30
there is a practice studio that contains three pianos. Up to
three student pianists are welcome to enter the studio to use the instruments simultaneously. When
they are done practicing, they leave. However, when a virtuoso arrives, she waits until there are no
others in the studio, at which point she enters the room and is permitted to practice alone until she
is ready to leave.
You are to model this problem using semaphores and count variables for synchronization. In
additional to meeting the criteria above, your solution should avoid starvation of any of the pianists
(e.g., a virtuoso will not be starved of the room if there is a steady stream of students arriving).
Your solution will consist of two threads (one for the student, one for the virtuoso). The following
are recommended semaphore and count variable declarations. Feel free to declare your own.
studentCount = 0
mutex = Semaphore(1)
turnstile = Semaphore(1)
studioEmpty = Semaphore(1)
pianoMultiplex = Semaphore(3)

how to create a semaphore for student thread and virtuoso thread respectively?

---

### Post by QIII on 2018-12-01
Please review  the [Forum Rules]("https://ubuntuforums.org/misc.php?do=showrules") and [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945").

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued..

Closed

---

