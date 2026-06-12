---
title: "Run to run mysql server"
date: 2007-06-12
forum: Programming Talk
---

### Post by yinglcs2 on 2007-06-12
Hi,

i have install mysql server from the package manager.
Can you please tell me how can i run mysql server from command prompt?
And what is the default username and password for that mysql server?

Thank you.

---

### Post by sithu on 2007-06-12
Well, follow me.
1.  go accessories->terminal.
2.  In command promt, you will see like this; yourname@yourdesktopname$.
3.  use su command. you will see password promt.type your root userpassword.
4.  if your password correct, you'll see like this; root@yourdesktopname#.
5.  you need to type, /etc/init.d/mysql start.
6.  When mysql server started, type mysql -u root mysql
7.  you'll see mysql promt. type set password for root@localhost=password('yourpassword');
     don't forget ";". this is really important.
8.  you'll see "query blah..blah...(0.08sec)blah...blah"
9.  then type \q
10. type exit
11. then you'll see "yourname@yourdesktopname$" again.
12. type mysql -u root -p
13. if you see password promt, you can use mysql.
if you need for more information, pls mail to [email]gnuauhtis@gmail.com[/email].
enjoy!;)

---

### Post by frolle on 2007-06-13
When i type: mysql -u root mysql

I get this error: 

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Any ideas?

---

### Post by frolle on 2007-06-13
I found the username and password in the debian config file.

---

### Post by ssam on 2007-06-13
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) has instructions for setting up MySQL

---

### Post by Westerberg on 2007-06-14
> Well, follow me.
1. go accessories->terminal.
2. In command promt, you will see like this; yourname@yourdesktopname$.
3. use su command. you will see password promt.type your root userpassword.
4. if your password correct, you'll see like this; root@yourdesktopname#.
5. you need to type, /etc/init.d/mysql start.
6. When mysql server started, type mysql -u root mysql
7. you'll see mysql promt. type set password for root@localhost=password('yourpassword');
don't forget ";". this is really important.
8. you'll see "query blah..blah...(0.08sec)blah...blah"
9. then type \q
10. type exit
11. then you'll see "yourname@yourdesktopname$" again.
12. type mysql -u root -p
13. if you see password promt, you can use mysql.
if you need for more information, pls mail to [email]gnuauhtis@gmail.com[/email].
enjoy!
This worked perfectly for me.  Thanks a million.

---

### Post by Dlambert on 2011-03-01
Thanks a bunch.

---

### Post by SACHINVD on 2011-07-14
> **frolle said:**
> When i type: mysql -u root mysql

I get this error: 

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Any ideas?

HI 
I am getting same error, How have you solve above error ?
Thanks

---

### Post by karlson on 2011-07-14
> **SACHINVD said:**
> HI 
I am getting same error, How have you solve above error ?
Thanks

```

mysql -u root -p mysql

```

---

### Post by lisati on 2011-07-15
With a four year gap between posts, it is possible that things have moved on and that the best advice has changed.
Thread closed.

---

