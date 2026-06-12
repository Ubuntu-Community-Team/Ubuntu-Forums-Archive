---
title: "Its urgent!! Psl help with this mysql!!!!!"
date: 2012-03-03
forum: Programming Talk
---

### Post by Drazer on 2012-03-03
Hey Guys 2moro is my Mysql Exam and Im not familiar with Ubuntu.....
My Queries are 
1) How To Start Mysql Like It shows "MySql>"
2) My sql service is Started but when I give command

root@drazer-GA-MA785GM-US2H:/home/drazer# service mysql start
start: Job is already running: mysql
root@drazer-GA-MA785GM-US2H:/home/drazer# mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
root@drazer-GA-MA785GM-US2H:/home/drazer# mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
root@drazer-GA-MA785GM-US2H:/home/drazer# 

How To solve This ...??? 
PLS HELP.....:(

---

### Post by Bodsda on 2012-03-03
... You'll need to use the correct password

Note that the MySQL root password may not be the same as your system root password

---

