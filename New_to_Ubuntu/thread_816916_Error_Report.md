---
title: "Error Report"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by jason1308 on 2008-06-03
When I try to install updates or any other software, I keep getting the following message : 

E:dpkg was interrupted, you must manually run 'dpkg --configue _a' to correct problem.

E:-cache->open ()failed, please report


I am a noob so basic instructions would be helpful.

Thanks in advance

---

### Post by Joeb454 on 2008-06-03
Open a terminal from Applications > Accessories > Terminal

Then copy the following code in, and enter your password when asked (it won't show anything being entered - even though it is)

```
sudo dpkg --configure -a
```

---

### Post by th3pr1nc30f3gypt on 2009-01-04
im new to ubuntu, a n00b
ive been having  multiple problems
1. it won't stutdown/restart properly anymore
says error msgs
i have to push the power button til it goes off
2. i tried to setup an ad-hoc wireless thing to tether my iPhone connection
can't connect to it or any infastructure networks anymore
how do I reset the stupidthing?

---

### Post by stevepett on 2009-08-14
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

When trying to update.
When I run that, it stops the keyboard working (completely) and I have to do a hard reboot. sudo dpkg --configure -a has run, but it has no effect and the updates still have not been installed.

Steve

---

### Post by ck-b on 2010-11-10
Hi

---

