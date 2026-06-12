---
title: "includes my commands in terminal launching time shell scripts"
date: 2013-01-04
forum: New to Ubuntu
---

### Post by richardjl on 2013-01-04
Hi:

I am very new to ubuntu. I remember there should a hidden shell script in which you can include your command which you need it to be executed during system start or terminal launched.

can anyone tell me which is the name of the shell ? Thanks!

---

### Post by Calinou on 2013-01-04
System start: /etc/rc.local

When opening a terminal: ~/.bashrc

You can edit the latter with any text editor as an unprivileged user. The former must be edited with sudo or gksudo (example: gksudo gedit /etc/rc.local).

---

### Post by Fahim Abdun-Nur on 2013-01-04
Terminal start is via bash rc [http://hacktux.com/bash/bashrc/bash_profile](http://hacktux.com/bash/bashrc/bash_profile)

---

### Post by richardjl on 2013-01-04
I tested. It works now. Thank you all very much.

---

