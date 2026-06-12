---
title: "Ubuntu 12.04 crash"
date: 2012-10-07
forum: New to Ubuntu
---

### Post by vivek40 on 2012-10-07
Hi I have a dual boot with win7 and ubuntu 12.04. Last night some UPS failure caused the system to crash without going through the entire shutdown process.When I rebooted Ubuntu it shows a dark screen with message like:-
dev/sda3 failed to unmount cleanly...
.....
..
sulogin:cannot open password database

and restarts all over...

I read :- [this link]("http://ubuntuforums.org/showthread.php?t=1917124") but dont understand how do I mount /etc from the live cd.

---

### Post by Gone fishing on 2012-10-07
I would start on the live cd and then repair using fsck have a look at this howto:

[http://swik.net/Ubuntu/Only+Ubuntu/How+to+Repair+a+corrupted+filesystem+in+Ubuntu/ctn8r](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Repair+a+corrupted+filesystem+in+Ubuntu/ctn8r)

---

