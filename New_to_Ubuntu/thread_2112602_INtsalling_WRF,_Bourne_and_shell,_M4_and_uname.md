---
title: "INtsalling WRF, Bourne and shell, M4 and uname"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by astriedinger on 2013-02-05
Hello guys, I am installing a software in my ubuntu 12.04 LTS and the software requires me to fIrst have the following utilities:
csh, bource and shell, make, M4, sed, awk, uname.

I am only missing so far the M4, bourne and shell (I dont get this one), and the uname utility.

CAN you please tell me how to install them or to check if I have them, I havent been able to..

KInd regards,

---

### Post by The Cog on 2013-02-05
I think this command should install all you need:
```
sudo apt-get install build-essential
```
uname should already be installed by default anyway
I am guessing that "Bourne and shell" means bash, which is the normal command interpreter and is installed by default.
Oh, and M4 is actually lower-case m4.

---

