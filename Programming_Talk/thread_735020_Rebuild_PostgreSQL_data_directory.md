---
title: "Rebuild PostgreSQL data directory"
date: 2008-03-25
forum: Programming Talk
---

### Post by glitch13 on 2008-03-25
Still kinda new to the Ubuntu/Debian world, but I had a question.

My old distro was gentoo, and when you wanted to rebuild a new postgres data directory, there was a package manager command you could run that would re-initialize a package, the same as it does when you first install it.  Hence, for postgres, it would recreate the initial, empty data directory.

I can't seem to figure out how to do this in Ubuntu.  After removing the current data directory, I tried the more low level postgres commands to do it:


```

$ sudo su postgres
$ /usr/lib/postgresql/8.2/bin/initdb -D /var/lib/postgresql/8.2/main
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale en_US.UTF-8.
The default database encoding has accordingly been set to UTF8.

creating directory /var/lib/postgresql/8.2/main ... ok
creating subdirectories ... ok
selecting default max_connections ... 100
selecting default shared_buffers/max_fsm_pages ... 24MB/153600
creating configuration files ... ok
creating template1 database in /var/lib/postgresql/8.2/main/base/1 ... ok
initializing pg_authid ... ok
initializing dependencies ... ok
creating system views ... ok
loading system objects' descriptions ... ok
creating conversions ... ok
setting privileges on built-in objects ... ok
creating information schema ... ok
vacuuming database template1 ... ok
copying template1 to template0 ... ok
copying template1 to postgres ... ok

WARNING: enabling "trust" authentication for local connections
You can change this by editing pg_hba.conf or using the -A option the
next time you run initdb.

Success. You can now start the database server using:

    /usr/lib/postgresql/8.2/bin/postgres -D /var/lib/postgresql/8.2/main
or
    /usr/lib/postgresql/8.2/bin/pg_ctl -D /var/lib/postgresql/8.2/main -l logfile start

```

Which seemed to work, but I was greeted with this upon trying to start the daemon:

```

$ sudo /etc/init.d/postgresql-8.2 start
* Starting PostgreSQL 8.2 database server                                                                
* The PostgreSQL server failed to start. Please check the log output:
2008-03-24 18:46:11 CDT FATAL:  could not load server certificate file "server.crt": No such file or directory
                                                                                                                           [fail]

```


Is there a "proper" way to do this in ubuntu?

---

### Post by shahjapan on 2008-10-03
Hey 

I had a same problem,

I made ssl OFF on postgres.conf file

```

vim /etc/postgresql/8.2/main/postgresql.conf

```
and comment the following line.
```

#ssl = true                             # (change requires restart)

```

---

### Post by shahjapan on 2008-10-03
If you really wish to SSL On then you need to run the following command and create a new server.key file in your new data directory.

with the following steps.

[LIST=1]
[*]openssl req -new -text -out server.req
[*]openssl rsa -in privkey.pem -out server.key
[*]rm privkey.pem
[*]openssl req -x509 -in server.req -text -key server.key -out server.crt
[*]chmod og-rwx server.key
[*]chown postgres : postgres server.key
[/LIST]

reference:
[http://developer.postgresql.org/pgdocs/postgres/ssl-tcp.html]("http://developer.postgresql.org/pgdocs/postgres/ssl-tcp.html")

---

