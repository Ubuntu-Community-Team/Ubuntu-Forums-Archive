---
title: "Default MySQL password?"
date: 2006-12-05
forum: Programming Talk
---

### Post by Josh1 on 2006-12-05
Hi everyone,
I have just installed Apache+MySQL+PHP using the below steps:
[code]
http://ubuntuguide.org/wiki/Ubuntu_Edgy#Apache_HTTP_Server
[code]
Using PHP5 and the default installation as it says. Now, when I go to http://localhost/phpmyadmin/ it asks for a username and password, usually for a fresh install of *AMP it's username "root" and password "" (blank, until you change it).

So my question is, what's the default user/password or how do I change the password?

Cheers,
Josh

---

### Post by daniminas on 2006-12-05
```
mysqladmin -u root password yournew
```

---

### Post by Josh1 on 2006-12-05
> **daniminas said:**
> ```
mysqladmin -u root password yournew
```

josh@josh:~$ mysqladmin -u root password yournew
bash: mysqladmin: command not found

---

### Post by Ramses de Norre on 2006-12-05
```
$ mysql -u root 
set password for root@localhost = password('xxxxxxx'); 
flush privileges; 
quit; 
```
And fill in the password instead of the xxx.

---

