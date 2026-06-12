---
title: "Can not acces cdrom"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by jamil_1 on 2008-07-31
I can not access my cdrom in ubuntu

---

### Post by cmnorton on 2008-07-31
We definitely need more information.

If you put a music or data CD in your drive do you get an icon on the screen?

Have you tried going to a command line (X-term) and issuing

sudo mount /dev/cdrom /media/cdrom

(Answer sudo with your logged in password, assuming you installed Ubuntu.)

Is your cdrom drive in the output of 

cat /proc/modules | grep cdrom

---

