---
title: "mysql issue"
date: 2010-07-24
forum: Packaging and Compiling Programs
---

### Post by shahin on 2010-07-24
I started having some problems with mysql after upgrading to lucid.  After some searching, I found a fix which is as follows:
```
sudo mkdir /var/run/mysqld/
sudo touch /var/run/mysqld/mysqld.sock
sudo chown mysql /var/run/mysqld/
sudo chown mysql /var/run/mysqld/mysqld.sock
sudo mysqld
```
Now I have to do this every time I reboot in order to get the functionality that I want.  Is there a way to automate this please?

---

