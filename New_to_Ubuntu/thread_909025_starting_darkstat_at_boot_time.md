---
title: "starting darkstat at boot time"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Circus-Killer on 2008-09-03
i've just installed darkstat and i want it to start at boot.

to start darkstat, i use /etc/init.d/darkstat start
so how do i get that to run at boot?

---

### Post by mrhhug on 2011-05-09
Darkstat is automatically added to startup if you installed from the ubuntu repos.

if you installed it yourself you can add it to your rc folders in /etc/rc0.d through /etc/rc5.d you want to add something like darkstat to 2,3,4,5. There are readme files in each of these directories you just need to make a symlink and name properly. 

or you can go to system>preferences>startup applications

---

