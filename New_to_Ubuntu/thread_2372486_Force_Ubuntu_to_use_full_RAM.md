---
title: "Force Ubuntu to use full RAM"
date: 2017-09-25
forum: New to Ubuntu
---

### Post by snake_eyes on 2017-09-25
Hello,

I've installed Ubuntu 16.04 with apache2, php7, mariadb and phpmyadmin

I've moved my application and trying to execute a long procedure, when I check the RAM I got the below

```

              total        used        free      shared  buff/cache   available
Mem:          64134         663       62766          38         704       63298
Swap:          1021           0        1021

```

So, how do I force OS to use the full RAM which is 64GB?

Regards

---

### Post by Tadaen_Sylvermane on 2017-09-25
You don't. It will use more as needed, you can't force it to use more as far as I know.

---

### Post by QIII on 2017-09-25
Hello.

Your applications will consume only as much memory as they require for the tasks they are performing.  "Force feeding" them memory will do no good.

---

### Post by snake_eyes on 2017-09-26
Hi,

Thank you for all for sharing your information ... 

I understand that the server will be dynamic, and when execute the command will get the actual needed to perform the action of the apache?

If yes, how about the databases, I'm using the MariaDB 10 with InnoDB , it has different mechanism or will work with the same behavior of the OS and RAM Utilization?

Best Regards

---

### Post by Tadaen_Sylvermane on 2017-09-26
About the only way to force it to use all the ram is to put the database into  a ramdisk. That has plenty of risks, but could potentially speed things up exponentially. I do it with my Minecraft servers, but I don't know how one would use a ramdisk for a database, while making sure it is safely backed up to non-volatile storage. Replication is a way to do this I suppose.

Even with this you will only use as much ram as the size of the db.

---

### Post by SeijiSensei on 2017-09-26
Linux is very efficient at managing memory and will use whatever it needs.  There's nothing you need to tune.

I run servers with Apache, PostgreSQL, MySQL, BIND9, and sendmail on virtual machines with 2-4 GB.  Performance is never an issue.

---

### Post by HermanAB on 2017-09-28
As far as a RAMdisk is concerned, the tmpfs file system is a RAM disk.  So you can use that to speed up your database, IF you have a proper UPS.

---

