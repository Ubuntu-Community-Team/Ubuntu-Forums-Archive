---
title: "postgres: pg_ctl problem"
date: 2011-05-16
forum: Programming Talk
---

### Post by Emsu on 2011-05-16
An old forum post said to run it in the following directory I looked for it in and it seems to exist:

michael@ubuntu:/usr/lib/postgresql/8.4/bin$ ls
clusterdb   dropdb    pg_controldata  pg_resetxlog  psql
createdb    droplang  pg_ctl          pg_restore    reindexdb
createlang  dropuser  pg_dump         postgres      vacuumdb
createuser  initdb    pg_dumpall      postmaster

But when I run it, I get the following:

michael@ubuntu:/usr/lib/postgresql/8.4/bin$ pg_ctl
pg_ctl: command not found

It wasn't working in Ubuntu 10 and isn't working in Ubuntu 11 either. Not sure what I'm doing wrong but every reinstall of postgres doesn't solve the problem and it seems like it's supposed to be something included in the standard postgres install.

---

### Post by SeijiSensei on 2011-05-16
If the program resides in the current directory, you need to run it by prefacing ./ like this "./pg_ctl".  Try that.  However you may need to run this with sudo or as the postgres user like this.

```

sudo su
[enter your password]
su postgres
/usr/lib/postgresql/8.4/bin/pg_ctl
exit

```

---

### Post by Emsu on 2011-05-16
Thanks! This worked for me. I was really confused.

---

