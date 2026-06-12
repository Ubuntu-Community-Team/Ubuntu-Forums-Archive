---
title: "[SOLVED] update manager"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by 12tipp12 on 2008-10-09
Hi, my problem is this, having installed and updated ubuntu yesterday, i attempted to install Buddi finance manager, during the installation it seemed to be installing java 5.2(i think) and it soon became obvious that my pc had frozen, which resulted in me shutting it down by use of the off button, on restart i again had a look at the update manager, and during the search process i encountered this error


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now i really am a total newbie so im uncertain where to even begin trying to sort this issue other than posting it in this forum, any help/advice will be greatly appreciated and perhaps i should point out that i also have windows xp installed on the same very old pc, any further info needed i will be happy to supply, thanks for taking the time to read my post and thanks in advance for any help/advice offered.


Bill

---

### Post by drs305 on 2008-10-09
> **12tipp12 said:**
> Hi, my problem is this, having installed and updated ubuntu yesterday, i attempted to install Buddi finance manager, during the installation it seemed to be installing java 5.2(i think) and it soon became obvious that my pc had frozen, which resulted in me shutting it down by use of the off button, on restart i again had a look at the update manager, and during the search process i encountered this error


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Now i really am a total newbie so im uncertain where to even begin trying to sort this issue other than posting it in this forum, any help/advice will be greatly appreciated and perhaps i should point out that i also have windows xp installed on the same very old pc, any further info needed i will be happy to supply, thanks for taking the time to read my post and thanks in advance for any help/advice offered.


Bill

To correct the immediate problem, do what it asks. Open a terminal (Applications, Accessories,  Terminal) and run:
```
sudo dpkg --configure -a
```
It will ask for your password. You won't see it being entered but just type it and hit ENTER when you have.

Welcome to ubuntu!

---

### Post by 12tipp12 on 2008-10-09
Hello drs305, many thanks, yes that appears to have solved part of the problem, but the update manager informs me that i have 1 broken package and use the filter to locate it, dare i ask where and how.

Bill

---

### Post by drs305 on 2008-10-09
> **12tipp12 said:**
> Hello drs305, many thanks, yes that appears to have solved part of the problem, but the update manager informs me that i have 1 broken package and use the filter to locate it, dare i ask where and how.

Bill

We'll stick to gui for the moment.

From within synaptic (System, Administration, Synaptic Package Manager) on the left side select Custom filters. Above that should be a list including 'Broken'. Click on that and you should see the broken ones on the right. Select and then in the top menu 'Edit, Fix Broken Packages'.

---

### Post by 12tipp12 on 2008-10-09
Hello again drs305, followed your instructions, but the end result was no broken package, when the initial warning appeared about a broken package it also had the jave package ready for install which i did, is it possible that by doing so it righted the broken package issue. and i repeat, many thanks for your help.


Bill

---

### Post by drs305 on 2008-10-09
> **12tipp12 said:**
> Hello again drs305, followed your instructions, but the end result was no broken package, when the initial warning appeared about a broken package it also had the jave package ready for install which i did, is it possible that by doing so it righted the broken package issue. and i repeat, many thanks for your help.


Bill

Yes, that is certainly possible.

If everything seems to be working now would you please mark this thread solved (you can change it back to 'unsolved' if something changes). Marking it solved allows other readers to find solutions that work and also permits 'helpers' concentrate on threads and posters still needing a solution.

To mark a thread solved, go to the "Thread Tools" link to the top right of the first post. Click on the link and then mark it solved.

Welcome to the ubuntu forums.

---

### Post by 12tipp12 on 2008-10-09
Thanks a million drs305, your help is very much appreciated.

Sincerely
Bill

---

