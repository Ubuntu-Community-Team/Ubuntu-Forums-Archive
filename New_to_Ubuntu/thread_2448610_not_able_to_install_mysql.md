---
title: "not able to install mysql"
date: 2020-08-10
forum: New to Ubuntu
---

### Post by samsoor on 2020-08-10
hello everyone, 
can someone tell me how to get rid of this error

 ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-8.0 (8.0.21-0ubuntu0.20.04.4) ...
Failed to stop mysql.service: Unit mysql.service not loaded.
invoke-rc.d: initscript mysql, action "stop" failed.
update-alternatives: error: alternative path /etc/mysql/mysql.cnf doesn't exist
dpkg: error processing package mysql-server-8.0 (--configure):
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 mysql-server-8.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


i get the error after running the following comand ```
sudo apt-get install --fix-broken
```

---

### Post by TheFu on 2020-08-10
Instead of using mysql, have you considered using mariadb?  All the other stuff you know from mysql works the same with mariadb. All the clients are the same.

---

### Post by ActionParsnip on 2020-08-11
What is the output of
```

apt-cache policy mysql-server-8.0

```
Thanks

Is this an upgrade to SQL or a new install?

---

### Post by SeijiSensei on 2020-08-11
```

Failed to stop mysql.service: Unit mysql.service not loaded.
invoke-rc.d: initscript mysql, action "stop" failed.

```

What version of Ubuntu is this? Ubuntu hasn't used the rc.d type of start/stop scripts for a few versions now. Modern Ubuntu uses systemd.

You could see if you can stop MySQL manually before installation with
```
sudo service mysql stop
```
if you're on a version that doesn't use systemd.

On modern systems, try 
```
sudo systemctl stop mysql.service
```

---

### Post by TheFu on 2020-08-11
```
Setting up mysql-server-8.0 (8.0.21-0ubuntu0.20.04.4) ...
```
Looks like 20.04.  I had a problem like this a few weeks ago with a different package. I don't recall the fix, but is was something like creating an empty file somewhere.

---

