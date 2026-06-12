---
title: "laptop-net not working"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by noorez on 2008-05-26
Hi, I'm trying to use the laptop-net package but i can't seem to get it working properly. Here is the result on the command line:

noorez@noorez-laptop:~$ sudo laptop_mode start
[sudo] password for noorez: 
Laptop mode enabled, active.
noorez@noorez-laptop:~$ sudo laptop_mode 
Laptop mode disabled, not active.
noorez@noorez-laptop:~$ 

can someone tell me why this is happening?

---

### Post by spiderbatdad on 2008-05-26
Normally you might start this program with sudo /etc/init.d/laptop-net/(some profile here) start
You should also have some scheme configured.
[http://www.swiss.ai.mit.edu/projects/omnibook/documentation/laptop-net.html](http://www.swiss.ai.mit.edu/projects/omnibook/documentation/laptop-net.html)

---

### Post by noorez on 2008-05-27
There is no directory /etc/init.d/laptop-net/ ... Also, I found under the man-page for laptop_mode that the service /etc/init.d/laptop-net needs to be running. How do I make sure that it is and also, how would I get it to run during boot-time.

---

