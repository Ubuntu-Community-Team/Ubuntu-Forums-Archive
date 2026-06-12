---
title: "Computer boots to different OS after lock."
date: 2014-07-24
forum: New to Ubuntu
---

### Post by sram180990 on 2014-07-24
Hello Guys,
I have a problem from last 10 - 15 days that when ever I keep my PC in Locked while downloading so that no wne should interrupt it. 
Why does it restarts and boots to another OS of Other HDD.
Why this problem is happening.
Suggest me some solution to avoid the problem

---

### Post by Bucky Ball on 2014-07-24
I can't help you with this, but to improve your chances I have changed your thread title to something that describes your problem. Please use descriptive thread titles in future to increase your chances of support. After all, 99% of people here need 'help' so best to tell us what you want help with in your thread title.

Good luck. ;)

---

### Post by sram180990 on 2014-07-24
ok buddy

---

### Post by grahammechanical on 2014-07-24
What version of Ubuntu are you using? What is the other OS on the other hard disk? Which hard disk has boot priority? In Ubuntu we can lock the desktop which will require the putting in of our password to unlock the desktop but unlocking Ubuntu does not restart the computer. It only gives us access to the desktop.

Sometimes an update/upgrade will require a restart of the machine. This usually the case if we have received a new Linux kernel. The Grub configuration files are re-written and a re-start is needed to load into the new Linux kernel. If the hard disk with Ubuntu on it has boot priority then a restart will give us a Grub boot menu with options to load either OS but Ubuntu will be at the top of the list and Ubuntu will load after a time delay. 

What are you downloading that requires a restart? Please check the boot priority of the hard drives. If the hard disk with the other OS has boot priority then a restart will load into that OS. Is this other OS a Linux distribution? How are you loading into Ubuntu? Do you get a boot menu?

Regards.



Regards.

---

