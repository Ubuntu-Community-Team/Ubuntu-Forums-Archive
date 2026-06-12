---
title: "Problem with database connection"
date: 2018-06-25
forum: New to Ubuntu
---

### Post by miljov on 2018-06-25
I never used Ubuntu, and now I installed Ubuntu 18.04, and I have a problem with connection to Database.

When I want to open Local Instance, i get this: 
[B]
 Your connection attempt failed for user 'root' from your host to server at localhost:3306:[/B]**  Authentication plugin 'caching_sha2_password' cannot be loaded: /usr/lib/mysql/plugin/caching_sha2_password.so: cannot open shared object file: No such file or directory**
**Please:**
**1 Check that mysql is running on server localhost**
**2 Check that mysql is running on port 3306 (note: 3306 is the default, but this can be changed)**
**3 Check the root has rights to connect to localhost from your address (mysql rights define what clients can connect to the server and from which machines) **
[B]4 Make sure you are both providing a password if needed and using the correct password for localhost connecting from the host address you're connecting from

[/B]I thought i forgot password so i reinstalled everything, but it's not worth it, again the same error is displayed. I can access mysql in terminal...but not on workbench
Can someone tell me what should I do to make it work?**&#8203;**

---

### Post by SeijiSensei on 2018-06-25
Have you ever used MySQL before on another platform like Windows?
IHave you used a database program like MySQL, PostgreSQL, or MSSQL before?

I suggest you read this at least twice to get started:  [https://dev.mysql.com/doc/mysql-security-excerpt/5.7/en/default-privileges.html](https://dev.mysql.com/doc/mysql-security-excerpt/5.7/en/default-privileges.html)

---

