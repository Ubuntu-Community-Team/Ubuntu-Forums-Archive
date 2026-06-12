---
title: "Problems installing updates."
date: 2008-10-29
forum: New to Ubuntu
---

### Post by jameswhite15 on 2008-10-29
When I try to install some updates I get the following error message.

Thx. :)

---

### Post by wizard10000 on 2008-10-29
So open a terminal window and run 

sudo dpkg --configure -a

Feed the terminal window a password when prompted.  All fixed  :)

---

### Post by Duck2006 on 2008-10-29
In the etrminal run,

sudo dpkg --configure -a

---

### Post by jameswhite15 on 2008-10-29
Thanks both of you, and out of interest what is the sudo bit for because I tried running it without and it said I need to be a super user or something.

---

### Post by Duck2006 on 2008-10-29
Use to to run commands as root.

---

