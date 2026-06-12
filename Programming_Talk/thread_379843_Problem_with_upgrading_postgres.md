---
title: "Problem with upgrading postgres"
date: 2007-03-08
forum: Programming Talk
---

### Post by lunarmelody on 2007-03-08
I'm trying to upgrade from postgres 7.4 to postgres 8.1.  I kept getting a non-compatibility error in synaptic.  I tried getting the package from the command line with apt-get, but keep getting this error:

Setting up postgresql-8.1 (8.1.8-0ubuntu6.10) ...
 * Starting PostgreSQL 8.1 database server                                       
 * pg_ctl: cannot be run as root
Please log in (using, e.g., "su") as the (unprivileged) user that will
own the server process.
Use of uninitialized value in concatenation (.) or string at /usr/bin/pg_ctlcluster line 295.
Error: could not exec  /usr/lib/postgresql/8.1/bin/pg_ctl start -D /var/lib/postgresql/8.1/main -l /var/log/postgresql/postgresql-8.1-main.log -s -o  -c config_file="/etc/postgresql/8.1/main/postgresql.conf"

Further experimentation with other commands showed that somehow the root account on my postgres got deleted:  "user 'root' does not exist".  

Does anyone have any idea how to fix this (short of uninstall/reinstall)?  Thanks!

---

