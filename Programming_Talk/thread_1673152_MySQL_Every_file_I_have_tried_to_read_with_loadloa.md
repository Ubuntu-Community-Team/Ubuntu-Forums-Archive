---
title: "MySQL: Every file I have tried to read with loadload_file() will only read /etc/hosts"
date: 2011-01-22
forum: Programming Talk
---

### Post by griffmcc on 2011-01-22
Every file I have tried to read with load_file() has failed except for  one, /etc/hosts.  However, I can't read any other files, for example, I  can't read /etc/fstab.  Note that /etc/hosts and /etc/fstab have the  same owner, group and permissions. 
 
```
griff@griff-ubuntu:~$ ls -l /etc/fstab
-rw-r--r-- 1 root root 756 2010-09-09 21:30 /etc/fstab

griff@griff-ubuntu:~$ ls -l /etc/hosts
-rw-r--r-- 1 root root 258 2010-09-09 21:34 /etc/hosts  
```I am using Ubuntu 10.04 LTS and MySQL 5.1.41-3ubuntu12.8. 
 
Here is my demonstration that I can use load_file to read /etc/hosts but  not /etc/fstab.  Notice I run mysql as root so there should be no  privilege or grant problems.  Does anyone have any idea what's going on? 
 
```
griff@griff-ubuntu:~$ mysql --user=root --password=XYZ craig 
Reading table information for completion of table and column names 
You can turn off this feature to get a quicker startup with -A 
 
Welcome to the MySQL monitor.  Commands end with ; or \g. 
Your MySQL connection id is 56 
Server version: 5.1.41-3ubuntu12.8 (Ubuntu) 
 
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement. 
 
mysql> select load_file('/etc/fstab'); 
+-------------------------+ 
| load_file('/etc/fstab') | 
+-------------------------+ 
| NULL                    | 
+-------------------------+ 
1 row in set (0.00 sec) 
 
mysql> select load_file('/etc/hosts'); 
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+ 
| load_file('/etc/hosts')                                                                                                                                                                                                                                               | 
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+ 
| 127.0.0.1    localhost 
127.0.1.1    griff-ubuntu 
 
# The following lines are desirable for IPv6 capable hosts 
::1     localhost ip6-localhost ip6-loopback 
fe00::0 ip6-localnet 
ff00::0 ip6-mcastprefix 
ff02::1 ip6-allnodes 
ff02::2 ip6-allrouters 
ff02::3 ip6-allhosts 
 | 
+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+ 
1 row in set (0.00 sec) 
```

---

