---
title: "MySQL++ install woes"
date: 2008-01-17
forum: Programming Talk
---

### Post by CaptainPatent on 2008-01-17
I'm using Xubuntu and ran a build-essential in order to install gcc,

I also (of course) installed MySQL using an apt-get update and then sudo apt-get install mysql-server.

Those are from the debian packages so I'm pretty sure it's the latest versions, but when I go to grab the latest code for MySQL++ it won't configure properly (and thus cannot be made)

The error I get is: 
checking for MySQL library directory... configure: error: Didn't find mysqlclient library in '/usr/lib64 /usr/lib /usr/lib64/mysql /usr/lib/mysql /usr/local/lib64 /usr/local/lib /usr/local/lib/mysql /usr/local/mysql/lib /usr/local/mysql/lib/mysql /opt/mysql/lib /opt/mysql/lib/mysql

I tried doing a apt-get install mysql-client, but after installing the server it says I already have one (don't know if that's actually correct)

I tried directing it to where (I think) the client is - var/lib/mysql/mysql - but once again I'm not too sure on that one, and because it didn't work, probably not.

Is there some inherent known problem with a debian or Ubuntu-based MySQL++ install? Am I doing anything wrong? If you need any information or have potential solutions, let me know!

---

### Post by geirha on 2008-01-17
You probably need to install libmysqlclient-dev. When you compile stuff, you generally need the packages ending with -dev of the dependencies.

---

### Post by CaptainPatent on 2008-01-17
That was it exactly! I think I had problems with that earlier (it's called libmysqlclient15-dev now and I missed that) so after an apt-get install libmysqlclient15-dev it configured and made perfectly!

Many thanks geirha!

---

