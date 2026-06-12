---
title: "starting with mysql"
date: 2008-04-14
forum: Programming Talk
---

### Post by MrGando on 2008-04-14
Hi guys, I installed mySQL I have worked a lot with postgre SQL but want to make a wordpress server, my problem is the followin , I connect to my ubuntu machine and get:

mrgando@Unicron:~$ mysql
ERROR 1045 (28000): Access denied for user 'mrgando'@'localhost' (using password: NO)

the I try:

mrgando@Unicron:~$ mysqladmin -u root password myPassword
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Could you guys help me a bit ? :), I really want to start a lot of stuff this year, and my own little blog for keeping update is just a small part of them 


Thanks for this forums.

---

### Post by tehwa on 2008-04-14
Hi mrgando,

enter:

```
mysql -u root -p
```
and enter your password when prompted (the myPassword you refer to in your post)

---

