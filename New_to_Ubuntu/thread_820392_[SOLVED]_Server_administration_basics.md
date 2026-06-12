---
title: "[SOLVED] Server administration basics"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by jflarm on 2008-06-06
Hi, all...

I am trying to monitor a server, and I don't know what should be a normal cpu load on a server.
Is there a manual or a webpage I could read about this?
I am using the command "vmstat" to see the user and system load in the system.

Thanks...

---

### Post by hyper_ch on 2008-06-06
My server has a load average of 0.2 on a AMD Athlon 64 X2 5600+ cpu.

I have around 30 webpages hosted there, teamspeak2 server, world of warcraft server and a DOD server running.

---

### Post by hyper_ch on 2008-06-06
basically on a single core everything below 1 is good, on a dualcore anything below 2 is good, on a quad core anything below 4 is good as server load.

---

### Post by jflarm on 2008-06-06
I am confused....

top - 07:35:05 up  7:22,  2 users,  load average: 0.58, 0.72, 0.71
Tasks: 195 total,   2 running, 193 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.4%us,  3.9%sy,  0.2%ni, 81.3%id,  1.6%wa,  0.3%hi,  0.3%si,  0.0%st

In this output of top, I see a load average...but in the command vmstat...

procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0  63028 226768 1037076    0    0    13    24  139  436 14  6 80  1

I see the US(user) and SY(system) and the ID(idle) time of the cpu. Does this reserves to the actual percentage time that the user and system use the cpu?
and also..what does this load average in the top commands refers to?

---

### Post by hyper_ch on 2008-06-06
the load average in top/htop is over a given time... the first one the last 10 secs, second one the last minute and third one the last 10 min - if I'm not mistaken.

No clue what vmstat shows. don't really even know what that is.

---

### Post by jflarm on 2008-06-06
Thank you anyway...I'll google this thing to learn more about the cpu load stuff...

---

### Post by rraj.be on 2008-06-06
Hope this help's you


```
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html")
```

---

### Post by jflarm on 2008-06-06
Actually, this page explains very well everything about CPU load...
thank you anyay..

[http://www.teamquest.com/resources/gunther/display/5/](http://www.teamquest.com/resources/gunther/display/5/)

---

