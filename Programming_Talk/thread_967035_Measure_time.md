---
title: "Measure time"
date: 2008-11-01
forum: Programming Talk
---

### Post by BioCleaner on 2008-11-01
Can someone please tell me how to measure the execution time of a simple program I create?
Is there a command in the shell? Or do I have to introduce something in the source code(I use C)?

---

### Post by slavik on 2008-11-01
the simplest way is by using the time command.

---

### Post by BioCleaner on 2008-11-01
Thanks! But it displays 3 times: real,user,sys. What is the time that programming contests or acm sites usually consider. I also found an option "-f %E" in the man text. Does this display the time that they take into account?

---

### Post by slavik on 2008-11-01
they don't count execution time, they count the time in minutes after the beginning of the contest until the solution was submitted.

---

### Post by BioCleaner on 2008-11-01
I will give you an example. For this problem I found on an acm site the maximum execution time is 2 seconds.
[http://acm.timus.ru/problem.aspx?space=1&num=1007](http://acm.timus.ru/problem.aspx?space=1&num=1007)
How can I find out the time my solution for the problem has used for a certain input?

---

### Post by slavik on 2008-11-01
err, I know that they usually kill your process if it's been running for more than 2 minutes, since if it has been running that long, it is probably wrong.

I wouldn't look at the 2 second time limit.

---

### Post by BioCleaner on 2008-11-01
Some problems even have 0.1 seconds time limit. I want to check at my computer if my solution exceeds the limit before I send it. I think that the "-f %E" option shows that time but I'm not sure. If I don't include that option it shows a time that I think is a little big.

---

### Post by slavik on 2008-11-01
look up the UVa judge :)

---

### Post by BioCleaner on 2008-11-01
In this case I can but in other cases like school programming contests...

---

### Post by CptPicard on 2008-11-01
Running times on different machines are not comparable anyway...

---

### Post by BioCleaner on 2008-11-02
I know that but even a bad apeoximation is better then no aproximation.

---

