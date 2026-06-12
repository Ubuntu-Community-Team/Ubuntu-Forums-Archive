---
title: "Mysql dump database from ubuntu to windows"
date: 2017-01-13
forum: New to Ubuntu
---

### Post by wagner3 on 2017-01-13
Hello guys.
I have a server that runs Ubuntu 14.04 with mysql. I'm trying to start a job that backups a specific mysql database.
The thing is, this database is very big (~20Gbs). 
I'm running this command to backup the database:

$ mysqldump -uuser -p databasename | gzip > outputfile.sql.gz

Is there any way that I can output the file direct to a windows machine on the same newtork? I don't want the file to be created on the ubuntu Server and then be transfered to another machine.

I don't have a lot of experience with Ubuntu, so I apologize if I said something that doesn't make sense.

Thank you!

---

### Post by geeksmith on 2017-01-13
You can mount a share from the windows machine to the Ubuntu machine and dump the backup directly there:
```
mount.cifs //{ip address}/{dir} /mnt/windowsbox --verbose -o "username=foo,password=bar"
mysqldump -uuser -p databasename | gzip > /mnt/windowsbox/outputfile.sql.gz
```

[http://manpages.ubuntu.com/manpages/precise/en/man8/smbmount.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/smbmount.8.html)

---

### Post by wagner3 on 2017-01-13
Geeksmith,

 Thank you so much! I'll try to do that and tell you how it worked. Thanks!

---

### Post by geeksmith on 2017-01-13
Glad to help! If this is the right solution, please use the "Thread Tools" menu at the top of the thread to mark this thread solved.

---

