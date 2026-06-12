---
title: "Suspend isn't working"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by Noah_Williams on 2014-03-18
I installed Ubuntu on my laptop last week, so I'm still very new to it. So far I love it, but the 'suspend' command doesn't work. I've looked all over this forum and tried everything, but nothing works. I have tried the 'sudo pm-suspend' command on the terminal, and for a while that worked, but today that stopped working too. I'm using a fairly old Toshiba Satellite, so maybe that has something to do with it? I'm really at a loss...

Thanks!

---

### Post by 7sbaV8Kt5PTh on 2014-03-19
Do you see any errors in /var/log/syslog after you issue the command?  Perhaps looking at the three scripts in /etc/pm/ could give a clue as to what it is doing...

---

