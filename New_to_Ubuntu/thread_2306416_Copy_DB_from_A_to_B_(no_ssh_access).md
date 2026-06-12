---
title: "Copy DB from A to B (no ssh access)"
date: 2015-12-15
forum: New to Ubuntu
---

### Post by rafael38 on 2015-12-15
Hello,

I am new to the Ubuntu world. The following circumstances bring me here:


[LIST=1]
[*]We have a client server A (limited access) where we only have mysql and web access. Thus we can access the database and see the application via browser. No acces via ssh.
[*]We set up a new server B (full access) where we want to copy the database from A automatically every night.
[/LIST]

Is this possible with no ssh access in the source server? How?

Thanks

---

### Post by Tadaen_Sylvermane on 2015-12-15
No. You will need either ssh or physical access to do something like that. It would only take a simple script to run every night but putting the script in place can't be done from mysql and the application in the browser.

---

### Post by SeijiSensei on 2015-12-15
It is possible to run mysqldump against a remote server, but only if your client can see port 3306 on the server.  In general leaving the MySQL port open to the world is a very bad idea for security reasons, but you can try pointing a local mysql client at the server like this:
```
mysql -h ip.addr.of.server -u username -ppassword dbname
```
Note there cannot be a space between -p and the password if there is one.

If that works (which I'll reiterate is a sizeable security hole), then you could run mysqldump with the same parameters to create a plain-text backup.  You'd need to write a script on the backup host to run mysqldump then delete and recreate the database with the updated information each night.

---

### Post by ian-weisser on 2015-12-15
To me, ssh seems the most secure and maintainable tool for this job.
There are lots of other ways, of varying degrees of security and hackiness.
How much time do you want to spend teaching people how to diagnose and fix it when it breaks?

---

### Post by SeijiSensei on 2015-12-16
Well, he can't use SSH if his provider doesn't offer that as an option.  I'd move to a different provider, but he may not have that flexibility.

---

