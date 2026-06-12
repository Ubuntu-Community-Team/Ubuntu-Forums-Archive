---
title: "Directory Permissions"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by DBrocks on 2008-04-28
Hey guys. I am running Ubuntu SE, with an FTP server. I was wondering, how do create a directory with permissions, so only one specific user, say "Joe" has Read/Write permissions, but nobody else can Read or Write to that folder? Thanks alot guys!

~Dan

---

### Post by OffAxis on 2008-04-28
generally you set the individual user up as a system user with a name/ password. You then create a folder for them; /home/joe/ and set the permissions with **chown**.

Next, you set the user up in the ftp program's .conf file.
What program are you using?

You could also try this:
[http://howtoforge.com/vsftpd_mysql_debian_etch](http://howtoforge.com/vsftpd_mysql_debian_etch)

---

### Post by bobplano on 2008-04-28
the command should be something like

```
chmod u=rw,go= directory
```

If you also need to change the user to Joe

```
sudo chown joe directory
```

---

### Post by DBrocks on 2008-04-28
> **OffAxis said:**
> generally you set the individual user up as a system user with a name/ password. You then create a folder for them; /home/joe/ and set the permissions with **chown**.

Next, you set the user up in the ftp program's .conf file.
What program are you using?

You could also try this:
[http://howtoforge.com/vsftpd_mysql_debian_etch](http://howtoforge.com/vsftpd_mysql_debian_etch)

proftpd

---

