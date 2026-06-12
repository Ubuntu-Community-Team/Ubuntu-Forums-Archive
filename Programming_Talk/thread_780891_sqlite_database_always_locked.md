---
title: "sqlite database always locked"
date: 2008-05-03
forum: Programming Talk
---

### Post by Max Carey on 2008-05-03
Hi, I'm trying to create and update a sqlite (v3.5.8) database in a c++ program. I open the database using
```
sqlite3 *db;

sqlite3_open("database.db", &db);
```

But any time I try to access the database after the call to open, sqlite returns SQLITE_BUSY (database is locked). Doesn't matter if I'm writing to or simply reading from the database. Any ideas?

---

### Post by Max Carey on 2008-05-04
bump

---

### Post by Max Carey on 2008-05-04
anybody?

---

### Post by mssever on 2008-05-05
I'm no sqlite3 expert, but I do know that only one process can access the database at a time. Beyond that, I dunno.

---

### Post by j.daniel on 2008-10-22
I'm a newbie myself, but I got a "database locked" on a totally fresh (i.e. empty) database from the command line. I could not do anything, not even "create table t1 (c text);" After some googling I found a suggestion which helped me. My database-file was on a remote CFIS-mounted share, and when I did the same in my home directory (i.e. local file-system), everything worked like a charm.

Cheers!
/ Daniel

---

### Post by stevescripts on 2008-10-22
Do you get the same behavior when you try to open the database from the commandline?

Also, does the code on this page work for you?

[http://www.sqlite.org/quickstart.html](http://www.sqlite.org/quickstart.html)

Steve

---

### Post by davedavedave on 2009-02-10
I had the same problem. Installed rails and sqlite3 on a fedora core 9 box where my home dir is NFS mounted. Any rails command that used the database cause 'database is locked' error. running sqlite3 first time (from command line, no parameters), .databases command caused 'database is locked' error. Then I tried in a directory on a local partition, no problem. Went back to the NFS partition, tried :

sqlite3 test.db
SQLite version 3.5.9
Enter ".help" for instructions
sqlite> .databases
Error: database is locked

On one hand, it probably is smart to at least warn me that the db file is being created on a remote host. But the error or warning should give more of a hint about what is wrong.

Thanks.

---

### Post by ajackson on 2009-02-11
It's not something simple like write permissions is it? On the local partition you have full access (I assume), on the remote one you might only have read access.

---

### Post by wsams on 2009-02-25
I have the same problem. I'm also trying to work with an sqlite3 file on a cifs mount. If anyone knows if this is even possible, that would be awesome. Thanks.

---

### Post by kajsa on 2009-09-17
> **ajackson said:**
> It's not something simple like write permissions is it? On the local partition you have full access (I assume), on the remote one you might only have read access.

It's not something simple like write permissions, but you're close - it has to do with how file locking works (poorly) on NFS-mounted files. I believe this is less of an issue with version 4 of the NFS protocol, but we're using 3 at work, and have had to move our sqlite db files to local disk to work-around this. 

See Section III-b at [http://www.time-travellers.org/shane/papers/NFS_considered_harmful.html](http://www.time-travellers.org/shane/papers/NFS_considered_harmful.html) for some further details.

---

### Post by gnowk on 2010-02-05
The problem has been fixed in Samba 3.2.5 available with Jaunty.

An alternative workaround is to mount with the option "nobrl":
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/117730/comments/9](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/117730/comments/9)

---

