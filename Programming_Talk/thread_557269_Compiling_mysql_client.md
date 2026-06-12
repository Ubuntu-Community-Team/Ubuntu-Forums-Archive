---
title: "Compiling mysql client"
date: 2007-09-22
forum: Programming Talk
---

### Post by smj on 2007-09-22
Hi,
I've just installed ubuntu 7.04-server.
I have done apt-get install build-essential.
Now I am trying to compile a simple mysql client written in c.
I know I need to use some compiler flag to tell it where the mysql libraries are but I can't find them.
Any help?

Thanks

---

### Post by smj on 2007-09-22
I've figured it out. For people having the same problem:

apt-get install mysql-client (Not sure if this one is actually needed)
apt-get install libmysqlclient15-dev

then when compiling i use
gcc -I/usr/include/mysql/ -L/usr/lib/mysql/ -lmysqlclient

---

