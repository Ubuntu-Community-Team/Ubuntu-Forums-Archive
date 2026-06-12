---
title: "segmentation fault under ubuntu"
date: 2015-01-05
forum: New to Ubuntu
---

### Post by sulley2 on 2015-01-05
hi all
i have a project that i do under ubuntu 
the project is network monitoring using rrdtool and i have do alot include 
intsallation of that tool
configuration of that tool 
but when  ever i try to check varification of the configuration i get the error of
/usr/local/rrdtool-1.3.1/share/rrdtool/examples# ./stripes.pl
Segmentation fault (core dumped)
root@sulley-VPCEG26EC:/usr/local/rrdtool-1.3.1/share/rrdtool/examples# 
please help me what shall i do to solve that segmentation fault

my email <snip>

---

### Post by sulley2 on 2015-01-05
please help me the solution for segmentation fault
how to solve it

---

### Post by s.fox on 2015-01-05
Hello, to protect you from email spam I have removed your email address from the thread.

---

### Post by lisati on 2015-01-05
*Thread moved to **New to Ubuntu**.*

---

### Post by The Cog on 2015-01-05
How did you install rrdtools?
The version in the repository (for Ubuntu 14.10) is 1.4.8.
If you just installed something you found on the internet somewhere, can I suggest that you remove that and install the one from the repository instead. The stuff in the repositories should always be your first choice as these have been compiled specifically for that version of Ubuntu. This command will install the repository version:
```
sudo apt-get install rrdtool
```

---

