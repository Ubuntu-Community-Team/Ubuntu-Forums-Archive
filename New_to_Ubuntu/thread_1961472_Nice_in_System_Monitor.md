---
title: "Nice in System Monitor"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by corncob on 2012-04-19
In System Monitor, Processing Tab, there is a column labled "Nice".  What does that mean?  The values are all zero except for pulseaudio (-11) and update-manager (10).

---

### Post by raja.genupula on 2012-04-19
Nice is appliction which deals with priortity of the application while running . we can use to chnage its priority . 

[http://manpages.ubuntu.com/manpages/jaunty/man2/nice.2.html](http://manpages.ubuntu.com/manpages/jaunty/man2/nice.2.html)

[http://www.cyberciti.biz/faq/howto-change-unix-linux-process-priority/](http://www.cyberciti.biz/faq/howto-change-unix-linux-process-priority/)

---

### Post by flurospar on 2012-04-19
Nice of a process is the priority of a process.

A process having:

0 nice has normal priority

nice < 0 has lower than normal priority

nice > 0 has higher than normal priority

A program called nice determines the nice(priority) of the process. You can run it this way:

nice `pidof <progname>`

or

nice <pid_of_program>

and renice changes the priority of a process:

renice -n <increment> `pidof <progname>`

or

renice -n <increment> <pid_of_program>

or

renice <nice> `pidof <progname>`

or

renice <nice> <pid_of_program>

---

### Post by The Cog on 2012-04-19
Niceness is given in terms of how nice it is to other users. That is, a low niceness is one that has proprity ove other users and takes away their CPU time. Thus pulseaudio has a very low niceness because it will take as much CPU as it wants, which is actually quite important for sound servers. On the other hand, update-manager has a high niceness and will only use CPU when normal users are not busy. 

So niceness is a measure of proprity, but backwards to my mind. High niceness is low priority.

---

### Post by corncob on 2012-04-19
Thanks everybody!  I was curious as to what this was.

---

### Post by for.i.am.root on 2012-04-19
> **flurospar said:**
> Nice of a process is the priority of a process.

A process having:

0 nice has normal priority

nice < 0 has lower than normal priority

nice > 0 has higher than normal priority

A program called nice determines the nice(priority) of the process. You can run it this way:


I thought the lower the number the higher the priority?

---

### Post by raja.genupula on 2012-04-20
> **for.i.am.root said:**
> I thought the lower the number the higher the priority?

See this it have better explanation 
[http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/](http://www.cyberciti.biz/faq/change-the-nice-value-of-a-process/)

---

