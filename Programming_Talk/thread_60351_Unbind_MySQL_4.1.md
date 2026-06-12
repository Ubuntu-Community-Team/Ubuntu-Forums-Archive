---
title: "Unbind MySQL 4.1"
date: 2005-08-27
forum: Programming Talk
---

### Post by phantomx on 2005-08-27
Sorry, I'm "cross-posting" [thread 60334](http://ubuntuforums.org/showthread.php?t=60334)
--------------------
Hi,
I installed MySQL 4.1.10a-Debian_2ubuntu0.1-log package and its running well, but it seems it's "binded" to localhost.

I connect to my work via a SSH port tunnel (ssh -L 13306:127.1:3306 ...), so when I try to connect to the remote MySQL server (on localhost:13306) my local MySQL server responds, hence I'm not allowed to connect the remote server. It doesn't matter which port I give (e.g: mysql -P 80) it always connects to my local server. ](*,)

I've checked /etc/mysql/my.cnf and it has commented the "bind" line, i.e:
#bind-address = 127.0.0.1

Any help will be appreciated.

---

