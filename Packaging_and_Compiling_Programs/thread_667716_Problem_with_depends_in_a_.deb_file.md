---
title: "Problem with depends in a .deb file"
date: 2008-01-14
forum: Packaging and Compiling Programs
---

### Post by KDB9000 on 2008-01-14
I was trying to install moodle using the ubuntu package, but I ran into a problem. I think I have tracked it down but I need some help on how to fix it. In the control file I have this (not going to list everything):

Depends: debconfig (>=0.5) | debconfig-2.0, libapache2-mod-php5 | php5-cgi, php5-pgsql | php5-mysql, php5-gd...
Recommends: postgresql | mysql-server
Suggests: php5-ldap

The problem is when I pick MySQL as the database, it doesn't load the php5-mysql, just the pgsql. I know that is because of the pipe ( | ) but I need to make it so if I want to install MySQL that it will install the PHP5-mysql with mysql-server. Same thing with the client. Is there a way to do this or am I SOL?

---

### Post by KDB9000 on 2008-01-17
Bump?

Anyone?

---

