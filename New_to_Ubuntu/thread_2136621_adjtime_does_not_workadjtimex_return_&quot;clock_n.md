---
title: "adjtime does not work/adjtimex return &quot;clock not synchronized&quot;"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by t2hieu on 2013-04-18
Hi all,

Anyone know how to adjust the system time on ubuntu 12.04?

I try to use adjtime/adjtimex to adjust the system time but it does not work:
- adjtime run successful, but the system time does not change.
- adjtimex return "clock not synchronized".

Thank you so much

---

### Post by slickymaster on 2013-04-18
Here it is: [Ubuntu Time Management]("https://help.ubuntu.com/community/UbuntuTime#Ubuntu_Time_Management")

---

### Post by t2hieu on 2013-04-18
Hi all,

Anyone know how to adjust the system time on ubuntu 12.04?

I try to use adjtime/adjtimex to adjust the system time but it does not work:
- adjtime run successful, but the system time does not change.
- adjtimex return "clock not synchronized".

Thank you so much

---

### Post by schragge on 2013-04-18
Is using [ntpd](http://manpages.ubuntu.com/manpages/quantal/en/man8/ntpd.8.html) or at least either [ntpdate](http://manpages.ubuntu.com/manpages/quantal/en/man8/ntpdate.8.html) or [chrony](http://manpages.ubuntu.com/manpages/quantal/en/man1/chrony.1.html) an option?

---

### Post by Elfy on 2013-04-18
Threads merged

Please do not post duplicates, it dilutes community effort.

---

