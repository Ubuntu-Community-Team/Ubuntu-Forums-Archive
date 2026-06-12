---
title: "Installing previous version of PHP and MySQL"
date: 2006-07-06
forum: Programming Talk
---

### Post by Peter Mount on 2006-07-06
Hi

I downloaded the Live CD version of Ubuntu 6.06. I'm thinking of downloading the Install CD for Ubuntu 6.06 if I've got time. I've already got the CDs for Ubuntu 5.10.

My web host uses php 4.3.11 and mysql 4.0.25-standard.

I've looked at this link: 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I don't think it explains how to install mysql 4.x. Is there a way I can install the versions of both php and mysql that I want? I don't mind if I install the latest version of Apache. I just want to match up my localhost install of php and mysql with the same versions of php and mysql that my web host has

Thanks

---

### Post by Appolusionist on 2006-07-08
> **Peter Mount said:**
> Hi

I downloaded the Live CD version of Ubuntu 6.06. I'm thinking of downloading the Install CD for Ubuntu 6.06 if I've got time. I've already got the CDs for Ubuntu 5.10.

My web host uses php 4.3.11 and mysql 4.0.25-standard.

I've looked at this link: 

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I don't think it explains how to install mysql 4.x. Is there a way I can install the versions of both php and mysql that I want? I don't mind if I install the latest version of Apache. I just want to match up my localhost install of php and mysql with the same versions of php and mysql that my web host has

Thanks

I took a quick look at that link and instead of using 

```
sudo apt-get install mysql-server
```

which will install mysql5 automatically. You will want to change that to...

```
sudo apt-get mysql-server-4.1
```

That will install MySql 4.1.15.

---

### Post by Peter Mount on 2006-07-09
Thanks for that Appolusionist

Your avatar looks great. Did you make that yourself?

Have a good day

---

### Post by ifokkema on 2006-07-09
> **Peter Mount said:**
> I downloaded the Live CD version of Ubuntu 6.06. I'm thinking of downloading the Install CD for Ubuntu 6.06 if I've got time.
The Live CD is also the Install CD. Did you notice the 'Install' icon on the Desktop?

> **Peter Mount said:**
> Is there a way I can install the versions of both php and mysql that I want? I don't mind if I install the latest version of Apache. I just want to match up my localhost install of php and mysql with the same versions of php and mysql that my web host has
If you do
```
apt-cache search mysql-server
```
you can see what versions of the mysql-server are available from your repositories. The same for PHP, but searching for 'php' or 'php scripting language' returns a lot of results :)

---

### Post by Peter Mount on 2006-07-09
Thanks ifokkema

I must have not noticed the "install" icon on the desktop. I'll install it later this week or on the weekend.

Have fun

---

