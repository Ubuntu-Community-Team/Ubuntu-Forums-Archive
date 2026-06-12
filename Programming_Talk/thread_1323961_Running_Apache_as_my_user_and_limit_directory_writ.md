---
title: "Running Apache as my user and limit directory write access"
date: 2009-11-12
forum: Programming Talk
---

### Post by raffaele181188 on 2009-11-12
Hello folks. I am developing a small website in PHP. By now, I always run Apache as user/group "apache", then put my user inside group "apache" and give my site directories group ownership to group "apache" and write permission to that group. This works just fine, but leads to some practical problems, like chgrp/chmod, or other dirty things like umask and default group. I'd like to get rid of this method, so I just want to use an httpd.conf in my home and launching an httpd process as my user, so it has normal write-access to all files and directories in my home. The problem is, to avoid disasters by my PHP script (like deleting all files in my "Documents" directory) I'd like to limit Apache/PHP write access to certain directory (eg ~/www/site1) either via httpd.conf or php.ini

How can I accomplish that?:p

---

### Post by raffaele181188 on 2009-11-13
up :)

---

