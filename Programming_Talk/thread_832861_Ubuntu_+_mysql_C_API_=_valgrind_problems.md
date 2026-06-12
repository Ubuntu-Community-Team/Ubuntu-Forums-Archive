---
title: "Ubuntu + mysql C API = valgrind problems"
date: 2008-06-18
forum: Programming Talk
---

### Post by martel80 on 2008-06-18
Hi,
has anyone tried to valgrind a C/C++ program using libmysqlclient? I ran into some troubles lately but I don't know if it is just me being lame or software package containing a bug.
I hope I don't break the rules by posting links to mysql forum where I already reported the issue...
[http://forums.mysql.com/read.php?45,210994,214481#msg-214481](http://forums.mysql.com/read.php?45,210994,214481#msg-214481)
There are two posts, one for Ubuntu 7 32-bit and one for Ubuntu 8 64-bit. Both the systems give similar errors.

Can anyone confirm the issue? Where else should I report the issue (if it turns out to be an issue, not just me :) ).

---

### Post by Thrawn01 on 2008-08-28
I'm seeing the same problems with "5.0.51a-3ubuntu5.1", This usually indicates a mis-matched mysql.h to libmysqlclient.so. 

I have libmysqlclient15off, mysql-client-5.0 and libmysqlclient15-dev installed.

I'm running RHEL4 with the 4.1 client and I don't get these errors. I'll have to compile mysql from scratch and test, I just don't have time atm.

---

