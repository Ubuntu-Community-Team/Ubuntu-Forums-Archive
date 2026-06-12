---
title: "[SOLVED] Problems  With Getting MySQL off the Ground"
date: 2008-09-03
forum: Packaging and Compiling Programs
---

### Post by salambo on 2008-09-03
I am running 8.0.4 LTS desktop version and would like to do some MySQL development in my language of choice: C.

I have gotten the C environment through "apt-get install build-essential" then I got mysql through "apt-get install mysql-server".

I used the "-I/var/lib/mysql/mysql/mysql-dfsg-5.0-5.0.51a/include" option when I compiled a test program that has "#include <mysql.h>" statement. The error that I get is "/var/lib/mysql/mysql/mysql-dfsg-5.0-5.0.51a/include/mysql.h:71:27: error: mysql_version.h: No such file or directory"

I did a "find / -name mysql_version.h" and sure enough, it is not on my system.

I know that I am probably missing something basic. I even did the following thinking that it might help:

apt-get remove mysql-server
apt-get source mysql-server

Same problem - same outcome. I appreciate your help.

---

