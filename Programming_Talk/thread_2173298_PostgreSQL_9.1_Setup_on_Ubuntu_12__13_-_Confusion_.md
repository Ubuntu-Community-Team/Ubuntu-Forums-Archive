---
title: "PostgreSQL 9.1 Setup on Ubuntu 12 / 13 - Confusion with PSQL run"
date: 2013-09-08
forum: Programming Talk
---

### Post by m.dr on 2013-09-08
[TABLE="width: 100%"]
[TR]
[TD]My questions are on PostgreSQL and PSQL on Ubuntu. Hope this is the right place. I will post it on General Questions as well.
...
I have installed PostgreSQL 9.1 on Ubuntu 13.04. 
I am a little confused on using PSQL.

I have DBMS background with Oracle / MySQL, so I am expecting psql shell to behave with some similarities - after initial setup.

1. On the Ubuntu doc it says after install to setup password for user: postgres:
Log in using: sudo -u postgres psql postgres --- I am able to log in.

2. Change password:
\password postgres -- I am able to change password, asks for new password twice and accepts.

...
3. Now I log out of the psql shell and expect I can directly run psql giving -d / -U options.
So I run: psql -d postgres -U postgres -W
Password for user postgres: -- Here I enter password I set up above
psql: FATAL: Peer authentication failed for user "postgres"

4. Also I had expected that if I just run psql I should get the psql command line like sqlplus or mysql.
But it does not. - Says psql does not exist.

...
5. So when I log in again using: sudo -u postgres psql postgres -- I run following commands:
postgres=# select version();
version 
------------------------------------------------------------------------------------------------------------
PostgreSQL 9.1.9 on x86_64-unknown-linux-gnu, compiled by gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3, 64-bit

postgres=# select current_user;
current_user 
--------------
postgres
(1 row)

postgres=# select current_database();
current_database 
------------------
postgres
(1 row)

postgres=# select inet_server_port(); -- SHOULD this not return a port number: 5432?
inet_server_port 
------------------
(1 row)

postgres=# select inet_server_addr(); -- SHOULD this not return 127.0.1.1?
inet_server_addr 
------------------
(1 row)

----------------------------------------------------------------------------
My confusion with 3, 4 is I am expecting to log in with psql and not use sudo to get to the psql shell.

Is there a setup aspect I am missing?

Also, as I mention in point 2, I set the password with \password.
It seems to completely ignore that.
It does as the password if I run: sudo -u postgres psql postgres -W
But logs in anyway if I run: sudo -u postgres psql postgres -- as well.

Please note I am able to create database, roles etc. grant them and such.

Put since I cannot run this command at bash: 
psql -d postgres -U postgres -W
psql -U postgres (or user created)

I cannot log in with those users.

What do I do to bypass sudo as the psql command using args -d / -U / -W is makes sense to me but this command:
sudo -u postgres psql postgres -- does not.


Thank you for your help.

Mono



[/TD]
[/TR]
[/TABLE]

---

