---
title: "help me"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by bayarja on 2008-05-08
hi all. i have some problem. it's about install java on ubuntu


that error. please you give some advice me
bayarja@bayarja-desktop:~$ sudo apt-get install sun-java6-jdk sun-java6-plugin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by skip mcshwang on 2008-05-08
Do you have synaptic open?

---

### Post by hyper_ch on 2008-05-08
next time please use a descriptive thread title and not a generic "need help" one... as you may see, sort of 99.999% of the people posting on this forum ask for help.

---

### Post by sujoy on 2008-05-08
make sure, syanptic, add/remove programs, and update manager are closed before you try this command. you are getting this error since they all access the repository and only one is allowed access at a time

---

