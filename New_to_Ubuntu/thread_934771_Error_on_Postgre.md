---
title: "Error on Postgre"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by rybaxs on 2008-09-30
```

psql: could not connect to server: No such file or directory
	Is the server running locally and accepting
	connections on Unix domain socket "/var/run/postgresql/.s.PGSQL.5432"?

```

Help me please! I've install and reinstall Postgre in my system but the error always occur.

---

### Post by rybaxs on 2008-10-01
```

user@user-desktop:/$ sudo /etc/init.d/postgresql-8.2 start
 * Starting PostgreSQL 8.2 database server                                                                                                                                           * The PostgreSQL server failed to start. Please check the log output:
2008-10-01 12:43:02 PHT FATAL:  unsafe permissions on private key file "server.key"
2008-10-01 12:43:02 PHT DETAIL:  File must be owned by the database user or root, must have no write permission for "group", and must have no permissions for "other".
                                                                                                                                                                             [fail]
user@user-desktop:/$ 



```

---

