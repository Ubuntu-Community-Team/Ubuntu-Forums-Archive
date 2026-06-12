---
title: "List users"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by rushinblue on 2008-07-10
What is the command to show the users set up on an Ubuntu Server?

Thanks

---

### Post by toolzen on 2008-07-10
You could get that info by doing:

# cat /etc/passwd

or

# lastlog

which will give you a list of every single user plus the last time they logged in (or "never logged in" if that user had not logged in ever).

---

### Post by Morpheun on 2008-07-10
Look at /etc/passwd

---

### Post by rushinblue on 2008-07-10
Thank you both very much.

---

### Post by joshdale on 2010-08-20
thank you :D

---

### Post by APSy on 2011-06-22
Thanks :)

---

### Post by jamesdouglas on 2011-08-27
# lastlog   <--- very nice command.  Thanks!

---

### Post by GonZo on 2012-02-10
> **jamesdouglas said:**
> # lastlog   <--- very nice command.  Thanks!

sure! very usefull

---

### Post by oldos2er on 2012-02-10
Back to sleepy sleep. Closed.

---

