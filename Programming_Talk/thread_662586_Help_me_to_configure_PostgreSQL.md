---
title: "Help me to configure PostgreSQL"
date: 2008-01-09
forum: Programming Talk
---

### Post by HuBaghdadi on 2008-01-09
Hi.
I have PostgreSQL8.2 installed on Ubuntu 7.10
I run the following commands:
```

sudo -u postgres psql
ALTER ROLE postgres WITH ENCRYPTED PASSWORD 'pgpassword';
\q
sudo -u postgres psql -d postgres < /usr/share/postgresql/8.2/contrib/adminpack.sql

```
Then, I tried to create a database:
createdb
But I got this error:
createdb: could not connect to database postgres: FATAL:  role "root" does not exist
What is going wrong (please note that I use hubaghdadi for logging into Ubuntu, not root username)?
Thanks.

---

### Post by pmasiar on 2008-01-09
Does Postgress have ubuntu-specific install instructions? Many projects do, see website.

If no luck, IRC to freenode and ask for help, every project under sun has a channel there.

OT: Just curious: you are really from Baghdad, as your nick suggests? :-)

---

### Post by HuBaghdadi on 2008-01-09
>>Just curious: you are really from Baghdad, as your nick suggests? 
No, I'm not. :)

---

### Post by x1a4 on 2008-01-09
Hi,

I find using **su** instead of **sudo** to be much better suited for administering PostgreSQL.

Try this:  ```
su - postgres
``` and administer your db as the 'postgres' user.

---

### Post by mlind on 2008-01-09
You can change to postgres user like
```

sudo su postgres

```
Then
```

psql -d postgres < /usr/share/postgresql/8.2/contrib/adminpack.sql

```

Here's how to create a new user and a new database if you need it later.
```

sudo su postgres
psql template1
*create user test password 'test'*
*create database test owner test*

```

to test the database and new user
```

psql -h localhost -U test

```

---

