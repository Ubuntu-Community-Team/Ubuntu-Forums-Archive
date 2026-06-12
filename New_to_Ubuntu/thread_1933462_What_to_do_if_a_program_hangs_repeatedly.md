---
title: "What to do if a program hangs repeatedly?"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by arroy_0209 on 2012-02-29
I am using ubuntu10.04LTS and my problem is that today I am unable to read from the "system log file viewer". The icon is present at the bottom panel and generally every time I start ubuntu, I check the log files. Today I tried and the window opened (to check messages and auth logs) but it is blank, with status reported as "loading". However the logs are  visible with the command from terminal
```
cat /var/log/auth.log |more
```. Surprisingly the command ps -aux is showing that the command gnome-system-log is using 192% of CPU. (How can it be more than 100%?)

I restarted the machine and the result remained the same. What should I do? Should I kill the above process with kill -9? Any other suggestions?

---

### Post by UnknownFearNG on 2012-02-29
This seems to be an on-going bug in Ubuntu. Take a look here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/493811](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/493811)

---

