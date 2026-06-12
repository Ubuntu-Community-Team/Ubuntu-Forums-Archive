---
title: "apt-get install openssh-server not working"
date: 2015-10-17
forum: New to Ubuntu
---

### Post by richard140 on 2015-10-17
I just installed unbuntu 14.04. (My first time using Ubuntu.)  Networking is working.  I tried to follow the instructions on the following page to install sshd:
[https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

I ran the following as root:
# apt-get install openssh-server
...
Package openssh-server is not available, but is referred to by another package.
...

Is there some additional configuration for apt-get ??

---

### Post by shoaib2 on 2015-10-17
try it with sudo...

---

### Post by richard140 on 2015-10-17
Never mind.   After reading the apt-get man page I ran  'apt-get update'.  Then I tried apt-get install openssh-server and it worked.
/etc/init.d/ssh start    worked and I can now ssh to my new Ubuntu box.
(Now I need to figure out how to get sshd to start at boot time.)

---

### Post by richard140 on 2015-10-17
sshd starts at boot time now:

sudo update-rc.d ssh defaults

---

