---
title: "Packet loss monitoring"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by wardave on 2012-02-17
I'm new to linux and was wondering for a easy way to monitor packet loss with ubuntu. My network connection gets packet loss at certain times of the day and sometimes I'm here when it happens but most of the time not. What I was needing is some way to continuously monitor and have it write to a log so I can have something to show my isp.

I have tried to do some research but the only program I found was sniffit but I wasn't able to find a good overview on it and I can't seem to understand the man page for it.

Any ideas?

I have also tried sniffit  -t 8.8.8.8 -x | grep output.txt and it didn't seem to work

---

### Post by wardave on 2012-02-18
Well I got it to run but it doesn't seem to log anything. I even tried running it with out the | grep output.txt to see if it would display anything for me and nothing.

---

### Post by wardave on 2012-02-18
No ideas uh?

---

### Post by Gone fishing on 2012-02-19
I was thinking maybe ntop but I think this link will do what you want

[http://www.cyberciti.biz/tips/simple-linux-and-unix-system-monitoring-with-ping-command-and-scripts.html](http://www.cyberciti.biz/tips/simple-linux-and-unix-system-monitoring-with-ping-command-and-scripts.html)

---

### Post by wardave on 2012-02-21
Thanks, will give it run to see how it goes =)

---

