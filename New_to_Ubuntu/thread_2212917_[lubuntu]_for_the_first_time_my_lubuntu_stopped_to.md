---
title: "[lubuntu] for the first time my lubuntu stopped to work"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by d_borghi on 2014-03-23
Hi all,


5 minutes ago, my little lubuntu has totally stopped to work, when i was watching sopcast (video stream). 
I had to brutally turn off my notebook.
When i re-turn on the pc, lubuntu has started to work normally.
Now i would like to looking for causes of my problem?
In windows there is the event viewer, in lubuntu what are there?


tnx
d_borghi

---

### Post by kc1di on 2014-03-24
most of the event logs in ubuntu are found in the /var folder.

---

### Post by 7sbaV8Kt5PTh on 2014-03-24
d_borghi,

You might want to look at the last 200 lines of /var/log/syslog and see if you see any errors there.  There is also /var/log/kern.log if it is something very low level.

---

