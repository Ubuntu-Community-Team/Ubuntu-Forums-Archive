---
title: "Using Django"
date: 2009-08-28
forum: Programming Talk
---

### Post by sumeshgupta on 2009-08-28
I have been reading about Django for web application development. There is a chapter on using database. In the django settings file there are certain changes to be done.

DATABASE_ENGINE = 'postgresql_psycopg2' (I have downloaded the suitable package)
DATABASE_NAME = 'mydb' (What should come here instead of mydb and how do I create a database?)

DATABASE_USER tells Django which username to use when connecting to
your database.(How do I configure database so that I can feed in some username in django settings file?)
DATABASE_PASSWORD tells Django which password to use when connecting
to your database (Same as username).

Whenever I try the command to connect to mydb it says authentication failed.](*,)
Any help will be highly appreciable please.

---

### Post by Copernicus1234 on 2009-08-28
1. Google on how to set up a postgres database and postgres user account.
2. Use that database name in DATABASE_NAME.
3. Use the database user in DATABASE_USER.
4. Use the database password in DATABASE_PASSWORD.

---

### Post by sumeshgupta on 2009-08-28
Thanks. I googled for the database and got my answers. I have an up and running db now.:)

---

