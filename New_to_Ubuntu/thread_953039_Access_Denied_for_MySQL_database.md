---
title: "Access Denied for MySQL database?"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by justinram22 on 2008-10-19
Ok, im 13 and am over my head i guess you could say, im trying to learn/create a website where people can submit data, and then have it post up on the website, which im pretty sure, if im understanding all the forums i have read, you need MySQL... anyway, it says that i do not have access, when i type this

> 
:`$mysql -p linksdb


I get

> 
ERROR 1045 (28000): Access denied for user 'justin'@'localhost' (using password: YES)


and then i read this form
[http://ubuntuforums.org/showthread.php?p=5858139](http://ubuntuforums.org/showthread.php?p=5858139)

and tried the following commands

> 

:`$mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g
Your MySQL connection id is 14
server version: 5.0.51a-3ubuntu5.1 (Ubuntu

Type 'help;' or '\h' for help.  Type '\c' to clear the buffer.

mysql>grant all privilages on *.* to justin@'localhost'
    ->identified by 'password' with grant option;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'privilages on *.* to justin@'localhost'
identified by 'password' with grant opti' at line 1



So i am totally confused as to what my problem is... any help would be greatly appreciated!

---

### Post by raptor2552 on 2008-10-19
I think you need quotes around the user name: grant all privilages on *.* to 'justin'@'localhost'

---

### Post by justinram22 on 2008-10-19
even with quotes around > 'justin'@'localhost' it has the exact same error......

---

### Post by raptor2552 on 2008-10-20
Try grant all on *.* to 'justin'@'localhost'

BTW privilages should be privileges... maybe where the syntax error is coming from

---

