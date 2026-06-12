---
title: "[SOLVED] Problem with update manager."
date: 2008-10-03
forum: New to Ubuntu
---

### Post by KiwiNeil on 2008-10-03
[HTML]Hi
I'm new to Ubuntu or any form of Linux

Ubuntu 8.4
The following error occured when I try to run the update manager option and reads as below.

An error occured

E: dpkg was interupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _ cache ->open() failed, please report...

Anyone know how to go about fixing this?[/HTML]

---

### Post by fooman on 2008-10-03
open a terminal window (applications > accessories > terminal) and type or copy/paste the following command into it:

```
sudo dpkg --configure -a
```

see if that helps.

---

### Post by perlluver on 2008-10-03
Please mark this as solved.

---

### Post by KiwiNeil on 2008-10-03
> **perlluver said:**
> Please mark this as solved.
Not sure if it is at this stage as the machine is on the other side of town. I will be trying the fix later today. 
Thanks

---

