---
title: "pgadmin3 restore fails"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by burtondav on 2013-05-22
Is it OK to ask a Postgres question here?

I'm trying to restore a db using pgAdmin3.  But, I'm getting the following:
[FONT=Lucida Grande]
pg_restore: [archiver (db)] connection to database "ndeavor_production" failed: FATAL:  password authentication failed for user "postgres"

I don't see any place to put in a password during the restore.

Thanks[/FONT]

---

### Post by SeijiSensei on 2013-05-23
I've never used pgadmin3, but I have restored PG databases from the command line many times using the psql client. Was the source created by running pg_dump?  

Usually the "postgres" user has no password, either at the OS level or the database level.  

Suppose the dump file is called mydatabase.dump.   I would follow these steps:

```

sudo su
[enter your password]
su postgres
cd
psql < /path/to/mydatabase.dump
exit
exit

```

If that does not work, try using "psql template1 < /path/to/mydatabase.dump".

I do use Microsoft Access as a GUI frontend from time to time after installing the ODBC driver for PostgreSQL in Windows.  That can be useful for importing large datasets in a spreadsheet or CSV/TSV formats.  Mostly I just run queries from the command line using psql.

---

### Post by burtondav on 2013-05-23
I used pgAdmin3 to backup the database.  I used the directory format.  Now, I'm trying to restore that same backup.  When I connect to the pg server, I use user=pgadmin and it has a password.  In the restore error log, there is this line [COLOR=#000000][FONT=Lucida Grande]--no-password.  I don't see any place in the restore screens to add a password.  There is a screen for 'security labels' but, I don't know what that's for.

I would really like to restore using pgAdmin3 and not the command line.

Thanks.[/FONT][/COLOR]

---

