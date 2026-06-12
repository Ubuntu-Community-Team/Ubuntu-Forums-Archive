---
title: "No /var/log/messages file in ubuntu"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by uutkarshsingh on 2013-04-13
Hello freinds i just got started with linux(ubuntu).. I was goig through the book "no starch press" for learning command line argument... I couls not find th efile "/var/log/messages" as is mentioned in some of the the  chapters .. I wonder why i could not find this.. Can someone tell me where is the equivalent file in ubuntu ? Thanks

---

### Post by ajgreeny on 2013-04-13
It is disabled in ubuntu since a long time ago, I think, but can be re-enabled if you want by editing /etc/rsyslog.d/50-default.conf as root, and removing the comment mark (#) at the start of the line that says ```
#    mail,news.none        -/var/log/messages
```

---

### Post by Doug S on 2013-04-13
I observe these two files instead of the now nonexistent messages file:
/var/log/syslog (by default rotates daily)
/var/log/kern.log
But do a general look around in /var/log and its subdirectories.

---

