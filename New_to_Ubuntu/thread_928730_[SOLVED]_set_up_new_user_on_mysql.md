---
title: "[SOLVED] set up new user on mysql"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by yorkie107 on 2008-09-24
Hi I'm trying to set up a new user in mysql for typo3 but I keep getting this error message. 

mark@mark-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 12
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> grant all privileges on Typo3.* to New-username@localhost identified by 'typo3';
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '-username@localhost identified by 'typo3'' at line 1
mysql> 

Thanks yorkie107

---

### Post by ianhaycox on 2008-09-24
Enclose New-username in quotes, e.g.

```
grant all privileges on Typo3.* to 'New-username'@localhost identified by 'typo3';
```

---

