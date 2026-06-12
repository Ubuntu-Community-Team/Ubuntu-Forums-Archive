---
title: "Trouble Booting Up"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by seth-neal84 on 2014-04-21
When I turn on my computer it can sometimes take 3 or 4 tries to get it to actually boot up.  Other times the screen will turn purple like it is going to boot up but will take around an hour to actually bring me to the login screen.  I am not exactly sure what I can do to solve this problem.  Can anyone help me with this?

---

### Post by oldfred on 2014-04-22
You may have log file viewer?

I look at dmesg. And it shows timestamps. I look for outright errors, tasks repeating and then failing or eventually working, and long times between timestamps. It should be booting in less than a minute on most systems. 

If no log file viewer look in /var/log/dmesg

 sudo egrep -i &#8216;error|warning&#8217; /var/log/dmesg
gksudo gedit /var/log/dmesg

It is long, do not need to post entire thing, but if you get errors, warnings or long times post the few commands around each of those.

---

