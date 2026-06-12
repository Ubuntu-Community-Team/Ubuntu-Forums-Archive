---
title: "different root"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by termvrl on 2012-11-10
Hi All,
what is different between sudo su - and sudo su,
i notice that will be diff, root@snort:/# & root@snort:~#

---

### Post by HiImTye on 2012-11-10
*sudo su -* logs you in using root's environment, where as *sudo su* logs you in using your environment (.bashrc, graphical settings for programs, etc)

---

### Post by termvrl on 2012-11-10
hi thanks.
is there any different? i mean, for e.g : when try to install something

---

### Post by HiImTye on 2012-11-10
the difference is if you just *sudo su* you might end up with permissions problems, which means that you need to switch to a tty and fix them before you can log in

---

### Post by mcduck on 2012-11-10
the recommended command to start a root session in Ubuntu is "*sudo -i*". It's the only one that correctly loads root's environment and behaves exactly as if you had logged in as root user.

---

